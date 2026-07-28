# Core Web Vitals API Examples

Code examples for integrating with the **Core Web Vitals** endpoint using different programming languages, HTTP clients, and request libraries. These examples demonstrate how to authenticate requests, send parameters, and process API responses.

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

This document provides example requests for the **Core Web Vitals** endpoint.

Examples are available for multiple programming languages and HTTP clients, allowing developers to integrate the API using their preferred technology stack.

## Endpoint

```
POST https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals
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
| `device` | string | No | Analysis device profile. Defaults to `desktop`. |

# Code Snippets

## C

### Libcurl

```c++
CURL *hnd = curl_easy_init();

curl_easy_setopt(hnd, CURLOPT_CUSTOMREQUEST, "POST");
curl_easy_setopt(hnd, CURLOPT_URL, "https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals");

struct curl_slist *headers = NULL;
headers = curl_slist_append(headers, "x-rapidapi-key: YOUR_API_KEY");
headers = curl_slist_append(headers, "x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com");
headers = curl_slist_append(headers, "Content-Type: application/x-www-form-urlencoded");
curl_easy_setopt(hnd, CURLOPT_HTTPHEADER, headers);

curl_easy_setopt(hnd, CURLOPT_POSTFIELDS, "url=https%3A%2F%2Fgoogle.com&device=desktop");

CURLcode ret = curl_easy_perform(hnd);
```

## Clojure

### clj-http

```clojure
(require '[clj-http.client :as client])

(client/post "https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals" {:headers {:x-rapidapi-key "YOUR_API_KEY"
                                                                                        :x-rapidapi-host "enterprise-seo-metrics.p.rapidapi.com"}
                                                                              :form-params {:url "https://google.com"
                                                                                            :device "desktop"}})
```

## C#

### HttpClient

```csharp
using System.Net.Http.Headers;
var client = new HttpClient();
var request = new HttpRequestMessage
{
	Method = HttpMethod.Post,
	RequestUri = new Uri("https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals"),
	Headers =
	{
		{ "x-rapidapi-key", "YOUR_API_KEY" },
		{ "x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com" },
	},
	Content = new FormUrlEncodedContent(new Dictionary<string, string>
	{
		{ "url", "https://google.com" },
		{ "device", "desktop" },
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
var client = new RestClient("https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals");
var request = new RestRequest(Method.POST);
request.AddHeader("x-rapidapi-key", "YOUR_API_KEY");
request.AddHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com");
request.AddHeader("Content-Type", "application/x-www-form-urlencoded");
request.AddParameter("application/x-www-form-urlencoded", "url=https%3A%2F%2Fgoogle.com&device=desktop", ParameterType.RequestBody);
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

	url := "https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals"

	payload := strings.NewReader("url=https%3A%2F%2Fgoogle.com&device=desktop")

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
POST /core-web-vitals HTTP/1.1
X-Rapidapi-Key: YOUR_API_KEY
X-Rapidapi-Host: enterprise-seo-metrics.p.rapidapi.com
Content-Type: application/x-www-form-urlencoded
Host: enterprise-seo-metrics.p.rapidapi.com
Content-Length: 43

url=https%3A%2F%2Fgoogle.com&device=desktop
```

## Java

### AsyncHttp

```java
AsyncHttpClient client = new DefaultAsyncHttpClient();
client.prepare("POST", "https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals")
	.setHeader("x-rapidapi-key", "YOUR_API_KEY")
	.setHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.setHeader("Content-Type", "application/x-www-form-urlencoded")
	.setBody("url=https%3A%2F%2Fgoogle.com&device=desktop")
	.execute()
	.toCompletableFuture()
	.thenAccept(System.out::println)
	.join();

client.close();
```

### java.net.http

```java
HttpRequest request = HttpRequest.newBuilder()
		.uri(URI.create("https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals"))
		.header("x-rapidapi-key", "YOUR_API_KEY")
		.header("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
		.header("Content-Type", "application/x-www-form-urlencoded")
		.method("POST", HttpRequest.BodyPublishers.ofString("url=https%3A%2F%2Fgoogle.com&device=desktop"))
		.build();
HttpResponse<String> response = HttpClient.newHttpClient().send(request, HttpResponse.BodyHandlers.ofString());
System.out.println(response.body());
```

### OkHttp

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/x-www-form-urlencoded");
RequestBody body = RequestBody.create(mediaType, "url=https%3A%2F%2Fgoogle.com&device=desktop");
Request request = new Request.Builder()
	.url("https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals")
	.post(body)
	.addHeader("x-rapidapi-key", "YOUR_API_KEY")
	.addHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.addHeader("Content-Type", "application/x-www-form-urlencoded")
	.build();

Response response = client.newCall(request).execute();
```

### Unirest

```java
HttpResponse<String> response = Unirest.post("https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals")
	.header("x-rapidapi-key", "YOUR_API_KEY")
	.header("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.header("Content-Type", "application/x-www-form-urlencoded")
	.body("url=https%3A%2F%2Fgoogle.com&device=desktop")
	.asString();
```

## JavaScript

### XMLHttpRequest

```javascript
const data = 'url=https%3A%2F%2Fgoogle.com&device=desktop';

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener('readystatechange', function () {
	if (this.readyState === this.DONE) {
		console.log(this.responseText);
	}
});

xhr.open('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals');
xhr.setRequestHeader('x-rapidapi-key', 'YOUR_API_KEY');
xhr.setRequestHeader('x-rapidapi-host', 'enterprise-seo-metrics.p.rapidapi.com');
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');

xhr.send(data);
```

### Axios

```javascript
import axios from 'axios';

const encodedParams = new URLSearchParams();
encodedParams.set('url', 'https://google.com');
encodedParams.set('device', 'desktop');

const options = {
  method: 'POST',
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals',
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
const url = 'https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals';
const options = {
	method: 'POST',
	headers: {
		'x-rapidapi-key': 'YOUR_API_KEY',
		'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
		'Content-Type': 'application/x-www-form-urlencoded'
	},
	body: new URLSearchParams({
		url: 'https://google.com',
		device: 'desktop'
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
	url: 'https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals',
	method: 'POST',
	headers: {
		'x-rapidapi-key': 'YOUR_API_KEY',
		'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
		'Content-Type': 'application/x-www-form-urlencoded'
	},
	data: {
		url: 'https://google.com',
		device: 'desktop'
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
val body = RequestBody.create(mediaType, "url=https%3A%2F%2Fgoogle.com&device=desktop")
val request = Request.Builder()
	.url("https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals")
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
	path: '/core-web-vitals',
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
  url: 'https://google.com',
  device: 'desktop'
}));
req.end();
```

### Request

```javascript
const request = require('request');

const options = {
  method: 'POST',
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals',
  headers: {
    'x-rapidapi-key': 'YOUR_API_KEY',
    'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  form: {
    url: 'https://google.com',
    device: 'desktop'
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

const req = unirest('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals');

req.headers({
	'x-rapidapi-key': 'YOUR_API_KEY',
	'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
	'Content-Type': 'application/x-www-form-urlencoded'
});

req.form({
	url: 'https://google.com',
	device: 'desktop'
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
encodedParams.set('url', 'https://google.com');
encodedParams.set('device', 'desktop');

const options = {
  method: 'POST',
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals',
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
encodedParams.set('url', 'https://google.com');
encodedParams.set('device', 'desktop');

const url = 'https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals';
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

NSMutableData *postData = [[NSMutableData alloc] initWithData:[@"url=https://google.com" dataUsingEncoding:NSUTF8StringEncoding]];
[postData appendData:[@"&device=desktop" dataUsingEncoding:NSUTF8StringEncoding]];

NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:@"https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals"]
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

let uri = Uri.of_string "https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals" in
let headers = Header.add_list (Header.init ()) [
	("x-rapidapi-key", "YOUR_API_KEY");
	("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com");
	("Content-Type", "application/x-www-form-urlencoded");
] in
let body = Cohttp_lwt_body.of_string "url=https%3A%2F%2Fgoogle.com&device=desktop" in

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
	CURLOPT_URL => "https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals",
	CURLOPT_RETURNTRANSFER => true,
	CURLOPT_ENCODING => "",
	CURLOPT_MAXREDIRS => 10,
	CURLOPT_TIMEOUT => 30,
	CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	CURLOPT_CUSTOMREQUEST => "POST",
	CURLOPT_POSTFIELDS => "url=https%3A%2F%2Fgoogle.com&device=desktop",
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

$response = $client->request('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals', [
	'form_params' => [
		'url' => 'https://google.com',
		'device' => 'desktop'
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
$request->setUrl('https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals');
$request->setMethod(HTTP_METH_POST);

$request->setHeaders([
	'x-rapidapi-key' => 'YOUR_API_KEY',
	'x-rapidapi-host' => 'enterprise-seo-metrics.p.rapidapi.com',
	'Content-Type' => 'application/x-www-form-urlencoded'
]);

$request->setContentType('application/x-www-form-urlencoded');
$request->setPostFields([
	'url' => 'https://google.com',
	'device' => 'desktop'
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
	'url' => 'https://google.com',
	'device' => 'desktop'
]));

$request->setRequestUrl('https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals');
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
$response = Invoke-WebRequest -Uri 'https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals' -Method POST -Headers $headers -ContentType 'application/x-www-form-urlencoded' -Body 'url=https%3A%2F%2Fgoogle.com&device=desktop'
```

### Invoke-RestMethod

```powershell
$headers=@{}
$headers.Add("x-rapidapi-key", "YOUR_API_KEY")
$headers.Add("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
$headers.Add("Content-Type", "application/x-www-form-urlencoded")
$response = Invoke-RestMethod -Uri 'https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals' -Method POST -Headers $headers -ContentType 'application/x-www-form-urlencoded' -Body 'url=https%3A%2F%2Fgoogle.com&device=desktop'
```

## Python

### http.client

```python
import http.client

conn = http.client.HTTPSConnection("enterprise-seo-metrics.p.rapidapi.com")

payload = "url=https%3A%2F%2Fgoogle.com&device=desktop"

headers = {
    'x-rapidapi-key': "YOUR_API_KEY",
    'x-rapidapi-host': "enterprise-seo-metrics.p.rapidapi.com",
    'Content-Type': "application/x-www-form-urlencoded"
}

conn.request("POST", "/core-web-vitals", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Requests

```python
import requests

url = "https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals"

payload = {
	"url": "https://google.com",
	"device": "desktop"
}
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

url <- "https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals"

payload <- "url=https%3A%2F%2Fgoogle.com&device=desktop"

encode <- "form"

response <- VERB("POST", url, body = payload, add_headers('x-rapidapi-key' = 'YOUR_API_KEY', 'x-rapidapi-host' = 'enterprise-seo-metrics.p.rapidapi.com'), content_type("application/x-www-form-urlencoded"), encode = encode)

content(response, "text")
```

## Ruby

### net::http

```ruby
require 'uri'
require 'net/http'

url = URI("https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Post.new(url)
request["x-rapidapi-key"] = 'YOUR_API_KEY'
request["x-rapidapi-host"] = 'enterprise-seo-metrics.p.rapidapi.com'
request["Content-Type"] = 'application/x-www-form-urlencoded'
request.body = "url=https%3A%2F%2Fgoogle.com&device=desktop"

response = http.request(request)
puts response.read_body
```

## Shell

### cURL

```shell
curl --request POST \
	--url https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals \
	--header 'Content-Type: application/x-www-form-urlencoded' \
	--header 'x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com' \
	--header 'x-rapidapi-key: YOUR_API_KEY' \
	--data url=https://google.com \
	--data device=desktop
```

### HTTPie

```shell
http --form POST https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals \
	Content-Type:application/x-www-form-urlencoded \
	x-rapidapi-host:enterprise-seo-metrics.p.rapidapi.com \
	x-rapidapi-key:YOUR_API_KEY \
	url=https://google.com \
	device=desktop
```

### Wget

```shell
wget --quiet \
	--method POST \
	--header 'x-rapidapi-key: YOUR_API_KEY' \
	--header 'x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com' \
	--header 'Content-Type: application/x-www-form-urlencoded' \
	--body-data 'url=https%3A%2F%2Fgoogle.com&device=desktop' \
	--output-document \
	- https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals
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

let postData = NSMutableData(data: "url=https://google.com".data(using: String.Encoding.utf8)!)
postData.append("&device=desktop".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://enterprise-seo-metrics.p.rapidapi.com/core-web-vitals")! as URL,
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
    "performance_ms": 106,
    "url": "https://google.com",
    "metrics": {
      "score": 1,
      "lcp_invalidated": false,
      "time_to_interactive": 464,
      "collected_data": {
        "observed_first_contentful_paint": 394,
        "observed_first_paint": 394,
        "observed_dom_content_loaded": 376,
        "total_blocking_time": 0,
        "observed_last_visual_change_ts": 1142446531467,
        "observed_largest_contentful_paint_all_frames": 394,
        "first_contentful_paint": 464,
        "observed_largest_contentful_paint_ts": 1142446532085,
        "observed_last_visual_change": 393,
        "observed_time_origin_ts": 1142446138467,
        "observed_first_paint_ts": 1142446532085,
        "observed_trace_end_ts": 1142448853010,
        "observed_speed_index": 394,
        "observed_first_visual_change": 393,
        "observed_largest_contentful_paint_all_frames_ts": 1142446532085,
        "largest_contentful_paint": 464,
        "observed_first_contentful_paint_all_frames": 394,
        "observed_cumulative_layout_shift_main_frame": 0,
        "observed_load_ts": 1142446516341,
        "cumulative_layout_shift": 0,
        "observed_first_visual_change_ts": 1142446531467,
        "observed_load": 378,
        "cumulative_layout_shift_main_frame": 0,
        "observed_trace_end": 2715,
        "observed_largest_contentful_paint": 394,
        "observed_speed_index_ts": 1142446532292,
        "observed_navigation_start_ts": 1142446138467,
        "max_potential_fid": 16,
        "observed_dom_content_loaded_ts": 1142446514934,
        "speed_index": 464,
        "interactive": 464,
        "observed_first_contentful_paint_ts": 1142446532085,
        "observed_cumulative_layout_shift": 0,
        "observed_time_origin": 0,
        "observed_first_contentful_paint_all_frames_ts": 1142446532085,
        "observed_navigation_start": 0
      }
    }
  }
}
```

See the endpoint documentation for the complete response schema and available fields.