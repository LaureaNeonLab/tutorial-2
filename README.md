# tutorial-2

## First things First

We are going to make use of a technology called Firebase during this tutorial. It is able to perfectly integrate into hybrid applications and reduces the production time considerably. If you have no experience in backend programming this will be a great tool for you to begin learning how it all fits together.

This app is a variation on a to do list. It will take input add it to a list and then be marked as done.

## Step 1 - Create a Persoanl Repo and then Blank Ionic App.

We will use a blank template and are only going to be using the app.js and index.html files during this example.

Lets add this app to your personal github accounts and not the LaureaNeonLab.
Remember when creating a repo remotely with code you already have created do not initialize with a README.md.

After the repo is ready we need our app. `ionic start blank` is the command for this.

Open the **www** folder in Visual Code with index.html and app.js side by side. 

In the `index.html` you should see in the `<body>` tag the following code:

```
<body ng-app="starter">

    <ion-pane>
      <ion-header-bar class="bar-stable">
        <h1 class="title">Ionic Blank Starter</h1>
      </ion-header-bar>
      <ion-content>
      </ion-content>
    </ion-pane>
    
  </body>
```

## Step 2 - Editing our app to something simpler.

We do not need the basic part in the blank app so remove everything between the  `<body>` tag. and we will begin fleshing it out with our own designs.

Lets add a header to our app with the follwing code between the `<body>` tags.

```
<ion-header-bar class="">
    <h1 class="title"></h1>
</ion-header-bar>
```

In the `class` attribute feel free to add whatever style you want, but try to be consistent in your designs so it looks good.

We also require the below code block just after our header to hold the list we will create:

```
<ion-content>
    <ion-list>
        <ion-item>
        </ion-item>
    </ion-list>
</ion-content>
```

This code is a content area that holds a list that holds items. Sounds pretty straight forward. Luckily the more items we create we wont have to duplicate this code for any more items. we will use an Angular directive called `ng-repeat` to repeat all our items using this block.

## Step 2 - Time for the app.js and what we will do there.

In the app.js you should see the following code:
```
angular.module('starter', ['ionic'])

.run(function($ionicPlatform) {
  $ionicPlatform.ready(function() {
    if(window.cordova && window.cordova.plugins.Keyboard) {
      // Hide the accessory bar by default (remove this to show the accessory bar above the keyboard
      // for form inputs)
      cordova.plugins.Keyboard.hideKeyboardAccessoryBar(true);

      // Don't remove this line unless you know what you are doing. It stops the viewport
      // from snapping when text inputs are focused. Ionic handles this internally for
      // a much nicer keyboard experience.
      cordova.plugins.Keyboard.disableScroll(true);
    }
    if(window.StatusBar) {
      StatusBar.styleDefault();
    }
  });
})
```
> Delete it!

We will write our own code from scratch. with the first statement being `angular.module('starter', ['ionic'])`

## Step 3 - Back to the index.

Lets just run our application from the command line with the following command to check both iOS and android views at the same time:

> ionic serve -w chrome --lab

Ok still pretty simple but it at least runs. Next we are going to add a button and a check button to tick our items in the list off. we will change our code to the following:

```
<body ng-app="starter">
    
    <ion-header-bar class="bar-dark">
        <h1 class="title">Items List</h1>
    </ion-header-bar>

    <ion-content>
        <ion-list>
            <ion-item>
            
            <ion-option-button class="button-balanced">
                <i class="icon ion-checkmark"></i>
            </ion-option-button>
            </ion-item>
        </ion-list>
    </ion-content>
    
  </body>
```

If we go back to our localhost server in the browser we can test this button.

It needs some css transition styles for the `<ion-item>` to allow the checkbox slide out in a fancy way. We will use the `ng-class` directive on the item tag.
We also want to allow this item to repeat so we also need `ng-repeat`. Our opening item tag should look like the following
 
> <ion-item ng-repeat="item in items" ng-class="{purchased: item.status === 'purchased'}">

for the purchased class we need to add our own style in `style.css` like follows:

```
.purchased {
    color: WHATVER YOU WANT;
    text-decoration: line-through;    
}
```

Our ng-repeat directive is linked to the item tag but we have no place to repeat the actually items. We use what is called an expression for this. it 2 way data binds data. for more information on this see the below link and add this expression in between the item tags:

>  https://docs.angularjs.org/guide/databinding 
> `{{item.name}}`

## Step 4 - We need something to control this functionality.

We know already that for the application we need `ng-app="starter"` so that when it is being run the system knows that this is where the application should be run.
However we have no functionality so we need a controller. Lets add one to the body tag as follows:

> `<body ng-app="starter" ng-controller="ListCtrl">`

We also need to add functions that will be listed in this controller, for this we need a button to add items to the list. Edit your header so it matches below:

```
<ion-header-bar class="bar-dark">
    <h1 class="title"></h1>
    <button class="button button-icon ion-plus" ng-click="addItem()"></button>
</ion-header-bar>
```

The `addItem()` is going to be added to our controller as part of the functionality inside the app known as `"starter"`. This should start making sense if not repeating this excersize from memory will help as good practice.

## Step 5 - Recap and onto The app.js Controller

In our app.js underneath the angular declartion we need to creat a controller called list Ctrl. It will be like the following code.

```
.controller
```
