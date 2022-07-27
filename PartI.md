![Protractor](./images/protractorLogo.png) 

# PROTRACTOR PART I
-------------

# **Index**
-------------


- [Protractor](#protractor)
  - [What is Protractor?](#what-is-protractor)
  - [What we will learn in this course?](#what-we-will-learn-in-this-course)
    - [Why we use protractor](#why-we-use-protractor)
    - [What are the prerequisite of protractor?](#what-are-the-prerequisite-of-protractor)
    - [Setting Up Protractor](#setting-up-protractor)
      - [Installing Protractor](#installing-protractor)
    - [Different frameworks in protractor](#different-frameworks-in-protractor)
      - [Using Jasmine](#using-jasmine)
      - [Using Mocha](#using-mocha)
      - [Using Cucumber](#using-cucumber)
      - [Using Serenity/JS](#using-serenityjs)
      - [Using a Custom framework](#using-a-custom-framework)
    - [What are different assertion and locators used in protractor?](#what-are-different-assertion-and-locators-used-in-protractor)
      - [Locators](#locators)
      - [Assertions](#assertions)
    - [What are the advantages and disadvantages of protractor?](#what-are-the-advantages-and-disadvantages-of-protractor)
      - [Advantages](#advantages)
      - [Disadvantages](#disadvantages)

## What is Protractor?
-------------

Protractor is an end-to-end test framework for Angular and AngularJS applications. 
 Protractor runs tests against your application running in a real browser, interacting with it as a user would.

It was built by a team in Google on the top of WebDriver.
We can see it as a replacement for the existing AngularJS E2E testing framework called “Angular Scenario Runner”.


## What we will learn in this course?
-------------

- Why we use Protractor?
- What are the prerequisite of protractor?
- Setting Up Protractor
- Different frameworks in protractor
- What are different assertion and locators used in protractor?
- What are the advantages and disadvantages of protractor?


### Why we use protractor?
-------------

Protractor framework is used for end-to-end testing for Angular and Angular.js application.
We can write protractor script using javaScript or typeScript.

Protractor runs on top of the selenium webdriver. 
Hence all the capabilities of webdriver are supported in protractor.

It has extra locators compared to selenium webdriver those are model,repeater, binding etc.

### What are the prerequisite of protractor?
-------------

We must have basic knowledge about [javaScript](https://javascript.info/) and [Angular.js.](https://angularjs.org/) 
We should aware about basic technologies used in testing.


Protractor is a [Node.js](https://nodejs.org/en/) program. To run Protractor, will need to have Node.js installed in our system.

To check version of node which are running in system use following command through cmd or terminal. The version should be grater than v0.10.0

```shell
node --version
```
Node.js comes with the Protractor [npm](https://www.npmjs.com/) package, which we can use to install Protractor.
We can check version of npm using following command in cmd or terminal.

```shell
npm --version
```

### Setting Up Protractor:
-------------

#### Installing Protractor
-------------

Use npm to install Protractor globally (omit the -g if you’d prefer not to install globally):

```shell
npm install -g protractor
```
 Check protractor is working by using following command in cmd or terminal.

```shell
protractor --version
```
The Protractor install includes the following:

* `prtractor` command line tool.
* `webdriver-manager` command line tool.
* Protractor AIP (library).


### Different frameworks in protractor
-------------

There are five frameworks in protractor [Jasmine](https://jasmine.github.io/), [Mocha](https://mochajs.org/), [Cucumber](https://github.com/protractor-cucumber-framework/protractor-cucumber-framework), [Serenity/JS](https://serenity-js.org/) and [Custom](https://github.com/angular/protractor/blob/5.4.1/lib/frameworks/README.md#custom-frameworks) Framework you can choose any one of these.

#### Using Jasmine:
-------------

Currently, Jasmine Version 2.x is supported and the default test framework when we install Protractor.

#### Using Mocha: 
-------------

If you would like to use the Mocha test framework, you'll need to use the BDD interface and Chai assertions with [Chai As Promised](https://www.chaijs.com/plugins/chai-as-promised/).

Download dependencies with npm. Use Following Commands.

```shell
npm install -g mocha
npm install chai
npm install chai-as-promised
```

We will need to require and set up Chai inside our test files:

```javascript
var chai = require('chai');
var chaiAsPromised = require('chai-as-promised');

chai.use(chaiAsPromised);
var expect = chai.expect;
```

We can then use Chai As Promised as such:

```javascript
expect(myElement.getText()).to.eventually.equal('some text');
```

Finally, set the 'framework' property to 'mocha', either by adding `framework: 'mocha'` to the config file or by adding `--framework=mocha` to the command line.

#### Using Cucumber
-------------

If you would like to use the Cucumber test framework, download the dependencies with npm. To download use following Commands

```shell
npm install -g cucumber
npm install --save-dev protractor-cucumber-framework
```

Set the 'framework' property to custom by adding `framework: 'custom'` and `frameworkPath: 'protractor-cucumber-framework'` to the `config file(cucumberConf.js)

#### Using Serenity/JS:
-------------

Serenity/JS is an acceptance testing library which can be integrated as a drop-in replacement of Mocha or Cucumber framework adapters to provide advanced scalability and reporting capabilities.

To use it, [install](https://serenity-js.org/handbook/integration/installation.html) and configure your test framework of choice.

To install Sanity/JS use following command:

```shell
npm install serenity-js --save-dev
```

and instruct Protractor to use the Serenity/JS adapter:

```javascript
exports.config = {
  framework: 'custom',
  frameworkPath: require.resolve('serenity-js')

  // ...
};
```

#### Using a Custom Framework:
-------------

You can check these two links [Framework Adapters for Protractor](https://github.com/angular/protractor/blob/5.4.1/lib/frameworks/README.md), [Custom Framework](https://github.com/angular/protractor/blob/5.4.1/lib/frameworks/README.md#custom-frameworks)


### What are different assertion and locators used in protractor?
-------------

#### Locators:
-------------

A locator tells Protractor how to find a certain DOM element. Protractor exports locator factories on the global by object. The most common locators are:

```javascript
// Find an element using a css selector.
by.css('.myclass')

// Find an element with the given id.
by.id('myid')

// Find an element using an input name selector.
by.name('field_name')

// Find an element with a certain ng-model.
// Note that at the moment, this is only supported for AngularJS apps.
by.model('name')

// Find an element bound to the given variable.
// Note that at the moment, this is only supported for AngularJS apps.
by.binding('bindingname')
```

The locators are passed to the `element` function, as below:

```javascript
element(by.css('some-css'));
element(by.model('item.name'));
element(by.binding('item.name'));
```

For more detailed about locator you can [click on this](https://www.protractortest.org/#/locators)

#### Assertions:
-------------

You can use Jasmine default assertion if you are using Jasmine framework, or you can use chai assertions.

For chai assertion [click on this](https://www.chaijs.com/plugins/chai-as-promised/).


### What are the advantages and disadvantages of protractor?
-------------

#### Advantages:
-------------

1. Protractor runs on top of the selenium webdriver. Hence all the capabilities of webdriver are supported in protractor.
2. It has extra locators compared to selenium webdriver those are model,repeater, binding etc.
3. It has default waits which waits for angular which is not present in selenium webdriver.
4. Easy to write and manage page objects.
5. If your application is angular based then it is better to go with protractor.
6. It supports behavior driven frameworks jasmine, mocha, cucumber etc.
7. Image comparison is very easy in protractor and it works great.
8. Running automation script in multiple machine is achieved in easy way in protractor.

#### Disadvantages:
-------------

1. It supports only javascript.
2. It runs very well in chrome browser. It don’t have much support on other browsers.
3. Robot class support is not there in Protractor

