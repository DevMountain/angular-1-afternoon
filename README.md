<img src="https://devmounta.in/img/logowhiteblue.png" width="250" align="right">

# Project Summary

In this project, we'll create an Angular application that displays a list of your friends. The list will be searchable and filterable through user interaction. You can see a live demo by clicking on the link below.

# Live Example

<a href="https://devmountain.github.io/angular-1-afternoon/">Click Me!</a>

## Setup

* Fork and clone this repository.
* Open the project directory in your coding IDE.

## Step 1

In this step, we'll create the skeleton of our Angular application.

### Summary

* Create a `js` folder at the root of the project.
* Create an `app.js` file in `js/`.
* Create a `friendCtrl.js` file in `js/`.
* Open `js/app.js` and create a new Angular application called `"myApp"`.
* Open `js/friendCtrl.js` and create a controller called `friendCtrl`.
  * Add a scope variable called test that equals `"Connected"`.
* Open `index.html`.
* Add a `script` tag for the Angular CDN.
* Add a `script` tag for `js/app.js`.
* Add a `script` tag for `js/friendCtrl.js`.
* Add `ng-app` and `ng-controller` to the HTML.
* Verify your `app` and `controller` are connected by adding `{{ test }}` to the HTML.
  * If `Connected` appears on the DOM, remove `{{ test }}` from the HTML and `$scope.test` from `js/friendCtrl.js`.

<details>

<summary> Detailed Instructions </summary>

<br />

Let's begin by creating a `js` folder at the root of the project. We'll use this folder to hold all our Angular javascript files. Inside this folder, create two new files: `app.js` and `friendCtrl.js`. We'll create our Angular application in `js/app.js`. Let's open this file and create an Angular application called `myApp`.

```js
angular.module("myApp", []);
```

Take note of the empty array after `"myApp"`, this is what tells Angular we are creating a new application. When we reference `myApp` we don't include the array again. We'll see an example of this when we create our controller. Now that our Angular application is made, let's make an Angular controller called `friendCtrl` in `js/friendCtrl.js`.

```js
angular.module("myApp").controller("friendCtrl", function( $scope ) {

}
```

As you can see, we did not use `angular.module("myApp", [])` but instead `angular.module("myApp")`. Now that we have our Angular app and controller, let's link the Angular CDN, our app, and our controller to `index.html` under `<!-- your scripts here -->`.

```html
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.6/angular.min.js"></script>
<script src="js/app.js"></script>
<script src="js/friendCtrl.js"></script>
```

Now that our `index.html` has access to Angular, our app, and our controller, we can edit the HTML to use our app and controller. On the opening `html` tag let's add the `ng-app` attribute and set it equal to the name of our app ( `myApp` ). And on the opening `body` tag let's add the `ng-controller` attribute and set it equal to the name of our controller ( `friendCtrl` ). 

```html
<html ng-app="myApp">
<body ng-controller="friendCtrl">
```

</details>

### Solution

<details>

<summary> <code> index.html </code> </summary>

```html
<!DOCTYPE html>
<html ng-app="myApp">
  <head>
    <title>Angular Friends</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css">
    <link rel="stylesheet" type="text/css" href="styles.css">
  </head>

  <body ng-controller="friendCtrl">
    <h1>The <strong>facebook</strong> Friend Machine</h1>

    <div class="friends">
      <form class="form-inline searchForm" role="form">
        <div class="form-group">
          <input class="form-control" placeholder="Search Anything About Your Friends">

          <select class="input-medium">
            <option>Name</option>
            <option>#Friends</option>
            <option>City</option>
            <option>State</option>
            <option>Country</option>
          </select>

          <select class="input-medium">
            <option value="-">Descending</option>
            <option value="+">Ascending</option>
          </select>
        </div>
      </form>

      <ul>
        <li class='friend'>
          <img class="profile-pic" src='http://placebear.com/50/50.jpg'>
          <h3>Cali Fornia</h3>
          <div class="location">
            Location: New Port Beach, California, United States
          </div>
          <div class="status">
            Status: I hate the snow. I wish I was on the beach right now!!!
          </div>
          <div class="num-friends">
            Friends: 1,367
          </div>
        </li>
      </ul>
    </div>

    <script src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
    <!-- your scripts here -->
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.6/angular.min.js"></script>
    <script src="js/app.js"></script>
    <script src="js/friendCtrl.js"></script>
  </body>
</html>
```

</details>

<details>

<summary> <code> js/app.js </code> </summary>

```js
angular.module("myApp", []);
```

</details>

<details>

<summary> <code> js/friendCtrl.js </code> </summary>

```js
angular.module("myApp").controller("friendCtrl", function( $scope ) {
  
});
```

</details>

## Step 2

### Summary

In this step, we'll add mock friend data to scope in `js/friendCtrl.js` and the display it in the HTML.

### Instructions

* Open `mock-data.json` and copy all the contents inside the file.
* Open `js/friendCtrl.js`.
* Add a `scope` variable called `friends` that equals what you copied from `mock-data.json`.
* Open `index.html` and locate the `ul` element.
* Underneath the only `li` element, add a new `li` element that uses `ng-repeat`.
  * Each friend object has the following properties: 
    * `name` - string
    * `pic-square` - string
    * `location` - object
      * `city` - string
      * `state` - string
      * `country` - string
    * `status` - string || null
    * `friend_count` - number
  * Follow the format of hard-coded `li` element.

<details>

<summary> Detailed Instructions </summary>

<br />

Let's begin by opening `js/friendCtrl.js` and adding a new `$scope` variable called `friends` that equals the array inside of `mock-data.json`.

```js
angular.module("myApp").controller("friendCtrl", function( $scope ) {
  $scope.friends = // array from mock-data.json
}
```

Now that our mock data is on `$scope` we can access it in our `HTML`. Using the `ng-repeat` attribute we can create a new `li` element that will loop through `$scope.friends`. We'll want our `li` element to follow the same format as the one provided. If you're not sure what properties are on each `friend` object, you can add a `console.log` in `js/friendCtrl.js` to log the value of `$scope.friends`. You should end up with an `li` element that looks like:

```html
<li class="friend" ng-repeat="friend in friends">
  <img class="profile-pic" ng-src="{{friend.pic_square}}" />
  <h3>{{ friend.name }}</h3>
  <div class="location">
    Location: {{ friend.location.city }}, {{ friend.location.state }}, {{ friend.location.country }}
  </div>
  <div class="status">
    Status: {{ friend.status }}
  </div>
  <div class="num-friends">
    Friends: {{ friend.friend_count }}
  </div>
</li>
```

</details>

### Solution

<details>

<summary> <code> index.html </code> </summary>

```html
<!DOCTYPE html>
<html ng-app="myApp">
  <head>
    <title>Angular Friends</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css">
    <link rel="stylesheet" type="text/css" href="styles.css">
  </head>

  <body ng-controller="friendCtrl">
    <h1>The <strong>facebook</strong> Friend Machine</h1>

    <div class="friends">
      <form class="form-inline searchForm" role="form">
        <div class="form-group">
          <input class="form-control" placeholder="Search Anything About Your Friends">

          <select class="input-medium">
            <option>Name</option>
            <option>#Friends</option>
            <option>City</option>
            <option>State</option>
            <option>Country</option>
          </select>

          <select class="input-medium">
            <option value="-">Descending</option>
            <option value="+">Ascending</option>
          </select>
        </div>
      </form>

      <ul>
        <li class='friend'>
          <img class="profile-pic" src='http://placebear.com/50/50.jpg'>
          <h3>Cali Fornia</h3>
          <div class="location">
            Location: New Port Beach, California, United States
          </div>
          <div class="status">
            Status: I hate the snow. I wish I was on the beach right now!!!
          </div>
          <div class="num-friends">
            Friends: 1,367
          </div>
        </li>

        <li class="friend" ng-repeat="friend in friends">
          <img class="profile-pic" ng-src="{{friend.pic_square}}" />
          <h3>{{ friend.name }}</h3>
          <div class="location">
            Location: {{ friend.location.city }}, {{ friend.location.state }}, {{ friend.location.country }}
          </div>
          <div class="status">
            Status: {{ friend.status }}
          </div>
          <div class="num-friends">
            Friends: {{ friend.friend_count }}
          </div>
        </li>
      </ul>
    </div>

    <script src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
    <!-- your scripts here -->
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.6/angular.min.js"></script>
    <script src="js/app.js"></script>
    <script src="js/friendCtrl.js"></script>
  </body>
</html>
```

</details>

<details>

<summary> <code> js/friendCtrl.js </code> </summary>

```js
angular.module("myApp").controller("friendCtrl", function( $scope ) {
  $scope.friends = // array from mock-data.json 
});
```

</details>

<br />

<img src="https://github.com/devmountain/angular-1-afternoon/blob/solution/readme-assets/1.png" />

## Step 3

### Summary

In this step, we will add a filter to our `ng-repeat`.

### Instructions

* Open `js/friendCtrl.js`.
* Add a new `scope` variable called `searchTerm` and default it to an empty string.
* Open `index.html`.
* Update the input with the class of `.form-control` to use an `ng-model` of `searchTerm`.
* Update the `li` element with the `ng-repeat` to filter by `searchTerm`.

<details>

<summary> Detailed Instructions </summary>

<br />

Let's begin by opening `js/friendCtrl.js` and adding a new `$scope` variable called `searchTerm` that equals `""`. We'll use this variable as the `ng-model` for the `input` element in our HTML. The `ng-model` will then capture what we type in the `input` element.

```js
angular.module("myApp").controller("friendCtrl", function( $scope ) {
  $scope.friends = // array from mock-data.json 

  $scope.searchTerm = "";
});
``` 

Open `index.html` and locate the `input` element with the class of `.form-control`. Add a `ng-model` attribute to it that equals `searchTerm`. Now that the `input` element is hooked up to `searchTerm` we can modify our `ng-repeat` attribute to include a filter based on the value of `searchTerm`. To add a filter to `ng-repeat` all you have to do is include a `|` and then `filter:scopeVariable`.

```html
<input class="form-control" placeholder="Search Anything About Your Friends" ng-model="searchTerm">
<li class="friend" ng-repeat="friend in friends | filter:searchTerm">
```

You can now test filtering your friends using the input field.

</details>

### Solution

<details>

<summary> <code> index.html </code> </summary>

```html
<!DOCTYPE html>
<html ng-app="myApp">
  <head>
    <title>Angular Friends</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css">
    <link rel="stylesheet" type="text/css" href="styles.css">
  </head>

  <body ng-controller="friendCtrl">
    <h1>The <strong>facebook</strong> Friend Machine</h1>

    <div class="friends">
      <form class="form-inline searchForm" role="form">
        <div class="form-group">
          <input class="form-control" placeholder="Search Anything About Your Friends" ng-model="searchTerm">

          <select class="input-medium">
            <option>Name</option>
            <option>#Friends</option>
            <option>City</option>
            <option>State</option>
            <option>Country</option>
          </select>

          <select class="input-medium">
            <option value="-">Descending</option>
            <option value="+">Ascending</option>
          </select>
        </div>
      </form>

      <ul>
        <li class='friend'>
          <img class="profile-pic" src='http://placebear.com/50/50.jpg'>
          <h3>Cali Fornia</h3>
          <div class="location">
            Location: New Port Beach, California, United States
          </div>
          <div class="status">
            Status: I hate the snow. I wish I was on the beach right now!!!
          </div>
          <div class="num-friends">
            Friends: 1,367
          </div>
        </li>

        <li class="friend" ng-repeat="friend in friends | filter:searchTerm">
          <img class="profile-pic" ng-src="{{friend.pic_square}}" />
          <h3>{{ friend.name }}</h3>
          <div class="location">
            Location: {{ friend.location.city }}, {{ friend.location.state }}, {{ friend.location.country }}
          </div>
          <div class="status">
            Status: {{ friend.status }}
          </div>
          <div class="num-friends">
            Friends: {{ friend.friend_count }}
          </div>
        </li>
      </ul>
    </div>

    <script src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
    <!-- your scripts here -->
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.6/angular.min.js"></script>
    <script src="js/app.js"></script>
    <script src="js/friendCtrl.js"></script>
  </body>
</html>
```

</details>

<details>

<summary> <code> js/friendCtrl.js </code> </summary>

```js 
angular.module("myApp").controller("friendCtrl", function( $scope ) {
  $scope.friends = // array from mock-data.json

  $scope.searchTerm = "";
});
```

</details>

<br />

<img src="https://github.com/devmountain/angular-1-afternoon/blob/solution/readme-assets/1g.gif" />

## Step 4

### Summary

In this step, we'll refactor the current filter to be more specific. Instead of a filter that will search the entire friend object, we will narrow it down to `name` and `state`.

### Instructions

* Open `js/friendCtrl.js`.
* Remove `searchTerm` from `scope`.
* Create a new `scope` variable called `filters` that equals an object with the following properties:
  * `name` - This should default to an empty string.
  * `state` - This should default to an empty string.
* Open `index.html`.
* Delete the original `input` and replace it with the following HTML:
  * <details>
  
    <summary> <code> input HTML </code> </summary>
    
    ```html
    <input class="form-control" placeholder="Search Name">
    <input class="form-control" placeholder="Search State">
    ```
    
    </details>
* Modify the new `input` elements to use the correct `ng-model`.
  * Hint: `$scope.filters.name` and `$scope.filters.state`.
* Modify the filter in the `ng-repeat` to specifically filter by `name` and `state`.
  * Hint: You can filter specifically by using object-like syntax.
    * <details>
    
      <summary> <code> Hint </code> </summary>
      
      ```js
      filter:{ property: scopeVariable, property: { property: scopeVariable } }
      ```
      
      </details>

<details>

<summary> Detailed Instructions </summary>

<br />

Let's begin by opening `js/friendCtrl.js` and removing `searchTerm` from `$scope`. Instead of just filtering through every property of a `friend` object, let's make an object that will contain specific filters. Let's call our new variable `$scope.filters` and add `name` and `state` as properties on it.

```js
angular.module("myApp").controller("friendCtrl", function( $scope ) {
  $scope.friends = // array from mock-data.json

  $scope.filters = {
    name: '',
    state: ''
  };
});
```

Now let's open `index.html` and apply our new `$scope` variable as a `ng-model`. Let's get rid of the `input` that's already there and replace it with two inputs.

```html
<input class="form-control" placeholder="Search Name">
<input class="form-control" placeholder="Search State">
```

We can then apply our `ng-model` to these inputs using `dot` notation. For the `input` element with the placeholder of `Search Name` let's apply `filters.name` as its `ng-model`. And let's apply `filters.state` as the other `input` element's `ng-model`.

```html
<input class="form-control" placeholder="Search Name" ng-model="filters.name">
<input class="form-control" placeholder="Search State" ng-model="filters.state">
```

We can then modify the `ng-repeat` filter to use our new `ng-models`. In Angular, when you want to use multiple filters we use an object-like syntax rather than `filter:scopeVariable`. So if we wanted to filter by name, we would do:

```html
<li class="friend" ng-repeat="friend in friends | filter:{ name: filters.name }">
```

The tricky part here is adding a filter for `state` because `state` is a property on a nested object. Luckily Angular allows us to filter by nested properties as long as we provided the parent object. This would look like:

```html
<li class="friend" ng-repeat="friend in friends | filter:{ name: filters.name, location: { state: filters.state } }">
```

Now you can test filtering specifically by a friend's name or state.

</details>

### Solution

<details>

<summary> <code> index.html </code> </summary>

```html
<!DOCTYPE html>
<html ng-app="myApp">
  <head>
    <title>Angular Friends</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css">
    <link rel="stylesheet" type="text/css" href="styles.css">
  </head>

  <body ng-controller="friendCtrl">
    <h1>The <strong>facebook</strong> Friend Machine</h1>

    <div class="friends">
      <form class="form-inline searchForm" role="form">
        <div class="form-group">
          <input class="form-control" placeholder="Search Name" ng-model="filters.name">
          <input class="form-control" placeholder="Search State" ng-model="filters.state">

          <select class="input-medium">
            <option>Name</option>
            <option>#Friends</option>
            <option>City</option>
            <option>State</option>
            <option>Country</option>
          </select>

          <select class="input-medium">
            <option value="-">Descending</option>
            <option value="+">Ascending</option>
          </select>
        </div>
      </form>

      <ul>
        <li class='friend'>
          <img class="profile-pic" src='http://placebear.com/50/50.jpg'>
          <h3>Cali Fornia</h3>
          <div class="location">
            Location: New Port Beach, California, United States
          </div>
          <div class="status">
            Status: I hate the snow. I wish I was on the beach right now!!!
          </div>
          <div class="num-friends">
            Friends: 1,367
          </div>
        </li>

        <li class="friend" ng-repeat="friend in friends | filter:{ name: filters.name, location: { state: filters.state } }">
          <img class="profile-pic" ng-src="{{friend.pic_square}}" />
          <h3>{{ friend.name }}</h3>
          <div class="location">
            Location: {{ friend.location.city }}, {{ friend.location.state }}, {{ friend.location.country }}
          </div>
          <div class="status">
            Status: {{ friend.status }}
          </div>
          <div class="num-friends">
            Friends: {{ friend.friend_count }}
          </div>
        </li>
      </ul>
    </div>

    <script src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
    <!-- your scripts here -->
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.6/angular.min.js"></script>
    <script src="js/app.js"></script>
    <script src="js/friendCtrl.js"></script>
  </body>
</html>
```

</details>

<details>

<summary> <code> js/friendCtrl.js </code> </summary>

```js
angular.module("myApp").controller("friendCtrl", function( $scope ) {
  $scope.friends = // array from mock-data.json

  $scope.filters = {
    name: '',
    state: ''
  };
});
```

</details>

<br />

<img src="https://github.com/devmountain/angular-1-afternoon/blob/solution/readme-assets/2g.gif" />

## Step 5

### Summary

In this step, we'll add the option to sort our friends by their properties in ascending and descending order.

### Instructions

* Open `js/friendCtrl.js`.
* Add a new `scope` property called `sorts` that equals an object with the following properties:
  * `property` - This should default to `"name"`.
  * `direction` - This should default to `"+"`.
* Open `index.html`.
* Assign the correct `ng-model` to the two `select` elements.
* Add a `value` attribute to each `option` element in the first `select` element.
  * This should equal the corresponding `property` on the `friend` object.
* Add an `orderBy` to the `ng-repeat` to order by `property` and `direction`.

<details>

<summary> Detailed Instructions </summary>

<br />

Let's being by opening `js/friendCtrl.js` and adding a new `$scope` variable called `sorts`. This will be an object to hold the `ng-model` values for sorting. We'll need two properies on this object: `property` - we'll use this to determine which property to sort by and `direction` - we'll use this to determine whether to display in ascending or decsending order.

```js
angular.module("myApp").controller("friendCtrl", function( $scope ) {
  $scope.friends = // array from mock-data.json

  $scope.filters = {
    name: '',
    state: ''
  };

  $scope.sorts = {
    property: 'name',
    direction: '+'
  };
});
```

We can then assign `property` and `direction` as `ng-models` to the the `select` elements in `index.html`

```html
<select class="input-medium" ng-model="sorts.property">
<select class="input-medium" ng-model="sorts.direction">
```

Before our `ng-model` will work with our first `select` element, we'll need to assign a `value` attribute to each `option` element. Otherwise our `ng-model` will never get updated with a value. Since this `ng-model` is looking for a friend `property` the value of each option must be spelt exactly the same as it is for each `friend` object. You can view what the property names are on a friend object by adding `console.log( $scope.friends )` in `js/friendCtrl.js`. You should end up with:

```html
<select class="input-medium" ng-model="sorts.property">
  <option value="name">Name</option>
  <option value="friend_count">#Friends</option>
  <option value="location.city">City</option>
  <option value="location.state">State</option>
  <option value="location.country">Country</option>
</select>
``` 

Now that our `ng-models` are ready to be used, all that's left is to add another `|` and `orderBy` to our `ng-repeat`. `orderBy` wokrs by using `+` for ascending and `-` for decsending. That's why the second `select` element uses `+` and `-` as its option values. The `+` or `-` needs to be immediately followed by a property to order by. So for example, ascending order by name would look like: `+name`. We can make this dynamic by using our `$scope.sorts` variable. 

```html
<li class="friend" ng-repeat="friend in friends | filter:{ name: filters.name, location: { state: filters.state } } | orderBy: sorts.direction + sorts.property">
``` 

You can now test ordering your friends by different properties.

</details>

### Solution

<details>

<summary> <code> index.html </code> </summary>

```html
<!DOCTYPE html>
<html ng-app="myApp">
  <head>
    <title>Angular Friends</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap-theme.min.css">
    <link rel="stylesheet" type="text/css" href="styles.css">
  </head>

  <body ng-controller="friendCtrl">
    <h1>The <strong>facebook</strong> Friend Machine</h1>

    <div class="friends">
      <form class="form-inline searchForm" role="form">
        <div class="form-group">
          <input class="form-control" placeholder="Search Name" ng-model="filters.name">
          <input class="form-control" placeholder="Search State" ng-model="filters.state">

          <select class="input-medium" ng-model="sorts.property">
            <option value="name">Name</option>
            <option value="friend_count">#Friends</option>
            <option value="location.city">City</option>
            <option value="location.state">State</option>
            <option value="location.country">Country</option>
          </select>

          <select class="input-medium" ng-model="sorts.direction">
            <option value="-">Descending</option>
            <option value="+">Ascending</option>
          </select>
        </div>
      </form>

      <ul>
        <li class='friend'>
          <img class="profile-pic" src='http://placebear.com/50/50.jpg'>
          <h3>Cali Fornia</h3>
          <div class="location">
            Location: New Port Beach, California, United States
          </div>
          <div class="status">
            Status: I hate the snow. I wish I was on the beach right now!!!
          </div>
          <div class="num-friends">
            Friends: 1,367
          </div>
        </li>

        <li class="friend" ng-repeat="friend in friends | filter:{ name: filters.name, location: { state: filters.state } } | orderBy: sorts.direction + sorts.property">
          <img class="profile-pic" ng-src="{{friend.pic_square}}" />
          <h3>{{ friend.name }}</h3>
          <div class="location">
            Location: {{ friend.location.city }}, {{ friend.location.state }}, {{ friend.location.country }}
          </div>
          <div class="status">
            Status: {{ friend.status }}
          </div>
          <div class="num-friends">
            Friends: {{ friend.friend_count }}
          </div>
        </li>
      </ul>
    </div>

    <script src="https://code.jquery.com/jquery-3.1.1.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
    <!-- your scripts here -->
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.6/angular.min.js"></script>
    <script src="js/app.js"></script>
    <script src="js/friendCtrl.js"></script>
  </body>
</html>
```

</details>

<details>

<summary> <code> js/friendCtrl.js </code> </summary>

```js
angular.module("myApp").controller("friendCtrl", function( $scope ) {
  $scope.friends = // array from mock-data.json

  $scope.filters = {
    name: '',
    state: ''
  };

  $scope.sorts = {
    property: 'name',
    direction: '+'
  };
});
```

</details>

<br />

<img src="https://github.com/devmountain/angular-1-afternoon/blob/solution/readme-assets/3g.gif" />

## Black Diamond

Create the filter using `ng-options` instead.

## Contributions

If you see a problem or a typo, please fork, make the necessary changes, and create a pull request so we can review your changes and merge them into the master repo and branch.

## Copyright

© DevMountain LLC, 2017. Unauthorized use and/or duplication of this material without express and written permission from DevMountain, LLC is strictly prohibited. Excerpts and links may be used, provided that full and clear credit is given to DevMountain with appropriate and specific direction to the original content.

<p align="center">
<img src="https://devmounta.in/img/logowhiteblue.png" width="250">
</p>
