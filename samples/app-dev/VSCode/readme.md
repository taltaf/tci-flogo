# Unit Testing


## Description

Unit testing is a technique where individual components or flows of an applications are tested in isolation. With unit testing, you can monitor the health of your application and detect errors in individual flows or Activity levels. While designing an application with multiple flows and activities, it becomes cumbersome to detect runtime errors at the flow and Activity levels. Using unit testing the errors at micro level are easily handled.

## Prerequisites

* You need go version=go1.20.12 or above, to be installed on your machine. For information about go installation on Windows, Mac, or Linux, see https://go.dev/doc/install" as a pre-req before running app locally.


## Creating Assertions

An assertion is a logical expression that evaluates to a boolean value. The expected versus actual output is compared by using an assertion expression. For the passed assertion, the expression evaluates to true.We can add one or more assertions to activity, errorhandler and flow output. You cannot create assertions for the activities that do not return output. 

1. Flow Output
Flow output is the output generated for the given flow for the given set of inputs. Flow output can have one or more assertions. To add assertions to the flow output the output must be defined. Then only you can see the assertions options in flow output. 

![Flow Output](../../../import-screenshots/VSCode/flowoutput.png)


2. Assert on Error
You can add assertions to the flow output to verify that the flow produces the correct data by comparing the actual output against predefined assertions. Assert on Error adds an assertion for the flow designed with error. To make the assetion pass without using error handler we can add flow output assertion to the flow output. 

![Assert on Error](../../../import-screenshots/VSCode/assertonerror.png)

3. Assert On Output
To compare the actual vs expected output, you can add multiple assertions on an activity, flow output, or error handler. We can use functions while adding assertions. This option is only visible for the activities having output.

![Assert on Output](../../../import-screenshots/VSCode/assertonoutput.png)

## Other Modes

1. Skip Execution
We can use skip an activity in unit testing if the activity does not have any output. 


2. Execute Default
When execute default is selected it does not affect any unit testing execution. We can also use this option to resert the configuration.

## Mocking Data
In unit testing, you can mock the data for the unit that is being tested. This is useful during unit testing so that the external dependencies are no longer a constraint to the unit under test. Using mock data the dependencies are replaced by closely controlled replacements that simulate the behavior of the real ones.

You can use the mock data for the activities that have an output. Expressions and functions are not evaluated in the values given to mock outputs, the input provided is passed as-is.

In unit testing, you can either use assertions or mock data to test the activities.

1. Mock Error
Use mock exceptions for an activity to find out whether the exception handling is being done correctly or not. This option is only visible for the activities having output. Add mock error to pass dummy error message to make the assertion pass.

![Mock Error](../../../import-screenshots/VSCode/mockerror.png)

2. Mock Outputs
You can use the mock data for the activities that have an output. Data mocks are fake data that is used to simulate real data in a controlled environment. Add mock ouput to pass dummy outputs to make the assertion pass.

![Mock Output](../../../import-screenshots/VSCode/mockoutput.png)

## Defining Flow Input
For a particular activity that has a flow input configured in the actual process, you must assign the flow input parameters before you run a test case. You can add separate test cases for each flow input.

## Import the sample

The sample app gets the zipcode of the customer for the given customer id. Added the assertions and mock for this sample app in which assert on error, assert on output, mock error and mock output.
In this if we pass the correct id in the flow input that would direct to the right url passed in invoke rest service, the the test case would pass and correct zipcode will be displayed and this we can assert using assert on output.
If we pass the id which doesn't exist in the flow input i:e that wouldn't direct to the right url passed in invoke rest service,, the the testcase would fail as it would not get the zip code of the customer and this we can assert using assert on error, dislaying the error message "Invalid path '.address.zipcode'. path not found." configured in the assertion
If the invokde rest service is down or inaccessabla and we want to mock the data and get the output, using mocking of data invoke rest will not be called, but we will still get the desired result from the data we have mocked.




1. Download the UnitTestingSample.flogo and UnitTestingSample.flogotest file.'

2. Put these files in VSCode workspace

![Unit Testing files in VSCode workspace](../../../import-screenshots/VSCode/import.png)



### Run the application

1. Click on the UnitTestingSample.flogotest

![.flogotest file](../../../import-screenshots/VSCode/Testing.png)

2. Click on the testing icon in VSCode on the left side. Expand the app name and the test suite and click on the run test button to see the test results.

![Testing icon](../../../import-screenshots/VSCode/Testing1.png)




## Outputs

After clicking on run test button a test result file will generate under test-results folder in your VScode workspace.

1. Assert on Error

![Sample Response](../../../import-screenshots/VSCode/assertonerroroutput)

2. Assert On Output

![Sample Response](../../../import-screenshots/VSCode/assertonerroroutput)

3. Mock Error

![Sample Response](../../../import-screenshots/VSCode/mockerror)

4. Mock Outputs

![Sample Response](../../../../import-screenshots/VSCode/mockoutput)
