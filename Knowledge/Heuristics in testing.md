Heuristics are mental shortcuts that allow an individual to make a decision, pass judgment, or solve a problem quickly and with minimal mental effort. 
They help us process large amounts of information and make many choices with limited amounts of time. They reduce the burden of decision-making and free up limited cognitive resources. When information is missing, or an immediate decision is necessary, heuristics act as “rules of thumb” that guide behaviour down the most efficient pathway. 
However, they can also be costly when they lead individuals to miss critical information or act on unjust biases. 

There are many software testing heuristics that can help guide you in your testing processes. You probably already know about the Goldilocks heuristic (even though you might not call it that). For example, when testing data input fields, you will probably try out data entries that are too big or too small, as well as the typical entries. This is rather thoroughly covered in [another Handbook chapter](https://infinum.com/handbook/books/qa/testing/testing-forms).


## Cheat sheet with different heuristics

In the image below, you can find an expanded overview of the Goldilocks heuristic along with a cheat sheet containing other interesting test heuristics you should keep in mind when you start testing:

![Heuristics cheatsheet](/img/Heuristics_Cheat_Sheet.png)

The full cheat sheet can be found [here](https://testobsessed.com/wp-content/uploads/2011/04/testheuristicscheatsheetv1.pdf).


## Mnemonics

The easiest way to remember some of the most popular heuristics is through mnemonics. Mnemonics are memory devices that help in the retention and retrieval of larger pieces of information. For example, you can remember the first letter of each word in a list of items.


### RCRCRC

One such mnemonic is [**RCRCRC**](https://searchsoftwarequality.techtarget.com/tip/A-software-experts-heuristic-for-regression-testing), which can give you inspiration for your regression testing. 

- **Recent:** what new features or new areas of code have been added?
- **Core:** what essential or critical functions or features must continue to work?
- **Risky:** what features or areas of code are inherently riskier? 
- **Configuration Sensitive:** what code is dependent on environment settings? 
- **Repaired:** what code has been changed to address defects and therefore may have created issues? 
- **Chronic:** which code may seem to be chronically breaking or having issues?


### I SLICED UP FUN

Another popular mnemonic for testing mobile apps is [**I SLICED UP FUN**](http://www.kohl.ca/articles/ISLICEDUPFUN.pdf).

- **Inputs into the device:** the ways in which you can interact with the device such as built-in keyboard/keypad, touch screen gestures, and typing
- **Store:** application requirements for store submissions
- **Location:** your current location or movement might have an impact on your tests
- **Interactions/Interruptions:** run other applications at the same time while testing your app 
- **Communication:** test how your app interacts with features related to communication (texting, emails, calls, voicemail, etc)
- **Ergonomics:** after some time using your app, do you have signs of physical stress
- **Data:** look for the data that is processed by the app (types of input, media, updates)
- **Usability:** while testing your app, look for any actions that are awkward, confusing, or slow
- **Platform:** make sure that you know the technical details about the device and the operating system version you are using
- **Function:** click all the buttons and fill out every form
- **User Scenarios:** imagine what some real users would do in your application. Try to create scenarios of real people/personas and how they react using the software
- **Network:** explore scenarios related to poor network connection, moving from one network to another, network without data, etc.


### FEW HICCUPS

[**FEW HICCUPS**](https://www.developsense.com/blog/2012/07/few-hiccupps/) is a mnemonic that can help you remember key words for oracles that could support you with identifying problems in your product. These oracles are particularly useful when a specification is missing or contains inadequate information. It’s important to note that all oracles are heuristics; they’re just a specific type of heuristic which could help you recognize problems in your product. 

- **Familiarity:** we expect the system to be inconsistent with patterns of familiar problems. We might start our test sessions in search of familiar issues, which might divert us from other issues
- **Explainability:** we expect a system to be understandable to the degree that we can articulately explain its behaviour to ourselves and others
- **World:** we expect the product to be consistent with things that we know about or can observe in the world
- **History:** the present version of the system should be consistent with past versions of it
- **Image:** the system should be consistent with an image that the organization wants to project (brand, reputation)
- **Comparable Products:** we expect the system to be consistent with systems that are in some way comparable
- **Claims:** the system should be consistent with things important people say about it
- **Users’ Desires:** the system should be consistent with ideas about what reasonable users might want
- **Product:** we expect each element of the system (or product) to be consistent with comparable elements in the same system
- **Purpose:** we expect the system to be consistent with the explicit and implicit uses to which people might put it 
- **Statutes:** we expect a system to be consistent with laws or regulations that are relevant to the product or its use

An important thing to remember when you're applying some of these (or other) heuristics is that not every heuristic is applicable to every app. And this is okay. You are allowed to cherry-pick what you think your testing would benefit the most from. 

## Personal heuristics

Now that you understand how other people use them, maybe you can think of some of your own heuristics. You can try the following:

- identify where you’re already using them - they can be anything, from the order in which you open the tabs in your browser when you are organizing your workday to the way you execute test cases
- always try to have some awareness of your testing decisions, think about why you are testing something and justify your decisions to avoid bias
- reflect on what you do and why you do it and this might help improve your testing processes, think about your testing activities, write a journal if you must 
- talk to a rubber duck to help you clear your mind
- test with a buddy
- teach others about what you do
