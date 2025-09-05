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

01-building workflow
GitHub action building blocks

![image.png](attachment:d9aa64da-052e-48c6-8cc7-628f388ce987:ef2be6c5-e5a3-46dc-a84e-d6f72da7659b.png)

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
