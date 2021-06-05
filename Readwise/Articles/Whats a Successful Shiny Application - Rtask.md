%%
ID: 3007931
Updated: 2020-06-12
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article1.be68295a7e40.png)

# About
Title: [[Whats a Successful Shiny Application - Rtask]]
Author: [[Agence Breizhtorm - Www.Breizhtorm.Fr]]
Category: #articles
Number of Highlights: ==7==
Last Highlighted: *2020-06-11*
Readwise URL: https://readwise.io/bookreview/3007931
Source URL: https://rtask.thinkr.fr/whats-a-successful-shiny-application/


# Highlights 
That seems like an obvious concept, but of course a Shiny application is successful and ready for production if the dev team was able to move from the idea to the actual implementation to the delivery of the app. It’s a very ‘engineer-oriented’ definition of success, but that’s a pragmatic one: a project that doesn’t exist can’t be labelled as a successful one.  ^65137768

---

Working in a framework like {golem} does help you reaching this goal: working inside a formalised structure will help you keep track of what is happening, and allows to grasp more easily what is contained in a given project. For example, if I today open a {golem} project I have never seen before, I will immediately be able to understand how the codebase is organised.  ^65137769

---

t’s Accurate
Once the application exists, the other parameter that defines a production-grade application is that it is accurate. In other words, the visualisation are correct, the algorithms return the answer they are supposed to, the information are the needed one, etc.  ^65137770

---

And yes, it happens that you deliver an application that works differently from the way it is expected to work. How do we prevent from that? First of all, by applying the “separation of concern”:

Business logic should be strictly separated from the application logic: build the back end and the non interactive functions separately from the interactive elements, work on them, validate them, and only once everything is thoroughly tested you can start integrating both together.
Build a strong and reliable testing suite, so that you can catch any bug that will come along your project.  ^65137771

---

It’s Usable
Your application exists, it’s accurate, but now you should get sure it’s usable—in other words, your audience should visit the app and find it user-friendly.  ^65137772

---

It’s Immortal
Of course nobody expect your app to live forever, but that’s what you should reach for: robustness along the years.  ^65137773

---

it is successful if it can exist in the long run, with all the hazards that this implies: new package versions that could potentially break the code base, sudden call for the implementation of new features in the global interface, changing key features of the UI or the back-end, and not to mention passing the code base along to someone who has not worked on the first version, and who is now in charge of developing the next version . And this, again, is hard to do without effective planning and efficient engineering.  ^65137774

