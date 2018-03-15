# dougsillars.github.io

Building fast and beautiful images for apps the the web.  

According to the HTTPArchive, &gt50% of all data on mobile websites are images, and the number of KB is grew by 5% year over year (March, 2017- March 2018).

Research shows that webpages and apps that are slow to load frustrate users.

&lth1&gt Speeding up A Slow Website: Optimizing Images&lt/h1&gt

In this excersise, we will use Cloudinary, a cloud based image delivery service to optimize a simple webpage and improve it's load time while still serving beautful images that will delight everyone who visits.

index.html is a pretend "summer vacation blog post" with 15 images.  The images were just uploaded straight from Google Photos, and as a result, the page weighs over 10 MB.

&lth2&gtTools&lt/h2&gt
We would like to take these images, and modify them to get the page to load faster.  To benchmark these tests, we'll use 2 tools:

1. &lta href="https://webspeedtest.cloudinary.com" target = "_blank"&gtWebsite Speed Test&lt/a&gt to test the performance of the images on the page.
2. &lta href="https://webpagetest.org" target="_blank"&gtWebPageTest&lt/a&gt to measure the load time of the page.

(note that these two tools are synced, if you run a WebPageTest run, you can access the Website Speed Test results from the "Image Analysis" link at the top of the page.

Here are links to the initial results (unoptimized):

&lta href="https://webspeedtest.cloudinary.com/results/180315_AS_9dc54a8880a3415473c2f1fd03ea3895" target="_blank"&gtWebsiteSpeedTest&lt/a&gt 
The initial page scores "mediocre" in WbSite Speed Test, but we can see that the page has 10MB of images, and Cloudinary can reduce the files to 732 KB - a data savings of 92%!
&ltimg width = "100%" src="https://dougsillars.github.io/original_score.png"/&gt

&lta href = "https://webpagetest.org/result/180315_0S_8d8676cea9714fd1bf6820d70cb139c6/" target = "_blank"&gtWebPageTest&lt/a&gt
Shows that the load time was 19.6s, and the SpeedIndex (a measurement of speed to paint the screen was 7258.
&ltimg width = "100%" src="https://dougsillars.github.io/Webpagetest_screenshot.png"/&gt


So, what steps can we take to make this page faster?  As I discussed in my presentation, there are several steps we can take. So, fork this page and begin Optimizing!

&ltb&gtImage Quality&lt/b&gt

The images on this page are all JPG images.  JPG is a lossy image format, meaning that as you lower the image quality, pixels are removed from the image - lowering the visual quality of the image.  Goole recomends that all images on the web be lowered to at least 85% quality to reduce file size.

You can adjust quality of images with any image processing tool. However, to simplify this exercise, we will use Cloudinary's tooling to change the quality on the fly. This is easily done by adjusting parameters in the url:
Here is the full quality image:
&lta href="http://res.cloudinary.com/hackchallenge/image/upload/w_2500/v1521063280/MyVacation/IMG_20160526_135242148_HDR.jpg" target="_blank"&gthttp://res.cloudinary.com/hackchallenge/image/upload/w_2500/v1521063280/MyVacation/IMG_20160526_135242148_HDR.jpg&lt/a&gt

and here is the image at quality = 50:
&lta href="http://res.cloudinary.com/hackchallenge/image/upload/w_2500,q_50/v1521063280/MyVacation/IMG_20160526_135242148_HDR.jpg" target="_blank"&gthttp://res.cloudinary.com/hackchallenge/image/upload/w_2500,q_50/v1521063280/MyVacation/IMG_20160526_135242148_HDR.jpg&lt/a&gt

By simply adding the q_50 parameter, Cloudinary generates an image at quality 50.  You can manually tweak the quality number for each image to find the optimal balance between quality and size, or you can use the "q_auto" parameter to create an image with the maximum quality reduction that is imperceptible to the human eye. CTry it with the image above!


&ltb&gtFormat&lt/b&gt

There are formats that have better compression algorithms than others. Since WebSite Speed Test and WebPageTest use desktop Chrome by default, we an use a format like Webp for potentially greater savings.

Rather than brute forcing through all the image formats, we can again leverage the Cloudinary toolchain, and add the "f_auto" parameter to the url - and Cloudinary will pick the best format (based on compatibility, size and quality) to deliver to the device.
&lta href="http://res.cloudinary.com/hackchallenge/image/upload/w_2500,q_auto,f_auto/v1521063280/MyVacation/IMG_20160526_135242148_HDR.jpg" target="_blank"&gthttp://res.cloudinary.com/hackchallenge/image/upload/w_2500,q_auto,f_auto/v1521063280/MyVacation/IMG_20160526_135242148_HDR.jpg&lt/a&gt


&ltb&gtPixels&lt/b&gt

All of these images are being delivered at a resolution much higher than required for a typical browser screen (and much too large for a mobile device!)  The device will resize the image, and shed unnecessary pixels from the image before it appears on the screen.  In some ways, this is double taxation - it costs time to download the large image, and then more time for the device to resize the file.

To resize these images, you can adjust the width parameter in the url.  In the sample image, it is set to 2500 (the parameter is w_2500). Open the image in a new tab, and adjust the number - and you'll see that a smaller (or larger) image is delivered to the browser:

&lta href="http://res.cloudinary.com/hackchallenge/image/upload/w_2500,q_auto,f_auto/v1521063280/MyVacation/IMG_20160526_135242148_HDR.jpg" target="_blank"&gthttp://res.cloudinary.com/hackchallenge/image/upload/w_2500,q_auto,f_auto/v1521063280/MyVacation/IMG_20160526_135242148_HDR.jpg&lt/a&gt

Again, we can brute force this change by manually changing the values for each image.  But this will only fix the image for one screen.  Which brings us to:

&ltb&gtResponsive Images&lt/b&gt

Now, you can adjust each image individually for the width, but we can also do so programmatically.  By enclosing the img tag in a picture tag, we can adjust the iamge that is delivered based on the viewport size:

<pre><code>
&ltpicture&gt
	&ltimg src="http://res.cloudinary.com/hackchallenge/image/upload/w_2500/v1521063217/MyVacation/IMG_20160619_173136306.jpg"
			srcset="http://res.cloudinary.com/hackchallenge/image/upload/w_500/v1521063217/MyVacation/IMG_20160619_173136306.jpg 500w, http://res.cloudinary.com/hackchallenge/image/upload/w_1000/v1521063217/MyVacation/IMG_20160619_173136306.jpg 1000w,http://res.cloudinary.com/hackchallenge/image/upload/w_1500/v1521063217/MyVacation/IMG_20160619_173136306.jpg 1500w"
sizes = "100vw"/&gt
&lt/picture&gt
</code></pre>

Test this out on the &lta href="https://dougsillars.github.io/picture.html"&gtpicture&lt/a&gt page. Resize the screen, and the check the url of the image!

The sizes parameter is also really cool.  In the example above, all images are sized to 100% of the view window.  However, in some cases, you could do something like:
<pre><code>
sizes ="min-width: 500px) 32vw, 100vw"
</code></pre>

In this case, if the screen is greater than 500 pixels wide, the image will take up just 1/3 of the screen, and below 500px, it will use 100% of the screen.  This is a great way to build multiple layouts for different device screen sizes.

<b>Preview Images</b>

In the last few secions, we have resized the images to balance the size and quality of the images.  In this final section, we are going to create placeholder images for each file. You may have seen this in appslike Facebook, Pinterest or Google Image search.  

I have created SVG images to load in the background before the larger image can be downloaded.  This is greta on slower connections, asn the screen is populated with color indicating an image is coming.  I used <a href="https://github.com/technopagan/sqip">SQIP</a> to create these thumbnails.

SVG files are vector graphics, and are stored as XML, so they can be added right to the HTML of your document:

<img src="http://res.cloudinary.com/hackchallenge/image/upload/w_2500/v1521063217/MyVacation/IMG_20160619_173136306.jpg">

<img src="https://dougsillars.github.io/plitvice.svg">