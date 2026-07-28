# CrUX Report API Examples

Code examples for integrating with the **CrUX Report** endpoint using different programming languages, HTTP clients, and request libraries. These examples demonstrate how to authenticate requests, send parameters, and process API responses.

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

This document provides example requests for the **CrUX Report** endpoint.

Examples are available for multiple programming languages and HTTP clients, allowing developers to integrate the API using their preferred technology stack.

## Endpoint

```
POST https://enterprise-seo-metrics.p.rapidapi.com/crux-report
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
| `device` | string | No | Device filter. Defaults to `all`. |

# Code Snippets

## C

### Libcurl

```c++
CURL *hnd = curl_easy_init();

curl_easy_setopt(hnd, CURLOPT_CUSTOMREQUEST, "POST");
curl_easy_setopt(hnd, CURLOPT_URL, "https://enterprise-seo-metrics.p.rapidapi.com/crux-report");

struct curl_slist *headers = NULL;
headers = curl_slist_append(headers, "x-rapidapi-key: YOUR_API_KEY");
headers = curl_slist_append(headers, "x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com");
headers = curl_slist_append(headers, "Content-Type: application/x-www-form-urlencoded");
curl_easy_setopt(hnd, CURLOPT_HTTPHEADER, headers);

curl_easy_setopt(hnd, CURLOPT_POSTFIELDS, "url=https%3A%2F%2Fgoogle.com&device=all");

CURLcode ret = curl_easy_perform(hnd);
```

## Clojure

### clj-http

```clojure
(require '[clj-http.client :as client])

(client/post "https://enterprise-seo-metrics.p.rapidapi.com/crux-report" {:headers {:x-rapidapi-key "YOUR_API_KEY"
                                                                                        :x-rapidapi-host "enterprise-seo-metrics.p.rapidapi.com"}
                                                                              :form-params {:url "https://google.com"
                                                                                            :device "all"}})
```

## C#

### HttpClient

```csharp
using System.Net.Http.Headers;
var client = new HttpClient();
var request = new HttpRequestMessage
{
	Method = HttpMethod.Post,
	RequestUri = new Uri("https://enterprise-seo-metrics.p.rapidapi.com/crux-report"),
	Headers =
	{
		{ "x-rapidapi-key", "YOUR_API_KEY" },
		{ "x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com" },
	},
	Content = new FormUrlEncodedContent(new Dictionary<string, string>
	{
		{ "url", "https://google.com" },
		{ "device", "all" },
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
var client = new RestClient("https://enterprise-seo-metrics.p.rapidapi.com/crux-report");
var request = new RestRequest(Method.POST);
request.AddHeader("x-rapidapi-key", "YOUR_API_KEY");
request.AddHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com");
request.AddHeader("Content-Type", "application/x-www-form-urlencoded");
request.AddParameter("application/x-www-form-urlencoded", "url=https%3A%2F%2Fgoogle.com&device=all", ParameterType.RequestBody);
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

	url := "https://enterprise-seo-metrics.p.rapidapi.com/crux-report"

	payload := strings.NewReader("url=https%3A%2F%2Fgoogle.com&device=all")

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
POST /crux-report HTTP/1.1
X-Rapidapi-Key: YOUR_API_KEY
X-Rapidapi-Host: enterprise-seo-metrics.p.rapidapi.com
Content-Type: application/x-www-form-urlencoded
Host: enterprise-seo-metrics.p.rapidapi.com
Content-Length: 43

url=https%3A%2F%2Fgoogle.com&device=all
```

## Java

### AsyncHttp

```java
AsyncHttpClient client = new DefaultAsyncHttpClient();
client.prepare("POST", "https://enterprise-seo-metrics.p.rapidapi.com/crux-report")
	.setHeader("x-rapidapi-key", "YOUR_API_KEY")
	.setHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.setHeader("Content-Type", "application/x-www-form-urlencoded")
	.setBody("url=https%3A%2F%2Fgoogle.com&device=all")
	.execute()
	.toCompletableFuture()
	.thenAccept(System.out::println)
	.join();

client.close();
```

### java.net.http

```java
HttpRequest request = HttpRequest.newBuilder()
		.uri(URI.create("https://enterprise-seo-metrics.p.rapidapi.com/crux-report"))
		.header("x-rapidapi-key", "YOUR_API_KEY")
		.header("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
		.header("Content-Type", "application/x-www-form-urlencoded")
		.method("POST", HttpRequest.BodyPublishers.ofString("url=https%3A%2F%2Fgoogle.com&device=all"))
		.build();
HttpResponse<String> response = HttpClient.newHttpClient().send(request, HttpResponse.BodyHandlers.ofString());
System.out.println(response.body());
```

### OkHttp

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/x-www-form-urlencoded");
RequestBody body = RequestBody.create(mediaType, "url=https%3A%2F%2Fgoogle.com&device=all");
Request request = new Request.Builder()
	.url("https://enterprise-seo-metrics.p.rapidapi.com/crux-report")
	.post(body)
	.addHeader("x-rapidapi-key", "YOUR_API_KEY")
	.addHeader("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.addHeader("Content-Type", "application/x-www-form-urlencoded")
	.build();

Response response = client.newCall(request).execute();
```

### Unirest

```java
HttpResponse<String> response = Unirest.post("https://enterprise-seo-metrics.p.rapidapi.com/crux-report")
	.header("x-rapidapi-key", "YOUR_API_KEY")
	.header("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
	.header("Content-Type", "application/x-www-form-urlencoded")
	.body("url=https%3A%2F%2Fgoogle.com&device=all")
	.asString();
```

## JavaScript

### XMLHttpRequest

```javascript
const data = 'url=https%3A%2F%2Fgoogle.com&device=all';

const xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener('readystatechange', function () {
	if (this.readyState === this.DONE) {
		console.log(this.responseText);
	}
});

xhr.open('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/crux-report');
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
encodedParams.set('device', 'all');

const options = {
  method: 'POST',
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/crux-report',
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
const url = 'https://enterprise-seo-metrics.p.rapidapi.com/crux-report';
const options = {
	method: 'POST',
	headers: {
		'x-rapidapi-key': 'YOUR_API_KEY',
		'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
		'Content-Type': 'application/x-www-form-urlencoded'
	},
	body: new URLSearchParams({
		url: 'https://google.com',
		device: 'all'
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
	url: 'https://enterprise-seo-metrics.p.rapidapi.com/crux-report',
	method: 'POST',
	headers: {
		'x-rapidapi-key': 'YOUR_API_KEY',
		'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
		'Content-Type': 'application/x-www-form-urlencoded'
	},
	data: {
		url: 'https://google.com',
		device: 'all'
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
val body = RequestBody.create(mediaType, "url=https%3A%2F%2Fgoogle.com&device=all")
val request = Request.Builder()
	.url("https://enterprise-seo-metrics.p.rapidapi.com/crux-report")
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
	path: '/crux-report',
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
  device: 'all'
}));
req.end();
```

### Request

```javascript
const request = require('request');

const options = {
  method: 'POST',
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/crux-report',
  headers: {
    'x-rapidapi-key': 'YOUR_API_KEY',
    'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  form: {
    url: 'https://google.com',
    device: 'all'
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

const req = unirest('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/crux-report');

req.headers({
	'x-rapidapi-key': 'YOUR_API_KEY',
	'x-rapidapi-host': 'enterprise-seo-metrics.p.rapidapi.com',
	'Content-Type': 'application/x-www-form-urlencoded'
});

req.form({
	url: 'https://google.com',
	device: 'all'
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
encodedParams.set('device', 'all');

const options = {
  method: 'POST',
  url: 'https://enterprise-seo-metrics.p.rapidapi.com/crux-report',
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
encodedParams.set('device', 'all');

const url = 'https://enterprise-seo-metrics.p.rapidapi.com/crux-report';
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
[postData appendData:[@"&device=all" dataUsingEncoding:NSUTF8StringEncoding]];

NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:@"https://enterprise-seo-metrics.p.rapidapi.com/crux-report"]
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

let uri = Uri.of_string "https://enterprise-seo-metrics.p.rapidapi.com/crux-report" in
let headers = Header.add_list (Header.init ()) [
	("x-rapidapi-key", "YOUR_API_KEY");
	("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com");
	("Content-Type", "application/x-www-form-urlencoded");
] in
let body = Cohttp_lwt_body.of_string "url=https%3A%2F%2Fgoogle.com&device=all" in

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
	CURLOPT_URL => "https://enterprise-seo-metrics.p.rapidapi.com/crux-report",
	CURLOPT_RETURNTRANSFER => true,
	CURLOPT_ENCODING => "",
	CURLOPT_MAXREDIRS => 10,
	CURLOPT_TIMEOUT => 30,
	CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	CURLOPT_CUSTOMREQUEST => "POST",
	CURLOPT_POSTFIELDS => "url=https%3A%2F%2Fgoogle.com&device=all",
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

$response = $client->request('POST', 'https://enterprise-seo-metrics.p.rapidapi.com/crux-report', [
	'form_params' => [
		'url' => 'https://google.com',
		'device' => 'all'
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
$request->setUrl('https://enterprise-seo-metrics.p.rapidapi.com/crux-report');
$request->setMethod(HTTP_METH_POST);

$request->setHeaders([
	'x-rapidapi-key' => 'YOUR_API_KEY',
	'x-rapidapi-host' => 'enterprise-seo-metrics.p.rapidapi.com',
	'Content-Type' => 'application/x-www-form-urlencoded'
]);

$request->setContentType('application/x-www-form-urlencoded');
$request->setPostFields([
	'url' => 'https://google.com',
	'device' => 'all'
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
	'device' => 'all'
]));

$request->setRequestUrl('https://enterprise-seo-metrics.p.rapidapi.com/crux-report');
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
$response = Invoke-WebRequest -Uri 'https://enterprise-seo-metrics.p.rapidapi.com/crux-report' -Method POST -Headers $headers -ContentType 'application/x-www-form-urlencoded' -Body 'url=https%3A%2F%2Fgoogle.com&device=all'
```

### Invoke-RestMethod

```powershell
$headers=@{}
$headers.Add("x-rapidapi-key", "YOUR_API_KEY")
$headers.Add("x-rapidapi-host", "enterprise-seo-metrics.p.rapidapi.com")
$headers.Add("Content-Type", "application/x-www-form-urlencoded")
$response = Invoke-RestMethod -Uri 'https://enterprise-seo-metrics.p.rapidapi.com/crux-report' -Method POST -Headers $headers -ContentType 'application/x-www-form-urlencoded' -Body 'url=https%3A%2F%2Fgoogle.com&device=all'
```

## Python

### http.client

```python
import http.client

conn = http.client.HTTPSConnection("enterprise-seo-metrics.p.rapidapi.com")

payload = "url=https%3A%2F%2Fgoogle.com&device=all"

headers = {
    'x-rapidapi-key': "YOUR_API_KEY",
    'x-rapidapi-host': "enterprise-seo-metrics.p.rapidapi.com",
    'Content-Type': "application/x-www-form-urlencoded"
}

conn.request("POST", "/crux-report", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

### Requests

```python
import requests

url = "https://enterprise-seo-metrics.p.rapidapi.com/crux-report"

payload = {
	"url": "https://google.com",
	"device": "all"
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

url <- "https://enterprise-seo-metrics.p.rapidapi.com/crux-report"

payload <- "url=https%3A%2F%2Fgoogle.com&device=all"

encode <- "form"

response <- VERB("POST", url, body = payload, add_headers('x-rapidapi-key' = 'YOUR_API_KEY', 'x-rapidapi-host' = 'enterprise-seo-metrics.p.rapidapi.com'), content_type("application/x-www-form-urlencoded"), encode = encode)

content(response, "text")
```

## Ruby

### net::http

```ruby
require 'uri'
require 'net/http'

url = URI("https://enterprise-seo-metrics.p.rapidapi.com/crux-report")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true

request = Net::HTTP::Post.new(url)
request["x-rapidapi-key"] = 'YOUR_API_KEY'
request["x-rapidapi-host"] = 'enterprise-seo-metrics.p.rapidapi.com'
request["Content-Type"] = 'application/x-www-form-urlencoded'
request.body = "url=https%3A%2F%2Fgoogle.com&device=all"

response = http.request(request)
puts response.read_body
```

## Shell

### cURL

```shell
curl --request POST \
	--url https://enterprise-seo-metrics.p.rapidapi.com/crux-report \
	--header 'Content-Type: application/x-www-form-urlencoded' \
	--header 'x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com' \
	--header 'x-rapidapi-key: YOUR_API_KEY' \
	--data url=https://google.com \
	--data device=all
```

### HTTPie

```shell
http --form POST https://enterprise-seo-metrics.p.rapidapi.com/crux-report \
	Content-Type:application/x-www-form-urlencoded \
	x-rapidapi-host:enterprise-seo-metrics.p.rapidapi.com \
	x-rapidapi-key:YOUR_API_KEY \
	url=https://google.com \
	device=all
```

### Wget

```shell
wget --quiet \
	--method POST \
	--header 'x-rapidapi-key: YOUR_API_KEY' \
	--header 'x-rapidapi-host: enterprise-seo-metrics.p.rapidapi.com' \
	--header 'Content-Type: application/x-www-form-urlencoded' \
	--body-data 'url=https%3A%2F%2Fgoogle.com&device=all' \
	--output-document \
	- https://enterprise-seo-metrics.p.rapidapi.com/crux-report
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
postData.append("&device=all".data(using: String.Encoding.utf8)!)

let request = NSMutableURLRequest(url: NSURL(string: "https://enterprise-seo-metrics.p.rapidapi.com/crux-report")! as URL,
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
    "performance_ms": 113,
    "url": "https://google.com",
    "metrics": {
      "round_trip_time": {
        "histogram": [
          {
            "start": 0,
            "end": 75,
            "density": 0.1999
          },
          {
            "start": 75,
            "end": 275,
            "density": 0.4765
          },
          {
            "start": 275,
            "density": 0.3236
          }
        ],
        "percentiles": {
          "p75": 363
        }
      },
      "cumulative_layout_shift": {
        "histogram": [
          {
            "start": "0.00",
            "end": "0.10",
            "density": 0.9936
          },
          {
            "start": "0.10",
            "end": "0.25",
            "density": 0.002
          },
          {
            "start": "0.25",
            "density": 0.0044
          }
        ],
        "percentiles": {
          "p75": "0.00"
        }
      },
      "largest_contentful_paint": {
        "histogram": [
          {
            "start": 0,
            "end": 2500,
            "density": 0.757
          },
          {
            "start": 2500,
            "end": 4000,
            "density": 0.122
          },
          {
            "start": 4000,
            "density": 0.121
          }
        ],
        "percentiles": {
          "p75": 2405
        }
      },
      "largest_contentful_paint_image_resource_load_delay": {
        "percentiles": {
          "p75": 1047
        }
      },
      "largest_contentful_paint_image_resource_load_duration": {
        "percentiles": {
          "p75": 228
        }
      },
      "largest_contentful_paint_resource_type": {
        "fractions": {
          "image": 0.1688,
          "text": 0.8312
        }
      },
      "experimental_time_to_first_byte": {
        "histogram": [
          {
            "start": 0,
            "end": 800,
            "density": 0.6595
          },
          {
            "start": 800,
            "end": 1800,
            "density": 0.1839
          },
          {
            "start": 1800,
            "density": 0.1566
          }
        ],
        "percentiles": {
          "p75": 1144
        }
      },
      "first_contentful_paint": {
        "histogram": [
          {
            "start": 0,
            "end": 1800,
            "density": 0.6761
          },
          {
            "start": 1800,
            "end": 3000,
            "density": 0.1361
          },
          {
            "start": 3000,
            "density": 0.1879
          }
        ],
        "percentiles": {
          "p75": 2309
        }
      },
      "form_factors": {
        "fractions": {
          "phone": 0.1426,
          "tablet": 0,
          "desktop": 0.8574
        }
      },
      "interaction_to_next_paint": {
        "histogram": [
          {
            "start": 0,
            "end": 200,
            "density": 0.795
          },
          {
            "start": 200,
            "end": 500,
            "density": 0.189
          },
          {
            "start": 500,
            "density": 0.016
          }
        ],
        "percentiles": {
          "p75": 140
        }
      },
      "largest_contentful_paint_image_element_render_delay": {
        "percentiles": {
          "p75": 289
        }
      },
      "largest_contentful_paint_image_time_to_first_byte": {
        "percentiles": {
          "p75": 751
        }
      }
    }
  }
}
```

See the endpoint documentation for the complete response schema and available fields.