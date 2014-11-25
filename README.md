Statesman document viewer
=========================

This is a fork of John Keefe's [Custom-Viewer-for-DocumentCloud](https://github.com/jkeefe/Custom-Viewer-for-DocumentCloud) for use with Austin American-Statesman documents.

## How to use

This assumes you've already uploaded your document to [DocumentCloud](https://www.documentcloud.org), filled out all the Document information (under Edit) and made the Access Level: Public Access.

* Go into DocumentCloud and open the document so you are viewing it.
* Get the part of the url that is between "https://www.documentcloud.org/documents/" and ".html".
	* If your original url is: https://www.documentcloud.org/documents/1202682-seekingexpertise.html
	* You want: 1202682-seekingexpertise
* Add that part of the url to the end of this: http://projects.statesman.com/documents/?doc=
* So it should look something like this: http://projects.statesman.com/documents/?doc=1202682-seekingexpertise

## Changes we've made

* Added our Austin American-Statesman logo, though it looks pretty damn big
* Changed the worker url from dc.html to index.html so we can just add the doc param to the end of /documents/


--------------------

[originally posted at http://johnkeefe.net/a-customized-viewer-for-documentcloud]

This post is for newsrooms using DocumentCloud, the fantastic document viewer developed by journalist-programmers at ProPublica and The New York Times.
---

Want a custom viewer for your site's documents? You can have ours.

I built it so that once you set it up, this viewer will automagicly fill in the title, source and "back-to-article" link based on information already associated with the document -- so one file serves all of your documents.

Here's how.

One-time Setup

You can make this work with a little knowledge of html and access to a web server. You'll need to host a single html page, called dc.html and a tiny javascript file, called jquery.url.min.js.

1. Download the html code for dc.html here: https://github.com/jfkeefe/Custom-Viewer-for-DocumentCloud

2. Use any text editor to edit the path to your logo image on line 101. (A logo that's 60 pixels high works well).

3. On line 101, change "www.wnyc.org" to your site's home page

4. Upload the file dc.html to a web server.

To extract the document info from the URL, the page uses a little JavaScript program called jquery.url.min.js which you can read about here: http://ajaxcssblog.com/jquery/url-read-get-variables/jquery/url-read-request-variables/ ... and download here: http://ajaxcssblog.com/wp-content/plugins/download-monitor/download.php?id=2 

Once you do:

5. Upload jquery.url.min.js to your web server (the page assumes it's in the js/ subdirectory)

6. If you need to chance the location of jquery.url.min.js, edit the path on line 38 of the html code and reupload.

Using the Viewer

To use the viewer, simply link to it with a URL that combines dc.html's location and the ID of the document it should load. For example, the base URL for the WNYC page is here:

http://project.wnyc.org/documents/dc.html

And the document I want to display is here:

https://www.documentcloud.org/documents/11275-bill-a11354.html

I combine them into a new link by taking the base URL, adding "?doc=" and then adding the document ID -- in this case it's 11275-bill-a11354 (without the .html). Like this:

http://project.wnyc.org/documents/dc.html?doc=11275-bill-a11354

Voila.

Pages and Annotations

For extra trickiness, you can jump to specific page numbers and annotations by adding references to them into your link. Here you need to append "#document/p" and the page number. So for page 2, you'd use:

http://project.wnyc.org/documents/dc.html?doc=11275-bill-a11354#document/p2

And for the annotation on page 3, it would be:

http://project.wnyc.org/documents/dc.html?doc=11275-bill-a11354#document/p3/a3975

(You get the annotation number -- and the whole phrase after the #, actually -- by clicking on the little "link" icon next to the annotation's title.)

That's it. 

Credits and Disclaimers

The base design is built on code the Chicago Tribune News Apps Team wrote, which I modified with help from the DocumentCloud folks to dynamically take up the title, source and related-story information from the document's metadata.

Note that the version of dc.html at project.wnyc.org contains extra tracking code specific to our servers. The version here does not. It's the one you should download.

And I don't warrant in any way that this is perfect code, so please use at your own risk.

If you modify it -- especially if you improve on what's here -- please let me know and I'll share the updates.