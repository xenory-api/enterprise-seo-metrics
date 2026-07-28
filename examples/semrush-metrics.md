# Semrush Metrics API Examples

Code examples for integrating with the **Semrush Metrics** endpoint using different programming languages, HTTP clients, and request libraries. These examples demonstrate how to authenticate requests, send parameters, and process API responses.

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

This document provides example requests for the **Semrush Metrics** endpoint.

Examples are available for multiple programming languages and HTTP clients, allowing developers to integrate the API using their preferred technology stack.

## Endpoint

```
POST https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics
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
| `domain` | string | Yes | Root domain to analyse (e.g. `google.com`) |

# Code Snippets

## C

### Libcurl

```c++
CURL *hnd = curl_easy_init();

curl_easy_setopt(hnd, CURLOPT_CUSTOMREQUEST, "POST");
curl_easy_setopt(hnd, CURLOPT_URL, "https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics");

struct curl_slist *headers = NULL;
headers = curl_slist_append(headers, "x-rapidapi-key: YOUR_API_KEY");
headers = curl_slist_append(headers, "x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com");
headers = curl_slist_append(headers, "Content-Type: application/x-www-form-urlencoded");
curl_easy_setopt(hnd, CURLOPT_HTTPHEADER, headers);

curl_easy_setopt(hnd, CURLOPT_POSTFIELDS, "domain=google.com");

CURLcode ret = curl_easy_perform(hnd);
```

## Clojure

### clj-http

```clojure
(require '[clj-http.client :as client])

(client/post "https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics" {:headers {:x-rapidapi-key "YOUR_API_KEY"
                                                                                    :x-rapidapi-host "enterprise-seo-metrics.p.rapidapi.com"}
                                                                          :form-params {:domain "google.com"}})
```

## C#

### HttpClient

```csharp
using System.Net.Http.Headers;
var client = new HttpClient();
var request = new HttpRequestMessage
{
	Method = HttpMethod.Post,
	RequestUri = new Uri("https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics"),
	Headers =
	{
		{ "x-rapidapi-key", "YOUR_API_KEY" },
		{ "x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com" },
	},
	Content = new FormUrlEncodedContent(new Dictionary<string, string>
	{
		{ "domain", "google.com" },
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
var client = new RestClient("https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics");
var request = new RestRequest(Method.POST);
request.AddHeader("x-rapidapi-key", "YOUR_API_KEY");
request.AddHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com");
request.AddHeader("Content-Type", "application/x-www-form-urlencoded");
request.AddParameter("application/x-www-form-urlencoded", "domain=google.com", ParameterType.RequestBody);
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

	url := "https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics"

	payload := strings.NewReader("domain=google.com")

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
POST /semrush-metrics HTTP/1.1
X-Rapidapi-Key: YOUR_API_KEY
X-Rapidapi-Host: enterprise-seo-metrics.p.rapidapi.com
Content-Type: application/x-www-form-urlencoded
Host: enterprise-seo-metrics.p.rapidapi.com
Content-Length: 17

domain=google.com
```

## Java

### AsyncHttp

```java
AsyncHttpClient client = new DefaultAsyncHttpClient();
client.prepare("POST", "https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics")
	.setHeader("x-rapidapi-key", "YOUR_API_KEY")
	.setHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.setHeader("Content-Type", "application/x-www-form-urlencoded")
	.setBody("domain=google.com")
	.execute()
	.toCompletableFuture()
	.thenAccept(System.out::println)
	.join();

client.close();
```

### java.net.http

```java
HttpRequest request = HttpRequest.newBuilder()
		.uri(URI.create("https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics"))
		.header("x-rapidapi-key", "YOUR_API_KEY")
		.header("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
		.header("Content-Type", "application/x-www-form-urlencoded")
		.method("POST", HttpRequest.BodyPublishers.ofString("domain=google.com"))
		.build();
HttpResponse<String> response = HttpClient.newHttpClient().send(request, HttpResponse.BodyHandlers.ofString());
System.out.println(response.body());
```

### OkHttp

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/x-www-form-urlencoded");
RequestBody body = RequestBody.create(mediaType, "domain=google.com");
Request request = new Request.Builder()
	.url("https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics")
	.post(body)
	.addHeader("x-rapidapi-key", "YOUR_API_KEY")
	.addHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.addHeader("Content-Type", "application/x-www-form-urlencoded")
	.build();

Response response = client.newCall(request).execute();
```

### Unirest

```java
HttpResponse<String> response = Unirest.post("https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics")
	.header("x-rapidapi-key", "YOUR_API_KEY")
	.header("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.header("Content-Type", "application/x-www-form-urlencoded")
	.body("domain=google.com")
	.asString();
```

## JavaScript

### XMLHttpRequest

```javascript
const data = 'domain=google.com';

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener('readystatechange', function () {
	if (this.readyState === this.DONE) {
		console.log(this.responseText);
	}
});

xhr.open('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics');
xhr.setRequestHeader('x-rapidapi-key', 'YOUR_API_KEY');
xhr.setRequestHeader('x-rapidapi-host', 'enterprise-seo-metrics.p.rapidapi.com');
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');

xhr.send(data);
```

### Axios

```javascript
import axios from 'axios';

const encodedParams = new URLSearchParams();
encodedParams.set('domain', 'google.com');

const options = {
  method: 'POST',
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics',
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
const url = 'https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics';
const options = {
	method: 'POST',
	headers: {
		'x-rapidapi-key': 'YOUR_API_KEY',
		'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
		'Content-Type': 'application/x-www-form-urlencoded'
	},
	body: new URLSearchParams({
		domain: 'google.com'
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
	url: 'https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics',
	method: 'POST',
	headers: {
		'x-rapidapi-key': 'YOUR_API_KEY',
		'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
		'Content-Type': 'application/x-www-form-urlencoded'
	},
	data: {
		domain: 'google.com'
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
val body = RequestBody.create(mediaType, "domain=google.com")
val request = Request.Builder()
	.url("https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics")
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
	path: '/semrush-metrics',
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
  domain: 'google.com'
}));
req.end();
```

### Request

```javascript
const request = require('request');

const options = {
  method: 'POST',
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics',
  headers: {
    'x-rapidapi-key': 'YOUR_API_KEY',
    'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  form: {
    domain: 'google.com'
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

const req = unirest('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics');

req.headers({
	'x-rapidapi-key': 'YOUR_API_KEY',
	'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
	'Content-Type': 'application/x-www-form-urlencoded'
});

req.form({
	domain: 'google.com'
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
encodedParams.set('domain', 'google.com');

const options = {
  method: 'POST',
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics',
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
encodedParams.set('domain', 'google.com');

const url = 'https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics';
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

NSMutableData *postData = [[NSMutableData alloc] initWithData:[@"domain=google.com" dataUsingEncoding:NSUTF8StringEncoding]];

NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:@"https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics"]
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

let uri = Uri.of_string "https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics" in
let headers = Header.add_list (Header.init ()) [
	("x-rapidapi-key", "YOUR_API_KEY");
	("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com");
	("Content-Type", "application/x-www-form-urlencoded");
] in
let body = Cohttp_lwt_body.of_string "domain=google.com" in

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
	CURLOPT_URL => "https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics",
	CURLOPT_RETURNTRANSFER => true,
	CURLOPT_ENCODING => "",
	CURLOPT_MAXREDIRS => 10,
	CURLOPT_TIMEOUT => 30,
	CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	CURLOPT_CUSTOMREQUEST => "POST",
	CURLOPT_POSTFIELDS => "domain=google.com",
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

$response = $client->request('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics', [
	'form_params' => [
		'domain' => 'google.com'
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
$request->setUrl('https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics');
$request->setMethod(HTTP_METH_POST);

$request->setHeaders([
	'x-rapidapi-key' => 'YOUR_API_KEY',
	'x-rapidapi-host' => 'enterprise-seo-metrics.p.rapidapi.com',
	'Content-Type' => 'application/x-www-form-urlencoded'
]);

$request->setContentType('application/x-www-form-urlencoded');
$request->setPostFields([
	'domain' => 'google.com'
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
	'domain' => 'google.com'
]));

$request->setRequestUrl('https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics');
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
$response = Invoke-WebRequest -Uri 'https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics' -Method POST -Headers $headers -ContentType 'application/x-www-form-urlencoded' -Body 'domain=google.com'
```

### Invoke-RestMethod

```powershell
$headers=@{}
$headers.Add("x-rapidapi-key", "YOUR_API_KEY")
$headers.Add("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
$headers.Add("Content-Type", "application/x-www-form-urlencoded")
$response = Invoke-RestMethod -Uri 'https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics' -Method POST -Headers $headers -ContentType 'application/x-www-form-urlencoded' -Body 'domain=google.com'
```

## Python

### http.client

```python
import http.client

conn = http.client.HTTPSConnection("enterprise-seo-metrics.p.rapidapi.com")

payload = "domain=google.com"

headers = {
    'x-rapidapi-key': "YOUR_API_KEY",
    'x-rapidapi-host': "enterprise-seo-metrics.p.rapidapi.com",
    'Content-Type': "application/x-www-form-urlencoded"
}

conn.request("POST", "/semrush-metrics", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Requests

```python
import requests

url = "https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics"

payload = { "domain": "google.com" }
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

url <- "https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics"

payload <- "domain=google.com"

encode <- "form"

response <- VERB("POST", url, body = payload, add_headers('x-rapidapi-key' = 'YOUR_API_KEY', 'x-rapidapi-host' = 'enterprise-seo-metrics.p.rapidapi.com'), content_type("application/x-www-form-urlencoded"), encode = encode)

content(response, "text")
```

## Ruby

### net::http

```ruby
require 'uri'
require 'net/http'

url = URI("https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Post.new(url)
request["x-rapidapi-key"] = 'YOUR_API_KEY'
request["x-rapidapi-host"] = 'enterprise-seo-metrics.p.rapidapi.com'
request["Content-Type"] = 'application/x-www-form-urlencoded'
request.body = "domain=google.com"

response = http.request(request)
puts response.read_body
```

## Shell

### cURL

```shell
curl --request POST \
	--url https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics \
	--header 'Content-Type: application/x-www-form-urlencoded' \
	--header 'x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com' \
	--header 'x-rapidapi-key: YOUR_API_KEY' \
	--data domain=google.com
```

### HTTPie

```shell
http --form POST https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics \
	Content-Type:application/x-www-form-urlencoded \
	x-rapidapi-host:enterprise-seo-metrics.p.rapidapi.com \
	x-rapidapi-key:YOUR_API_KEY \
	domain=google.com
```

### Wget

```shell
wget --quiet \
	--method POST \
	--header 'x-rapidapi-key: YOUR_API_KEY' \
	--header 'x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com' \
	--header 'Content-Type: application/x-www-form-urlencoded' \
	--body-data domain=google.com \
	--output-document \
	- https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics
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

let postData = NSMutableData(data: "domain=google.com".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://enterprise-seo-metrics.p.rapidapi.com/semrush-metrics")! as URL,
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
    "performance_ms": 1507,
    "domain": "google.com",
    "data": {
      "metrics": {
        "authority_score": 100,
        "total_backlinks": 45168718551,
        "organic_traffic": 4761203167,
        "referring_domains": 49761505,
        "score_metrics": {
          "link_power": 6.99,
          "search_traffic": 6.99,
          "naturalness": 6,
          "health": 45,
          "health_v2": 45,
          "is_poor_links": false,
          "is_poor_network": false,
          "is_poor_ip_subnets": false,
          "is_poor_refdomain_ip": false
        },
        "backlink_audit": {
          "lost_backlinks": 0,
          "new_backlinks": 646345011,
          "new_referring_domains": 240545,
          "lost_referring_domains": 0,
          "last_updated": "2026-06-22T04:00:00"
        }
      },
      "distribution": {
        "organic_traffic": {
          "aggregate": 4761203167,
          "databases": [
            {
              "alpha_2": "AE",
              "country": "United Arab Emirates",
              "traffic": 22988191
            },
            {
              "alpha_2": "AF",
              "country": "Afghanistan",
              "traffic": 2887630
            },
            {
              "alpha_2": "AL",
              "country": "Albania",
              "traffic": 3006821
            },
            {
              "alpha_2": "AM",
              "country": "Armenia",
              "traffic": 2734037
            },
            {
              "alpha_2": "AO",
              "country": "Angola",
              "traffic": 3886870
            },
            {
              "alpha_2": "AR",
              "country": "Argentina",
              "traffic": 55152549
            },
            {
              "alpha_2": "AT",
              "country": "Austria",
              "traffic": 14347994
            },
            {
              "alpha_2": "AU",
              "country": "Australia",
              "traffic": 37416609
            },
            {
              "alpha_2": "AZ",
              "country": "Azerbaijan",
              "traffic": 8936775
            },
            {
              "alpha_2": "BA",
              "country": "Bosnia and Herzegovina",
              "traffic": 3623664
            },
            {
              "alpha_2": "BD",
              "country": "Bangladesh",
              "traffic": 65334519
            },
            {
              "alpha_2": "BE",
              "country": "Belgium",
              "traffic": 19076651
            },
            {
              "alpha_2": "BG",
              "country": "Bulgaria",
              "traffic": 8814454
            },
            {
              "alpha_2": "BH",
              "country": "Bahrain",
              "traffic": 1926592
            },
            {
              "alpha_2": "BN",
              "country": "Brunei Darussalam",
              "traffic": 645284
            },
            {
              "alpha_2": "BO",
              "country": "Bolivia",
              "traffic": 8538251
            },
            {
              "alpha_2": "BR",
              "country": "Brazil",
              "traffic": 194003697
            },
            {
              "alpha_2": "BS",
              "country": "Bahamas",
              "traffic": 344280
            },
            {
              "alpha_2": "BW",
              "country": "Botswana",
              "traffic": 1021544
            },
            {
              "alpha_2": "BY",
              "country": "Belarus",
              "traffic": 4776521
            },
            {
              "alpha_2": "BZ",
              "country": "Belize",
              "traffic": 425572
            },
            {
              "alpha_2": "CA",
              "country": "Canada",
              "traffic": 67857963
            },
            {
              "alpha_2": "CD",
              "country": "Congo (Democratic Republic of the)",
              "traffic": 5185262
            },
            {
              "alpha_2": "CH",
              "country": "Switzerland",
              "traffic": 14870917
            },
            {
              "alpha_2": "CL",
              "country": "Chile",
              "traffic": 26082945
            },
            {
              "alpha_2": "CM",
              "country": "Cameroon",
              "traffic": 2728152
            },
            {
              "alpha_2": "CO",
              "country": "Colombia",
              "traffic": 59524070
            },
            {
              "alpha_2": "CR",
              "country": "Costa Rica",
              "traffic": 5223459
            },
            {
              "alpha_2": "CV",
              "country": "Cabo Verde",
              "traffic": 345491
            },
            {
              "alpha_2": "CY",
              "country": "Cyprus",
              "traffic": 2860832
            },
            {
              "alpha_2": "CZ",
              "country": "Czechia",
              "traffic": 14143433
            },
            {
              "alpha_2": "DE",
              "country": "Germany",
              "traffic": 87407058
            },
            {
              "alpha_2": "DK",
              "country": "Denmark",
              "traffic": 10544854
            },
            {
              "alpha_2": "DO",
              "country": "Dominican Republic",
              "traffic": 7934051
            },
            {
              "alpha_2": "DZ",
              "country": "Algeria",
              "traffic": 26890029
            },
            {
              "alpha_2": "EC",
              "country": "Ecuador",
              "traffic": 23131058
            },
            {
              "alpha_2": "EE",
              "country": "Estonia",
              "traffic": 2883529
            },
            {
              "alpha_2": "EG",
              "country": "Egypt",
              "traffic": 60138510
            },
            {
              "alpha_2": "ES",
              "country": "Spain",
              "traffic": 97479209
            },
            {
              "alpha_2": "ET",
              "country": "Ethiopia",
              "traffic": 8173946
            },
            {
              "alpha_2": "FI",
              "country": "Finland",
              "traffic": 12218557
            },
            {
              "alpha_2": "FR",
              "country": "France",
              "traffic": 113363781
            },
            {
              "alpha_2": "GE",
              "country": "Georgia",
              "traffic": 4464963
            },
            {
              "alpha_2": "GH",
              "country": "Ghana",
              "traffic": 5771173
            },
            {
              "alpha_2": "GR",
              "country": "Greece",
              "traffic": 14821833
            },
            {
              "alpha_2": "GT",
              "country": "Guatemala",
              "traffic": 9731572
            },
            {
              "alpha_2": "GY",
              "country": "Guyana",
              "traffic": 594673
            },
            {
              "alpha_2": "HK",
              "country": "Hong Kong",
              "traffic": 15200603
            },
            {
              "alpha_2": "HN",
              "country": "Honduras",
              "traffic": 5406454
            },
            {
              "alpha_2": "HR",
              "country": "Croatia",
              "traffic": 9263817
            },
            {
              "alpha_2": "HT",
              "country": "Haiti",
              "traffic": 1840332
            },
            {
              "alpha_2": "HU",
              "country": "Hungary",
              "traffic": 17835095
            },
            {
              "alpha_2": "ID",
              "country": "Indonesia",
              "traffic": 389028027
            },
            {
              "alpha_2": "IE",
              "country": "Ireland",
              "traffic": 11007852
            },
            {
              "alpha_2": "IL",
              "country": "Israel",
              "traffic": 10727406
            },
            {
              "alpha_2": "IN",
              "country": "India",
              "traffic": 912832501
            },
            {
              "alpha_2": "IS",
              "country": "Iceland",
              "traffic": 675518
            },
            {
              "alpha_2": "IT",
              "country": "Italy",
              "traffic": 84688571
            },
            {
              "alpha_2": "JM",
              "country": "Jamaica",
              "traffic": 1852268
            },
            {
              "alpha_2": "JO",
              "country": "Jordan",
              "traffic": 8042697
            },
            {
              "alpha_2": "JP",
              "country": "Japan",
              "traffic": 95441452
            },
            {
              "alpha_2": "KH",
              "country": "Cambodia",
              "traffic": 7672289
            },
            {
              "alpha_2": "KR",
              "country": "South Korea",
              "traffic": 50256627
            },
            {
              "alpha_2": "KW",
              "country": "Kuwait",
              "traffic": 4281486
            },
            {
              "alpha_2": "KZ",
              "country": "Kazakhstan",
              "traffic": 11972329
            },
            {
              "alpha_2": "LB",
              "country": "Lebanon",
              "traffic": 4376759
            },
            {
              "alpha_2": "LK",
              "country": "Sri Lanka",
              "traffic": 14928798
            },
            {
              "alpha_2": "LT",
              "country": "Lithuania",
              "traffic": 6391486
            },
            {
              "alpha_2": "LU",
              "country": "Luxembourg",
              "traffic": 1523406
            },
            {
              "alpha_2": "LV",
              "country": "Latvia",
              "traffic": 3302049
            },
            {
              "alpha_2": "LY",
              "country": "Libya",
              "traffic": 4207437
            },
            {
              "alpha_2": "MA",
              "country": "Morocco",
              "traffic": 25446743
            },
            {
              "alpha_2": "MD",
              "country": "Moldova",
              "traffic": 2834117
            },
            {
              "alpha_2": "ME",
              "country": "Montenegro",
              "traffic": 1184489
            },
            {
              "alpha_2": "MG",
              "country": "Madagascar",
              "traffic": 2578848
            },
            {
              "alpha_2": "MN",
              "country": "Mongolia",
              "traffic": 4559109
            },
            {
              "alpha_2": "MT",
              "country": "Malta",
              "traffic": 1351157
            },
            {
              "alpha_2": "MU",
              "country": "Mauritius",
              "traffic": 1259243
            },
            {
              "alpha_2": "MX",
              "country": "Mexico",
              "traffic": 133910734
            },
            {
              "alpha_2": "MY",
              "country": "Malaysia",
              "traffic": 53822791
            },
            {
              "alpha_2": "MZ",
              "country": "Mozambique",
              "traffic": 3471230
            },
            {
              "alpha_2": "NA",
              "country": "Namibia",
              "traffic": 955866
            },
            {
              "alpha_2": "NG",
              "country": "Nigeria",
              "traffic": 22003994
            },
            {
              "alpha_2": "NI",
              "country": "Nicaragua",
              "traffic": 3483116
            },
            {
              "alpha_2": "NL",
              "country": "Netherlands",
              "traffic": 26815297
            },
            {
              "alpha_2": "NO",
              "country": "Norway",
              "traffic": 9061717
            },
            {
              "alpha_2": "NP",
              "country": "Nepal",
              "traffic": 15329536
            },
            {
              "alpha_2": "NZ",
              "country": "New Zealand",
              "traffic": 8509630
            },
            {
              "alpha_2": "OM",
              "country": "Oman",
              "traffic": 4767176
            },
            {
              "alpha_2": "PA",
              "country": "Panama",
              "traffic": 4618634
            },
            {
              "alpha_2": "PE",
              "country": "Peru",
              "traffic": 46965995
            },
            {
              "alpha_2": "PH",
              "country": "Philippines",
              "traffic": 106661017
            },
            {
              "alpha_2": "PK",
              "country": "Pakistan",
              "traffic": 80174643
            },
            {
              "alpha_2": "PL",
              "country": "Poland",
              "traffic": 65781379
            },
            {
              "alpha_2": "PT",
              "country": "Portugal",
              "traffic": 24301593
            },
            {
              "alpha_2": "PY",
              "country": "Paraguay",
              "traffic": 4435103
            },
            {
              "alpha_2": "QA",
              "country": "Qatar",
              "traffic": 4044355
            },
            {
              "alpha_2": "RO",
              "country": "Romania",
              "traffic": 21653739
            },
            {
              "alpha_2": "RS",
              "country": "Serbia",
              "traffic": 9520785
            },
            {
              "alpha_2": "RU",
              "country": "Russia",
              "traffic": 60939183
            },
            {
              "alpha_2": "SA",
              "country": "Saudi Arabia",
              "traffic": 44801690
            },
            {
              "alpha_2": "SE",
              "country": "Sweden",
              "traffic": 16538320
            },
            {
              "alpha_2": "SG",
              "country": "Singapore",
              "traffic": 15735922
            },
            {
              "alpha_2": "SI",
              "country": "Slovenia",
              "traffic": 5063493
            },
            {
              "alpha_2": "SK",
              "country": "Slovakia",
              "traffic": 8795718
            },
            {
              "alpha_2": "SN",
              "country": "Senegal",
              "traffic": 3248129
            },
            {
              "alpha_2": "SV",
              "country": "El Salvador",
              "traffic": 4911560
            },
            {
              "alpha_2": "TH",
              "country": "Thailand",
              "traffic": 57980641
            },
            {
              "alpha_2": "TN",
              "country": "Tunisia",
              "traffic": 17931464
            },
            {
              "alpha_2": "TR",
              "country": "Turkey",
              "traffic": 127011263
            },
            {
              "alpha_2": "TT",
              "country": "Trinidad and Tobago",
              "traffic": 1289379
            },
            {
              "alpha_2": "TW",
              "country": "Taiwan",
              "traffic": 30004810
            },
            {
              "alpha_2": "UA",
              "country": "Ukraine",
              "traffic": 30696385
            },
            {
              "alpha_2": "UK",
              "country": null,
              "traffic": 102285614
            },
            {
              "alpha_2": "US",
              "country": "United States",
              "traffic": 555997415
            },
            {
              "alpha_2": "UY",
              "country": "Uruguay",
              "traffic": 5803368
            },
            {
              "alpha_2": "VE",
              "country": "Venezuela",
              "traffic": 29192805
            },
            {
              "alpha_2": "VN",
              "country": "Vietnam",
              "traffic": 91760238
            },
            {
              "alpha_2": "ZA",
              "country": "South Africa",
              "traffic": 40151075
            },
            {
              "alpha_2": "ZM",
              "country": "Zambia",
              "traffic": 2519350
            },
            {
              "alpha_2": "ZW",
              "country": "Zimbabwe",
              "traffic": 2028225
            }
          ]
        },
        "referring_domains": {
          "aggregate": 1000000,
          "records": [
            {
              "authority_score": 0,
              "referring_domains": 26284
            },
            {
              "authority_score": 1,
              "referring_domains": 2019
            },
            {
              "authority_score": 2,
              "referring_domains": 248692
            },
            {
              "authority_score": 3,
              "referring_domains": 13454
            },
            {
              "authority_score": 4,
              "referring_domains": 16830
            },
            {
              "authority_score": 5,
              "referring_domains": 25780
            },
            {
              "authority_score": 6,
              "referring_domains": 48542
            },
            {
              "authority_score": 7,
              "referring_domains": 45794
            },
            {
              "authority_score": 8,
              "referring_domains": 49477
            },
            {
              "authority_score": 9,
              "referring_domains": 47258
            },
            {
              "authority_score": 10,
              "referring_domains": 37755
            },
            {
              "authority_score": 11,
              "referring_domains": 27116
            },
            {
              "authority_score": 12,
              "referring_domains": 20038
            },
            {
              "authority_score": 13,
              "referring_domains": 16374
            },
            {
              "authority_score": 14,
              "referring_domains": 14932
            },
            {
              "authority_score": 15,
              "referring_domains": 14976
            },
            {
              "authority_score": 16,
              "referring_domains": 15597
            },
            {
              "authority_score": 17,
              "referring_domains": 16129
            },
            {
              "authority_score": 18,
              "referring_domains": 17194
            },
            {
              "authority_score": 19,
              "referring_domains": 17707
            },
            {
              "authority_score": 20,
              "referring_domains": 18113
            },
            {
              "authority_score": 21,
              "referring_domains": 17815
            },
            {
              "authority_score": 22,
              "referring_domains": 18045
            },
            {
              "authority_score": 23,
              "referring_domains": 17618
            },
            {
              "authority_score": 24,
              "referring_domains": 17145
            },
            {
              "authority_score": 25,
              "referring_domains": 16365
            },
            {
              "authority_score": 26,
              "referring_domains": 15363
            },
            {
              "authority_score": 27,
              "referring_domains": 14174
            },
            {
              "authority_score": 28,
              "referring_domains": 13236
            },
            {
              "authority_score": 29,
              "referring_domains": 12129
            },
            {
              "authority_score": 30,
              "referring_domains": 10950
            },
            {
              "authority_score": 31,
              "referring_domains": 9696
            },
            {
              "authority_score": 32,
              "referring_domains": 8896
            },
            {
              "authority_score": 33,
              "referring_domains": 8183
            },
            {
              "authority_score": 34,
              "referring_domains": 7405
            },
            {
              "authority_score": 35,
              "referring_domains": 6654
            },
            {
              "authority_score": 36,
              "referring_domains": 6311
            },
            {
              "authority_score": 37,
              "referring_domains": 5676
            },
            {
              "authority_score": 38,
              "referring_domains": 5081
            },
            {
              "authority_score": 39,
              "referring_domains": 4617
            },
            {
              "authority_score": 40,
              "referring_domains": 4287
            },
            {
              "authority_score": 41,
              "referring_domains": 4021
            },
            {
              "authority_score": 42,
              "referring_domains": 3545
            },
            {
              "authority_score": 43,
              "referring_domains": 3304
            },
            {
              "authority_score": 44,
              "referring_domains": 3042
            },
            {
              "authority_score": 45,
              "referring_domains": 2633
            },
            {
              "authority_score": 46,
              "referring_domains": 2435
            },
            {
              "authority_score": 47,
              "referring_domains": 2126
            },
            {
              "authority_score": 48,
              "referring_domains": 1992
            },
            {
              "authority_score": 49,
              "referring_domains": 1748
            },
            {
              "authority_score": 50,
              "referring_domains": 1502
            },
            {
              "authority_score": 51,
              "referring_domains": 1313
            },
            {
              "authority_score": 52,
              "referring_domains": 1287
            },
            {
              "authority_score": 53,
              "referring_domains": 1093
            },
            {
              "authority_score": 54,
              "referring_domains": 943
            },
            {
              "authority_score": 55,
              "referring_domains": 799
            },
            {
              "authority_score": 56,
              "referring_domains": 678
            },
            {
              "authority_score": 57,
              "referring_domains": 626
            },
            {
              "authority_score": 58,
              "referring_domains": 502
            },
            {
              "authority_score": 59,
              "referring_domains": 524
            },
            {
              "authority_score": 60,
              "referring_domains": 469
            },
            {
              "authority_score": 61,
              "referring_domains": 424
            },
            {
              "authority_score": 62,
              "referring_domains": 390
            },
            {
              "authority_score": 63,
              "referring_domains": 373
            },
            {
              "authority_score": 64,
              "referring_domains": 335
            },
            {
              "authority_score": 65,
              "referring_domains": 349
            },
            {
              "authority_score": 66,
              "referring_domains": 333
            },
            {
              "authority_score": 67,
              "referring_domains": 362
            },
            {
              "authority_score": 68,
              "referring_domains": 326
            },
            {
              "authority_score": 69,
              "referring_domains": 304
            },
            {
              "authority_score": 70,
              "referring_domains": 264
            },
            {
              "authority_score": 71,
              "referring_domains": 244
            },
            {
              "authority_score": 72,
              "referring_domains": 224
            },
            {
              "authority_score": 73,
              "referring_domains": 202
            },
            {
              "authority_score": 74,
              "referring_domains": 148
            },
            {
              "authority_score": 75,
              "referring_domains": 148
            },
            {
              "authority_score": 76,
              "referring_domains": 142
            },
            {
              "authority_score": 77,
              "referring_domains": 138
            },
            {
              "authority_score": 78,
              "referring_domains": 102
            },
            {
              "authority_score": 79,
              "referring_domains": 102
            },
            {
              "authority_score": 80,
              "referring_domains": 84
            },
            {
              "authority_score": 81,
              "referring_domains": 78
            },
            {
              "authority_score": 82,
              "referring_domains": 70
            },
            {
              "authority_score": 83,
              "referring_domains": 70
            },
            {
              "authority_score": 84,
              "referring_domains": 64
            },
            {
              "authority_score": 85,
              "referring_domains": 48
            },
            {
              "authority_score": 86,
              "referring_domains": 50
            },
            {
              "authority_score": 87,
              "referring_domains": 35
            },
            {
              "authority_score": 88,
              "referring_domains": 33
            },
            {
              "authority_score": 89,
              "referring_domains": 31
            },
            {
              "authority_score": 90,
              "referring_domains": 31
            },
            {
              "authority_score": 91,
              "referring_domains": 29
            },
            {
              "authority_score": 92,
              "referring_domains": 24
            },
            {
              "authority_score": 93,
              "referring_domains": 19
            },
            {
              "authority_score": 94,
              "referring_domains": 20
            },
            {
              "authority_score": 95,
              "referring_domains": 18
            },
            {
              "authority_score": 96,
              "referring_domains": 10
            },
            {
              "authority_score": 97,
              "referring_domains": 10
            },
            {
              "authority_score": 98,
              "referring_domains": 15
            },
            {
              "authority_score": 99,
              "referring_domains": 16
            },
            {
              "authority_score": 100,
              "referring_domains": 46
            }
          ]
        }
      }
    }
  }
}
```

See the endpoint documentation for the complete response schema and available fields.