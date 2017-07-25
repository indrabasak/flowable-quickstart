[![Build Status][travis-badge]][travis-badge-url]


Flowable Quickstart
===============================
This is a quick start example of [flowable](http://www.flowable.org/). It is a Java
Business Process Management (BPM) engine forked from [Activiti](https://www.activiti.org).

The example can be found [here](http://www.flowable.org/docs/userguide/index.html#getting.started.command.line).

This is an example which creates `flowable` Process Engine using a memory-based h2 embedded database.
It loads the `holiday-request.bpmn20.xml`.

The process prompts the user name, number of holiday request, and a reason for request. 
Once the user inputs those information from command line, the process creates a task
for the manager and requests the manager approval. Once the manager approves, the
process exits.

Please note the example holiday request process doesn't have any type of
error handling.

### Build
Execute the following command from the parent directory to build the project:
```
mvn clean install
```

### Run
To run the application from the terminal,
```
java -jar target/flowable-quickstart-1.0.0-SNAPSHOT-full.jar 
```

You should notice the application starting:
```
ProcessEngine [default] Version: [6.1.1.0]
Found process definition [Holiday Request] with id [holidayRequest:1:3]
Who are you?
```

When prompted for name, enter a name. For example, `Jane Doe` and hit return.
This should prompt you for the number of holidays you are requesting.

```
Who are you?
Jane Doe
How many holidays do you want to request?
```

Enter any number, for example `7` and hit return. This should you prompt you
for a reason.

```
How many holidays do you want to request?
7
Why do you need them?
```

Enter a reason, e.g., `Vacation`, and hit return.
```
Why do you need them?
Vacation
```

This starts a process instance and  notifies the manager about a new task. Also 
prompts the manager the task number he/she wants to complete.

```
You have 1 tasks:
1) Approve or reject request
Which task would you like to complete?
```

Once you enter the task number `1`. It should show you the task description and
asks fr approval.

```
Which task would you like to complete?
1
Jane Doe wants 7 of holidays. Do you approve this?
```

Once the manager imputs `y`, the process exits.
```
Jane Doe wants 7 of holidays. Do you approve this?
y
Calling the external system for employee Jane Doe
startEvent took 2 milliseconds
approveTask took 7028 milliseconds
decision took 2 milliseconds
externalSystemCall took 2 milliseconds

Process finished with exit code 0
```

[travis-badge]: https://travis-ci.org/indrabasak/flowable-quickstart.svg?branch=master
[travis-badge-url]: https://travis-ci.org/indrabasak/flowable-quickstart/