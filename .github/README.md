# On 

#push , pull_request : these are trigger events.

# workflow_dispatch: it will enable you to trigger the workflow in UI

# github hosted resources 2 core cpu, 7 gb ram, 14 gigabite disk

# Vm is scoped to a job

# default variable
- $RUNNER_OS

# discussion about action. action is like a release/library which we can use do to 
# certain  task that is related to particular component/platform etc

# Event Filter : example push event will be trigger under certain condition

- branches
- branch_ignore
- tags
- tags_ignore
- path 
- path_ignore 

# pull_request event have multiple activity which we can leverage

- opened
- syncronized
- closed
- assigned
- labeled
- edited

# Expression: using dynamic values/expression in your workflows

- expression can be used to reference info from multi sources within the workflow
- must be used the ${{ expression }}
- can be any combination of literal values like (string, numbers, boolean, null)
- values passed via many workflow contexts
- built in functions provided by github action
- support the use of operators such as ( >, <, !=, =, &&, || etc) 

# Inputs: inputs are runtime parameters that let you control a workflow when you manually trigger it.

# Command-line arguments for a CI/CD pipeline

| Type      | Use case        |
| --------- | --------------- |
| `string`  | Versions, names |
| `boolean` | Feature flags   |
| `choice`  | Environments    |
| `number`  | Limits, counts  |


# Variables: set and reuse non-sensitive information

- It can be define as workflow level, job level and step level as well

# multiple workflows

- we can define at organization level and repository level and environment level.
- repo variable would be override the organization variable and env variable will override the repo variable.

# organizational variable & environment variable
- In organizational variable we can define/select which repo can access that variable
- setting > security > secrets & variables> action > organizational variable

# Functions

- GitHub Actions functions are Expression language functions
- Used where	${{ }}, if:, env:, matrix:
- Comparable to	Ternary + utility helpers
- Most used	contains(), startsWith(), success(), fromJSON()

# General purpose: startWith(), endsWith(), contains(), fromJson(), toJson()

- Example: if: contains(github.ref, 'release') # It will check all the ref which contain release
- Default bolean value returns (true/false)

- startWith() : startsWith(github.ref, 'refs/heads/') # same as contains

- endWith() : endWith (github.ref, '/main'): 

- fromJson() : json to object

- toJson () : object to json

# status check function#

- success() , failure(), always(), cancelled()

- success() : All previous steps succeeded

- failure() : Any previous step failed

All previous steps succeeded	false
Job just started (no steps yet)	false
Job was cancelled	           false
Step skipped	               false

- when exit 1 would be the result the condition satisfy

- cancelled() : Workflow cancelled

- always() : Always (even on failure)

# utility functions

- hashFiles(path) : Hash file contents

if: hashFiles('**/package-lock.json') != ''

# Controling execution flow #

- Execute steps and jobs conditionally, and set dependencies between jobs

- standard execution: downstream jobs and steps executed if upstream jobs/steps runs successfully
- conditionally excution: we can add a condition as if is not been canceld then execute every step

- ex: if: ${{ !cancelled () }} 

- Non dependent execution: if we are excuting multi jobs the job are not other job. they are run separately.

- Dependent execution: "needs" key can be used which we can use to a job dependent on other job for execution.

# inputs and outputs#

- inputs provide info to customize workflow and actions
- it enable us to request specific info form workflow which will be defined and it can be used in runtime.

types:
  - string : echo "returns string value, use: name, tags, paths"
  - boolean: echo "returns boolean value, value: true or false"
  - choice: echo "dropdown control , use: provide a choice to choose"
  - environment: "env picker, use: use in env approval"
  - number: "return as number, use: count, limits"

# outputs are values we produce in one place (in a step/job/workflows) and use it next step o another job or a caller workflow.

- Outputs → discovered during execution

- The step must have an id:
- Write name=value into $GITHUB_OUTPUT
- Read it as: steps.<id>.outputs.<name>



