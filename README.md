---


---

<h1 id="part-3">Part 3</h1>
<p>This section will aim to give you an understanding of how to programatically make API requests and use the data</p>
<h1 id="some-notes-before-starting">Some notes before starting</h1>
<p>You’re going to want to clone this repository, and switch to this branch (part-3) if you want the python files to follow along! Or you can download the file directly from the web version of github by just clicking on it and clicking download!<br>
You will most likely also need to type ‘pip install requests’ in your command line for the code to work, as it uses a library called requests to fulfil our HTTP requests to the APIs!</p>
<h1 id="a-simple-python-to-make-http-get-requests">A simple Python to make HTTP GET requests</h1>
<p>The program <a href="http://simple-python-request-get.py">simple-python-request-get.py</a> is a very simple example of how to use python to programatically make HTTP GET requests and to use the data that is returned from it! It uses a library called “requests” to make a GET request to any URL that you specify, then it saves the output in a variable called <code>api_request_response</code>, we then convert it into JSON and save it in a variable called <code>response_data</code>.</p>
<p>JSON and Python are friendly, in fact, they’re so friendly that you can treat a JSON object in python as a simple dictionary! This makes sense, because a python dictionary is a store of key:value pairs, and so is JSON.</p>
<p>If you need a refresher, a python dictionary looks like (and is defined as) this:</p>
<pre><code>fruit_colors = {
  "apple": "red",
  "orange": "orange",
  "banana": "yellow"
}
</code></pre>
<p>This looks familiar, right? Yes! It does, because it is identical to how a JSON object looks! In fact, it is syntactically the same as the response that we got when making a request to the Rates API earlier in this workshop!</p>
<p>The equivalent JSON object for fruit_colors would look like this:</p>
<pre><code>   "fruit_colors": {
   "apple":"red",
   "orange":"orange",
   "banana":"yellow"
}
</code></pre>
<p>In python, to obtain a value from our fruit_colors dictionary, we would do something like <code>fruit_colors[key]</code> with the <em>key</em> being the value of the key in the pair we want to find the value for (Yeah, thats a mouthful). For example:</p>
<p><code>banana_color = fruit_colors['banana']</code></p>
<p>This would return us the value for the key ‘banana’ in our dictionary fruit_colors!</p>
<p>Now, lets go back to the reponse that we got from earlier when we made a request to the Rates API:</p>
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
<p>What would the python dictionary equivalent of this big JSON object look like? Hint: it would look <em>very</em> similar:</p>
<pre><code>
rates_dictionary = {
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
<p>What did we do? We <em>literally</em> just added <code>rates_dictionary =</code> to the beginning of that JSON block, as you can see, JSON and python dictionaries are considered identical.</p>
<p>Now that we can think of JSON objects as python dictionaries, we know that we can access individual pieces of data just like we did with the fruit_colors dictionary. For example, if we wanted to access the base currency, we would do something like</p>
<p><code>base_currency = rates_dictionary['base']</code></p>
<p>If we wanted to access the exchange rate of BGN, we would do something like</p>
<p><code>bgn_rate = rates_dictionary['rates']['BGN']</code></p>
<p>The block <code>rates_dictionary['rates']</code> is what we call a <em>multilevel dictionary</em>.</p>
<p>Now that you have been refreshed on python dictionaries and its relationship with JSON, feel free to try out the program <em><a href="http://simple-python-get-example.py">simple-python-get-example.py</a></em> and see how it works! It’s a short and concise program</p>
<h1 id="a-post-request-whats-a-post-request">A POST request? What’s a POST request?</h1>
<p>Now that we have some understanding of HTTP GET and how we would make such a request with python, lets quickly talk about POST requests. I know you guys want to get to google cloud already but that part will be very quick and simple once we get this stuff out of the way!</p>
<p>A POST request is a HTTP request that is used to submit data to an endpoint. Usually, they are used by APIs that require the user to submit some sort of data, usually, it will be data that cannot be submitted through a simple parameter in the URL. It is also considered slightly more <em>secure</em> because parameters are not sent directly in the URL.</p>
<p>In a POST request, when you wish to send data or parameters to an endpoint/API, you put them in the <em>body</em> of the request, not in the request URL! POST requests also give you the flexibility to send different types of data, whereas in a GET request you are mostly limited to data in the form of a query string and parameters, you can send files, JSON, XML, binary, and much more with a POST request.</p>
<p>To demonstrate an example of a POST request, we will use the silly but simple API called <a href="http://api.shoutcloud.io/V1/SHOUT">SHOUT CLOUD</a>. This stupid but fun API takes input from a POST request (text) and turns everything to upper case and returns it back to you! It serves literally no purpose but it will be a simple example for the purposes of our testing. It also lets us experiment with POSTing data that is not a query string, instead, we will be sending JSON in our POST request body to the API!</p>
<p>As per their documentation, the shoutcloud API takes in an input JSON object that looks something like this:</p>
<pre><code>{
  "INPUT": "text to turn into upper case"
}
</code></pre>
<p>This is simple, but notice that we are sending JSON-formatted to the api now, we are NOT doing something like <code>?input=text to turn into upper case</code>. This would be odd to do with a GET request, but since we are now using POST it should allow us to do it with no real difficulties!</p>
<p><em>Around this point, you should download the <a href="http://simple-python-post-example.py">simple-python-post-example.py</a> program from this branch to follow along with me better during the actual workshop.</em></p>
<p>Looking at the new python program, we can see that the only real difference is that our input data is now a dictionary, and that the method that we call on the requests library is <code>post()</code>, and we send the headers with our request as well, with <code>headers=request_headers</code> in the parameters of the post() function call.</p>
<p>One major and important thing to note here is the headers! In our headers, we specified something called the <code>Content-Type</code>. This header tells the endpoint what type of data it will be receiving so it knows how to properly handle them, and it also structures and formats our request so that it can be processed without any issues! Right now, we have it set to <code>Content-Type: application/json</code>. This makes it so that our input data can be JSON-formatted (in fact, it HAS to be json formatted now!) What would happen if you changed the content type to something else? Or didn’t send the headers at all? Try it out!</p>
<p>Lets look at the RAW request that this program actually sends to the API:</p>
<pre><code>POST /V1/SHOUT HTTP/1.1
Host: api.shoutcloud.io
Content-Type: application/json
Cache-Control: no-cache

{"INPUT": "Hello world!"}
</code></pre>
<p>This is the RAW request, this is what the request is defined as in the actual Hyper Text Transfer Protocol! The keyword at the very beginning specifies what TYPE of request it is, in this case it is <code>POST</code>, and then the text after it specifies the path to make the request to and the protocol version to use. The <code>host</code> header specifies the actual server to make the request to, and the <code>Content-Type</code> specifies what type of data is in the request. Next, we see something interesting, after all of the headers, there is a space and then our actual request body! As you can see, the input ‘parameters’ are not in the URL and are instead in a section after the headers, which we refer to as the body of the request. This is advantageous because we can put all different types of data in the body of a POST request, it doesn’t even have to be text! POST requests even support special characters. In a way, POST requests are superior because GET requests are character limited, format limited, and have a whole multitude more limitations.</p>
<p>Lets quickly also look at the raw HTTP request that we made to the Rates API earlier, just for sake of comparison:</p>
<pre><code>GET /api/latest?base=CAD HTTP/1.1
Host: api.ratesapi.io
Content-Type: application/json
Cache-Control: no-cache
</code></pre>
<p>As you can see, our input (base=CAD) is in the path section! There is no body.</p>
<p>Now, lets finally get started with Google Cloud</p>
<p><a href="https://github.com/Kav-K/RUHacks-API-Workshop/tree/part-4"></a></p><h3><a href="https://github.com/Kav-K/RUHacks-API-Workshop/tree/part-4">Click here to go to Part 4 (or switch your branch to part-4)</a></h3><p></p>

