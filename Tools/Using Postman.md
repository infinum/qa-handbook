> *Quality is not an act, it is a habit.*
 
## When to use Postman?

* When you want to verify the API abides to the spec
* When you want to check if the API is returning the appropriate data
* To write API tests
* When something is not testable via the frontend app
* When you want to set up your test environment quickly


## HTTP request Methods:
HTTP defines a set of request methods to indicate the desired action to be performed for a given resource.
Here are a few most used methods while testing:

* `GET` method requests a representation of the specified resource. Requests using GET should only retrieve data.
* `POST` method is used to submit an entity to the specified resource, often causing a change in state or side effects on the server.
* `PUT` method replaces all current representations of the target resource with the request payload.
* `DELETE` method deletes the specified resource.
* `PATCH` method is used to apply partial modifications to a resource.

You can find more about the HTTP request methods [here](https://assertible.com/blog/7-http-methods-every-web-developer-should-know-and-how-to-test-them).


## HTTP response status codes:

HTTP response status code is a response from server of request that is displayed in three digit number. Responses are separated in five categories in which first number represents class of response. 

There are many HTTP response status codes, here are the most important ones with whom you will meet regularly and which you need to know:

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

You can find more details on HTTP response status codes [here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status).

## How Postman works?

Postman has a really simple work flow that is repeated for every request. 
Pre-request script is executed before request and tests are executed after response. Code in both pre-request scripts and tests is written in JavaScript, but do not worry it is really simple and easy to understand. 

Here is what the flow of each request looks like:

![Postman_flow.png](/img/Postman_flow.png)

## Workspaces

*Workspaces* act as a working areas that helps you organize your collections and requests. One workspace could contain all the collections needed for one project. Also, it is possible to invite people to join your workspace and in that way you can collaborate with your teammates.

### Creation of a Workspace 

1. Click **Workspaces** drop-down in top left corner
2. Click **New Workspace**
3. Enter name of Workpace, Summary and wheter if this Workspace will be shared with your Team, Pubilic or it will be Personal (Only for you) 
4. Click **Create Workspace** button  

Now you created your Workspace. If you click on **Workspaces** drop-down again you will see your newly created Workspace in a list. This is a list of all of yours Workspaces and from here you can edit and switch in-between them. Also, name of currentlu choseen Workspace is displayed under Workspaces drop-down.

##Collections

*Collections* are folders that help you organize your requests. Each collection can test different modules or related APIs. Also, having a collection is helpful if you need to monitor requests, and it is easy to export and share them. 

### Creation of a Collection

1. Click **New** button right from name of chosen Workspace 
2. Click **Collection**.
3. Enter collection name and press enter. 

Great, collection is created and now you can add requests. 

## Creation and execution of a request 

**Note:** Further in this article [PokeAPI](https://pokeapi.co/) will be used as an example. 

Once collection is created you need to add a reqest to it. There are a few ways to do it so let's begin. 

1. Expand your collection 
2. Click **Add a request** 
3. Enter the name of request, let's name this request "GET Pokemons"
4. Hit enter button 
5. Set `GET` as your HTTP request method and paste following URL `https://pokeapi.co/api/v2/pokemon/`to URL input field

 ![Postman_test_request.png](/img/Postman_test_request.png) 
 
6. Execute request by clicking the **Send** button

Great, now you executed a request. As a response in a Body, you can see a list of 20 Pokemons in JSON format.

![Postman_first_20_pokemons.png](/img/Postman_first_20_pokemons.png)

## Environments and variables 

An environment is a set of key-value pairs (key represents the name of the variable).
Environments let you customize requests using variables to switch between different setups
without changing your requests. 

From the list of Pokemons that you got after executin a request, let's save Bulbasaur's URL to an environmental variable. For that, first you need to add the environment.

### Creation of environment

1. In the top right corner tap the *eye* icon
2. Since you do not have environments, tap the **Add** button in the *Environment* card 
3. Environment card should open as a tab. Enter name of environment. Let's name it "Pokemons"

 ![Postman_variable.png](/img/Postman_variable.png)

4. Tap **Save** button.

 Great, now you have an empty variable in which you can add data. To switch in between environments clisk on Environments drop-down and choose desired one.

 **TIP:** Name your variables (constants) with the uppercase so that is easier to separate them from the rest of the code, for example in pre-request scripts and tests.
 
### Writing a value into the variable
 
There are two ways how you can enter a value to a variable:

* You can enter a specific value to **Initial** and **Current** values input fields. Value can be everything from URL-s, strings, numbers. Usually, both **Initial** and **Current** values are the same.

	* The **Initial Value** is synced to your account via the Postman servers and shared with any collaborators who have access to the environment.

	* The **Current Value** is local to your Postman app, and is never synced to your account or shared with your team—unless you choose to persist it.

* Or you can save a value from response to a variable. 
 
	1. Open "GET Pokemons" request.
	2. Switch to **Tests** tab inside this request.       
	3. Add following line of code in **Tests** tab:

	 ```
	const data = pm.response.json();
	pm.environment.set("BULBASAUR_URL", data.results[0].url);
	```

	3. Execute request by clicking **Send** button.

 This line of code will save in variable "BULBASAUR_URL" whatever is the value of `data.results[0].url` key, in this case Bulbasaur's URL. If you now open "Pokemons" environment you will see that variable contains Bulbasaur's URL. 


### Using variables

Using variables you avoid copy-paste of URL and the good thing is that variables can be used as many times as you need. 

To use variable you need to enter name of variable in between double curly braces. It should look like this: `{{VARIABLE}}`. This way Postman will read and use a value from a variable. Or you can use combination of variable and URL like this: `{{VARIABLE}}/example_url`.

* Let's now use "BULBASAUR_URL" variable and value stored inside her. 

1. Create a new `GET` request but this time instead of URL enter `{{BULBASAUR_URL}}`in URL input field  
2. Execute request. 

As a response, you will get more technical information about Bulbasaur.  

![Postman_expected_result.png](/img/Postman_expected_result.png)

* **TIP:** If there is an error, variable `{{BULBASAUR_URL}}` will be red indicating that you either misspelled its name or the variable does not exist - you did not create it and add it to your environment or you are using wrong environment. 


## Pre-request scripts

Pre-request scripts are snippets of code that can be added to a collection, a folder, or a single request within a collection that is executed before the request is sent. The pre-request script can be super usefull and best example of it is for a token creation.

### Adding pre-request script to a single request:

1. Open "GET Pokemons" request 
2. Switch to **Pre-request Script** tab

Let's take a loot at example of pre-request script for token creation:

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


## Writing tests 

With Postman you can write and run tests, and they run every time you run a request. They are really halepfull when you are using collection runner because they give you good preview if request went well or failed. 

Good thing about tests is that Postman offers "Snippets" or list of already written tests. Simply clicking on them you can add them and best thing is that you can add as many tests you need.

### Adding snippets:

1. Open "GET Pokemons" request
2. Switch to **Tests** tab 
3. Right from text field locate "SNIPPETS" list
4. Find "Status code: Code is 200" snippet and clicking on it 

 Now you will see code like this: 

 ```
 pm.test("Status code is 200", function () {
 pm.response.to.have.status(200);
 });
 ```

5. Execute request
6. In response of a request, switch to the **Test Results** tab 

	Here you should see test "Status code is 200" marked as PASS.
 
![Postman_status200.png](/img/Postman_status200.png)

 **TIP:** Add one or two empty rows so that your tests are separated and in that way easier for reading.

### Adding more complex tests 
	
Sometimes it can happen that the status of response is 200 but the body is empty. In this case, we need to add some complexity. Let's now check if the response returned something that does not change, for example, Bulbasaur's base experience. 

1. For this test we will need to add the "BASE_EXPERIANCE" variable and set the value to 64
2. Add the following code under "Status code: Code is 200" 

 ```
pm.test("Base experience", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.base_experience.toString()).to.eql(pm.environment.get("BASE_EXPERIANCE"));
});
```
3. Execute request
 
 If status is 200 and base experience is indeed 64, tests will be marked as passed. 

![Postman_2x_tests.png](/img/Postman_2x_tests.png)

## Collection runner

The Collection Runner allows users to run sets of requests in a specified sequence against specific environments. You can also set number of iteration, delay, save response keep variable values...

1. Click collection that you want to run
2. After collection tab is opened click **Run** button
2. Another tab with all requests inside collection should open
3. Choose which requests you want to include in this run. For this example let's leave them all selected 
4. Make sure that you are using correct environment for your collection
5. Click **Run "name of collection"** button
 
Postman will display request executions and test results in real time.
If any test in a request script fails during the collection run, request will be listed as failed but with proper response status. 

![Postman_test_fail.png](/img/Postman_test_fail.png)

If all tests from the list are listed as passed then the request will also be listed as passed. 

![Postman_tests_success.png](/img/Postman_tests_success.png)

**TIP:** Results can be exported by clicking on the **Export Results** button and attached to the regression test or any other type of tests if it is required. 
 
## Collection monitoring

Collection monitor is basically a scheduled collection runner. As mentioned value of collection run is in tests. Setting up monitor you collection runn will be run as frequent as you want and if one of these tests fails, you will  automatically receieve email notification.

### Setting up collection monitoring 

1. Click **Monitors** in your Workspace menu on left side of Postman
2. Click **Create a Monitor** 
3. Add monitor name
4. Select collection that you want to monitor
5. Select environment for your collection
6. Set time when do you want for your monitor to be executed
7. Select "Receive email notification for run failures and errors" checkbox 
8. Enter email address whey you want to get notification

Great, now your collection will be run at set time and you will be notified if one of your requests failed. 

## Additional resources:

Check a blog post from one of our QA members [Writing API Tests? Postman Delivers
](https://infinum.com/the-capsized-eight/postman-API-testing)

Also see this interesting article [Testing APIs with Postman: 10 common challenges & solutions
](https://medium.com/distant-horizons/testing-apis-with-postman-10-common-challenges-solutions-c4674c78528d).

---
![using-postman.gif](/img/using-postman.gif)

