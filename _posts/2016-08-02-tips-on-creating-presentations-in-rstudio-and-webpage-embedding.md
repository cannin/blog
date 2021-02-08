---
title: "Tips on Creating Presentations with RStudio and Webpage Embedding"
header:
  teaser: "post_teasers/programming_900x450.png"
  image: "post_teasers/programming_1600x450.png"
categories:
  - r
author: Augustin Luna
---

RStudio provides functionality to [make presentations in R](https://support.rstudio.com/hc/en-us/sections/200130218-R-Presentations) in a way very similar to [knitr reports](http://yihui.name/knitr/). Presentations produced in RStudio are dependent on the on [reveal.js HTML presentation framework](http://lab.hakim.se/reveal-js/), and like knitr reports, these presentations are nice way of embedding both code chucks and have the results shown that are dynamically generated when the presentation is created. There are number of very helpful features in tools like Microsoft Powerpoint that are missing when making presentations in RStudio. A template presentation is available at [this GitHub repository](https://github.com/cannin/r-presentation-template) that has the features described in this post.

Users are likely to need to customize the template to suit their aesthetic tastes, but it should serve as a good starting point for more advanced features from RStudio presentations.  

## Simplifying Authoring using CSS

The tips below depend on investing sometime with [CSS](http://www.w3schools.com/css/css_intro.asp) to get some useful features for creating presentations with RStudio.

### Quick Access to Font Sizes and Image Centering

A [CSS stylesheet can be associated with the slide deck](https://support.rstudio.com/hc/en-us/articles/200532307-Customizing-Fonts-and-Appearance) and a style can be associated with each slide. The rpres.css contains a few helpful styles, specifically the ones below:

```
# For an image only slide, center the image
class: center-img

# For overall smaller font size for the slide content
class: smaller
```

### Simplified Positioning using CSS

debug.R contains code to display vertical and horizontal grid lines on the slide every 10% of the slide; this is done through HTML elements and CSS. To activate these grid lines, the content must be sourced in using the the following commands placed at the top of the rpres.Rpres file:

```
`r if(file.exists("debug.R")) { source("debug.R"); I(grid) }`
```

This works by placing the necessary HTML elements into the grid variable and them then directly writing this content into the slide using I().

### Highlight Elements in Images

Sometimes it is useful to put a circle or square over some portion of an image to highlight some important part. An [HTML div](http://www.w3schools.com/tags/tag_div.asp) is used to place either box or a ellipse on top of the image. The type of highlight is described by the class attribute, and the height, width, and position are described in the style attribute; the positioning of which is made easier with debug.R.

The CSS code also allows filling in the shape to allow writing a label as shown in the ellipse  

```html
RStudio Overview
===
class: center-img

<img src="img/rstudio.png" height="600px" />

<div class="box" style="height: 10%; width: 20%; top: 30%; left: 20%">
  <span class="filled" style="font-size: 2rem !important">Editor<span>
</div>

<div class="ellipse" style="height: 10%; width: 20%; top: 30%; left: 20%"></div>
```

Below is a screenshot featuring both debugging grid lines for slides and CSS-based highlights:

![Screenshot Showing Grid Lines and Highlights on RStudio knitr Presentations]({{ site.url }}{{ site.baseurl }}/images/tips_presentation_rstudio_highlight.png){: .full}

## Embedding Presentations in Webpages

Embedding presentations in webpages, like blog posts, is nice since it allows readers to browse presentation content without visiting another page. To get an effect similar to [SlideShare](http://www.slideshare.net/), is relatively simple using [Bootstrap](http://getbootstrap.com/) and [screenfull.js](https://github.com/sindresorhus/screenfull.js/); Bootstrap provides the HTML element (i.e. a panel) where the presentation will be embedded and screenfull.js provides functionality for a clickable button that will maximize the presentation to full screen.

The necessary HTML is in "embed" folder of the template repository. The code below shows the important code elements to embed the presentation; it also provides link to a PDF version of the presentation (instructions on producing a PDF version are later in this post).

```html
<script type="text/javascript">
$(document).ready(function() {
  $('#fs-overview-link').click(function () {
    if (screenfull.enabled) {
      screenfull.request($('#fs-overview-target')[0]);
    }
  });
});
</script>
  <div class="panel panel-default">
      <div class="panel-heading">
          <h2 class="panel-title">
              R Basics (<a href="http://slides.lunean.com/r-presentation-template/rpres.pdf">PDF</a>) <a id="fs-overview-link" class="pull-right" href="#"><i class="fa fa-arrows-alt"></i></a>
          </h2>
      </div>
      <div class="panel-body">
          <div class="embed-responsive embed-responsive-4by3">
              <iframe id="fs-overview-target" src="http://slides.lunean.com/r-presentation-template/rpres.html" allowfullscreen seamless>
                  <p>Your browser does not support iframes.</p>
              </iframe>
              <!--<iframe src="http://www.w3schools.com">-->
                  <!--<p>Your browser does not support iframes.</p>-->
              <!--</iframe>-->
          </div>
      </div>
  </div>
```

## Embedding Google Analytics into Presentations

head.R contains typical code for Google Analytics. Additionally, it provides an example for triggering events by listening to events that occur in the presentation. In the example, an event is sent to Google Analytics whenever a user changes slides this helps get a sense of engagement of users in the presentation content.

Similar to debug.R, the content of head.R can be added into the presentation by adding this line at the top:

```
`r if(file.exists("head.R")) { source("head.R"); I(head) }`
```

Code for tracking slide changes:

```javascript
Reveal.addEventListener('slidechanged', function(event) {
  console.log('Slide Index: ' + event.indexh);
  ga('send', 'event', 'Slide Index', 'click', event.indexh);
});
```

## Generating PDF Versions of Presentations

PDF versions of presentations are useful since sometimes one encounters a venue that lacks software support (e.g. old browsers), but typically static PDF files are not an issue. Also, some users may want to a hard copy of presentations for taking notes or to look at offline. There is no quick button in RStudio for creating PDF versions of slides. Even though Reveal.js provides a print stylesheet for printing to PDF slides the experience can be a pain because the results are less than optimal. Thankfully, there is a tool called [Decktape](https://github.com/astefanutti/decktape) that works much better.

With [Decktape](https://github.com/astefanutti/decktape) installed, there are two steps:

1. Serve your presentation on a web server

There are a lot of ways to do this. Below is a way that depends on [NodeJS](https://nodejs.org/en/) for a quick webserver installed in the [cannin/nodejs-http-server](https://hub.docker.com/r/cannin/nodejs-http-server/) container made with [Docker](https://www.docker.com/) to simplify its usage without worrying about installing it on the locally.

```bash
docker run --name slides -p 8080:8080 -v $(pwd):/site -w /site -t cannin/nodejs-http-server:0.10.25
```

Note: $(pwd) is the current directory.

2. Run Decktape

```sh
./bin/phantomjs ./decktape.js reveal http://localhost:8080/rpres.html rpres.pdf
```

## Embedded Template Presentation

Template presentation embedded with debugging turned on.

{% include slides.html
  title="RStudio Presentation Tips"
  prefix="http://slides.lunean.com/r-presentation-template/rpres"
%}
