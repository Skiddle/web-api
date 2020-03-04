# Skiddle Events Web API


## Getting Started

The Skiddle Events API has been developed to follow RESTful principles where possible (and not overly complicated). The aim has been to create an API which is simple and intuitive to use rather than following strict policies to the letter.

At present we don't have any client libraries available, but any REST library that allows you to specify the end-point can be used with this API.

### Return format

All results are returned in plain-text JSON format which is cross-platform compatible.

### Authentication

> All requests require a valid API key. For a free api key please [apply here](https://www.skiddle.com/api/join.php).

To access the API you must specify your API KEY on all requests. This should be in the format 'api_key=abcdefghijklmnop'

We monitor all requests and reserve the right to rate-limit or block any excessive requests. Limits are continually changed - please contact us if you are expecting to hit our API frequently.

### HTTPS

All requests must be made over HTTPS (TLS v1.2+)

---

## Events

Events search endpoint: **https://www.skiddle.com/api/v1/events/search/** (method: GET) Gets multiple events based upon search parameters (see below).

> An example of a valid URL (returning gigs near Manchester City Centre) would be: https://www.skiddle.com/api/v1/events/search/?api_key=abcdefghijklmnop&latitude=53.4839&longitude=-2.2446&radius=5&eventcode=LIVE&order=distance&description=1

Event details endpoint: **https://www.skiddle.com/api/v1/events/12345/** (method: GET) Gets information for a single event.


### Event search parameters

#### GEOGRAPHICAL

**latitude:** (decimal, optional) Specify a latitude to find nearby events (eg 53.000)

**longitude:** (decimal, optional) Specify a longitude to find nearby events (eg -1.234)

**radius:** (integer, optional) Find events within the specified miles radius (eg 10)

**_To use geo searching, all 3 of the above parameters must be specified._**

**country:** (string, optional) Find events within a certain country, using a specific ISO country code (eg GB)

**getdistance:** (bool, optional) Return the distance from your specified location _(for this parameter to work, you must also provide a latitude and a longitude)_


#### EVENT FILTERS

**keyword:** (string, optional) Search events using a keyword

**eventcode:** (string, optional) Filter by type of event. Note the category is selected by the event promoter when submitting the event so can be subjective! Choose from:

- FEST = Festivals
- LIVE = Live music
- CLUB = Clubbing/Dance music
- DATE = Dating event
- THEATRE = Theatre/Dance
- COMEDY = Comedy
- EXHIB = Exhibitions and Attractions
- KIDS = Kids/Family event
- BARPUB = Bar/Pub event
- LGB = Gay/Lesbian event
- SPORT = Sporting event
- ARTS = The Arts


**ticketsavailable:** (bool, optional) Find only events with tickets available to purchase

**specialFeatured:** (bool, optional) Find events which are recommended by Skiddle

**imagefilter:** (bool, optional) Find only events which have an image attached

**description:** (bool, optional) Passing this parameter will mean that your results will contain artist and genre information for each event

**under18:** (bool, optional) Find only events which under 18's are allowed to attend

**minDate:** (string, optional) Find events on or after this date. Format as YYYY-MM-DD

**maxDate:** (string, optional) Find events before or on this date. Format as YYYY-MM-DD

**venueid:** (integer, optional) Find events at a particular venue. See the venues search for details. Can either be an integer, or a string of comma seperated integers (eg venueid=1,2,3)

**b:** (integer, optional) Find events attached to a particular brandID (eg Ministry of Sound). See the brands search for details

**a:** (integer, optional) Find events that a particular artistID is tagged to (eg Riva Starr). See the artsits search for details

**g:** (integer, optional) Find events that a particular genreID is tagged to (eg Pop). Can either be an integer, or a string of comma separated integers (eg g=1,2,3)

**order:** (string, optional) Specify sort order. Choose from:


- date = will order by event date
- bestselling = will order by bestselling events
- trending = will return the events in trending order for the preceding week (default)
- goingto = will order the events by the amount of people attending
- distance = will return the events from closest to furthest from your specified location _(for this parameter to work, you must also provide a latitude and a longitude)_


**limit:** (integer, optional) Specify number of records returned (max 100, default 20)

**shufflelimit:** (integer, optional) Used in conjunction with limit, API will retrieve {shufflelimit} events, randomise them, then return final {limit} events. This can be used to return a random subset of events that changes each time.

**offset:** (integer, optional) Specify record number to start at (for paging, in conjunction with limit, order) (default 0)

---

## Venues

Venues search endpoint: **https://www.skiddle.com/api/v1/venues/** (method: GET) Gets multiple venues based upon search parameters (see below)

Venue details endpoint: **https://www.skiddle.com/api/v1/venues/12345/** (method: GET) Gets information for a single venue

### Venue search parameters

#### GEOGRAPHICAL

**latitude:** (decimal, optional) Specify a latitude to find nearby venues(eg 53.000)

**longitude:** (decimal, optional) Specify a longitude to find nearby venues(eg -1.234)

**radius:** (decimal, optional) Find venues within the specified miles radius (eg 10)

**_To use geo searching, all 3 of the above parameters must be specified._**

#### VENUE FILTERS

**type:** (string, optional) Type of venue. Chose from:

- B = Bar/Pub
- N = Nightclub
- L = Live Music
- O = Outdoor venue
- T = Theatre
- S = Sports ground
- G = Gallery

**limit:** (integer, optional) Specify number of records returned (max 100, default 20)

**offset:** (integer, optional) Specify record number to start at (for paging, in conjunction with limit, order) (default 0)

---
 
## Artists

Artists search endpoint: **https://www.skiddle.com/api/v1/artists/** (method: GET) Gets multiple artists based upon search parameters (see below)

### Artist search parameters

**name:** (string, optional) Name of artist to search for

**venueid:** (integer, optional) Find artists playing at a particular venue. See the venues search for details (as an integer)

**b:** (integer, optional) Find artists playing for a particular brandID (eg Ministry of Sound). See the brands search for details
