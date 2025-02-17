## To Configure ssh key to ServerPc with LocalPc

### Local pc

```
ssh-keygen -t rsa -b 4096 -f ~/.ssh/github     // without passphrase
```

### Server pc

```
sudo nano ~/.ssh/authorized_keys (append) -> cat ~/.ssh/github.pub (local pc)
```

### Github Repository Settings

```
github -> Repository settings -> secrets and variables -> New Secrets
SSH_PRIVATE_KEY -> cat ~/.ssh/github
SSH_HOST -> server ip (52.136.157.119)
SSH_USER -> server user (root)
```

### Deployment

refers to the process of moving code from a development or staging environment to a production environment where it becomes accessible to users. This process can include various steps such as building, testing, configuring, and finally releasing the application to a server.

### Production

refers to the environment where the final version of the application is running, accessible to end-users. It's the live environment where real data is processed and where the application's reliability, security, and performance are critical.

### YAML (short for "YAML Ain't Markup Language")

is a human-readable data serialization format that is often used for configuration files and data exchange between languages with different data structures.

- name: is optional and acts more like a label or title for the workflow. It is primarily used for clarity and organization, helping you and others quickly identify what the workflow does when viewing the repository's Actions tab.

- on: - The event that triggers the workflow.

```
    on:
      push:
        branches:
          - main
    on:
      pull_request:
        branches:
          - main
```

- concurrency key is used to manage and limit the number of workflows that run concurrently for the same project.

```
    concurrency:
      group: main
      cancel-in-progress: true
```

- jobs: section defines one or more jobs that will run as part of your workflow. Each job runs independently in a fresh virtual environment and can consist of multiple steps.

- runs-on: key specifies the type of virtual machine or environment the job will run on. GitHub provides several environments, such as ubuntu-latest, windows-latest, macos-latest, and more.

- steps: section within a job defines the individual tasks that the job will perform. Each step runs sequentially within the job's environment.

- uses: Refers to a reusable action from the GitHub Actions Marketplace. These actions are pre-built scripts that perform common tasks.

- with: Passes input parameters to the action specified in uses.
