> *Design is not just what it looks and feels like. Design is how it works.*

The right way for preventing errors in the app and making sure that everything works smoothly is by testing the design while the app is still in the making. This way we can detect problem areas and flows of the app before the final design is done and make changes accordingly. 

This means that we check the design part while it's still in the wireframe stage, where screens have the functional elements and their placement in the app. So basically one step before all the fancy visuals that we see in the final result. 

For that we need a **prototype** (which is usually done in Figma or Invision). It’s a clickable mock prototype of the app made by designers lacking the animations, hover states, moving components... 

So you have the prototype and you're ready to test. What next? 

Here is a checklist that will help you! It can also be used for the finished design if needed.

## QA checklist example

**APP NAME:** My Telecom

**TYPE:** Telecom app

**SHORT INTRO:** With My Telecom you can quickly and easily manage your account. We have many cool features that can help you to track your consumption, buy data options or share MB with friends and family if you have some extra. It is available to all of our customers, no matter which service you use (prepaid, private subscribers, Internet users, etc.)

**INFINUM SIDE:** Frontend, design, QA

**TARGET GROUP:** Users of My Telecom (prepaid, postpaid, business) aged 15 to 99

**USER EXAMPLES:**

Ana

- 21 years old
- Student
- She’s great with mobile phones and apps, performs all the actions quickly and easily
- Interested in free options, bill top up and new features

Mario

- 48 years old
- Business man
- He knows how to perform basic actions, not so great with new apps, does the same three things every time he enters the app and is easily confused
- He wants to see his balance and bill overview, he sometimes wants to activate extra options


**MAIN ACTIONS IN THE APP:**
Balance and overview of the activated options
Bill top up / Bill payment
Activating extra options and packages
Review of requests


**TESTING:**

**1. Initial app exploration** - Overview of the app, general impression of the information clarity and flows

**2. (Optional) Adding new feature** - comparison with the existing app

- Flow logic - screens and flows behave in an expected way
- Funcionality logic - actions (buttons, animations, clicking and swiping,...) behave in the same way
- UI - the look and feel fits in the app (color, illustration, fonts, shadows,...)

**3. Detailed testing:**

- Action execution - Can you finish the whole flow in an ideal way? If not, what’s stopping you? How far can the average user get?
- Flow simplicity - Can users navigate through the app in a way that’s easy to understand? Is there any part (flows, screens, information) that is confusing or complicated? Should we add/remove some steps?
- Time needed - How much time does it take to finish the actions? Is that too much/too little?
- Error detection - Is it easy to make a mistake? Can user recover and get back on track in an easy manner?

**4. UI element consistency (only some things can be checked on wireframes, others are only for finished design)**

- Margins and padding
- Fonts (size, style, color, placement)
- Colors
- Buttons (design + states: active, disabled, loading, hover)
- Placement of the elements on the page (alignment)
Illustrations/photos/animations/videos have the same style

**5. List of all screens**  - check if there are any missing screens

- Empty states
- Onboarding screens
- Extra screens

**6. Platform consistency** 

- Navigation placement
- Design of buttons (specific for platform, for example share button)
- Native buttons (for example - back button)...

---

![dil.gif](/img/dil.gif)
