# The Test Suite

The test suite is just a group of test cases bundled together for some reason.

---
## Minimalistic Test Case

This is the minimal test case. It does nothing at all.

---
## Test Case with Steps

This test contains multiple steps. Any bullet or number list considered as steps list. Steps can be defined hierarchical too.

- This is the first step
- Ans the second step
  - This is a sub-step of second step
  - Additional sub-step to be completed
- [?] Now it's time to validate something
- Perform additional step
- :mag: and do validation once again
- And the final step

---
## Fill Login Form

This is a reusable Test Case. It's possible to "invoke" steps of this case from other Test Case. To reuse these steps, you need to include a reference to the Test Case, replacing 'whitespace' characters with 'dash' ``-``, like this: ``[Reuse Fill Login](#Fill-Login-Form)``

- Enter $User and $Password into corresponding fields
- Press **Login** button

---
## Reuse Test Case

This test case reuse step bock defined in current file (same Test Suite)

- First step
- Second step
- Reuse step block [Fill Login](#Fill-Login-Form)

---
## Test Case with Assertion

This test case contains assertions. Assertion is a special step that describes validation and not action. To define an assertion
start you sentence with special emoji character, either :a: (``:a:`` - assertion) or :mag: (``:mag:`` - magnify glass, for inspection). During test execution **test-md** runner will allow user to specify **Passed** or **Failed** result for validation step.

- Open 'New Order' form
- Click on 'States' dropbox
- :a: Validate that values in this dropbox are sorted alphabetically
- Select 'AZ' and press 'OK' button
- :mag: Validate that new order contains 'Arizona' as a 'Target State'

---
## Test Case with Parameters and Test Data

To specify test parameter, use the ``$`` character, following by parameter name (w/o spaces). Parameter can be embedded into _Test Case_ description and steps. The parameter scope is defined by _Test Case_, i.e. it's vissible only within same _Test Case_ where it's defined.

To specify list of possible values, we recommend to use tables embedded into _Test Case_, where each column represents a paramater and row is used to specify iterations and parameter values that are used in each iteration.

| Title  | Edition | Count | Price |
|---    |---      |---    |---    |
| The Hitchhiker's Guide to the Galaxy  | Kindle | 1 | 7.70 |
| Ender's Game | Paperback | 2 | 9.74 |

- Go to [Amazon](http://www.amazon.com) bookstore
- Search for $Title book
- Select the book $Edition edition
- [?] make sure that price is equal to $Price
- Add $Count of found book into your shopping cart
- Proceed to 'Checkout' page to see your order

---
## Report Error from Test Case

Tested can report an unexpected error for any step. Each error might also contain more detailed description. For example, default CLI
Test Runner allows reporting error by pressing **e** characted during step run.

- This is first step, it can be skipped by pressing 's' character in CLI test runner
- The second step, to report an error in CLI test runner press 'e'!
- The third step should not be executed

## Shell script Test Case

This test case contains a shell script. The shell script can be defined at test case level or at step level

```
    ls -a
    echo pwd
```

- Step with code

    ```
        uname -a
        echo "done"
    ```
- Step without any code

---
## JavaScript Test Case

This test contains script written is JavaScript. If you are using Web Test Runner then browser JS engine will be used. For CLI
Test Runner, you need to install node.js

```javascript
function test() {
  console.log("notice the blank line before this function?");
}
test()
```
