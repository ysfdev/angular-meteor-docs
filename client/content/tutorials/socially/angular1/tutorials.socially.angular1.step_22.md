{{#template name="tutorials.socially.angular1.step_22.md"}}
{{> downloadPreviousStep stepName="step_21"}}

Ionic is a CSS and JavaScript framework. It is highly recommended that before starting this step you will get yourself familiar with its [documentation](http://ionicframework.com/docs/).

In this step we will learn how to add Ionic library into our project, and use its powerful directives to create cross platform mobile (Android & iOS) applications.

We will achieve this by creating separate views for web and for mobile  so be creating a separate view for the mobile applications, but we will keep the shared code parts as common code!

### Adding Ionic

Using ionic is pretty simple - first, we need to install it:

    $ meteor npm install ionic-sdk --save

To use ionic in our app we have to install `angular-sanitize`:

    $ meteor npm install angular-sanitize --save

Ionic doesn't support yet alpha version of `angular-ui-router`, we need to install the latest stable:

    $ meteor npm install angular-ui-router@^0.2.18 --save

Now we've got all of modules. Let's add the first module to Socially:

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.4"}}

The second one is Ionic. We need to import not one but two files. It should look like this:

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.5"}}

Now's the time to add some style:

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.6"}}


### Separate the Socially view

We will do the same thing as we did in previous chapter with `Login` component.

Let's create a view for the web. We can achieve this by copying the content of `socially.html`:

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.7"}}

Now let's take care of mobile view:

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.8"}}

This is a simple navigation layout. As you can see it is pretty similar to the web view.

> The `ion-nav-view` tag is similar to the `ui-view` tag

Last thing to do is to implement these views:

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.9"}}

We will no longer use `socially.html`, so let's remove it!

By now, the navigation bar is empty, we can change this by adding `ionNavTitle`:

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.11"}}


### Running mobile app

We will use the techniques we learned in Step 21 of the tutorial and run the project in our favorite emulator, I used Android so

    $ meteor run android

Socially is working but the list of parties looks terrible!

### Use Ionic in list of parties

The web view stays the same so let's just copy `partiesList.html` to `web.html`:

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.12"}}

For the purpose of tutorial we want to keep mobile version of Socially as simple as possible.

Let's display only name, description, image and list of RSVPs.

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.14"}}

Ok! We have both views. It's time to implement them and remove the old `partiesList.html` file:

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.15"}}

There is a terribly looking margin at the top of the first party. This will fix it:

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.16"}}

You've probably noticed an issue with images. It happens because `jalik:ufs` package saves an absolute path of a file. So if you uploaded an image in the browser its path will contain `http://localhost:3000`.

But hey! We're on the mobile app so the port is different.

We can fix it by creating a filter. Let's call it `DisplayImageFilter`:

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.17"}}

Done, we have it! Now we want to use it:

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.18"}}

{{> DiffBox tutorialName="meteor-angular1-socially" step="22.19"}}

And... we're done!

## Summary

In this tutorial we showed how to use Ionic and how to separate the whole view for both, web and mobile.

We also learned how to share component between platforms, and change the view only!

We also used Ionic directives in order to provide user-experience of mobile platform instead of regular responsive layout of website.

{{/template}}
