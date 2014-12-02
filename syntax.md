# test-md Syntax (Convention) Specification

The **test-md** sytax is not really a new syntax and not a syntax at all, but a convention above already existing and popular markdown syntax.

## The model

**test-md** uses plain text files to define _Test Cases_. One file can contain multiple _Test cases_ and _Test suites_.
_Test Suite_ is just a logical group of several _Test cases_. Files can be stored in folders, in such case folder can also be used as a _Test Suite_.

## Test Case defintion

The double hashtag ``##`` (with space before name) defines a _Test Case_.
_Test Case_ lasts till next test case or till end of file. _Test Case_ might contain test description and steps.

**test-md** runner must be able to list all _Test Cases_ in file and execute all or selected _Test Case_ in any order.

```
## Minimalistic Test Case

This is the minimal test case. It does nothing at all.
```

## Test Case step defintion

The dash ``-`` or other bullet character, like ``*`` and ``+``, can define a _Test Case_ step. Steps can be hierarchical: use ``tab`` character do define a next level.
There are two types of steps: ***action*** step and ***validation*** step. ***Action*** step represents an action, user should take, where ***validation*** step is a checkpoint, where user must state if step passed or failed. To define a ***validation*** step it should start with magnifier emoji :mag:(``:mag:``) tag.

To execute _Test Case_, **test-md** runner must execute all steps one by one. For ***action*** step, user will be able to mark it as **Done**, skip step or report an unexpected **Error** with option to provide additional Error details. For ***validation*** step, user can mark it as **Passed** or **Failed** with option to provide additional details about the failure.

```
## Test Case with Steps

This test contains multiple steps. Any bullet or number list considered as steps list. Steps can be defined as hierarchical list too.

- This is the first step
- And this is the second step
  - This is a sub-step of second step
  - Additional sub-step to be completed
- :mag: Now it's time to validate something
- And the final step
```

## Special Tags

### Hashtag

Typing an ``#`` symbol, followed by a any word (without spaces), will specify a hashtag. Hashtag can be used simplify search and classification of _Test Cases_.

### Username

Typing an ``@`` symbol, followed by a username, will specify a person. The context, in which this tag is used, defines a meaning for the use.

### Parameter

Typing an ``$`` symbol, followed by a any word (without spaces), can be used to specify a parameter. Parameter can be substitute by some value, during _Test Case_ execution.

## Test Case Parameters

Parameter can be embedded into _Test Case_ description and steps. The parameter scope is defined by _Test Case_, i.e. it's vissible only within same _Test Case_ where it's defined.

To specify list of possible values, we recommend to use tables embedded into _Test Case_, where each column represents a parameter and row is used to specify iterations and parameter values that are used in each iteration.

**test-md** runner could select one of the following options to execute parametrized _Test Case_.

The first option is to create a new _Test Case_ result for each iteration. In such case, the result name must also include an additional signature, composed from mixture of parameter names and iteration number.

For example:
``Parametrized Test Case User1-Pswd1 - Run (2014-11-04T10:15:16Z)``

Where parameter values used in this iteration can be specified in quote block following description, like this:

```
> User1: admin
> Pswd1: qwerty
```

---

## Test Case Result

For any _Test Suite_ or _Test Case_ execution, **test-md** runner must report an execution result. There are two files that every **test-md** framework should produce.

The first file is a generic summary of _Test Suite_ execution in [xUnit](http://windyroad.com.au/dl/Open%20Source/JUnit.xsd) XML format. The xUnit format is widely supported and popular format for reporting test results. Many CI, build and management tools are able to parse and present test results based on this format. That's why we recommend to produce at least one xUnit file for every _Test Suite_ run.

**test-md** runner should also produce a more detailed result file, that contains execution details for every _Test Case_, that had been executed. This detailed result file is also based on Markdown syntax and follows convention defined bellow.

### Detailed Test Result Convention

The double hashtag ``##`` (with space before name) defines a _Test Case Result_, which should have same name as a _Test Case_, following by dash ``-`` character, "Run" word and [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) timestamp, that specifies execution time of this _Test Case_.

Description is an optional, it can be either copy of _Test Case_ description or text, provided by user, during _Test Case_ execution.

It's also possible to report _Test Case_ performance and user, who did the actual run. The performance time should de reported in quote ``<`` after description. User can also be reported in same or additional quote with user tag, like this ``@alexei``

#### Steps

The dash ``-`` or other bullet character, like ``*`` and ``+``, defines an executed _Test Case_ step. Step text is a copy of _Test Case_ text, but **test-md** runner can allow user to modify this text.

To specify _Test Case_ step status, we recommend to use special emoji characters (Why emoji? - Language independent, parseable and nicely presented).

Special emoji characters meaning:
- :+1: (``:+1:``) - validation success
- :-1: (``:-1:``) - validation failure
- :x: (``:x:``) - unexpected error

If step does not start with special emoji character, it's either **Done** or **Skipped**. Use two surrounding tildes ``~~`` to mark skipped step, like this ``- ~~Skipped step~~``

#### Detailed Test Case Result example:

```
## Plain Test Case - Run (2014-11-04T10:15:16Z)

This is how Test Set run will look like. Title contains an original Test Case name, following dash and 'Run' word and also a timestamp in ISO 8601 format. Quote under description contains duration according to above format
> PT10M45S
> @alexei

- This is executed step
- :mag: Verify that everything is OK
  > :+1: The validation passed
- ~~Non executed step~~
- Doing this step, produces unexpected Error
  > :x: Error - everything crashed! Help!
- :mag: Verify something that always fail
  > :-1: Fail - Hmm... the validation fails indeed!
```
