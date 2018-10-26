# Open Event Webapp

The Open Event Web App is a web application that can generate event websites by getting data from JSON files and media files, that are stored in a compressed zip file. You can also access the application through a Rest API. Websites that are generated by the "web app generator" can be uploaded to any web location, e.g. on Github pages or any server (e.g. via ftp).

[![Build Status](https://travis-ci.org/fossasia/open-event-webapp.svg?branch=development)](https://travis-ci.org/fossasia/open-event-webapp?branch=development)

![Dependencies](https://david-dm.org/fossasia/open-event-webapp.svg)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/c5b7e2ca3e4640c9b38e2f3274072583)](https://www.codacy.com/app/dev_19/open-event-webapp?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=fossasia/open-event-webapp&amp;utm_campaign=Badge_Grade)
[![Code Climate](https://codeclimate.com/github/fossasia/open-event-webapp/badges/gpa.svg?branch=development)](https://codeclimate.com/github/fossasia/open-event-webapp)
[![codecov](https://codecov.io/gh/fossasia/open-event-webapp/branch/development/graph/badge.svg)](https://codecov.io/gh/fossasia/open-event-webapp)
[![Gitter](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/fossasia/open-event-webapp?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

## Usage

NOTE: You can try out the app at  https://opev-webgen.herokuapp.com

The development version is available here: https://opev-webgen-dev.herokuapp.com

## Sample Event App

A sample app is added to this repo as a Github Pages site. You can see the live site at http://fossasia.github.io/open-event-webapp/

## Installation/Deployment

### Installation of the Web App Generator

#### How do I install Web App Generator on a Server

Please check out [the documentation here](/docs/INSTALLATION.md).

#### How do I install Web App Generator on my local machine

Please check out [the documentation here](/docs/INSTALLATION_LOCAL.md).

#### How do I install Web App Generator on Google Cloud

To install the system on Google Cloud please refer to the [Google Cloud installation readme](/docs/INSTALLATION_GOOGLE.md).

#### How do I install Web App Generator on AWS

To install the system on AWS please refer to the [AWS installation readme](/docs/INSTALLATION_AWS.md).

#### How do I install Web App Generator on Digital Ocean

To install the system on Digital Ocean please refer to the [Digital Ocean installation readme](/docs/INSTALLATION_DIGITALOCEAN.md).

#### How do I install Web App Generator on Docker

To install system with Docker please refer to the [Docker installation readme](/docs/INSTALLATION_DOCKER.md).

#### How do I deploy Web App Generator with Heroku

Please read how to deploy to [Heroku here](/docs/INSTALLATION_HEROKU.md)

### How do I deploy it with Heroku

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/fossasia/open-event-webapp/tree/development)   

## The Generator Web Form

 - Once deployed, you'll find the generator running on http://localhost:5000, it should look like this  

![Generator Screencast](docs/screencast.gif)

 - Add your **email id**, **name of app** (name of event),

 - Then upload the zip file that contains all JSON files for *speakers*, *sessions*, *sponsors*, *event*, *tracks* and *locations* (These you should get from an orga-server or through the API after you have created your event there).

 - Now when you click on **GENERATE APP and DOWNLOAD** button, you'll get to download a zip of the event website.

## Accessing the Generator via REST API

Once deployed, the generator can also be used via a REST API.
A `POST` endpoint at `/generate` gets set up, which you can hit using the following parameters -

```http
POST /generate HTTP/1.1
Host: localhost:5000
Cache-Control: no-cache
Content-Type: multipart/form-data

Content-Disposition: form-data; name="email"
a@a.com

Content-Disposition: form-data; name="name"
appname

Content-Disposition: form-data; name="url"
http://json.com/url

Content-Disposition: form-data; name="theme"
light

Content-Disposition: form-data; name="speakerfile"; filename="/path/to/speakers.json"


Content-Disposition: form-data; name="sessionfile"; filename="/path/to/sessions.json"


Content-Disposition: form-data; name="eventfile"; filename="/path/to/event.json"


Content-Disposition: form-data; name="sponsorfile"; filename="/path/to/sponsors.json"


Content-Disposition: form-data; name="trackfile"; filename="/path/to/tracks.json"


Content-Disposition: form-data; name="locationfile"; filename="/path/to/locations.json"
```

If you're using Jquery/AJAX, the code, for example would look like this
```javascript
var form = new FormData();
form.append("email", "a@a.com");
form.append("name", "appname");
form.append("url", "http://json.com/url");
form.append("theme", "light");
form.append("speakerfile", {"0":{}});
form.append("sessionfile", {"0":{}});
form.append("eventfile", {"0":{}});
form.append("sponsorfile", {"0":{}});
form.append("trackfile", {"0":{}});
form.append("locationfile", {"0":{}});

var settings = {
  "async": true,
  "crossDomain": true,
  "url": "http://localhost:5000/generate",
  "method": "POST",
  "headers": {
    "cache-control": "no-cache"
  },
  "processData": false,
  "contentType": false,
  "mimeType": "multipart/form-data",
  "data": form
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

## LICENSE
OpenEvent Webapp - A webapp and it's generator, written under the FOSSASIA Open Event project. The Open Event project aims to make server and client software required for hosting events/conferences easy to build and configure.

Copyright (C) 2016, FOSSASIA

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.

## Maintainers
The project is maintained by
-Saksham Sharma <br>
-Avni Bhardwaj <br>
<br>
******************************************************************************************************************************
