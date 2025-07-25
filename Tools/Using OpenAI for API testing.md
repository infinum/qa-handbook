### Purpose
This guide explains how to create functional API tests using OpenAPI, OpenAI (ChatGPT), and [Postman](https://infinum.com/handbook/qa/tools/using-postman), with
no prior experience needed.
### Step 1: Generate Postman Collection + Tests with ChatGPT
Upload the OpenAPI file to ChatGPT and ask:
```
Here is an OpenAPI 3.0 spec. Please generate a complete Postman collection (v2.1 format) with:
- All endpoints
- Example request bodies and headers
- Functional tests for status codes (200, 201, 401, 404, 422)
- Test response fields like user.id, user.email
Use placeholder tokens where needed. Output raw JSON for Postman import.
```
### Step 2: Import into Postman
1. Open Postman.
2. Click **Import**.
3. Import the **JSON** file generated from ChatGPT.

![postman-import.png](/img/postman-import.png)  

### Step 3: Run Requests and View Test Results
1. Open a request.
2. Check the **Body** tab.
3. Click **Send** to run it.
4. Go to the **Scripts tab**, and use the **Post-response** Script section to write your test code.

![postman-tests.png](/img/postman-tests.png)

### Common Issue: 404 Not Found
- Check that the base URL is correct (not localhost).
- Ensure the HTTP method and endpoint path match.
- If authentication is needed, include headers like access-token, client, and uid.
### Tip for Edge Cases
Duplicate a request, rename it, and modify input data to simulate errors like 422 or 401.
### Summary
- Use ChatGPT to generate everything in one step.
- Import and run requests in Postman.
- Review test results under the Test Results tab.
### Small Tweaks, Big Difference
ChatGPT may not provide perfect results on the first try, but with a bit of experimentation and prompt refinement, it can produce highly effective and accurate outputs.
### How Reliable is the Output from ChatGPT?
ChatGPT is quite effective for generating functional Postman collections from clean OpenAPI documentation, especially when:
- The OpenAPI spec uses version 3.0 or newer.
- Example request/response data is present.
- Standard RESTful patterns are followed.

However, there are limitations:

- ChatGPT may miss undocumented edge cases or custom behaviors.
- Authentication flows (e.g., OAuth, token refresh) might be oversimplified.
- Placeholder values need manual replacement (e.g., localhost, sample tokens).

In short: ChatGPT is great for scaffolding, but human review is essential for real-world test coverage.

### Are There Other Tools for This?
Yes. Tools similar to ChatGPT that can help generate Postman collections or test scenarios from OpenAPI include:

- GitHub Copilot (with Copilot Chat) – Can assist in code/test generation if used in a code editor.
- Gemini (Google) – Accepts OpenAPI specs and can generate API test suggestions.
- Claude (Anthropic) – Good at parsing structured API documentation and producing formatted outputs.
- Custom GPTs (OpenAI) – You can build a specialized GPT that automatically handles OpenAPI-to-test automation flows.

These tools vary in output quality and may require some prompt tuning, but ChatGPT remains one of the most capable for this exact use case.
