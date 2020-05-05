---


---

<h1 id="part-2">Part 2</h1>
<p>This section will aim to give you an understanding of what APIs are and why we use them.</p>
<h1 id="what-is-an-api">What is an API?</h1>
<p>An API is a means for a company, organization, or individual to make their data or functions/features accessible and integratable for a large amount of developers without the need for the developer themself to put in a large amount of overhead work. For an example, the <a href="https://openweathermap.org/api">OpenWeatherMap API</a> provides developers with a way to access on-demand and reliable weather data for locations all across the world without the developer needing to do any work in the collection of that data. They simply make a quick request to the API and they will get data back instantly. Another example is the <a href="https://api.ratesapi.io/api/latest">Rates API</a> which is a free API that displays accurate and real-time exchange rates for foreign and domestic currency.</p>
<h1 id="what-can-you-use-apis-for">What can you use APIs for?</h1>
<p>I think the answer to this question should be pretty clear by now hopefully! You can use APIs to access data from companies, organizations, or individuals, (e.g: going back to the OpenWeatherMap API, you can use it in your application to get weather data on demand for your users) and you can use APIs to access certain functions from different providers as well. That all sounds good, but how do we start using APIs?</p>
<h1 id="how-do-you-use-an-api">How do you use an API?</h1>
<p>The primary method of communication for <em>most</em> APIs is through HTTP requests. You would simply make an HTTP (GET,POST,CREATE,UPDATE,etc) request to an endpoint. As mentioned earlier, the most common types of HTTP requests are GET and POST.</p>
<p>An endpoint is an external facing service that is open to the internet, or your internal network that accepts requests to the API, processes them, and then returns back a response! An endpoint could be an IP address (e.g 192.180.0.1) or an endpoint could be a web link (<a href="http://mywebsite.com/api">http://mywebsite.com/api</a>). Most API endpoints are web links like the latter. We will not get into the details of how they work and how to write them, because that’s out of the scope of this workshop, instead we will focus on how to use them, such as how to make requests to them and do stuff with the data that we get back!</p>
<h1 id="making-a-request-to-an-api">Making a request to an API</h1>
<p>In this very simple demonstration, we will make a GET request to the Rates API, the Rates API is an API that displays and returns back the current exchange rates for foreign currency. To make a request to this API and get our desired information back all you have to do is send it an HTTP GET request! You can very simply make an HTTP GET request using a browser by just putting the link to the API in the address bar of your browser. Try it out! Copy this link and paste it into your address bar in another tab: <code>https://api.ratesapi.io/api/latest</code></p>
<p>You should see a bunch of seemingly messy information that looks something like this:</p>
<p><code>{"base":"EUR","rates":{"GBP":0.84325,"HKD":8.4658,"IDR":14919.11,"ILS":3.72,"DKK":7.4721,"INR":77.6945,"CHF":1.0667,"MXN":20.3563,"CZK":24.965,"SGD":1.5127,"THB":34.082,"HRK":7.459,"MYR":4.5059,"NOK":10.0953,"CNY":7.6025,"BGN":1.9558,"PHP":55.061,"SEK":10.5373,"PLN":4.2569,"ZAR":16.2331,"CAD":1.4495,"ISK":137.9,"BRL":4.6995,"RON":4.7693,"NZD":1.7055,"TRY":6.5775,"JPY":119.73,"RUB":69.3198,"KRW":1290.63,"USD":1.0901,"HUF":337.93,"AUD":1.626},"date":"2020-02-11"}</code></p>
<h1 id="what-is-this-stuff-how-can-we-use-it">What is this stuff? How can we use it?</h1>
<p>The response that you got (the html you saw in the browser after putting the link in the address bar) is in a format called JSON. the JSON format is a data format that a very large majority of APIs will use, because it is supported well and it is simple to interpret and use programatically. If we clean it up a little bit with a tool called <a href="https://jsonlint.com/">JSON Lint</a> we can see that the data itself is actually quite neatly arranged:</p>
<pre><code>{
	"base": "EUR",
	"rates": {
		"GBP": 0.84325,
		"HKD": 8.4658,
		"IDR": 14919.11,
		"ILS": 3.72,
		"DKK": 7.4721,
		"INR": 77.6945,
		"CHF": 1.0667,
		"MXN": 20.3563,
		"CZK": 24.965,
		"SGD": 1.5127,
		"THB": 34.082,
		"HRK": 7.459,
		"MYR": 4.5059,
		"NOK": 10.0953,
		"CNY": 7.6025,
		"BGN": 1.9558,
		"PHP": 55.061,
		"SEK": 10.5373,
		"PLN": 4.2569,
		"ZAR": 16.2331,
		"CAD": 1.4495,
		"ISK": 137.9,
		"BRL": 4.6995,
		"RON": 4.7693,
		"NZD": 1.7055,
		"TRY": 6.5775,
		"JPY": 119.73,
		"RUB": 69.3198,
		"KRW": 1290.63,
		"USD": 1.0901,
		"HUF": 337.93,
		"AUD": 1.626
	},
	"date": "2020-02-11"
}
</code></pre>
<p>Clean, right?<br>
JSON stores data in key-value pairs, similar to that of a Dictionary in python, or a HashMap in java, if you’ve used them before. In the data that we got, we can see that in <code>"base": "EUR",</code> the key is <em>base</em> and the value is <em>EUR</em>. If you look one line after that, the key is <em>rates</em> and the value is another JSON object that consists of all of the exchange rates! If you’re familiar with Python, you can think of it as a bunch of nested dictionaries! Or you can think of it as mappings within mappings, with no real limits.</p>
<p>Now, we see that the base currency is EUR, but we’re not in Europe! (unfortunately) How do we change that? Luckily for us, the API developer has written a feature that lets us change that by sending a request with a <em>parameter</em> to the API!</p>
<h1 id="parameters">Parameters</h1>
<p>A lot of the times, APIs will have things called parameters, what parameters do is they allow you to request different things from the API. In our case, we want to request that the base currency be “CAD” instead of “EUR”. We will do this by modifying a parameter in the request to the API called “base”. Like JSON, parameters are also with the request to the API in key=value pairs. They look like this for a GET request:</p>
<p><code>http://mywebsite.com/api?a_parameter=a_value</code></p>
<p>The <code>?</code> denotes the start of a list of parameters!<br>
What if you wanted to have multiple parameters? It would look like this:</p>
<p><code>http://mywebsite.com/api?a_parameter=a_value&amp;another_parameter=another_value</code></p>
<p>Simple? right?</p>
<p>Let’s try it with the rates API. The parameter is called “base” and the value is called “CAD”, so our GET request would look like this:</p>
<p><code>https://api.ratesapi.io/api/latest?base=CAD</code></p>
<p>After you type that into your browser, you should see a similar response to earlier, but with the base currency now being CAD!</p>
<p>This is called url-encoded parameters. We are giving the API options for it to handle in our GET request so that we can manipulate the information that we get back!</p>
<h1 id="get-and-post-requests-and-parameters">GET and POST requests and Parameters</h1>
<p>Parameters are sent in the URL of the API for a GET request, like above:</p>
<p><code>https://api.ratesapi.io/api/latest?base=USD</code></p>
<p>However, with a POST request, the parameters for the request are sent in what’s called the <em>body</em> of the request, the request ends up looking something like this:</p>
<pre class=" language-post"><code class="prism  language-post">User-Agent: HTTPTool/1.0
Content-Type: application/x-www-form-urlencoded
Content-Length: 32

a_parameter=a_value&amp;another_parameter=another_value
</code></pre>
<p>The parameters are after the headers of the request, and are not in the URL!</p>
<p>You’ve now learned how to make a request to an API and how they work in a generalized sense, continue to the next part where we start programatically using the data!</p>
<p><a href="https://github.com/Kav-K/RUHacks-API-Workshop/tree/part-3"></a></p><h3><a href="https://github.com/Kav-K/RUHacks-API-Workshop/tree/part-3">Click here to go to Part 3 (or switch your branch to part-3)</a></h3><p></p>

