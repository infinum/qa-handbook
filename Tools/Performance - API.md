> *If an end user perceives bad performance from your website, her next click will likely be on your-competition.com.*

This document is a short intro on performance testing and using k6 and JMeter, two performance testing tools.

## Performance testing 101

In a nutshell, performance testing is checking the stability & responsiveness of a system under a certain workload. Every system has its limits, performance testing is used to find those limits.

Performance and user experience are tightly correlated. The two big factors you wish to analyze are **stability** (does the system work under load?) and **responsiveness** (is the system quick enough under load).


#### Rule of thumb for responsiveness

These highly depend on the context, but in general:

- Response time up to 200 ms - Great 🏎️
- Response time 200 ms to 1000 ms - Acceptable 🚶
- Response time more than 1000 ms - Unacceptable 🐌

See this interesting article on [UX and time scales](https://www.nngroup.com/articles/powers-of-10-time-scales-in-ux/).

#### Modalities

- Load testing - full load
- Stress testing - extreme load
- Soak testing - full load for a long period of time
- Spike testing - dramatic changes in load
- etc.

### Other important metrics

- Concurrency - how many active users are executing requests in parallel
- Throughput - how many requests are being executed in a unit of time
- Error rate - % of failed requests
- CPU usage.
- Memory usage.
- Database query times.
- etc.

#### Approach

Since performance testing can be done in a variety of ways, it is crucial to:

- Examine the system you are testing and its use cases.
- Decide on metrics that will be examined.
- Decide on realistic goals that should be met.
- Decide on when, where, what, how to test.
- Keep in mind not all software projects are comparable with Netflix or Amazon.

#### When to test

Again, this depends on the context of the project, but here are some potential triggers:

- You are releasing the app for the first time.
- You are releasing a new feature.
- You are releasing to a new audience.
- You are changing the underlying architecture.
- You have refactored an API.
- Every time you make changes.
- etc.

#### Where to test

Most of the time:

- On production if it is not live yet.
- On an environment that closely mimics production in all other cases.

Use the expertise of our DevOps team to get a test environment up and running.

#### What to test

- The million dollar question. 🤑 
- Context is crucial.
- Use analytics (e.g., Firebase) and monitoring data (e.g., New Relic) to figure out what your users are actually doing, when they are doing it, and how many of them are doing it.
- Most times, you want to simulate a certain realistic use case, not just hit all the endpoints or just a single endpoint. 

#### How to test

There is no silver bullet. Experimentation and project context will get you on the right path. 

Some important parameters that you will need to decide upon are:

- Number of users
- Total duration
- Stable or increasing/decreasing load
- Number of requests per user/per second
- Which endpoints to hit
- etc.



## k6.io

#### Installing k6

- `brew install node
- `brew install k6`

#### Usage

You can do one of three things:

- Code the entire test
- Convert a HAR file to a k6 script
- Convert a Postman collection to a k6 script

#### Sample test

	import http from 'k6/http';
	import { check } from 'k6';
	
	export let options = {
	    vus: 50,
	    duration: '60s'
	};
	
	export default function() {
	    let url = `https://myurl`;
	    let response = http.get(url);
	
	    check(response, {
	        'Status was 200': r => r.status == 200,
	        'Transaction time was below 1000ms': r => r.timings.duration < 1000
	    });
	}


#### Converting your HAR file to a k6 script

- Export a HAR file that you wish to convert from your browser or Charles/Proxyman
- Run `k6 convert -O my-load-test.js my-har-file.har`
- Edit the script if necessary, removing any unwanted requests or sleep() calls.

#### Postman-to-k6
- You can also use your Postman collection to get to a performance test in a matter of minutes
- Run `sudo npm install -g postman-to-k6`
- You will need to export your Postman collection and environment
- Run `postman -to-k6 collection.json --environment environment.json -o postman.js` to get a k6 script

#### Running a load test with your k6 script

- Run the load test with your desired params: `k6 run --vus 100 --duration 500s --rps 50 my-load-test.js`
- The params can also be added to the script itself, then you would just run `k6 run my-load-test.js`
- The aforementioned would run your script with 100 virtual users for a duration of 500 seconds with a max RPS (requests per second) cap of 50 shared across all virtual users.
- k6 works with the concept of virtual users (VUs), which run scripts - "they're essentially glorified, parallel while(true) loops".
- For more options, see [k6.io/docs/using-k6/options](https://k6.io/docs/using-k6/options)

#### Useful docs

- Setup and teardown - https://k6.io/docs/using-k6/test-life-cycle 
- Types of performance tests - https://k6.io/docs/test-types 
- Intro to load testing - https://k6.io/docs/testing-guides/api-load-testing
- Running large tests - https://k6.io/docs/testing-guides/running-large-tests   

## JMeter

JMeter is Apache's load testing tool that is sometimes perceived as the industry standard.

#### Installation & running

- To install it, execute `brew install jmeter`
- To run it, execute `jmeter`

#### Components

JMeter works with components. This is a very broad overview:

- **Thread groups** - Similar to k6's virtual users.
- **Samplers** - Think of them as protocols - HTTP, FTP, JDBC, etc.
- **Listeners** - Methods for displaying the test output.
- **Configuration** - Constants, test data, various managers, etc.
- **Logic controllers** - Loops, if statements, etc.
- **Assertions** - Verification.
- **Timers**
- **Pre Processors**
- **Post-Processors**

Find more info on the above in [Apache's Introduction docs](https://jmeter.apache.org/usermanual/component_reference.html).

#### Building a simple test plan

- Create a new test plan
- Add a Thread Group
	- Select a number of users/threads
	- Select the ramp-up period - the number of seconds before starting each user
	- Select the loop count - the number of times the test will be repeated
- Add a HTTP Request Default
	- Add the base URL to the "Server name or IP" field
- Add a HTTP Header Manager
	- Add headers if needed
- Add HTTP requests to your Thread Group
	- Add the endpoint
	- Select the method (GET, POST, PUT, DELETE...)
	- Add the header params if needed
	- Add the body data if needed
- Add the desired listeners
	- The Aggregate Graph and Summary Report are useful
	- Remember to specify the output path for each

![jmeter-example.png](/img/jmeter-example.png)

#### Running a simple test plan

- Export the test to a .jmx file and run: `jmeter -n -t myTest.jmx`
- Read up on the [CLI params](https://jmeter.apache.org/usermanual/get-started.html#non_gui)

---

![load-testing.gif](/img/load-testing.gif)
