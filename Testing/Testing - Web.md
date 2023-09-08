> *Fast, good, cheap: pick only two.*

## Summary

This article is a compendium of useful tips & tricks for testing web apps.

- <a href=#chrome-hard-refresh-or-deleting-cache-refresh>Chrome hard refresh or deleting cache refresh</a>
- <a href=#clearing-browser-cookies-and-cache>Clearing browser cookies and cache</a>
- <a href=#how-to-compare-two-different-texts>How to compare two different texts</a>
- <a href=#how-to-simulate-offline-state-in-different-browsers>How to simulate offline state in different browsers</a>
- <a href=#selecting-test-devices>Selecting test devices</a>
- <a href=#testing-cookies>Testing cookies</a>
- <a href=#testing-web-apps-on-several-devices-simultaneously>Testing web apps on several devices simultaneously</a>
- <a href=#testing-web-app-ui-behaviour-with-content-amount-variations>Testing web app UI behaviour with content amount variations</a>

### Chrome hard refresh or deleting cache refresh

1. Hold Shift and click the Reload button.
2. Hold down Cmd and then press R.

or you can just:

Open the Chrome DevTools by clicking the right click and click Inspect. Once the Chrome DevTools are open, just right click the refresh button and a menu will drop down. This menu gives you the option of doing a hard refresh, or even clearing the cache and do a hard refresh automatically.

### Clearing browser cookies and cache

In this section of the handbook you will learn or be reminded on how to quickly clear cache and delete cookies in every browser you use for testing.

To quickly summon window with options to clear cookies and cache on different browsers, press the following keyboard combination: 

- **Firefox**: `Cmd + Fn + Shift + Backspace (Delete)`
- **Chrome**: `Shift + Cmd + Backspace (Delete)`
- **Safari**: `Cmd + Alt + E`
- **Internet Explorer**: `Ctrl + Shift + Backspace (Delete)`

All of this commands for each browser should do the trick and help you to clear everything needed withouth you going into browser settings to do it.

### How to compare two different texts

- Sometimes there is a need to compare two slightly different texts. There are several different web sites that we can use to compare two texts and find differences between them. 
- One of them is [https://text-compare.com/](https://text-compare.com/) 
- By letting this tool to find differences between two texts, you are going to save quite a lot of time. 

### How to simulate offline state in different browsers

**Chrome**

First thing you have to is open the developer console window. On Windows you can use **Ctrl+Shift+J**, while on Mac you can use **Ctrl+Option+J**.

Next, click on **Application** --> **Service Workers** --> select **Offline**

<span style="display:block; border: 1px solid #e0e0e0; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:100%;">![](/img/Offline_mode.png)</span>

**Mozilla Firefox**

Go to Firefox **File** --> **Work Offline** 

<span style="display:block; border: 1px solid #e0e0e0; margin-top:15px; margin-bottom:15px; margin-left:auto; margin-right:auto; width:100%;">![](/img/firefox_offline.png)</span>

Now, why would you want to simulate offline state in Chrome or any other browser? 

Here are some of the reasons:

1. When you want to test out how will your WebApp behave when there is no Internet connection
2. When you want to test out different API errors, although this is specific to a certain WebApp & sometimes can't be done
3. When you don't want to lose Internet connection on a test device but just on a tab you're testing (works only on Chrome)

Also, if you're trully hardcore there is some interesting info in this [article](https://www.creativebloq.com/how-to/make-your-app-work-offline-with-service-workers) but you probbaly shouldn't go that far :)

### Selecting test devices

When testing a web app, it's important to know which major browsers we are supporting and what is the current market share. This is project-dependent so make sure to check with your project team.

To check the market share, you can use pages such as [Net Marketshare](https://netmarketshare.com/browser-market-share.aspx).

### Testing cookies

**What is a cookie?**

Cookies are files created by websites you visit. They make your online experience easier by saving browsing information. With cookies, sites can keep you signed in, remember your site preferences, and give you locally relevant content.

**Content of a Cookie**

The cookie consists of mainly three things:

* The name of the server the cookie was sent from
* Cookies Lifetime
* A value. This is usually a randomly generated unique number

By default, the activities of storing and sending cookies are invisible to you. However, you can change your settings to allow you to approve or deny cookie storage requests, delete stored cookies automatically when you close browser, and more.

**Types of Cookies**

- **Session Cookies:** These cookies are active until the browser that triggers the cookie is open. When we close the browser this session cookie gets deleted.
- **Persistent Cookies:** These cookies are written permanently on the user machine and it lasts for months or years
 
**How to test Cookies – Sample Test Cases**

To view all the cookies that are stored, navigate to browser Settings or Preferences. In Chrome, click on Advanced. Under the Privacy and security section, click on Site Settings and then click on Cookies and site data.

If you want to view cookies for a particular website, first open a Developer Tools, then click on Application tab. On the left-hand side in the Menu find Storage -> Cookies. 

![](/img/Cookies.png)

You can delete one cookie, edit cookies or you can delete all the cookies.

Now let's start with some test cases you can go through to test the cookie:

- **No personal or sensitive data is stored in the Cookie.**

	If you have no option than saving sensitive data in a Cookie, then make sure that the data stored in a cookie is stored in an encrypted format.
 
- **No overuse of cookies.** 

	This will annoy users if the browser is prompting for cookies more often and this could result in loss of site traffic and eventually loss of business.

- **Disable the Cookies from your browser settings.**

	If you are using cookies on your site, your sites major functionality will not work by disabling the Cookies.
 
 	Navigate to the site see if appropriate messages are displayed to the user like “For smooth functioning of this site make sure that Cookies are enabled on your browser”.
 
 	There should not be any page crash due to disabling the Cookies. (Please make sure that you close all the browsers, delete all previously written cookies before performing this test)
 
- **Delete Cookie.**

	Allow the site to write the cookies and then close all browsers and manually delete all Cookies for a website under test. Access the web pages and check the behavior of the pages.

- **Cookie Testing on Multiple browsers.**

	Check if your web application page is writing the cookies properly on different browsers as intended and site works properly using these Cookies.
 
- **Validate if an expiration date is set accordingly to requirements.** 

	In some cases, it is vital to check if the Cookie expiration date is updated working with an application (to refresh session for example). This can be checked in browser console or Cookie file itself.
 
- **If some Cookies are user-specific,** it is important to ensure that they are deleted or simply ignored if another user logs into application unless it was said differently in a specification.

As cookies can play an important part in how smoothly a website functions, it’s pretty important that you test how they are written and stored in your hard drive by the the websites you visit. The issue of security is important too because of the significant information stored locally within each cookie.

These are some of the test cases to be considered while testing website Cookies.

### Testing web apps on several devices simultaneously

Check out [Responsively App](https://responsively.app/).

### Testing web app UI behaviour with content amount variations

When you want to quickly change the content on a page (i.e. to check what the page would look like if there is more/less text, how buttons would look like with longer/shorter labels etc.), you can use the `document.designMode='on'` command in the browsers' console:

1. open the console
2. enter `document.designMode='on'`
3. hit Enter

The `designMode` should be enabled and you can edit the content.
