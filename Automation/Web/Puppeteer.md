> *Quality is free, but only to those who are willing to pay heavily for it. - DeMarco, Lister*

## What is Puppeteer?

Getting down to brass tacks, Puppeteer is probably the easiest way to do some UI automation in Chrome or Chromium. It can run in either full or headless mode (without the full browser UI).

## Use cases

The potential use cases are neatly summed up on their [GitHub page](https://github.com/puppeteer/puppeteer):

- *Generate screenshots and PDFs of pages.*
- *Crawl a SPA (Single-Page Application) and generate pre-rendered content (i.e. "SSR" (Server-Side Rendering)).*
- *Automate form submission, UI testing, keyboard input, etc.*
- *Create an up-to-date, automated testing environment. Run your tests directly in the latest version of Chrome using the latest JavaScript and browser features.*
- *Capture a timeline trace of your site to help diagnose performance issues.*
- *Test Chrome Extensions.*

### Prerequisites

- Install [node.js & npm](https://nodejs.org/en/download/package-manager/#macos).

### Installing Puppeteer

- Global install: `npm install -g puppeteer`
- Local install: `npm install puppeteer`

### Example

Let's say you want to go through a login flow on a particular web page and fetch a token from the URL at the very end.

This is how quickly and easily you can do it using Puppeteer:

	const puppeteer = require('puppeteer');
	
	// Get data from environment variables
	
	const loginUrl = process.env.URL;
	const email = process.env.EMAIL;
	const password = process.env.PASSWORD;
	
	(async () => {
	
		// Start the browser
		
		const browser = await puppeteer.launch({ headless: true });
		const page = await browser.newPage();
	
		// Pass the login flow
		
		await page.goto(loginUrl, { waitUntil: 'networkidle0' });
		await page.type('#email', email);
		await page.type('#password', password);
		await page.click('#next');
		await page.waitForNavigation({ waitUntil: 'networkidle0' });
		const url = page.url();
	
		// TODO: Parse the URL to retrieve the token
		
		// const token = ...
		
		console.log(token);
	  
		// Close the browser
		
		await browser.close();
		
	})();
	
Just save the above to a .js file and run it with `node script.js`.

## Docs

For more info on all functionalities, check out their [GitHub page](https://github.com/puppeteer/puppeteer).
