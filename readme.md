## A handy utility to simplify reacting to media queries within JavaScript

### What is it?

It's a small (228 bytes) utility that sits atop window.matchMedia. If you want to run some JavaScript code when a given media query is matched (and/or unmatched), you might find it useful.

### Why does it exist?

I wanted a way to keep all of my code oriented media queries together using a succinct key/value format (where *key* is a media query, and *value* is a function (action) I want to execute when the given media query is matched/unmatched. Generally, you want to test for media query matches upon initial page load and on an ongoing event driven basis, this takes care of wiring up to window.matchMedia for both cases.  

### How do I use it?

Create an object that consists of keys (your media queries) and values (your action functions). Call the *responsiveActions* function, passing this object.  Your action functions will be triggered when the associated media queries are matched and unmatched. A truthy value will be passed - you can use this to see if the associated media query was just matched or unmatched. 

Should you need the original mediaQueryList object (as in, the object that is passed to event handlers when working directly with MediaQueryList.addListener) you can do so via your action functions' second argument.

The example below should clarify how 'responsive actions' work.

    var actions = {

        'screen and (min-width: 500px) and (max-width: 799px)': function (matches) {

            if (matches) {
                console.log("500 to 799 is now active");
            } else {
                console.log("500 to 799 is no longer active");
            }

        },

        'screen and (min-width: 900px)': function (matches) {

            if (matches) {
                console.log("900 plus is active");
            } else {
                console.log("900 plus is no longer active");
            }

        }

    }

    responsiveActions(actions);


Too easy. Just remember to reference the 'responsive-actions.js' or 'responsive-actions-min.js' file and you should be good to go. 