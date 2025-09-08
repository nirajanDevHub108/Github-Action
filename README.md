***Repository contains all the notes and code***

# GitHub Actions Basics

GitHub Actions is a CI/CD (Continuous Integration/Continuous Deployment) platform that allows you to automate your build, test, and deployment pipeline directly within your GitHub repository.

## Key Concepts

- **Workflows:** YAML files stored in the `.github/workflows` directory of your repository that define your automation processes.
- **Events:** Specific activities that trigger a workflow (e.g., push, pull request, issue creation).
- **Jobs:** A set of steps that execute on the same runner (virtual environment).
- **Steps:** Individual tasks that run commands or actions.
- **Actions:** Reusable units of code that can be used in workflows.
- **Runners:** Servers that run your workflows when they're triggered.

**01-building workflow**

GitHub action building blocks


workflows:

    are defined at the repository level

- Define which triggers actually start the workflow
- They are composed of one or more jobs

Jobs

- are defined at the workflow level
- Define in which execution environment they are run
- are composed of one or more steps
- Run in parallel by default

Steps

- They are defined at the job level
- Define the actual script or GitHub Action that will execute
- runs sequentially by default

**02- workflow events**

# **Events that trigger workflows**

# You can configure your workflows to run when a specific activity on GitHub happens, at a scheduled time, or when an event outside of GitHub occurs.

pull_request

Runs your workflow when activity on a pull request in the workflow's repository occurs. For example, if no activity types are specified, the workflow runs when a pull request is opened or reopened or when the head branch of the pull request is updated. For activity related to pull request reviews, pull request review comments, or pull request comments, use the [`pull_request_review`]


For example, you can run a workflow when a pull request has been opened or reopened.

```yaml
on:
  pull_request:
    types: [opened, reopened]
```

You can use the event context to further control when jobs in your workflow will run. For example, this workflow will run when a review is requested on a pull request, but the `specific_review_requested` job will only run when a review by `octo-team` is requested.

**on fork**
**on push**
and so on ....

VISIT THIS LINK for more info:
[text](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#pull_request)

# **03-worflow-Runners**
virtual servers that executes the jobs from workflow
-Github-hosted Runner

-Self-Hosted Runners

# **Note/warning*

Do not use self-hosted runners in public repositories.

- Keep the VM resources in mind, especially when running commands that rely on parallel execution, ex, parallel jest tests

# *GITHUB ACTION/Actions*

custom applications to perform complex, frequently repeated tasks 
Enables great flexibility with key-value pair
can be combined with other steps ,encapstulates with other task
we can create our own actions for public /private  use

# *Event Filters*
it specify under which conditions a specific event triggers our workflow
-push event 
something on specified branches(like ,main,sit,UAT) , branches_ignore,tags,tags_ignore,path,paths_ignore

# *Activity Types*
specify which types of certain trigger execute our workflow

-pull_request event
  -opened,synchronize,closed,assigned,labeled,edited (these are the activity of pull request)

 # *Workflow Contexts* 
 -access information about runs,variable jobs,and much more
 -Github provides multiple sources of data in diffrent context so thta we can easily provide all the necessary information to our workloads
-github :commit -SHA ,Event name,ref of branch or tag triggering the flow
-env : contains var that have been defined in a workflow,step
-inputs: contains input properties passed via the keyword with to an action, to a reusable workflow,or to trigger manually
- vars contans custom config variable at organization,repo levels
-secrets,matrix,needs ...