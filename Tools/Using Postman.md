> *Quality is not an act, it is a habit.*
 
## Why do we use Postman?

* To write API tests
* It has a nice and intuitive interface
* It is relatively easy to use even for newbies


# When do we use Postman?
* When you want to test if the API abides to the spec
* When you want to check if the API is returning the appropriate data
* When something is not testable via the frontend app
* When you want to set up your test environment quickly


# HTTP request Methods:
HTTP defines a set of request methods to indicate the desired action to be performed for a given resource.
Here are a few most used methods while testing:

* The `GET` method requests a representation of the specified resource. Requests using GET should only retrieve data.
* The `POST` method is used to submit an entity to the specified resource, often causing a change in state or side effects on the server.
* The `PUT` method replaces all current representations of the target resource with the request payload.
* The `DELETE` method deletes the specified resource.
* The `PATCH` method is used to apply partial modifications to a resource.

You can find more about HTTP request methods on this [link](https://assertible.com/blog/7-http-methods-every-web-developer-should-know-and-how-to-test-them).


# HTTP response status codes:
Even there are many HTTP response status codes, here are most important that we need to know:

* `200` - **OK**
* `201` - **Created**
* `202` - **Accepted**
* `304` - **Not Modified**
* `400` - **Bad request**
* `401` - **Unauthorized**
* `403` - **Forbidden**
* `404` - **Not Found**
* `408` - **Request Timeout**
* `500` - **Internal error**

You can find more HTTP responses on this [link](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status).


# Postman navigation 

You can find more information about basic Postman navigation on [POSTMAN Learning Center](https://learning.postman.com/docs/getting-started/navigating-postman/).


# Postman request flow

Here is what the flow of each request looks like:

![flow.png](/img/flow.png)


# Workspaces and collections 

Postman has *workspaces* that help you organize your requests/tests and collaborate with your teammates. One workspace could contain all the collections needed for one project.

1. To create a new Workspace click **Workspaces** drop-down -> **New Workspace**
2. Enter name of Workpace, Summary and wheter if this Workspace will be shared with your Tema, Pubilic or it will be Personal (Only for you). Also Postman offers you to invite people to join your workspace. 

*Collections* are folders that help organize your requests. Each collection can test different modules or related APIs. Also, having a collection is helpful if you need to monitor some requests and it is easy to export and share them. 

1. To create a collection click **New -> Collection**.
2. Enter collection name and press enter. 

# Creation and execution of a request 

Once we have a collection we need to add reqest to it. There are a few ways how to do it but lets use simplest one.

1. Click on **New -> Request**. 
2. Enter name of request and chose Workspace that you just created. For this purpose lets name this request" "GET Pokemons"
3. Click "Save to - name of collection" buton.
4. Set `GET` as your HTTP request method and paste desired URL. For this purpose, we will use `https://pokeapi.co/api/v2/pokemon/`. 
5. Execute request by clicking **Send** button.

Great, now we executed our request. As a response in our Body, we can see a list of 20 Pokemons in JSON format.

![first_20_pokemons.png](/img/first_20_pokemons.png)

# Environments and variables 

An environment is a set of key-value pairs (key represents the name of the variable).
Environments let you customize requests using variables to switch between different setups
without changing your requests. 

From list of Pokemons, let's save Bulbasaur's URL to environmental variable. For that first we need to add environment.

1. In top right corner tap *eye* icon.
 
 **(SLIKA)**

2. Since you do not have environments, tap **Add** button in *Environment* card. 
3. Environment card should open as a tab. Enter name of environment. Let's name it "Pokemons".

 ![variable.png](/img/variable.png)

4. Tap **Save** button.

 Great, now we have an empty variable in which we can add data. 

 **TIP:** Name your variables with the upper case so that is easier to separate them, for example in pre-request scripts or tests.
 
###Writing a value into the variable
 
There are two ways how you can enter a value to a variable:

1. You can enter a specific value to **Initial** and **Current** values input fields. Value can be everything from URL-s, strings, numbers. Usually, both **Initial** and **Current** values are the same.

	* The **Initial Value** is synced to your account via the Postman servers and shared with any collaborators who have access to the environment.

	* The **Current Value** is local to your Postman app, and is never synced to your account or shared with your team—unless you choose to persist it.

	**TIP:** If you enter a value to "Initial" field and hit "Tab", "Current" value field will be automatically filled with what is in "Initial" field. 


2. Or you can save a value from response to a variable. 
 
	1. Open "GET Pokemons" request.
	2. Switch to **Tests** tab inside this request.       
	3. Add following line of code in **Tests** tab:

	 ```
	var data = pm.response.json();
	pm.environment.set("BULBASAUR_URL", data.results[0].url);
	```

	3. Execute request by clicking **Send** button.

 This line of code will save in variable "BULBASAUR_URL" whatever is the value of `data.results[0].url` key, in this case Bulbasaur's URL. If you now open "Pokemons" environment you will see that variable contains Bulbasaur's URL. 


# Using a variables

Let's now use "BULBASAUR_URL" variable and value stored inside her. To do that you need to enter name of variable in between double curly braces. It should look like this: `{{VARIABLE_THAT_YOU_WANT_TO_USE}}`. This way Postman will read and use a value from a variable. 

1. Create a new `GET` request but this time instead of URL enter `{{BULBASAUR_URL}}`. 
2. Execute request. 

In the image below, you can see the expected result - more technical information about Bulbasaur.  

![expected_result.png](/img/expected_result.png)

* **TIP:** If there is an error, variable `{{BULBASAUR_URL}}` will be red indicating that you either misspelled its name or the variable does not exist. 

Using variables we avoid copy-paste of URL and the good thing is that variables can be used as many times as we need. 
Or we can extend it with an additional endpoint like this: `{{BULBASAUR_URL}}/example_url`.


# Pre-request scripts

Are snippets of code written in JavaScript. A pre-request script can be added to a collection, a folder, or a single request within a collection that is executed before the request is sent. In many cases on our project pre-request script is super usefull and best example of using it is a token creation.

1. To add pre-request scrupt to a single request open "GET Pokemons" request. 
2. Switch to **Pre-request Script** tab

Since values for token are sensitive, here is an example of how a pre-request script for token creation should look like:

```
 const loginRequest = {
    url: pm.environment.get{"BASE_URL"} + "auth/login",
    method: 'POST',
    header: {'Content-Type':'application/json'},
    body: {
        mode: 'raw',
        raw: JSON.stringify({"username": "admin", "password": "infinum"})
    }
};

 pm.sendRequest(loginRequest, function (err, res) {
    const loginResponse = res.json();
    pm.environment.set("TOKEN", loginResponse.token);
});
```

First part of the code contains URL, HTTP method, header and body with username and password that are necessary for generation of a token. 
Second part of the code will save the generated token to the **TOKEN** variable, and we can use this variable and its value in other requests if needed. 


# Writing tests 

With Postman you can write and run tests, written in JavaScript and they runs every time you run a request. 
You can add as many tests as needed, depending on how many things you want to test.

1. Open "GET Pokemons" request.
2. Switch to **Tests** tab. 

 * Postman offers "Snippets" or already written tests. They are located right from *Tests* input field. 
 
3. Find "Status code: Code is 200" snippet and clicking on it. 

 Now you will see code like this: 

 ```
 pm.test("Status code is 200", function () {
 pm.response.to.have.status(200);
 });
 ```

4. Execute request.
5. In response of a request, switch to the **Test Results** tab. 

	Here you should see test "Status code is 200" marked as PASS.
 
![status200.png](/img/status200.png)
	
Sometimes it can happen that the status of response is 200 but the body is empty. In this case, we need to add some complexity. Let's now check if the response returned something that does not change, for example, Bulbasaur's base experience. 

1. For this test we will need to add the "BASE_EXPERIANCE" variable and set the value to 64.
2. Add the following code under "Status code: Code is 200". 

 **TIP:** Add one or two empty rows so that your tests are separated and in that way easier for reading.

 ```
pm.test("Base experience", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.base_experience.toString()).to.eql(pm.environment.get("BASE_EXPERIANCE"));
});
```
3. Execute request
 
 If status is 200 and base experience is indeed 64, tests will be marked as passed. 

![2x_tests.png](/img/2x_tests.png)

# Collection runner

The Collection Runner allows users to run sets of requests in a specified sequence against specific environments. 

1. Inside collection click **Run**.
2. Tab with all requests inside collection should open. 
3. Choose which requests you want to include in this run. For this example let's leave them all selected. 
4. Set environment in which you want this run to be executed. 

 * You also have an option to set number of iteration, delay, save response and some other but for this example we do  not need all of that.
 
5. Click "Run Test Collection" button.
 
Postman will display request executions and test results in real time.
If any test in a request script fails during the collection run, request will be listed as failed but with proper response status. 

![test_fail.png](/img/test_fail.png)

If all tests from the list are listed as passed then the request will also be listed as passed. 

![tests_success.png](/img/tests_success.png)

**TIP:** Results can be exported by clicking on the **Export Results** button and attached to the regression test or any other type of tests if it is required. 
 
# Collection monitoring

Collection monitor – a scheduled collection runner. The value of monitors lies in test scripts. When running collection, a monitor will use tests to validate the responses it's receiving. When one of these tests fails, the user automatically receives email notification or it can be configured to receive alerts via Slack.


# Additional resources:

Check a blog post from one of our QA members [Writing API Tests? Postman Delivers
](https://infinum.com/the-capsized-eight/postman-API-testing)

Also see this interesting article [Testing APIs with Postman: 10 common challenges & solutions
](https://medium.com/distant-horizons/testing-apis-with-postman-10-common-challenges-solutions-c4674c78528d).

---
![using-postman.gif](/img/using-postman.gif)

