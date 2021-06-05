%%
ID: 2894416
Updated: 2020-06-02
%%
![](https://readwise-assets.s3.amazonaws.com/static/images/article0.00998d930354.png)

# About
Title: [[One Observer for All Buttons in Shiny Using JavaScript  jQuery]]
Author: 
Category: #articles
Number of Highlights: ==4==
Last Highlighted: *2020-06-02*
Readwise URL: https://readwise.io/bookreview/2894416
Source URL: http://www.open-meta.org/technology/one-observer-for-all-buttons-in-shiny-using-javascriptjquery/


# Highlights 
As an alternative to actionButton(), however, it’s pretty simple to have a JavaScript / jQuery function that watches for <button> clicks and uses Shiny.onInputChange() to let R and Shiny know the id of the button that was clicked.  ^63623502

---

Here’s some sample jQuery code for setting this up on the JavaScript side. Include this in your script file. (There’s more on basic JavaScript/Shiny interactions, including how to set up the script file, in How to get Shiny on the server and JavaScript in the browser talking to each other.  ^63623503

---

Next let’s look at Shiny.onInputChange() in the final line. It sends the button’s id to an observer inside Shiny called js.button_clicked. It appends the BUTTON_CLICK_COUNT onto the button’s id. So, if the button id is view_1 (in this example, view means a View Project button, 1 indicates the the row the button is in), what the js.button_clicked observer would receive is something like view_1_1.

The BUTTON_CLICK_COUNT is just a trick to make sure Shiny thinks the input has changed . Without that, sometimes a button will go dead because although Shiny.onInputChange() sees the click, it doesn’t think anything has changed, so it doesn’t send the id back to the server. All of the other code in the embedded function does nothing but come up with that number. Once back in Shiny on the server, the click count is meaningless.  ^63623504

---

For each type of button you have, you include code in this observer that reacts to the type of button (in this example, View Project or Join Project) and the exact row the button was in (in n). And that’s how you can have any number of buttons and just one observer in Shiny server.

This method can be extended to include other HTML elements. In the next post, Adding anchors to our Shiny button observer, the JavaScript / jQuery event handler also deals with menus that have href-less anchors.

I figured out this trick after reading JavaScript & jQuery while traveling over spring break. This is the most readable programming book I’ve ever encountered.  ^63623505

