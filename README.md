# Fast and Beautiful Images - a Workshop

You've just listened to a talk on image performance - now let's try it out!

(If you missed the talk, and still want to participate, <a href="README2.md">here is more detail</a>.)  You can also see slides of a <a href="https://www.slideshare.net/dougsillars/fast-and-beautiful-images-dublinjs">representative talk</a>.

In this repository, I have built a *Very Slow* website.  The images were just uploaded straight from Google Photos, and as a result, the page weighs over 10 MB. <a href = "https://dougsillars.github.io/">Try it!</a> (See what I mean?)

Testing this site on <a href="www.webpagetest.org">WebPageTest</a> shows that it takes 19s to load on a desktop:
<img src="http://res.cloudinary.com/dougsillars/image/upload/f_auto,q_auto/v1532248748/WPT_o5mnbs.png">

<h2>Let's Make It Better: Getting Started</h2>

Let's clone this repo, and get it hosted on the internet (using GitHub Pages):
1. Visit <a href="https://pages.github.com">pages.github.com</a><br/>
2. Set up a repository named <github username>.github.io<br/>
3. Once this is created, you are given the option to import from another repository. <br/>
Enter:"https://github.com/dougsillars/dougsillars.github.io", and you've forked this repository into your own GitHub Pages repository.
5. In your new repo settings - allow publishing to GitHub Pages. 
6. Download the source to your laptop using Git, and we can begin updating this page with your favorite editor.






<h1>Off to the races!</h1>
Ok!  Now you have all the code you need to update the webpage in this gist.  Optimize all you can, and test with Website Speed Test and WebPageTest.

<b>Big hint</b>:
Simply use Client Hints (as described above), and add the following parameters to your images <b>"q_auto,f_auto,w_auto"</b>, and your images will be pretty well optimized. Add a lazy Loading Library, and you'll be set!


When you are completed, you can submit your results into this form:

<h2><a href="https://docs.google.com/forms/d/e/1FAIpQLSdYhsJWpZGrzrg76MmSzkKxSlyfvblDX9_SmaKi7Q39R0FLTw/viewform">Submit Your Site!</a></h2>
To run the required tests, your site must be hosted and accessible from the internet.  You can use GitHub Pages.
1. Visit pages.github.com<br/>
2. set up a repository named <github username>.github.io<br/>
3. once this is created, you are given the option to import from another repository. <br/>
Enter:"https://github.com/dougsillars/dougsillars.github.io", and you've cloned this repository into your own GitHub Pages repository.
5. In your new repo settings - allow publishing to GitHub Pages.