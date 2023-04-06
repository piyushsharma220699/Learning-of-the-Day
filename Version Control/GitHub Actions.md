GitHub Actions is a continuous integration and continuous delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline. You can create workflows that build and test every pull request to your repository, or deploy merged pull requests to production.

## Basic Understanding

![[Workflow-Contents.jpg]]

Basically, you do some EVENTS in your repository. An event can be anything eg: creating a pull request, commenting on an issue, creating a branch etc. Now for some events, you want some ACTION to happen. Let's say everytime you push something to your main branch, you want to mail someone reagarding this commit. So to achive this type of behaviour, you create WORKFLOWS in your github repository.

These WORKFLOWS are written in YAML syntax and are defined in the .github/workflows directory (dedicated). You can define multiple workflows, each performing a different set of actions.

YOU DO SOME EVENT ON THE REPOSITORY, THAT EVENT TRIGGERS A WORKFLOW WHICH CONSISTS OF SOME JOBS (containing series of tasks) THAT IT EXECUTES.

It somewhat looks like:
- Repository contains the .github/workflows folder.
- .github/workflows contains the workflows which will get triggered on some events defiined.
- Each workflow contains multiple jobs.
- Each job contains multiple tasks.


![[Workflow-Actions.jpg]]


Now, here's the list of all the EVENTS that can trigger a WORKFLOW : 
https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#webhook-events

Now, each of this WORKFLOW that performs an ACTION, runs on some virtual machine (Also called as RUNNER), which you specify. Runners are processes on a server that run the workflow when it’s triggered. Each runner is responsible for executing a given job. Runners are hosted on cloud but can also be self-hosted in custom environments.

Also, by default each job in a GitHub Actions workflow is executed on a separate runner, which is a virtual machine or container environment. This isolation ensures that the jobs do not interfere with each other and allows for parallel execution of multiple jobs, improving the overall workflow execution time.

Also, these jobs are executed independently and in parallel with other jobs (subject to the availability of runners ofc), however, you can define dependencies between jobs, which can impact their execution order (by defining them in the YAML file). The default limit is 20 concurrent jobs, but this can be increased by contacting GitHub support.

![[Workflow-Event-And-Runner.png]]

As the GitHub Actions [Documentation](https://docs.github.com/en/actions) states, actions are “**individual tasks** that you can combine to create jobs and customize your workflow”. On the other hand, [Workflows](https://docs.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow#about-workflows) are “**custom automated processes** that you can set up in your repository to build, test, package, release, or deploy any project on GitHub”. 

## Github Actions Marketplace

Now, the thing is that you can build your own actions too, or you can use some open-source actions too from the GitHub Marketplace. Add those to your workflow directly when they meet your needs.

Link to Actions Marketplace: https://github.com/marketplace?type=actions

## Sample GitHub Workflow

![[Starter-Workflow-Demo.png]]

- Name : Name of the Workflow
- on : The event on which the workflow will get triggered. Here's the link :: https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows#webhook-events
- jobs : This contains all the jobs of the workflow. Right now it contains only one job with the name 'build'
- 'build' is the name of the Job
- 'build' job runs-on an ubuntu-latest. 
- 'steps' provides all the steps present inside the job. Every statement running with a '-' is a new step.
- uses: It is used to reference an action that is defined in a separate repository or Docker container, and include it as a step in the workflow. When the workflow is run, the runner will download the specified version of each action and run it as a step in the job.
- 'name' is the name of the step, this will be shown in the GitHub Actions. 'run' is the command that will be run.

Here's another example : 

![[Workflow-yaml-job.png]]

## Important Links : 

1. https://towardsdatascience.com/github-actions-everything-you-need-to-know-to-get-started-537f1dffa0ed
2. https://codefresh.io/learn/github-actions/github-actions-workflows-basics-examples-and-a-quick-tutorial/
3. https://docs.github.com/en/actions

Here's a list of Actions : https://github.com/sdras/awesome-actions
