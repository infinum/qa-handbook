> “It’s hardware that makes a machine fast.  It’s software that makes a fast machine slow.” — Craig Bruce


There are multiple ways to set up a Jenkins job. 
Jenkins is very customizable but the configuration will also depend on your project - how the project is set up, which plugins you want to use, which framework you are using, and so on.

Maybe the team is already using Jenkins and it is configured to match the current way of work. In that case you could probably reuse the current configuration, with minor tweaks.

There are quite a few things to learn about Jenkins. This is just a short primer on creating a new job with a few examples.

For more information on Jenkins, check the [official documentation](https://www.jenkins.io/doc/book/getting-started/).

## Prerequisites

Jenkins should be installed and set up (plugins installed, connected to a VCS, etc.) on your machine.

You need an Admin account to manage Jenkins configuration.


## Creating a job

1. Log into Jenkins
2. Open Dashboard
3. Click _New Item_ in the left-hand side menu
4. Enter the job name
- **NOTE**: Avoid using spaces since it may cause issues
- You might want to include the name of the VCS branch being used in the name of the job to easily distinguish it from other jobs

5.Select the _Freestyle project_ option
- If you already have a job created, and you want to reuse its configuration, you can create a new item from an existing one
- In the _Copy from field_ type in the name of the branch from which you want to copy the configuration

6. Click _OK_
- Configuration page will open

7. In the _Description_ text field type in the jobs description
- The description will be shown under the job name on the job details page

8. In the _Source Code Management_ section, select VCS you want to use (e.g. Git)
9. In the _Repository URL_ enter the link to your GitHub repository 
10. In the _Branches to build_ enter the branch you want to use when running the job (e.g. _*/master_)
11. In the _Build Triggers_ section select the option that will trigger the job 
12. In the _Schedule_ text field type in the cron syntax to specify when to run the job
- For example: `H 22 * * 1,3,5`
- This will run the job on Monday, Wednesday and Friday starting at 22 PM 

13. In the _Build Environment_ section select the Abort the build if it’s stuck
- This is an important step since if the build gets stuck it might go on for days if not handled properly

14.In the _Time-out strategy_ select _Absolute_
- In the _Timeout minutes_, enter after how many minutes you want to abort the job
- NOTE: This is just one of the approaches, and not the best one since the timeout is hardcoded. If the build normally takes longer than the specified time, the Jenkins will abort it

15. In the _Build_ section click the _Add build step_ button and select _Execute a shell_ option
16. In the Command text field type in the commands to run when the job starts
- For example, you can specify the script that should be run and the command to start the tests

```
./scripts/start_appium_server.sh
python3 -m pytest
```

17. In the Post-build Actions section select an action to do after the job is done
- You might want to archive the artifacts such as logs, zip or jar files
- You could also send an email notification to a specified email

18. Apply and save the changes


## Multibranch pipeline

In a Multibranch Pipeline project, Jenkins automatically discovers, manages and executes Pipelines for branches that contain a `Jenkinsfile` in source control.
This way, you can have different `Jenkinsfile` for each branch of the same project

Prerequisites:
- `Jenkinsfile` should be added in the root of your project

1. Open Jenkins
2. Click _New Item_ in the left-hand side menu
3. Enter a name for your pipeline / job
- **NOTE**: Avoid using spaces since it may cause issues
4. Select _Multibranch Pipeline_ option 
5. Click _OK_
- A configuration page will open
6. In the _Description_ text field type in the jobs description
- The description will be shown under the job name on the job details page
7. In the _Branch Sources_ section, select VCS you want to use (e.g. Git)
8. In the _Project Repository_ enter the link to your GitHub repository 
9. Save the project
- Jenkins automatically scans the specified repository and creates items for each branch in the repository that contains a Jenkinsfile
- In case the scan does not start automatically, click the _Scan Organization Folder Now_ / _Scan Multibranch Pipeline Now_ in the left-hand side menu

![jenkins_scan_multibranch_pipeline.png](/img/jenkins_scan_multibranch_pipeline.png)

For more information on Jenkins Pipeline, check the [official documentation](https://www.jenkins.io/doc/book/pipeline/).


## How to start a job manually

1. Open Jenkins
2. Open a job
3. Click Build now in the left-hand side menu

![jenkins_build_now.png](/img/jenkins_build_now.png)

### Check console log

1. Open Jenkins
2. Open a job
3. Open a build details by clicking the build number
4. Click Console Output in the left-hand side menu

![jenkins_console_output.png](/img/jenkins_console_output.png)


## Additional resources
[Jenkins tutorial](https://www.youtube.com/watch?v=89yWXXIOisk&list=PLhW3qG5bs-L_ZCOA4zNPSoGbnVQ-rp_dG&ab_channel=AutomationStepbyStep)


---

![dilbert_automation_jenkins_jobs.png](/img/dilbert_automation_jenkins_jobs.png)
