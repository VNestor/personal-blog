---
title: Retrieving reviews using Google API
date: "2022-03-08"
description: A simple explanation on how I managed to retrieve reviews using Google API and the obstacles I encountered, using React.js.
---

## Prequel

When working on a website for a small business, I wanted to have a reviews section for their website I was building using React.js. At first, I thought all I had to do was sign up for Google Cloud, get an API key, then make an API request, and I'd be done. That was not the case. Getting reviews from Google can be much simpler if you're working with a CMS that have plugins readily available, like WordPress. This situation did not call for that, and I thought the task would be simple enough that I didn't need to install an npm package. So I thought I'd try to figure it on my own and quickly realized that was not the case.

## Getting Started

First, I needed to learn where I can get reviews from a small business that is on Google. I turned to the Google Places API because it is returns most information about a business that are registered with Google, including reviews. **Note: Google Places only provide the five most recent reviews, if you need more, you might want to look elsewhere**. In order to get retrieve data using the API you will need two things, an API key and the Place ID of the business you'd like to get reviews for.

## Getting an API Key

You will need to do the following to get an API key:

- Create a Google Cloud Account.
- Create a project.
- Enable billing. (_Google Cloud provides $300 in free credits but will need a card on file._)
- Enable the Places API.
- Go to the Credentials section on the Google Cloud dashboard, on the top of the screen you should see **+Create Credentials** and generate an API key.

That's it for generating an API key! This was a simple overview of the process. For a step by step process, click [here](https://developers.google.com/maps/documentation/places/web-service/cloud-setup).

## Understanding the Places API

We will be using the Places API with the following URL:

```js
https://maps.googleapis.com/maps/api/place/details/json?place_id=PLACE_ID&key=YOUR_API_KEY
```

This will return a very large JSON file, but don't worry because what we want is at the very end of it.
So we have our API key, now we need the Place ID. The Place ID is a unique ID that Google uses to identify a place in the Google Places database and on Google Maps. The URL above requires the place ID of the business you would like to retrieve reviews from.

### Option 1

Fortunately, Google has a web service that will easily retrieve the ID for you, you can find that [here](https://developers.google.com/maps/documentation/places/web-service/place-id). Sometimses the web service is down so there is another option.

### Option 2

You can also retrieve the Place ID on Google Chrome by searching for the business on Google, ensure that the business appears on the right hand right, and right clicking, selecting _inspect_, and searching for "data-pid". It is a string of random numbers and characters and should look something like this:

```js
data-pid="PLACE_ID"
```

Great! Now you have the Place ID and your API key, let's start making GET requests!

## Making the API Call

As I mentioned earlier, I will be using React.js to make the GET request, so we will be using _React Hooks_ and _fetch_. Below is a simple version of how I fetched the data from the Places API in my Reviews component. I will not get into detail about what each part of my code does. **This is for educational purposes only, if you are going to deploy an application using API Keys, make sure they are hidden.** If you are learning React, and not familiar with Hooks, check out React's [intro to hooks](https://reactjs.org/docs/hooks-intro.html).

```js

...

const Reviews = () => {
  const [isLoading, setIsLoading] = useState(true);
  const [data, setData] = useState([]);

  useEffect(() => {
    getReviews();
  }, []);

  const getReviews = () => {
    fetch("https://maps.googleapis.com/maps/api/place/details/json?place_id=PLACE_ID&key=YOUR_API_KEY")
      .then((res) => res.json())
      .then((response) => {
        setData(response.result);
        setIsLoading(false);
      })
      .catch((error) => console.log("An Error Occured: " + error));
  };

  return (
    ...
  );
};

export default Reviews;
```

What I want to focus on is what happens when this fetch request is made. Take a look at your console (make sure you're using console.log(), and you run into an error. If you make fetch requests often you've probably seen this before:

```js
No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'http://localhost:3000' is therefore not allowed access.
```

## Why Don't We Have access To This data?

You might be thinking to yourself, I have an API key, why isn't my code working? And the answer is, it is! If you take the same URL, with the parameters filled in, and use something like [Postman](https://www.postman.com/), you will get a JSON response back. Without getting too into it, the reason it is working with Postman and not your code is because of Cross-Origin Resource Sharing, better known as [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS). CORS is a server-side configuration which clients, like your browser, choose to enforce and other developments tools, like Postman, choose to not enforce.

## Getting Access To The Data On Our Browser

When looking online for a solution, all I found was "add a an HTTP header to the server: Access-Control-Allow-Origin: \*" and you'd be done. Because we want to access data from Google's servers, we can't add an HTTP header since it is not our server. Also adding the request headers to our fetch function will not work either because Google's server does not allow certain methods to be called without authorization.

### The Solution, Kind Of

So how do we get the response we were expecting? We use a CORS proxy! A CORS proxy will add the neccesary CORS headers to the proxied request. The proxy we will be using is [CORS Anywhere](https://github.com/Rob--W/cors-anywhere/). Keep in mind, we will be making our own CORS proxy, so make sure you have [git](https://git-scm.com/) and [heroku cli](https://devcenter.heroku.com/articles/heroku-cli_) installed. Once installed follow these intructions:

```js
git clone https://github.com/Rob--W/cors-anywhere.git
cd cors-anywhere/
npm install
heroku create
git push heroku master
```

Once done, your new heroku project will be running and you will be using the url it is being hosted on.
It should look like this:

_This is only an example, do not use this URL. Use your own._

```js
https://cryptic-headland-94862.herokuapp.com/
```

You will need this URL to be appended to the request URL, and then making the GET request on that new URL.
It will looks like this:

```js
https://cryptic-headland-94862.herokuapp.com/https://maps.googleapis.com/maps/api/place/details/json?place_id=PLACE_ID&key=YOUR_API_KEY
```

This doesn't look great, but we can always seperate them and append them later.

The final result should look something like this:

```js

...

const CORS_PROXY_URL = "https://cryptic-headland-94862.herokuapp.com/"
const GOOGLE_URL = "https://maps.googleapis.com/maps/api/place/details/json?place_id=PLACE_ID&key=YOUR_API_KEY";

const Reviews = () => {
  const [isLoading, setIsLoading] = useState(true);
  const [data, setData] = useState([]);

  useEffect(() => {
    getReviews();
  }, []);

  const getReviews = () => {
    fetch(CORS_PROXY_URL + GOOGLE_URL)
      .then((res) => res.json())
      .then((response) => {
        setData(response.result);
        setIsLoading(false);
      })
      .catch((error) => console.log("An Error Occured: " + error));
  };

  return (
    ...
  );
};

export default Reviews;
```

##

- You can find the Place ID for a business [here](https://developers.google.com/maps/documentation/places/web-service/place-id).
- There is a great guide on how to host your own CORS proxy [here](https://stackoverflow.com/questions/43871637/no-access-control-allow-origin-header-is-present-on-the-requested-resource-whe/43881141#43881141).
