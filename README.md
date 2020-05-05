---


---

<h1 id="part-1">Part 1</h1>
<p>This section will dive into what ‘requests’ are, specifically GET and POST requests, two very important things that are important to understand before working with APIs!</p>
<h1 id="what-is-a-request">What is a request?</h1>
<p>Requests, in the realm of computer science, are everywhere. You are probably making thousands of requests per day without even knowing it!</p>
<p>Simply put, a request is an important component of the HyperText Transfer Protocol (HTTP) and is used to do things like retrieve websites, send information to websites, update information, and etcetera. Requests, as aforementioned, are everywhere. When you type <a href="http://google.com">google.com</a> into your address bar, you are making a HTTP request to actually get the web page and display it in your browser! When you go to log into google, facebook, twitter, etc, you are making a HTTP request to send your login details to the website to be verified! Requests are an integral part of your everyday use of the internet.</p>
<p>There are two main types of requests that you should be familiar with, and they are GET and POST requests. Intuitively, GET requests are used to obtain information, and POST requests are used to push(‘post’) information to a website or server!</p>
<h1 id="what-does-a-request-look-like">What does a request look like?</h1>
<p>Lets try something ourselves in order to better understand what a request looks like! Earlier, I said that when you put a website in your address bar and go to it, you’re doing a HTTP request! Lets try that out!</p>
<p>We will need google chrome for this, we will go to <a href="http://google.com">google.com</a> in chrome and open our chrome developer tools by right clicking the page and clicking “Inspect”<br>
<img src="https://i.imgur.com/KVRmBkj.png" alt="enter image description here"><br>
In the popup that appears, we will then click the “Network” tab:<br>
<img src="https://i.imgur.com/22LqFsQ.png" alt="enter image description here"><br>
Then, we will <strong>reload the page</strong> and you will see some things populate in that window that was just opened! We will click “<a href="http://www.google.com">www.google.com</a>” after it populates:<br>
<img src="https://i.imgur.com/ivAsVaV.png" alt="enter image description here"><br>
You will then see all the information about the request to <a href="http://www.google.com">www.google.com</a> pop up!<br>
It should look something like this:<br>
<img src="https://i.imgur.com/BeK4GjA.png" alt="enter image description here"><br>
That box that you see is the request information! This is a GET request, more in the next section!</p>
<h1 id="get-request">Get Request</h1>
<p>In the request that we made to <a href="http://google.com">google.com</a> earlier, when we inspect it with chrome developer tools we see the request information. It shows us the URL that we made the request to, in our case this was <a href="http://google.com">google.com</a>, it shows us the type of request that we made in the “Request Method” field, in our case, it was a GET request! This makes sense, because we were simply GETting the web page to display in our browser!</p>
<p>You also will notice a section called “<strong>Request Headers</strong>”.  Headers are extremely important. Headers contain information about the client, the request itself, and what information is being sent in the request. You can think of it sort of like “information about the information” (?) <em>(I’m not an english major sorry)</em></p>
<p>In the request headers you’ll find fields such as “User Agent”, which gives the receiving server about what type of browser is being used to make the request, or fields such as “referrer” which tells the receiving server where the browser was before the request was made. There are many, many more request headers and we need not go in depth with them for the purpose of this workshop.</p>
<h1 id="post-request">Post Request</h1>
<p>Now, lets look at POST requests! POST requests are used when you have to submit data to a website. You can also submit data with GET requests (we will see that later on in this workshop) but POST requests are preferred because they can handle arbitrarily large amounts of data, and multitudes of different formats. They are also often more flexible than GET requests.</p>
<p>POST requests are most commonly used on login pages! Lets try this out, lets go through the same process as we did for <a href="http://google.com">google.com</a> but with <a href="http://imgur.com">imgur.com</a>.</p>
<p>Click <a href="https://imgur.com/signin">here</a> to go to the sign in page for imgur. Follow the same steps as previously to open your chrome developer tools, and the Network tab. Once you have the network tab open, fill in something random in the username and password field and hit “Sign In”.</p>
<p>Once you hit sign in, the network tab in your chrome inspection tool should populate, and you should see a request to <a href="http://imgur.com/signin">imgur.com/signin</a>! Click on that to see more information about the request that we just made:<br>
<img src="https://i.imgur.com/zmAOIwU.png" alt="enter image description here"><br>
<img src="https://i.imgur.com/DHNb5rK.png" alt="enter image description here"><br>
As you can see, it looks very similar to the GET request that we made to google earlier, with some key differences. The “Request Method” is now “POST”, and we have this new section called “Form Data”.  This new form data section contains the information that we submitted along with our POST request to the imgur server! As you can see, it contains the username and the password that we sent when we tried to log in. It also has some extra stuff like the “remember” field for if we wanted imgur to remember our password.</p>
<p>We will get more into GET and POST requests and start properly using them in the next part, and we will learn of some of the finer intricacies that these requests have!</p>
<p><a href="https://github.com/Kav-K/RUHacks-API-Workshop/tree/part-2"></a></p><h3><a href="https://github.com/Kav-K/RUHacks-API-Workshop/tree/part-2">Click here to go to Part 2 (or switch your branch to part-2)</a></h3><p></p>
