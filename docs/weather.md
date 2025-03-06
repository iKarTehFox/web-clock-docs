---
title: Weather
layout: default
parent: Features
nav_order: 6
---
# Weather
{: .no_toc }
The Weather options allow you to display the current weather conditions in a widget using the [OpenWeatherMap API](https://openweathermap.org/api).

{: .tip }
All of these settings can be set with [URL parameters](/docs/url-params#weather-widget-parameters).

![A screenshot of the Weather menu options.](/assets/images/docs-Features/weather/weather.png)

## Table of contents
{: .no_toc .text-delta }
1. TOC
{:toc}

## Appearance
![A screenshot of site with the weather widget enabled.](/assets/images/docs-Features/weather/appearance.png)

## Options
### OpenWeatherMap AppID
The "AppID" is an API key that you can get (for free) from the [OpenWeatherMap website](https://home.openweathermap.org/api_keys). In order to use the API, you must have an OpenWeatherMap account.

![A screenshot of the OpenWeatherMap AppID field.](/assets/images/docs-Features/weather/appid.png)

{: .important }
> It may take a while for your API key to start working if you just created it. If you continue to have issues, you can contact OpenWeatherMap support.
>
> **Online Web Clock is not operated or endorsed by OpenWeatherMap. I cannot provide you support for your account.**

### Location
You can choose to manually enter a location's latitude and longitude, or you can use the "Get location" button to set it automatically.

![A screenshot of the Location latitude and longitude fields and GPS button.](/assets/images/docs-Features/weather/location.png)

For example, New York City is located at **40.7128° N, 74.0060° W**, or **40.7128, -74.0060**.

{: .note }
Using the "Get location" button requires access to your device's GPS. Your precise location is used in accordance with the Privacy Policy and Terms of [Online Web Clock](https://online-clock.pages.dev/privacy) and [OpenWeatherMap](https://openweather.co.uk/privacy-policy).

### Units
You have the option to display the weather using the metric or imperial system, which changes the units used to display the temperature and wind speed.

![A screenshot of the Units radio buttons.](/assets/images/docs-Features/weather/units.png)

{: .tip-title }
> Fun fact
> 
> Once enabled, the weather widget will update once every 15 minutes.
> 
> If left to run continuously for a month (30 days), the API will only have been called 2,880 times, which is significantly less than the 1,000,000 API monthly call limit for free accounts.

### Widget Position
With this button toggle, you can drag the weather widget to a different position on the page. You can also reset its position to the default.

![A screenshot of the Widget Position options.](/assets/images/docs-Features/weather/widgetposition.png)
