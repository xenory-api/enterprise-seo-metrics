# Moz Metrics API Examples

Code examples for integrating with the **Moz Metrics** endpoint using different programming languages, HTTP clients, and request libraries. These examples demonstrate how to authenticate requests, send parameters, and process API responses.

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

This document provides example requests for the **Moz Metrics** endpoint.

Examples are available for multiple programming languages and HTTP clients, allowing developers to integrate the API using their preferred technology stack.

## Endpoint

```
POST https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics
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
curl_easy_setopt(hnd, CURLOPT_URL, "https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics");

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

(client/post "https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics" {:headers {:x-rapidapi-key "YOUR_API_KEY"
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
	RequestUri = new Uri("https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics"),
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
var client = new RestClient("https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics");
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

	url := "https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics"

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
POST /moz-metrics HTTP/1.1
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
client.prepare("POST", "https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics")
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
		.uri(URI.create("https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics"))
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
	.url("https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics")
	.post(body)
	.addHeader("x-rapidapi-key", "YOUR_API_KEY")
	.addHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.addHeader("Content-Type", "application/x-www-form-urlencoded")
	.build();

Response response = client.newCall(request).execute();
```

### Unirest

```java
HttpResponse<String> response = Unirest.post("https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics")
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

xhr.open('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics');
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
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics',
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
const url = 'https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics';
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
	url: 'https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics',
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
	.url("https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics")
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
	path: '/moz-metrics',
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
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics',
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

const req = unirest('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics');

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
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics',
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

const url = 'https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics';
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

NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:@"https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics"]
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

let uri = Uri.of_string "https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics" in
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
	CURLOPT_URL => "https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics",
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

$response = $client->request('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics', [
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
$request->setUrl('https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics');
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

$request->setRequestUrl('https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics');
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
$response = Invoke-WebRequest -Uri 'https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics' -Method POST -Headers $headers -ContentType 'application/x-www-form-urlencoded' -Body 'domain=google.com'
```

### Invoke-RestMethod

```powershell
$headers=@{}
$headers.Add("x-rapidapi-key", "YOUR_API_KEY")
$headers.Add("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
$headers.Add("Content-Type", "application/x-www-form-urlencoded")
$response = Invoke-RestMethod -Uri 'https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics' -Method POST -Headers $headers -ContentType 'application/x-www-form-urlencoded' -Body 'domain=google.com'
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

conn.request("POST", "/moz-metrics", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Requests

```python
import requests

url = "https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics"

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

url <- "https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics"

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

url = URI("https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics")

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
	--url https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics \
	--header 'Content-Type: application/x-www-form-urlencoded' \
	--header 'x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com' \
	--header 'x-rapidapi-key: YOUR_API_KEY' \
	--data domain=google.com
```

### HTTPie

```shell
http --form POST https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics \
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
	- https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics
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

let request = NSMutableURLRequest(url: NSURL(string: "https://enterprise-seo-metrics.p.rapidapi.com/moz-metrics")! as URL,
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
    "performance_ms": 59,
    "domain": "google.com",
    "metrics": {
      "domain_authority": 94,
      "page_authority": 91,
      "spam_score": 1,
      "total_pages": 1601251461,
      "deleted_pages": 164168712,
      "pages_crawled": 17104973,
      "external_pages": 1601237259,
      "nofollow_pages": 130780890,
      "outbound_pages": 4977777,
      "redirect_pages": 361022707,
      "link_propensity": 0.000010230943,
      "outbound_domains": 175,
      "deleted_root_domains": 185266,
      "root_domains_linking": 1312893,
      "indirect_root_domains": 351671,
      "nofollow_root_domains": 210370,
      "external_indirect_pages": 216149555,
      "external_nofollow_pages": 130780890,
      "external_redirect_pages": 361008517
    }
  }
}
```

See the endpoint documentation for the complete response schema and available fields.