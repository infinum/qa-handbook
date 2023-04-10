# Exploratory testing

### Introduction

Exploratory testing is a type of software testing where the tester actively explores the application to discover defects, rather than following a strict plan or script. This approach allows for more flexibility and creativity in the testing process. As a tester, you can discover and test new areas of the application as they come up. It's a great way to find defects quickly and efficiently. It is especially useful for finding defects in new or untested areas of the application.

### Web and Mobile App Testing

Exploratory testing on web and mobile apps is similar, but there are some differences in the testing process due to the different characteristics of web and mobile apps. It's important to understand the different characteristics of each platform. 

- For example, when testing web apps, you need to check that it works correctly on different browsers, operating systems, screen sizes and resolutions to ensure it looks and behaves correctly on different devices. 
- On the other hand, mobile app need to be tested on different devices, operating systems, screen sizes and resolutions and also in different orientations (portrait and landscape) to ensure that it works correctly on different devices. Additionally, mobile apps needs to be tested on different network conditions to ensure that they can handle different network speeds and connection types. Also, mobile apps have different interaction patterns such as gestures, touch, and different navigation patterns which need to be tested on different platforms (iOS, Android, etc.)

### Heuristics in Exploratory Testing

Heuristics are general principles or rules of thumb that can be used to guide the testing process. In exploratory testing, heuristics can be used to guide the tester in discovering defects and testing new areas of the application. Some common heuristics that can be used in exploratory testing include error guessing, boundary testing, cause-and-effect graphing, checklists, pair testing, exploring the application with different perspectives and mind mapping. If you want to learn more about heuristics, check out the [Heuristics in the testing](https://infinum.com/handbook/qa/testing/heuristics-in-testing) section of our QA handbook.

### Creativity and Research in Exploratory Testing

Creativity and research are essential elements in exploratory testing, as they allow you to think outside the box and discover new areas of the application that may not have been considered in the test plan.
Creativity in testing allows you to come up with new and unexpected ways of testing the application, which can lead to the discovery of defects that more traditional testing methods may have missed. For example, a creative tester may come up with a new test scenario or test case that is not included in the test plan, but that uncovers a defect in the application.
Research is also important in exploratory testing, as it allows you to gain a deeper understanding of the application and its functional requirements, including its intended use, limitations, and potential problem areas, as well as any known issues or defects. This knowledge can be used to focus the testing on the most important areas of the application and identify defects more quickly and efficiently.
By combining creativity and research in testing, you can ensure that they are performing efficient and effective exploratory testing, and that you are discovering and reporting on defects in the application in a timely manner. 

### Testing
Before you start exploratory testing, it's important for you to have a good understanding of the application's functional requirements and any known issues or defects.
During exploratory testing, it's important for you to document the areas of the application that have been tested, any defects that have been identified, and any testing observations or questions that arise. This information can be used to improve the testing process and to create a more comprehensive test plan for future testing.
Exploratory testing can be done using different techniques such as ad-hoc testing, risk-based testing, and not to forget "Rapid Testing" and "Session-based Test Management" (SBTM) which were developed by James Bach. Rapid Testing is a process that emphasizes on fast testing, and SBTM is a technique that involves setting a time-box for testing and recording the areas explored and defects found during that session. It's important for you to understand the different techniques and choose the one that fits the specific testing situation.
Exploratory testing is a continuous process, and it's important for you to review and improve the testing process after each testing session to ensure that the most important areas of the application are being tested and that any defects found are being addressed.

When doing exploratory testing you should:

- Determine the time you will spend, e.g. 2 hours.
- Determine how many sessions you will have.
- Determine whether you will test alone or with someone else.
- Determine a goal of your testing.
- Determine an approach you will take.
- Write down all the questions you had.
- Write down the steps you have taken.
- Write down the issues you have found.

Sometimes, all of the above is planned via an exploratory testing charter. Other people really like using mind maps. In any case, the whole point is in investigating and freely exploring what you have set out to test. You will need to find out which test planning method works best for you.

Read more on exploratory testing from [Cem Kaner](https://secureservercdn.net/198.71.189.51/13j.276.myftpupload.com/pdfs/QAIExploring.pdf) or [James Bach](https://www.satisfice.com/exploratory-testing).


#### Examples

An example of a feature in an application could be a "QR code scanner" feature similar to the one offered by Google. Some steps that could be taken during an exploratory testing session for this feature include:

- Verify that the QR code scanner page loads correctly and all elements are displayed correctly, including the camera preview and the scan button.
- Test the functionality of the QR code scanner, including scanning a variety of QR codes and ensure that it can read and decode them correctly and show the appropriate action.
- Test the functionality of the "back" button, including verify that it takes the user back to the previous page.
- Test the functionality of the flash button, including verify that it turns on and off the flash when needed.
- Test the functionality of the "share" button, including verify that it can share the scanned QR code data to other apps.
- Test the functionality of the QR code scanner in different network conditions, such as different connection types (Wi-Fi, cellular) and speeds, to ensure that it can handle different network conditions.
- Test the QR code scanner feature with different mobile devices to ensure compatibility and verify that it works on both iOS and Android.
- Test the QR code scanner feature in different lighting conditions and verify that it can read the QR codes in low light conditions.
- Test the QR code scanner feature with different size of QR codes and verify that it can read and decode them correctly.
- Test the QR code scanner feature with different types of QR codes like url, contact, text, and event etc.
- Test the QR code scanner feature with different barcode data, such as invalid barcodes, to ensure that it can handle different types of barcode data.
- Test the feature in different orientations (portrait and landscape) to ensure that it works correctly on different devices.
- Test the feature in different scenarios, such as scanning a barcode on a real product 

![Exploratory testing QR snanner steps](/img/Exploratory_Testing_QR_code_scanner_steps.png)

This is one example of an exploratory testing session, but the specific steps taken may vary depending on the application and the feature being tested.

Here is an example of something that you may not discover while testing with the test cases, but you can discover while doing exploratory tests.

An example of a feature in an application could be a "search" feature for an e-commerce website. While testing the feature with test cases, a you might only test the feature with a set of predefined search queries, such as searching for a specific product by name or category. However, during exploratory testing, you might discover a problem with the search feature when searching for a product using a misspelled or a non-standard (synonyms) word.

For example, while doing exploratory testing, a tester might accidentally type "sneakers" instead of "shoes" in the search bar. Upon submitting the search, the tester might notice that the website returns no results, even though there are products that would match the search query. This could indicate that the website's search algorithm does not account for misspellings or alternative spellings of words, and that it is not able to suggest a correct spelling. This is an issue that might not be discovered while testing with predefined test cases, but it could be found while doing exploratory testing.

Although exploratory testing is in core informal, you still need to have some formalities, and those are to record all your findings, thoughts, plans, ideas, bugs…
You need to ask yourself what you want from this exploration, what you want to find. **Write it down**.
While testing exploratory, you will find new and interesting bugs and issues. Definitely **write them down**.
Do you think you will recall all the steps to reproduce a newly founded bug? Just **write it down**.

Now that you have all the data and info. It is up to you how you will manage them – you can arrange them in checklists, spreadsheets, drawings, mental mapping, or whatever you fancy.