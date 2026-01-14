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
