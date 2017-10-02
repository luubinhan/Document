---
layout: 'content'
title: 'Unit Test'
description: 'Unit Testing is a level of software testing where individual units/ components of a software are tested. The purpose is to validate that each unit of the software performs as designed.'
---

# Unit test - "Unit of code"

Usually a **function** in an *object* or *module*

Should be isolated from dependencies, no network access, no database access

Unit test using Mocha

```js
suite('My test suite name', function(){
    setup(function(){
        // do setup before tests
    }); // Setup

    teardown(function(){
        // clean up after tests
    });

    test('x should do y', function(){
        // test something
    });
});
```


# TDD: Test-Driven Development
A process for when you write and run your tests.
1. Start by writing a test
2. Run the test and any other tests.
3. Write the minimum amount of code required to make the test pass
4. Run the tests to check the new test passes
5. Opitionally refactor your code
6. Repeat from 1

You have to write your tests before writing code.

# BDD: Behavior-Driven Development