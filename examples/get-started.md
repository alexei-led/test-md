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
- :mag: Now it's time to validate something
- And the final step

---
## Fill Login Form

This is a reusable Test Case. It's possible to "invoke" steps of this case from other Test Case. To reuse these steps, you need to include a reference to the Test Case, skipping 'whitespace' characters, like this: ``[Reuse Fill Login](#FillLoginForm)``

- Enter $User and $Password into corresponding fields
- Press **Login** button

---
## Reuse Test Case

This test case reuse step bock defined in current file (same Test Suite)

- First step
- Second step
- Reuse step block [Fill Login](#FillLoginForm)

---
## Test Case with Assertion

This test case contains assertions. Assertion is a special step that describes validation and not action. To define an assertion
start you sentence with special emoji character :mag: ``:mag:`` . During test execution **test-md** runner will allow user to specify **Passed** or **Failed** result for validation step.

- Open 'New Order' form
- Click on 'States' dropbox
- :mag: Validate that values in this dropbox are sorted alphabetically
- Select 'AZ' and press 'OK' button
- :mag: Validate that new order contians 'Arizon' as a 'Target State'

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
