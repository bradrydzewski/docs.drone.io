---
layout: default
title: Browser Testing
---
This following browsers and browser test utilities are available to your build:

* Firefox `/usr/bin/firefox`
* Chromium `/usr/bin/chromium-browser`
* Chrome `/usr/bin/google-chrome`
* Chrome Driver `/usr/local/bin/chromedriver`
* PhantomJS

You may also install other popular testing frameworks using npm or apt-get:

* `sudo npm -g install karma`
* `sudo apt-get install [your favorite testing tool]`

Before starting any browser tests you'll need to start an xwindows session.
Include the following command in your build script:

```
sudo start xvfb
```

