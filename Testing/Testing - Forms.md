> *“No amount of testing can prove a software right, a single test can prove a software wrong.”*

## Testing forms

Forms are often the hiding place of complicated business logic so we will start off this section with a quick primer on testing forms.

Since the set of inputs a non-trivial form can take is often infinite, it is literally impossible to test everything. This is why you need to be smart about it by using some basic testing techniques and shortcuts.

### Why do we test forms

#### 1. Security

Malicious users can exploit text fields to get information they shouldn't have and it can be done by SQL injections or some kind of scripting. 

#### 2. Stability

When a user is able to input data that the application is not equipped to handle, the application can react in unexpected ways, such as crashing or refusing to save.

#### 3. Visual Consistency

When a field has too many characters in it, it can affect the way a page is displayed. Make sure that everything is done by design and consistent. 

#### 4. Health of the Database

When fields are not validated correctly, all kinds of erroneous data can be saved to the database.  This can affect both how the application runs and how it behaves.

### Equivalence partitioning

Equivalence partitioning is partitioning a set of possible inputs into classes. Each member of the class is deemed identical to all other.

Let's say you have an input field which can only accept **numbers in the range of 1-200.000**. These would be the equivalence classes you have to check:

- Numbers that are smaller than the min (smaller than 1)
- Number that are within the range (1-200.000)
- Numbers that are above max (larger than 200.000)

#### Boundary value analysis
We can expand on the aforementioned by including **boundary value analysis** as well. That means you would also use the following inputs:

- The min number
- The max number
- Numbers around the min and max number

Here's an example:

![bva.png](/img/bva.png)

We do this because almost everyone had a problem with [OBOE](https://en.wikipedia.org/wiki/Off-by-one_error) in their coding carrer.

#### Addendum
Additionally, because you are curious, you could also:

- Input a number that falls outside of the [32-bit integer range](https://en.wikipedia.org/wiki/2,147,483,647)
- Input something that is not a number
- Input nothing
- etc. (use your imagination)

Even Google had a problem with the first point:
*In December 2014, Google said that PSY's music video "Gangnam Style" had exceeded the 32-bit integer limit for YouTube view count, necessitating YouTube to upgrade the counter to a 64-bit integer.*


#### Field validation table

Let's look at some data types and inputs that are considered valid and invalid.

| Data Type           | Valid Inputs                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       | Invalid Inputs                                                                                                                                                                                                                               
|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Integers or Numbers | • Only Numbers<br>• Less than the limit (N)<br>• Enter the value within the limit (N + 1)/2                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | • More than the limit (N + 1)<br>• Numbers with precision<br>• Numbers in Exponential Form<br>• Negative Integers<br>• Only Alphabets<br>• Numbers + Alphabets<br>• Numbers + Special Characters<br>• Unicode Characters e.g. U+0000, U+0001 |
| String              | • Only Alphabets<br>• Only Numbers<br>• Only Special Characters<br>• Numbers + Alphabets<br>• Numbers + Special Characters<br>• Alphabets + Special Characters<br>• Less than the limit (N)<br>• Enter the value within the limit (N + 1)/2                                                                                                                                                                                                                                                                                                                                                                                                                        | • More than the limit (N + 1)<br>• Unicode Characters e.g. U+0000, U+0001                                                                                                                                                                       
| Date                | • Check that whether date picker is present or not<br>• Check that date field is non editable<br>• Ensure that, upon right clicking on the date field, paste option should be disabled & copy option should be enabled<br>• Ensure that, upon clicking on date in the calendar, it should be displayed in the date field<br>• Select a leap year and verify the days in February month<br>• Select a non leap year and verify the days in February month<br>• Ensure that, calendar is having provision to select any year, month (combo box, drop down list, links etc.)<br>• Ensure that, clear button is present in the date picker to remove the selected date|                                                                                                                                                                                                                   


### Forms feat. UX - Capitalization & keyboard types

To round this off, let's relax and talk about UX and capitalization in forms.

You'll rarely find capitalization principles and keyboard type suggestions in your projects' requirements list. That's because these things are very often on the "goes without saying" list, but it's always a good idea to confirm the implementation.


| Input field type | Capitalization and other rules                                                                                                                                                                                      | Input type |
|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|---|------|
| Name/surname     | • Each word should start with the capital letter.<br>• All letters and symbols are allowed.                                                                                                                      | text       |   |      |
| Email            | • All letters and symbols are allowed.                                                                                       | email      |   |      |
| Phone number     | • Only numbers are allowed.                                                                                                                                                                                          | tel        |   | <br> |
| Number           | • Numbers and symbols are allowed.<br>• Try to use the "tel" input type as often as you can, because the "number" type is useful only when symbols are allowed. In all other cases, "tel" type is the superior option. | number     |   |      |
| Password         | • All characters are allowed<br>• All characters are hidden by default.                                                                                      | password   |   |      |
| Date             | • The default date picker component should appear.                                                                                                                                                                   | date       |   |      |


### BugMagnet 

There is an awesome plugin for Chrome and Firefox that can be used for testing forms. You can pick it up right [here](https://bugmagnet.org/) on this link and after it is installed, just click right-click on any form and input any kind of data that can break the input form. 
