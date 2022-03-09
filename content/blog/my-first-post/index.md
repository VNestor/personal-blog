---
title: Retreiving reviews using Google API.
date: "2022-03-08"
description: A simple explanation on how I managed to retrieve reviews using Google API and the obstacles I encountered.
---

## Prequel

When working on [Fruces'](https://www.fruces.com/) website, I wanted to have a reviews section for their website. At first, I thought all I had to do was sign up for Google Cloud, get an API key, then make an API request, and I'd be done. That was not the case. Getting reviews from Google can be much simpler if you're working with a CMS that have plugins readily available, like WordPress. This situation did not call for that, and I thought the task would be simple enough that I didn't need to install an npm package. So I thought I'd try to figure it on my own and quickly realized that was not the case.

## Getting Started

First, I needed to learn where I can get reviews from a small business that is on Google. I turned to the Google Places API. **Note: Google Places only provide the five most recent reviews, if you need more, you might want to look elsewhere**.

- You can find the Place ID for a business [here](https://developers.google.com/maps/documentation/places/web-service/place-id).
- There is a great guide on how to host your own CORS proxy [here](https://stackoverflow.com/questions/43871637/no-access-control-allow-origin-header-is-present-on-the-requested-resource-whe/43881141#43881141).
