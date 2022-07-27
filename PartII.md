<img src="./images/protractorLogo.png" alt="Protractor" style="zoom:50%;" />

# PROTRACTOR PART II


### Let Start with some basic spec creation

#### What is **describe**, **spec** and **it** block

* describe - A test suite begins with a call to the global Jasmine function describe with two parameters: a string and a function. The string is a name or title for a spec suite - usually what is being tested. The function is a block of code that implements the suite.
* spec - Specs are defined by calling the global Jasmine function it, which, like describe takes a string and a function. The string is the title of the spec and the function is the spec, or test. A spec contains one or more expectations that test the state of the code. An expectation in Jasmine is an assertion that is either true or false. A spec with all true expectations is a passing spec. A spec with one or more false expectations is a failing spec.
* it - Since describe and it blocks are functions, they can contain any executable code necessary to implement the test. JavaScript scoping rules apply, so variables declared in a describe are available to any it block inside the suite.

**Example**

```javascript
describe('Protractor Demo App', function() {
  it('should have a title', function() {
    //code should be written here
  });
});
```

#### Assignment I

1. Create a project in ide include all dependencies.
2. Configure your framework in config file e.g. custom, jasmin etc.

### First script for protractor 

##### When you start writhing first script in protractor do the following thing in your project
* Add ``"protractor": "./node_modules/protractor/built/cli.js"`` in a package.json file in script section to run cli tool
* Add ``"pretest":"npm run webdriver-update && tsc"`` in a package.json file in script section. It convert your typescript test file to javascipt.
* Add ``"test": "protractor Path_of_your_javascript_file/conf.js"`` in a package.json file in script section. Using npm run test you can execute your test after adding test in script.

#### Things to be need to add in configuration file

* Add ``framework:'custom'`` //you can add any framework which you want to use e.g. jasmine, Mocha, Cucumber etc.
* Add ``specs : [  '../path of your test script']`` //Invoke test while executing framework.
* Add ``capabilities : {'browserName': 'chrome'}`` //Invoke chrome browser.

#### Example of test script

```typescript
import {browser,element,by} from "protractor"; // invoke browser, element and by from protractor

describe('Protractor Demo App', function() {
  it('should have a title', aynch ()=> {
		await browser.get('http://example.angularWebPage.com/'); // invoke browser and navigate to the website
		await element(by.id('button')).clikc() // click() function is used here
  });
});

```

#### Locators used in Protractor 

1. by.className
2. by.id
3. by.CSS
4. by.linkText
5. by.name
6. by.partialLinkText
7. by.tagName
8. by.xpath
9. by.binding
10. by.model

#### Assignment II

1. Write your first test spec use following website ['Calculator webpage'](http://juliemr.github.io/protractor-demo/)
2. Try to add each locator define above.
3. Try to write multiple test spec and execute using test script which is define in package.json
4. Try to automate login functionality of given website [Login Webpage](https://www.globalsqa.com/angularJs-protractor/registration-login-example/#/login)



### Cucumber BDD 

#### Lets Started with Cucumber BDD Framework

Cucumber is a software tool that supports behavior-driven development. 
Central to the Cucumber BDD approach is its ordinary language parser called Gherkin. 
It allows expected software behaviors to be specified in a logical language that customers can understand.

#### To Add Cucumber Framework in Project you need following dependency

```sh
npm install cucumber --save-dev
npm install protractor-cucumber-framework --save-dev
```

#### Feature in Cucumber BDD Framework

The Feature keyword's aim is to collect relevant scenarios and provide a high-level description of a software feature.

Example 
```feature
	
	Feature: Login Functionality
	
	Scenario Outline: Validate Login Functionality
	Given User navigate to webpage 
	When User enter <userId> and <password>
	Then User click on login button
	
	Example:
	| userId  | password    |
	| abcUser | xyzconnect  |
	
```

#### Assignment III

1. Create first feature file for ['Calculator webpage'](http://juliemr.github.io/protractor-demo/)

#### Step Definitions in Cucumber BDD Framework

Cucumber scenarios become automated tests with the addition of what are
called step definitions. A step definition is a block of code associated with one or
more steps by a regular expression

Example:
```javascript

import {Given,When,Then} from "cucumber"; // invoking Given, When, Then keyword from cucumber 
import {browser,element,by} from "protractor"; // invoking browser, element and by from protractor

Given('User navigate to webpage', async()=> {
    await browser.get('http://loginexample.com/');
});

When('user enter {string} and {string}', async(string, string2)=> {
    await element(by.id('userId')).sendKeys(string);
    await element(by.id('password')).sendKeys(string2);
});

Then('User click on login button', async()=> {
	await element(by.id('button')).clikc() // click() function is used here
});

```


#### Assignment IV

1. Create Step Definition for pevious assignment.


#### Assignment V

1. Create End-to-End automation testing and add all features which you add previous assignment


### References:

- [Protractor Official Documents](https://www.protractortest.org/#/).
- [Video Tutorial Course](https://www.udemy.com/course/protractor-tutorial/).
- [JavaScript Tutorials](https://www.w3schools.com/js/).
- [TypeScript Tutorials](https://www.tutorialspoint.com/typescript/index.htm).
- [Angular.JS Tutorials](https://www.w3schools.com/angular/).



