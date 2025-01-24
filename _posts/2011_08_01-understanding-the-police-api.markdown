---
layout: post
title:  "Understanding the Police API: An perfect introduction to API programming"
date:   2011-08-01 10:50:18 +0000
categories: revived code
---

When I found myself gazing at the news during lunch the other day, my attention was suddenly caught by the announcement of an iPhone application which can tell you about the crime history of your current location.

Like any developer, as soon as I saw this my first response was “Wow, the police have an API”. And so they do, http://www.police.uk/api/docs/ . The police API is a RESTFul JSON Web service that uses HTTP GET requests to fetch JSON formatted data about a multitude of (historical) crime and police related information, this being said the data seems to only be about a month behind. The API is authenticated, using an API key you must apply for, and then BASIC HTTP Authentication.

At this point I decided I didn’t want to let the side down, and should probably build a Windows Phone 7 “Crime Hunter” app. As always its my belief that things done in mobile environments are always harder than on the desktop , you will see later why they aren’t with Phone 7, but this didn’t stop me from making a desktop application first.

While looking through the details of the API fo r this, I realised – this really is as simple as a web API gets – which makes it a perfect introduction for those who have never worked with a web API like this before. Nice simple and clean.

**Desktop Proof Of Concept**
This is a simple class with a single function that prints out the HTTP response. This serves simply to ensure that the API is working and returning Data. Pop in your API password and it should work straight away.

`using System;
using System.Text;
using System.Net;
using System.IO;
using System.Web;

    class UkPoliceInterface
    {
        // API Credentials - Pass in by constructor in common use
        private string apiUsername = "";
        private string apiPassword = "";

        public string AuthorisedRequest(String requestUrl)
        {

            // Create a new WebRequest to the URL Passed
            WebRequest dataRequest = WebRequest.Create(requestUrl);

            // Add a BASIC Authentication header to the data request, using the API Username and Password
            dataRequest.Headers["Authorization"] = "Basic " + Convert.ToBase64String(Encoding.ASCII.GetBytes(apiUsername + ":" + apiPassword));

            // Wrap to catch errors
            try
            {
                // Request the response object and save it locally
                WebResponse dataResponse = dataRequest.GetResponse();

                // Get the response stream and wrap it in a stream reader
                StreamReader dataStreamReader = new StreamReader(dataResponse.GetResponseStream(), Encoding.UTF8);

                // Return the string
                return dataStreamReader.ReadToEnd();
            }
            catch (Exception ee)
            {
                // If Something went wrong, throw a generic exception at this time
                throw new Exception("Could Not Complete Web Query ("+ee.Message+")");
            }
        }
}`

This function simply creates a new .NET WebRequest object, this neat little object encapsulates the process of making a request to a URI and provides a few methods for getting the response.

In the case, its sister object WebReponse takes the response and allows us to write it down to a stream, with the help of the StreamReader class , this means we can now write the stream down to a local string, and voila , theres the response. Some Lovely JSON…

`[
    {
        "category": "vehicle-crime",
        "id": 1976260,
        "location": {
            "latitude": "52.6240688",
            "street": {
                "id": 165758,
                "name": "On or near Godsons Hill"
            },
            "longitude": "-1.4157945"
        },
        "context": "",
        "month": "2011-06"
    },
    {
        "category": "burglary",
        "id": 1976261,
        "location": {
            "latitude": "52.6240688",
            "street": {
                "id": 165758,
                "name": "On or near Godsons Hill"
            },
            "longitude": "-1.4157945"
        },
        "context": "",
        "month": "2011-06"
    },
    {
        "category": "vehicle-crime",
        "id": 2013093,
        "location": {
            "latitude": "52.6241922",
            "street": {
                "id": 203088,
                "name": "On or near Hillside"
            },
            "longitude": "-1.4153054"
        },
        "context": "",
        "month": "2011-06"
    },
    {
        "category": "anti-social-behaviour",
        "id": 2019201,
        "location": {
            "latitude": "52.6260645",
            "street": {
                "id": 209891,
                "name": "On or near Horseshoe Close"
            },
            "longitude": "-1.4212784"
        },
        "context": "",
        "month": "2011-06"
    },
    {
        "category": "other-crime",
        "id": 2245928,
        "location": {
            "latitude": "52.6233953",
            "street": {
                "id": 436377,
                "name": "On or near Warwick Lane"
            },
            "longitude": "-1.4033061"
        },
        "context": "",
        "month": "2011-06"
    },
    {
        "category": "burglary",
        "id": 2245929,
        "location": {
            "latitude": "52.6233953",
            "street": {
                "id": 436377,
                "name": "On or near Warwick Lane"
            },
            "longitude": "-1.4033061"
        },
        "context": "",
        "month": "2011-06"
    }
]`

Now I knew that the API works as expected, on to coding it up for Windows Phone 7, See my part 2 Post on how!