# Anchor Text Analysis API Examples

Code examples for integrating with the **Anchor Text Analysis** endpoint using different programming languages, HTTP clients, and request libraries. These examples demonstrate how to authenticate requests, send parameters, and process API responses.

## Table of Contents

- [Overview](#overview)
- [Code Snippets](#code-snippets)
  - [C](#c)
    - [Libcurl](#libcurl)
  - [Clojure](#clojure)
    - [clj-http](#clj-http)
  - [C#](#c-1)
    - [HttpClient](#httpclient)
    - [RestSharp](#restsharp)
  - [Go](#go)
    - [NewRequest](#newrequest)
  - [HTTP](#http)
    - [HTTP/1.1](#http11)
  - [Java](#java)
    - [AsyncHttp](#asynchttp)
    - [java.net.http](#javanethttp)
    - [OkHttp](#okhttp)
    - [Unirest](#unirest)
  - [JavaScript](#javascript)
    - [XMLHttpRequest](#xmlhttprequest)
    - [Axios](#axios)
    - [fetch](#fetch)
    - [jQuery](#jquery)
  - [Kotlin](#kotlin)
    - [OkHttp](#okhttp-1)
  - [Node.js](#nodejs)
    - [HTTP](#http-1)
    - [Request](#request)
    - [Unirest](#unirest-1)
    - [Axios](#axios-1)
    - [Fetch](#fetch-1)
  - [Objective-C](#objective-c)
    - [NSURLSession](#nsurlsession)
  - [OCaml](#ocaml)
    - [CoHTTP](#cohttp)
  - [PHP](#php)
    - [cURL](#curl)
    - [Guzzle](#guzzle)
    - [pecl/HTTP v1](#peclhttp-v1)
    - [pecl/HTTP v2](#peclhttp-v2)
  - [Powershell](#powershell)
    - [Invoke-WebRequest](#invoke-webrequest)
    - [Invoke-RestMethod](#invoke-restmethod)
  - [Python](#python)
    - [http.client](#httpclient)
    - [Requests](#requests)
  - [R](#r)
    - [httr](#httr)
  - [Ruby](#ruby)
    - [net::http](#nethttp)
  - [Shell](#shell)
    - [cURL](#curl-1)
    - [HTTPie](#httpie)
    - [Wget](#wget)
  - [Swift](#swift)
    - [NSURLSession](#nsurlsession-1)
- [Example Response](#example-response)

# Overview

This document provides example requests for the **Anchor Text Analysis** endpoint.

Examples are available for multiple programming languages and HTTP clients, allowing developers to integrate the API using their preferred technology stack.

## Endpoint

```
POST https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis
```

## Authentication

All examples require the following headers:

| Header | Description |
|--------|-------------|
| `x-rapidapi-key` | Your RapidAPI authentication key |
| `x-rapidapi-host` | Enterprise SEO Metrics API host |
| `Content-Type` | application/x-www-form-urlencoded |

## Request Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `url` | string | Yes | Domain or URL to analyse |

# Code Snippets

## C

### Libcurl

```c++
CURL *hnd = curl_easy_init();

curl_easy_setopt(hnd, CURLOPT_CUSTOMREQUEST, "POST");
curl_easy_setopt(hnd, CURLOPT_URL, "https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis");

struct curl_slist *headers = NULL;
headers = curl_slist_append(headers, "x-rapidapi-key: YOUR_API_KEY");
headers = curl_slist_append(headers, "x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com");
headers = curl_slist_append(headers, "Content-Type: application/x-www-form-urlencoded");
curl_easy_setopt(hnd, CURLOPT_HTTPHEADER, headers);

curl_easy_setopt(hnd, CURLOPT_POSTFIELDS, "url=google.com");

CURLcode ret = curl_easy_perform(hnd);
```

## Clojure

### clj-http

```clojure
(require '[clj-http.client :as client])

(client/post "https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis" {:headers {:x-rapidapi-key "YOUR_API_KEY"
                                                                                    :x-rapidapi-host "enterprise-seo-metrics.p.rapidapi.com"}
                                                                          :form-params {:url "google.com"}})
```

## C#

### HttpClient

```csharp
using System.Net.Http.Headers;
var client = new HttpClient();
var request = new HttpRequestMessage
{
	Method = HttpMethod.Post,
	RequestUri = new Uri("https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis"),
	Headers =
	{
		{ "x-rapidapi-key", "YOUR_API_KEY" },
		{ "x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com" },
	},
	Content = new FormUrlEncodedContent(new Dictionary<string, string>
	{
		{ "url", "google.com" },
	}),
};
using (var response = await client.SendAsync(request))
{
	response.EnsureSuccessStatusCode();
	var body = await response.Content.ReadAsStringAsync();
	Console.WriteLine(body);
}
```

### RestSharp

```csharp
var client = new RestClient("https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis");
var request = new RestRequest(Method.POST);
request.AddHeader("x-rapidapi-key", "YOUR_API_KEY");
request.AddHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com");
request.AddHeader("Content-Type", "application/x-www-form-urlencoded");
request.AddParameter("application/x-www-form-urlencoded", "url=google.com", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

## Go

### NewRequest

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io"
)

func main() {

	url := "https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis"

	payload := strings.NewReader("url=google.com")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("x-rapidapi-key", "YOUR_API_KEY")
	req.Header.Add("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	req.Header.Add("Content-Type", "application/x-www-form-urlencoded")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := io.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

## HTTP

### HTTP/1.1

```http
POST /anchor-text-analysis HTTP/1.1
X-Rapidapi-Key: YOUR_API_KEY
X-Rapidapi-Host: enterprise-seo-metrics.p.rapidapi.com
Content-Type: application/x-www-form-urlencoded
Host: enterprise-seo-metrics.p.rapidapi.com
Content-Length: 17

url=google.com
```

## Java

### AsyncHttp

```java
AsyncHttpClient client = new DefaultAsyncHttpClient();
client.prepare("POST", "https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis")
	.setHeader("x-rapidapi-key", "YOUR_API_KEY")
	.setHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.setHeader("Content-Type", "application/x-www-form-urlencoded")
	.setBody("url=google.com")
	.execute()
	.toCompletableFuture()
	.thenAccept(System.out::println)
	.join();

client.close();
```

### java.net.http

```java
HttpRequest request = HttpRequest.newBuilder()
		.uri(URI.create("https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis"))
		.header("x-rapidapi-key", "YOUR_API_KEY")
		.header("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
		.header("Content-Type", "application/x-www-form-urlencoded")
		.method("POST", HttpRequest.BodyPublishers.ofString("url=google.com"))
		.build();
HttpResponse<String> response = HttpClient.newHttpClient().send(request, HttpResponse.BodyHandlers.ofString());
System.out.println(response.body());
```

### OkHttp

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/x-www-form-urlencoded");
RequestBody body = RequestBody.create(mediaType, "url=google.com");
Request request = new Request.Builder()
	.url("https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis")
	.post(body)
	.addHeader("x-rapidapi-key", "YOUR_API_KEY")
	.addHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.addHeader("Content-Type", "application/x-www-form-urlencoded")
	.build();

Response response = client.newCall(request).execute();
```

### Unirest

```java
HttpResponse<String> response = Unirest.post("https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis")
	.header("x-rapidapi-key", "YOUR_API_KEY")
	.header("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.header("Content-Type", "application/x-www-form-urlencoded")
	.body("url=google.com")
	.asString();
```

## JavaScript

### XMLHttpRequest

```javascript
const data = 'url=google.com';

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener('readystatechange', function () {
	if (this.readyState === this.DONE) {
		console.log(this.responseText);
	}
});

xhr.open('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis');
xhr.setRequestHeader('x-rapidapi-key', 'YOUR_API_KEY');
xhr.setRequestHeader('x-rapidapi-host', 'enterprise-seo-metrics.p.rapidapi.com');
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');

xhr.send(data);
```

### Axios

```javascript
import axios from 'axios';

const encodedParams = new URLSearchParams();
encodedParams.set('url', 'google.com');

const options = {
  method: 'POST',
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis',
  headers: {
    'x-rapidapi-key': 'YOUR_API_KEY',
    'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  data: encodedParams,
};

try {
	const response = await axios.request(options);
	console.log(response.data);
} catch (error) {
	console.error(error);
}
```

### fetch

```javascript
const url = 'https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis';
const options = {
	method: 'POST',
	headers: {
		'x-rapidapi-key': 'YOUR_API_KEY',
		'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
		'Content-Type': 'application/x-www-form-urlencoded'
	},
	body: new URLSearchParams({
		url: 'google.com'
	})
};

try {
	const response = await fetch(url, options);
	const result = await response.text();
	console.log(result);
} catch (error) {
	console.error(error);
}
```

### jQuery

```javascript
const settings = {
	async: true,
	crossDomain: true,
	url: 'https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis',
	method: 'POST',
	headers: {
		'x-rapidapi-key': 'YOUR_API_KEY',
		'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
		'Content-Type': 'application/x-www-form-urlencoded'
	},
	data: {
		url: 'google.com'
	}
};

$.ajax(settings).done(function (response) {
	console.log(response);
});
```

## Kotlin

### OkHttp

```kotlin
val client = OkHttpClient()

val mediaType = MediaType.parse("application/x-www-form-urlencoded")
val body = RequestBody.create(mediaType, "url=google.com")
val request = Request.Builder()
	.url("https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis")
	.post(body)
	.addHeader("x-rapidapi-key", "YOUR_API_KEY")
	.addHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.addHeader("Content-Type", "application/x-www-form-urlencoded")
	.build()

val response = client.newCall(request).execute()
```

## Node.js

### HTTP

```javascript
const qs = require('querystring');
const http = require('https');

const options = {
	method: 'POST',
	hostname: 'enterprise-seo-metrics.p.rapidapi.com',
	port: null,
	path: '/anchor-text-analysis',
	headers: {
		'x-rapidapi-key': 'YOUR_API_KEY',
		'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
		'Content-Type': 'application/x-www-form-urlencoded'
	}
};

const req = http.request(options, function (res) {
	const chunks = [];

	res.on('data', function (chunk) {
		chunks.push(chunk);
	});

	res.on('end', function () {
		const body = Buffer.concat(chunks);
		console.log(body.toString());
	});
});

req.write(qs.stringify({
  url: 'google.com'
}));
req.end();
```

### Request

```javascript
const request = require('request');

const options = {
  method: 'POST',
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis',
  headers: {
    'x-rapidapi-key': 'YOUR_API_KEY',
    'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  form: {
    url: 'google.com'
  }
};

request(options, function (error, response, body) {
	if (error) throw new Error(error);

	console.log(body);
});
```

### Unirest

```javascript
const unirest = require('unirest');

const req = unirest('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis');

req.headers({
	'x-rapidapi-key': 'YOUR_API_KEY',
	'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
	'Content-Type': 'application/x-www-form-urlencoded'
});

req.form({
	url: 'google.com'
});

req.end(function (res) {
	if (res.error) throw new Error(res.error);

	console.log(res.body);
});
```

### Axios

```javascript
const axios = require('axios');

const encodedParams = new URLSearchParams();
encodedParams.set('url', 'google.com');

const options = {
  method: 'POST',
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis',
  headers: {
    'x-rapidapi-key': 'YOUR_API_KEY',
    'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  data: encodedParams,
};

async function fetchData() {
	try {
		const response = await axios.request(options);
		console.log(response.data);
	} catch (error) {
		console.error(error);
	}
}

fetchData();
```

### Fetch

```javascript
const fetch = require('node-fetch');

const encodedParams = new URLSearchParams();
encodedParams.set('url', 'google.com');

const url = 'https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis';
const options = {
  method: 'POST',
  headers: {
    'x-rapidapi-key': 'YOUR_API_KEY',
    'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  body: encodedParams
};

try {
	const response = await fetch(url, options);
	const result = await response.text();
	console.log(result);
} catch (error) {
	console.error(error);
}
```

## Objective-C

### NSURLSession

```objectivec
#import <Foundation/Foundation.h>

NSDictionary *headers = @{ @"x-rapidapi-key": @"YOUR_API_KEY",
                           @"x-rapidapi-host": @"enterprise-seo-metrics.p.rapidapi.com",
                           @"Content-Type": @"application/x-www-form-urlencoded" };

NSMutableData *postData = [[NSMutableData alloc] initWithData:[@"url=google.com" dataUsingEncoding:NSUTF8StringEncoding]];

NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:@"https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis"]
                                                       cachePolicy:NSURLRequestUseProtocolCachePolicy
                                                   timeoutInterval:10.0];
[request setHTTPMethod:@"POST"];
[request setAllHTTPHeaderFields:headers];
[request setHTTPBody:postData];

NSURLSession *session = [NSURLSession sharedSession];
NSURLSessionDataTask *dataTask = [session dataTaskWithRequest:request
                                            completionHandler:^(NSData *data, NSURLResponse *response, NSError *error) {
	                                            if (error) {
		                                            NSLog(@"%@", error);
	                                            } else {
		                                            NSHTTPURLResponse *httpResponse = (NSHTTPURLResponse *) response;
		                                            NSLog(@"%@", httpResponse);
	                                            }
                                            }];
[dataTask resume];
```

## OCaml

### CoHTTP

```ocaml
open Cohttp_lwt_unix
open Cohttp
open Lwt

let uri = Uri.of_string "https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis" in
let headers = Header.add_list (Header.init ()) [
	("x-rapidapi-key", "YOUR_API_KEY");
	("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com");
	("Content-Type", "application/x-www-form-urlencoded");
] in
let body = Cohttp_lwt_body.of_string "url=google.com" in

Client.call ~headers ~body `POST uri
>>= fun (res, body_stream) ->
	(* Do stuff with the result *)
```

## PHP

### cURL

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, [
	CURLOPT_URL => "https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis",
	CURLOPT_RETURNTRANSFER => true,
	CURLOPT_ENCODING => "",
	CURLOPT_MAXREDIRS => 10,
	CURLOPT_TIMEOUT => 30,
	CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	CURLOPT_CUSTOMREQUEST => "POST",
	CURLOPT_POSTFIELDS => "url=google.com",
	CURLOPT_HTTPHEADER => [
		"Content-Type: application/x-www-form-urlencoded",
		"x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com",
		"x-rapidapi-key: YOUR_API_KEY"
	],
]);

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
	echo "cURL Error #:" . $err;
} else {
	echo $response;
}
```

### Guzzle

```php
<?php

$client = new \GuzzleHttp\Client();

$response = $client->request('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis', [
	'form_params' => [
		'url' => 'google.com'
	],
	'headers' => [
		'Content-Type' => 'application/x-www-form-urlencoded',
		'x-rapidapi-host' => 'enterprise-seo-metrics.p.rapidapi.com',
		'x-rapidapi-key' => 'YOUR_API_KEY',
	],
]);

echo $response->getBody();
```

### pecl/HTTP v1

```php
<?php

$request = new HttpRequest();
$request->setUrl('https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis');
$request->setMethod(HTTP_METH_POST);

$request->setHeaders([
	'x-rapidapi-key' => 'YOUR_API_KEY',
	'x-rapidapi-host' => 'enterprise-seo-metrics.p.rapidapi.com',
	'Content-Type' => 'application/x-www-form-urlencoded'
]);

$request->setContentType('application/x-www-form-urlencoded');
$request->setPostFields([
	'url' => 'google.com'
]);

try {
	$response = $request->send();

	echo $response->getBody();
} catch (HttpException $ex) {
	echo $ex;
}
```

### pecl/HTTP v2

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append(new http\QueryString([
	'url' => 'google.com'
]));

$request->setRequestUrl('https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders([
	'x-rapidapi-key' => 'YOUR_API_KEY',
	'x-rapidapi-host' => 'enterprise-seo-metrics.p.rapidapi.com',
	'Content-Type' => 'application/x-www-form-urlencoded'
]);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

## Powershell

### Invoke-WebRequest

```powershell
$headers=@{}
$headers.Add("x-rapidapi-key", "YOUR_API_KEY")
$headers.Add("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
$headers.Add("Content-Type", "application/x-www-form-urlencoded")
$response = Invoke-WebRequest -Uri 'https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis' -Method POST -Headers $headers -ContentType 'application/x-www-form-urlencoded' -Body 'url=google.com'
```

### Invoke-RestMethod

```powershell
$headers=@{}
$headers.Add("x-rapidapi-key", "YOUR_API_KEY")
$headers.Add("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
$headers.Add("Content-Type", "application/x-www-form-urlencoded")
$response = Invoke-RestMethod -Uri 'https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis' -Method POST -Headers $headers -ContentType 'application/x-www-form-urlencoded' -Body 'url=google.com'
```

## Python

### http.client

```python
import http.client

conn = http.client.HTTPSConnection("enterprise-seo-metrics.p.rapidapi.com")

payload = "url=google.com"

headers = {
    'x-rapidapi-key': "YOUR_API_KEY",
    'x-rapidapi-host': "enterprise-seo-metrics.p.rapidapi.com",
    'Content-Type': "application/x-www-form-urlencoded"
}

conn.request("POST", "/anchor-text-analysis", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Requests

```python
import requests

url = "https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis"

payload = { "url": "google.com" }
headers = {
	"x-rapidapi-key": "YOUR_API_KEY",
	"x-rapidapi-host": "enterprise-seo-metrics.p.rapidapi.com",
	"Content-Type": "application/x-www-form-urlencoded"
}

response = requests.post(url, data=payload, headers=headers)

print(response.json())
```

## R

### httr

```r
library(httr)

url <- "https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis"

payload <- "url=google.com"

encode <- "form"

response <- VERB("POST", url, body = payload, add_headers('x-rapidapi-key' = 'YOUR_API_KEY', 'x-rapidapi-host' = 'enterprise-seo-metrics.p.rapidapi.com'), content_type("application/x-www-form-urlencoded"), encode = encode)

content(response, "text")
```

## Ruby

### net::http

```ruby
require 'uri'
require 'net/http'

url = URI("https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Post.new(url)
request["x-rapidapi-key"] = 'YOUR_API_KEY'
request["x-rapidapi-host"] = 'enterprise-seo-metrics.p.rapidapi.com'
request["Content-Type"] = 'application/x-www-form-urlencoded'
request.body = "url=google.com"

response = http.request(request)
puts response.read_body
```

## Shell

### cURL

```shell
curl --request POST \
	--url https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis \
	--header 'Content-Type: application/x-www-form-urlencoded' \
	--header 'x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com' \
	--header 'x-rapidapi-key: YOUR_API_KEY' \
	--data url=google.com
```

### HTTPie

```shell
http --form POST https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis \
	Content-Type:application/x-www-form-urlencoded \
	x-rapidapi-host:enterprise-seo-metrics.p.rapidapi.com \
	x-rapidapi-key:YOUR_API_KEY \
	url=google.com
```

### Wget

```shell
wget --quiet \
	--method POST \
	--header 'x-rapidapi-key: YOUR_API_KEY' \
	--header 'x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com' \
	--header 'Content-Type: application/x-www-form-urlencoded' \
	--body-data url=google.com \
	--output-document \
	- https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis
```

## Swift

### NSURLSession

```swift
import Foundation

let headers = [
	"x-rapidapi-key": "YOUR_API_KEY",
	"x-rapidapi-host": "enterprise-seo-metrics.p.rapidapi.com",
	"Content-Type": "application/x-www-form-urlencoded"
]

let postData = NSMutableData(data: "url=google.com".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://enterprise-seo-metrics.p.rapidapi.com/anchor-text-analysis")! as URL,
                                        cachePolicy: .useProtocolCachePolicy,
                                    timeoutInterval: 10.0)
request.httpMethod = "POST"
request.allHTTPHeaderFields = headers
request.httpBody = postData as Data

let session = URLSession.shared
let dataTask = session.dataTask(with: request as URLRequest, completionHandler: { (data, response, error) -> Void in
	if (error != nil) {
		print(error as Any)
	} else {
		let httpResponse = response as? HTTPURLResponse
		print(httpResponse)
	}
})

dataTask.resume()
```

# Example Response

Successful responses return `JSON` data:

```json
{
  "success": true,
  "results": {
    "performance_ms": 829,
    "url": "google.com",
    "data": {
      "page-level": {
        "url": "https://www.google.com/",
        "total_links": 10,
        "internal": 8,
        "external": 2,
        "distribution": {
          "exact-match": 8,
          "branded": 1,
          "naked-url": 0,
          "generic": 0,
          "image": 0,
          "empty": 1
        },
        "anchor_tags": [
          {
            "href": "https://mail.google.com/mail/&amp;ogbl",
            "text": "Gmail",
            "type": "exact-match",
            "is_internal": false,
            "is_nofollow": false
          },
          {
            "href": "https://www.google.com/imghp?hl=en&amp;ogbl",
            "text": "Images",
            "type": "exact-match",
            "is_internal": true,
            "is_nofollow": false
          },
          {
            "href": "https://www.google.com/intl/en/about/products",
            "text": "",
            "type": "empty",
            "is_internal": true,
            "is_nofollow": false
          },
          {
            "href": "https://accounts.google.com/ServiceLogin?hl=en&amp;passive=true&amp;continue=https://www.google.com/&amp;ec=GAZAmgQ",
            "text": "Sign in",
            "type": "exact-match",
            "is_internal": false,
            "is_nofollow": false
          },
          {
            "href": "https://www.google.com/advanced_search?hl=en&amp;authuser=0",
            "text": "Advanced search",
            "type": "exact-match",
            "is_internal": true,
            "is_nofollow": false
          },
          {
            "href": "https://www.google.com/intl/en/ads/",
            "text": "Advertising",
            "type": "exact-match",
            "is_internal": true,
            "is_nofollow": false
          },
          {
            "href": "https://www.google.com/services/",
            "text": "Business Solutions",
            "type": "exact-match",
            "is_internal": true,
            "is_nofollow": false
          },
          {
            "href": "https://www.google.com/intl/en/about.html",
            "text": "About Google",
            "type": "branded",
            "is_internal": true,
            "is_nofollow": false
          },
          {
            "href": "https://www.google.com/intl/en/policies/privacy/",
            "text": "Privacy",
            "type": "exact-match",
            "is_internal": true,
            "is_nofollow": false
          },
          {
            "href": "https://www.google.com/intl/en/policies/terms/",
            "text": "Terms",
            "type": "exact-match",
            "is_internal": true,
            "is_nofollow": false
          }
        ]
      },
      "domain-level": {
        "backlinks": {
          "aggregate": 7712067120,
          "distribution": [
            {
              "anchor_type": "branded",
              "backlinks": 1720027326,
              "examples": [
                "Google Maps öffnen",
                "Google Karte anzeigen",
                "Google Mapで見る"
              ],
              "percentage": {
                "value": 0.223030647845,
                "scaled": 22.3031,
                "scale_unit": "percent",
                "scale_factor": 100,
                "significant_figures": 6
              }
            },
            {
              "anchor_type": "partial-match",
              "backlinks": 2086163998,
              "examples": [
                "Opens in new tab",
                "Política de Privacidade",
                "🐆 ¡Navega más rápido con la app!"
              ],
              "percentage": {
                "value": 0.270506462864,
                "scaled": 27.0506,
                "scale_unit": "percent",
                "scale_factor": 100,
                "significant_figures": 6
              }
            },
            {
              "anchor_type": "exact-match",
              "backlinks": 2937557149,
              "examples": [
                "Nastavení reklam",
                "Nawiguj",
                "Cookies"
              ],
              "percentage": {
                "value": 0.380903991536,
                "scaled": 38.0904,
                "scale_unit": "percent",
                "scale_factor": 100,
                "significant_figures": 6
              }
            },
            {
              "anchor_type": "generic",
              "backlinks": 310651919,
              "examples": [
                "Street View",
                "Cancel - Exit this Site",
                "Check Website"
              ],
              "percentage": {
                "value": 0.04028127792,
                "scaled": 4.0281,
                "scale_unit": "percent",
                "scale_factor": 100,
                "significant_figures": 5
              }
            },
            {
              "anchor_type": "other",
              "backlinks": 320996534,
              "examples": [
                "09 55 00 66 33",
                "qui",
                "G+"
              ],
              "percentage": {
                "value": 0.041622632299,
                "scaled": 4.1623,
                "scale_unit": "percent",
                "scale_factor": 100,
                "significant_figures": 5
              }
            },
            {
              "anchor_type": "naked-url",
              "backlinks": 297486045,
              "examples": [
                "https://support.google.com/policies/contact/general_privacy_form",
                "www.google.com",
                "https://policies.google.com/privacy?hl=pl"
              ],
              "percentage": {
                "value": 0.038574099573,
                "scaled": 3.8574,
                "scale_unit": "percent",
                "scale_factor": 100,
                "significant_figures": 5
              }
            },
            {
              "anchor_type": "images",
              "backlinks": 39184147,
              "examples": [
                "android icon, opens in new window",
                "Optimize the following images",
                "Google Reverse Image Search"
              ],
              "percentage": {
                "value": 0.005080887704,
                "scaled": 0.5081,
                "scale_unit": "percent",
                "scale_factor": 100,
                "significant_figures": 5
              }
            }
          ],
          "top_backlinks": {
            "authority_score": [
              {
                "authority_score": 100,
                "referring_text": "Google Workspace Updates: New community features for Google Chat and an update on Currents",
                "referring_page": "https://workspaceupdates.googleblog.com/2023/04/new-community-features-for-google-chat-and-an-update-currents%20.html",
                "anchor_text": "Google Domains",
                "anchor_url": "https://domains.google.com/about/",
                "first_seen": "2025-11-23T00:00:00.000Z",
                "last_seen": "2026-06-25T00:00:00.000Z"
              },
              {
                "authority_score": 100,
                "referring_text": "Descargar Firefox para Escritorio desde Mozilla",
                "referring_page": "https://www.firefox.com/es-AR/",
                "anchor_text": "Descargalo en Google Play",
                "anchor_url": "https://play.google.com/store/apps/details?id=org.mozilla.firefox&amp;referrer=utm_source%3Dwww.firefox.com%26utm_medium%3Dreferral%26utm_campaign%3Ddownload",
                "first_seen": "2025-11-21T00:00:00.000Z",
                "last_seen": "2026-05-05T00:00:00.000Z"
              },
              {
                "authority_score": 100,
                "referring_text": "Google Chrome 谷歌浏览器官方下载 - 安全极速的网络浏览器",
                "referring_page": "https://zh-google.sh.cn/",
                "anchor_text": null,
                "anchor_url": "https://www.google.com/chrome/?platform=mac",
                "first_seen": "2026-06-09T00:00:00.000Z",
                "last_seen": "2026-06-09T00:00:00.000Z"
              },
              {
                "authority_score": 100,
                "referring_text": "Google Chrome 谷歌浏览器官方下载 - 安全极速的网络浏览器",
                "referring_page": "https://zh-google.sh.cn/",
                "anchor_text": null,
                "anchor_url": "https://www.google.com/chrome/?platform=win",
                "first_seen": "2026-06-09T00:00:00.000Z",
                "last_seen": "2026-06-09T00:00:00.000Z"
              },
              {
                "authority_score": 100,
                "referring_text": "Сетка — социальная сеть для нетворкинга от hh.ru",
                "referring_page": "https://setka.ru/",
                "anchor_text": "Ссылка на Google Play",
                "anchor_url": "https://play.google.com/store/apps/details?hl=ru&amp;id=com.setka&amp;pli=1&amp;referrer=appmetrica_tracking_id%3D1037661656152318991%26ym_tracking_id%3D10519822690293597043",
                "first_seen": "2025-09-13T00:00:00.000Z",
                "last_seen": "2025-12-01T00:00:00.000Z"
              },
              {
                "authority_score": 100,
                "referring_text": "MyBB - Free and Open Source Forum Software",
                "referring_page": "https://mybb.com/",
                "anchor_text": null,
                "anchor_url": "https://www.google.com/search",
                "first_seen": "2025-12-01T00:00:00.000Z",
                "last_seen": "2026-06-24T00:00:00.000Z"
              },
              {
                "authority_score": 100,
                "referring_text": "AddToAny - Share",
                "referring_page": "https://www.addtoany.com/share",
                "anchor_text": "AddToAny for Chrome",
                "anchor_url": "https://chrome.google.com/webstore/detail/addtoany-share-anywhere/ffpgijchhhkhnokafdeklpllijgnbche",
                "first_seen": "2025-11-19T00:00:00.000Z",
                "last_seen": "2026-05-20T00:00:00.000Z"
              },
              {
                "authority_score": 99,
                "referring_text": "Firefox: The fast, private browser that keeps you safe — Firefox.com",
                "referring_page": "https://www.firefox.com/es-AR/",
                "anchor_text": "Descargalo en Google Play",
                "anchor_url": "https://play.google.com/store/apps/details?hl=es&amp;id=org.mozilla.firefox&amp;referrer=utm_source%3Dwww.firefox.com%26utm_medium%3Dreferral%26utm_campaign%3Dhome",
                "first_seen": "2026-04-13T00:00:00.000Z",
                "last_seen": "2026-06-23T00:00:00.000Z"
              },
              {
                "authority_score": 99,
                "referring_text": "line HK 下載入口 - 主頁",
                "referring_page": "https://line.bn.hl.cn/",
                "anchor_text": "🤖 Android 手機 Google Play · Android 8+ · 免費 ›",
                "anchor_url": "https://play.google.com/store/apps/details?id=jp.naver.line.android",
                "first_seen": "2026-04-21T00:00:00.000Z",
                "last_seen": "2026-04-21T00:00:00.000Z"
              },
              {
                "authority_score": 98,
                "referring_text": "Skytech Communications",
                "referring_page": "https://www.skytech.com/",
                "anchor_text": "Google Play Store",
                "anchor_url": "https://play.google.com/store/apps/details?id=com.skytech.omnivoxmobile",
                "first_seen": "2025-11-20T00:00:00.000Z",
                "last_seen": "2026-06-20T00:00:00.000Z"
              }
            ],
            "domain_rating": [
              {
                "alt": "",
                "anchor": "sign up",
                "is_dofollow": true,
                "domain_rating": 96,
                "organic_traffic": 387,
                "link_type": "text",
                "link_context": "a Google account. If you are not a user yet, sign up for a new account. When trying to make a connection,",
                "url_from": "https://learn.microsoft.com/en-us/connectors/youtube/",
                "url_to": "https://google.com/",
                "first_seen": "2022-10-15T11:12:06Z",
                "last_seen": "2026-04-14T06:21:11Z"
              },
              {
                "alt": "",
                "anchor": "Explore",
                "is_dofollow": true,
                "domain_rating": 96,
                "organic_traffic": 218,
                "link_type": "text",
                "link_context": "Explore",
                "url_from": "https://datacenters.microsoft.com/home/",
                "url_to": "https://google.com/",
                "first_seen": "2025-06-26T10:23:13Z",
                "last_seen": "2026-04-12T16:14:32Z"
              },
              {
                "alt": "",
                "anchor": "google",
                "is_dofollow": true,
                "domain_rating": 94,
                "organic_traffic": 17742,
                "link_type": "text",
                "link_context": "sediakan ini memang di khususkan untuk anda yang mencarinya di google , silahkan bookmark website weebly ini karena kami selalu melakukan",
                "url_from": "https://analisa88.weebly.com/",
                "url_to": "https://google.com/",
                "first_seen": "2022-08-03T02:06:45Z",
                "last_seen": "2026-04-20T11:25:40Z"
              },
              {
                "alt": "",
                "anchor": "",
                "is_dofollow": true,
                "domain_rating": 94,
                "organic_traffic": 3882,
                "link_type": "text",
                "link_context": "",
                "url_from": "https://anugrahbodi.github.io/",
                "url_to": "https://google.com/",
                "first_seen": "2025-08-06T11:28:46Z",
                "last_seen": "2026-05-24T14:58:04Z"
              },
              {
                "alt": "",
                "anchor": "Google",
                "is_dofollow": true,
                "domain_rating": 94,
                "organic_traffic": 370,
                "link_type": "text",
                "link_context": "( Google )",
                "url_from": "https://www.w3.org/TR/trace-context/",
                "url_to": "https://google.com/",
                "first_seen": "2022-01-28T13:10:33Z",
                "last_seen": "2026-05-31T09:09:27Z"
              },
              {
                "alt": "",
                "anchor": "I AM NOT YET 18",
                "is_dofollow": true,
                "domain_rating": 94,
                "organic_traffic": 163,
                "link_type": "text",
                "link_context": "I AM NOT YET 18",
                "url_from": "https://relxaustralia.myshopify.com/products/infinity-device",
                "url_to": "https://google.com/",
                "first_seen": "2025-08-27T11:33:58Z",
                "last_seen": "2026-04-23T21:20:19Z"
              },
              {
                "alt": "",
                "anchor": "Google Inc.",
                "is_dofollow": true,
                "domain_rating": 94,
                "organic_traffic": 112,
                "link_type": "text",
                "link_context": "( Google Inc. )",
                "url_from": "https://www.w3.org/TR/geolocation/",
                "url_to": "https://google.com/",
                "first_seen": "2021-05-29T20:40:41Z",
                "last_seen": "2026-05-31T09:07:11Z"
              },
              {
                "alt": "",
                "anchor": "Google",
                "is_dofollow": true,
                "domain_rating": 94,
                "organic_traffic": 93,
                "link_type": "text",
                "link_context": "Google",
                "url_from": "https://augmentedperception.github.io/total_relighting/",
                "url_to": "https://google.com/",
                "first_seen": "2022-06-13T10:40:44Z",
                "last_seen": "2026-04-18T19:30:47Z"
              },
              {
                "alt": "",
                "anchor": "Enter 9 now activate code",
                "is_dofollow": true,
                "domain_rating": 94,
                "organic_traffic": 86,
                "link_type": "text",
                "link_context": "Enter 9 now activate code",
                "url_from": "https://9nowcomactivate.weebly.com/",
                "url_to": "https://google.com/",
                "first_seen": "2025-09-30T13:21:50Z",
                "last_seen": "2026-04-20T19:43:45Z"
              },
              {
                "alt": "",
                "anchor": "Gemini",
                "is_dofollow": true,
                "domain_rating": 94,
                "organic_traffic": 81,
                "link_type": "text",
                "link_context": "Thanks to AlonsoAliaga and Gemini for his hard work during the development of this tool.",
                "url_from": "https://alonsoaliaga.github.io/generator/",
                "url_to": "https://google.com/",
                "first_seen": "2026-03-28T07:40:14Z",
                "last_seen": "2026-04-26T19:04:04Z"
              }
            ]
          }
        }
      }
    }
  }
}
```

See the endpoint documentation for the complete response schema and available fields.