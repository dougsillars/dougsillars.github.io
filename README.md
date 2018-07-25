# Fast and Beautiful Images - a Workshop

You've just listened to a talk on image performance - now let's try it out!

(If you missed the talk, and still want to participate, <a href="README2.md">here is more detail</a>.)  You can also see slides of a <a href="https://www.slideshare.net/dougsillars/fast-and-beautiful-images-dublinjs">representative talk</a>.

In this repository, I have built a *Very Slow* website.  The images were just uploaded straight from Google Photos, and as a result, the page weighs over 10 MB. <a href = "https://dougsillars.github.io/">Try it!</a> (See what I mean?)

Testing this site on <a href="www.webpagetest.org">WebPageTest</a> shows that it takes 19s to load on a desktop:
<img src="http://res.cloudinary.com/dougsillars/image/upload/f_auto,q_auto/v1532248748/WPT_o5mnbs.png">

<h2>Let's Make It Better: Getting Started</h2>

Let's clone this repo, and get it hosted on the internet (using GitHub Pages):
1. Login (or create an account) at <a href="https://www.github.com">Github</a><br/>
2. Create a new repository.<br/>
3. Once this is created, you are given the option to import from another repository. <br/>
Enter:"https://github.com/dougsillars/dougsillars.github.io", and you've forked this repository into your own GitHub Pages repository.
5. In your new repo settings - allow publishing to GitHub Pages. The very slow page will be published to \<username\>.github.io/\<repo name\>
6. Download the source to your laptop using Git, and we can begin updating this page with your favorite editor.
7. Push the changes to GitHub and document the savings with the tools listed below.


<h2>Tools</h2>
To speed up this webpage, we need to load everything faster.  Simply put, these images need to get smaller, so they download faster. To benchmark these tests, we'll use 2 tools:

1. <a href="https://webspeedtest.cloudinary.com" target = "_blank">Website Speed Test</a> to test the performance of the images on the page.
2. <a href="https://webpagetest.org" target="_blank">WebPageTest</a> to measure the load time of the page.

(note that these two tools are synced, if you run a WebPageTest run, you can access the Website Speed Test results from the "Image Analysis" link at the top of the page.

Here are links to the initial results (unoptimized):

<a href="https://webspeedtest.cloudinary.com/results/180315_AS_9dc54a8880a3415473c2f1fd03ea3895" target="_blank">WebsiteSpeedTest</a> 
The initial page scores "mediocre" in WebSite Speed Test, but we can see that the page has 10MB of images, and Cloudinary can reduce the files to 732 KB - a data savings of 92%!
<img width = "100%" src="https://dougsillars.github.io/img/original_score.png"/>

<a href = "https://webpagetest.org/result/180315_0S_8d8676cea9714fd1bf6820d70cb139c6/" target = "_blank">WebPageTest</a>
Shows that the load time was 19.6s, and the SpeedIndex (a measurement of speed to paint the screen was 7258.
<img width = "100%" src="https://dougsillars.github.io/img/Webpagetest_screenshot.png"/>


<h1>Let's Get Started</h1>
Ok!  Now you have all the code you need to update the webpage in this gist.  Optimize all you can, and test with Website Speed Test and WebPageTest.

<h2>Hints</H2>

1. Image Size/Format/Quality
Look at the parameters in the Cloudinary URLs.  The images are full size, so use the optimization techniques from the presentation (and in <a href="README2.md">README2</a>) to optimize the image delivery size/format/quality. Check out the section on Client Hints for Chrome as well.

2. Lazy Loading.  There are examples in the  <a href="README2.md">README2</a> on how to lazy load the images.


When you are completed, you can submit your results into this form for a chance to win a €100 Amazon Gift Certificate!

<h3><a href="https://docs.google.com/forms/d/e/1FAIpQLSdYhsJWpZGrzrg76MmSzkKxSlyfvblDX9_SmaKi7Q39R0FLTw/viewform">Submit Your Site!</a></h3>

<h2>Appendix</h2>
Other fun things we can do with Cloudinary:

1. add sepia effects: add e\_sepia:80 to the parameters.  Change the number to change hues. 
2. Change the image hue with  e\_hue.
3. Lighten images with e\_fill\_light
4. Trim image edges e\_trim:10 (use any value 1-100).
5. Face recognition: g\_faces.  Add glasses (30 pixels wide - for clown sized - go bigger): l\_glasses,w\_30
6. Face blurring - e\_blur\_faces
7. Grayscale image - e\_grayscale
8. Colorizing image e\_grayscale/e\_tint:15:blue (change color and % tinting)
