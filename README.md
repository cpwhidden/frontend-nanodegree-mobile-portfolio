## Website Performance Optimization portfolio project

Your challenge, if you wish to accept it (and we sure hope you will), is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques you've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

To get started, check out the repository, inspect the code,

### Getting started

####Part 1: Optimize PageSpeed Insights score for index.html

Some useful tips to help you get started:

1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok http 8080
  ```

### Optimizations

#### Portfolio page

* Images were compressed to appropriate sizes, increasing page load speed.
* CSS inlined, reducing number of round trips during page loading.
* Google Analytics JavaScript loaded asynchronously, which before was render-blocking on page load.
* Local font requested before requesting Google font, reducing a round trip request during page load.

#### Pizza page

* Scrolling alogrithms batches layout invalidations first before batching style changes, which optimizes the critical rendering path and improves scrolling frame rate.
* Likewise for pizza resizing, all layout invalidations were batched first, then style changes are batched.
* Limited generated pizzas to 24, vastly reducing computation at page load.
* Declared variables used in functions in global scope in order to speed up computational efficiency.
* Used 'getElement' functions that are faster than 'querySelector' functions in order to speed up computation efficiency.
* Optimized pizza CSS for efficient painting by forcing moving pizzas to render in seperately painted layers without backface visibility.


### How to build images with Grunt

* Two Gruntfiles are used, each `running grunt-responsive-images`, one for root-folder assets and one for the `views` folder assets.
* All current dependencies are already included in the repo
* Configure image build options in the `Gruntfile.js` file if you want different options for your images.
* Build by `cd`ing into the folder where your Gruntfile is and run `grunt`
