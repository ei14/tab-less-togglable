Tab-less
========

This extension allows you to disable tabbed browsing. When windowed mode is
set, your browser will open windows wherever possible rather than use tabs.

This repository is a fork of
[iainbeeston/tab-less](https://github.com/iainbeeston/tab-less). Unlike the
original, this version allows you to toggle between windowed and tabbed mode by
clicking the icon or by using a keyboard shortcut. It lacks some features of
the original:

* Clicking the icon does not close all unfocused windows. Rather, it toggles
between windowed and tabbed mode.
* The icon badge does not display the number of open windows. This makes it
easier to see the icon, which changes to indicate the current mode.

Installation
-----

### Chrome Web Store

[This extension can be downloaded via the Chrome Web Store.](https://chrome.google.com/webstore/detail/tab-less-togglable/ofolfkcaiejibcgljnccbaaledlbmdhd?hl=en&authuser=0)

### Building from source

1. [Install Node.js and
npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
2. Install Grunt: `npm install -g grunt-cli`
    * On a Mac: `brew install grunt-cli`
3. Install [ImageMagick](https://imagemagick.org/script/download.php)
    * On a Mac: `brew install imagemagick`
4. Clone the repository: `git clone https://github.com/ei14/tab-less-togglable.git`
5. Enter the repository folder: `cd tab-less-togglable`
6. Install the dependencies: `npm install`
7. Build the extension: `grunt`
8. In Chrome, go to `chrome://extensions` and enable *Developer mode* in the
upper right corner
9. Install the extension. There are two different ways to do this; choose one:
    1. Load unpacked. Useful for testing and quick installation.
        * Click *Load unpacked*
        * Navigate to `tab-less-togglable/dist` and open
    2. Pack and install. Produces a `.crx` file that enables you to easily
    install the extension on multiple browsers.
        * Click *Pack extension > Browse*
        * Navigate to `tab-less-togglable/dist` and open
        * Click *Pack extension*. This will produce a file called `dist.crx`
        which can be used to install the extension on any Chrome-like browser.
        Feel free to rename this file to something more descriptive, such as
        `tab-less-togglable.crx`.
        * Run Chrome with the file.
            * From the command line this looks like `chrome
            tab-less-togglable.crx`
            * On a GUI, you may be able to simply double-click the `.crx` file

Configuration
-------------

There is not much to configure, but you can set a keyboard shortcut that
switches between tabbed and windowed mode.

In Chrome, go to `chrome://extensions/shortcuts` and scroll to Tab-less
Togglable. Click the pencil icon and type your desired shortcut.

Usage
-----

Upon being installed, the extension begins in tabbed mode. This mode does
absolutely nothing, allowing tabs to be created without being converted into
windows.

To switch to tab-less mode, click the icon, or use a keyboard shortcut if you
set one. This immediately converts all open tabs into separate windows. In
tabbed mode, for every instance a new tab would be created, an appropriate new
window is created instead.

To switch back to tabbed mode, click the icon (or shortcut) again.

Note: switching back to tabbed mode does *not* collapse the individual windows
back into tabs. If you have many tabs open and switch to tab-less mode, all the
tabs will be separated into individual windows; there is no way to undo this
without manually recombining the windows one by one.

FAQs
----

* Why would you want to disable tabs?

Because I sometimes find it difficult to find the tab I'm looking for. Tabs can
sometimes obscure the browsing experience, and I sometimes find it easier to
browse the web when I can see all of my windows at once. Most modern operating
systems can arrange windows elegantly and efficiently, making tabs defunct in
many cases.

* If you don't like tabs, then just don't use them! You don't need an extension for that

Increasingly, browsers force tabs on you by default. It does not provide an
option to default to using windows rather than tabs. This extension lets you
override that behaviour to open windows instead, to make it seamless for users
like myself.

* Why should I use Tab-less-togglable rather than New Tab, New Window?

1. Tab-less-togglable does not require any access to your browsing history at all (most extensions require access to your browsing history or the current page you're viewing).
2. It's designed to be as light-weight and simplistic as possible.
3. There's no magic, it just moves tabs to a new window, whenever they're opened, whenever windowed mode is on (using the default settings for a new window).

* Why is this a fork of [iainbeeston/tab-less](https://github.com/iainbeeston/tab-less) instead of a pull request?

1. [iainbeeston/tab-less](https://github.com/iainbeeston/tab-less) contains
features that this extension removed for the sake of convenient toggling.
2. [iainbeeston/tab-less](https://github.com/iainbeeston/tab-less) is more
minimalistic and does not rely on browser storage like this fork does.
3. [iainbeeston](https://github.com/iainbeeston) is a much more competent
JavaScript developer than I.
[iainbeeston/tab-less](https://github.com/iainbeeston/tab-less) is well
optimized and comes with unit testing, whereas this fork has room for
improvement.

Bugs and limitations
--------------------

The parent extension, Tab-less, was built for the old Manifest V2 standard, but
between the release of Tab-less and Tab-less Togglable, the Chrome store has
stopped accepting extensions that use Manifest V2.

With the new Manifest V3, there is a known bug with Chrome that prevents the
service worker code from running for more than 30 seconds of time where the user
is inactive. Working around this bug required a bit of a messy hack, and it
sacrifices the ability of the extension to continue running when there are no
website tabs open --- e.g. only `chrome://` tabs, only `file://` tabs, etc.

If you notice that the extension isn't converting tabs to separate windows like
it's supposed to, click the icon twice (or use the shortcut twice).

Contributing
------------

All the code for this extension is open-sourced and can be found online at
https://github.com/ei14/tab-less-togglable. I'd be happy to receive any
feedback, hear about any bugs or accept any pull-requests for new code at that
address.

I will merge all relevant changes from the upstream repository, so if your
contributions apply to both this extension and
[iainbeeston/tab-less](https://github.com/iainbeeston/tab-less), consider
pushing to [iainbeeston/tab-less](https://github.com/iainbeeston/tab-less)
first.
