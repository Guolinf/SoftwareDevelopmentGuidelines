# Example of a workflow:
```
name: LVL_CI_example

# on controls when this specific action will run.
on:
  # The event/s you want to trigger this action
  [push, pull_request]:
    # Which branch/es the action will run on
    branches: [ master ]

#job defines a sequence of tasks that will run when this workflow is triggered. 
job: 
  # A unique id for a job containing only _ or letters, this one is called build
  build:
    # Specifies which kind of machine the job is run on. 
    # It's up to you which machine to use but github hosted runners are highly encouraged.
    runs-on: ubuntu-latest
    
    #steps defines a tasks to run as part of the job, the following steps 
    steps: 
      # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
      - uses: actions/checkout@v2
      
      #--build project--
      
      ## Below are some examples of how to run code
      
      - name: example 1
      run: echo run can run scripts
      
      - name: example 2
      run: |
      echo it can also run
      echo multi-line scripts
      
      # this example uses a code from another file
      - name: example 3
        uses: ./.github/actions/my-action
      
      
      
  test: 
     runs-on: ubuntu-latest
     
     steps:
      # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
      - uses: actions/checkout@v2
      
      #--run your tests--
      
  package:
    runs-on: ubuntu-latest
     
     steps:
      # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
      - uses: actions/checkout@v2
      
      #--run your packaging steps--
  
```