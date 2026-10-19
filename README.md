02_05 Solution: Connect Jenkins to Github
In this challenge you’ll connect a GitHub repository and a Jenkins project to implement continuous integration (CI). The goal is to configure GitHub to send webhooks to Jenkins so the job is triggered when a change is pushed to the repo.

Challenge Tasks
Create a new GitHub repo and add the exercise files for this lesson.
Create a new pipeline project that pulls the code from the repo and uses the Jenkinsfile for the project definition.
Configure the repository and the pipeline project to allow pushes to the repo to trigger the pipeline.
This challenge should take 15–20 minutes to complete.

Prerequisites
To connect Jenkins and GitHub, you need to have the following in place:

A Jenkins server that is publicly accessible on the internet. Follow the steps in the exercise files document “Deploy a Jenkins Server” for details on setting up a Jenkins server.
A GitHub account
Instructions
Create a new, public repo on GitHub and include a README.md file during the creation process.
Upload the exercise files for this challenge.
Select the Code button.
Select HTTPS.
Select the stacked squares icon to copy the repo URL to the clipboard.
Create a new pipeline project in your Jenkins server.
Select New Item and enter item name (use the same name as your repo if possible)
Select Pipeline project
Under Build Triggers, select the checkbox next to GitHub hook trigger for GITScm polling.
Under Pipeline, select Pipeline script from SCM.
Under SCM, select Git.
Under Repository URL, paste in the repo URL.
Under Branch Specifier (blank for 'any'), change master to main.
Select Save → Build Now. NOTE: The project must run at least one successful build before connecting to GitHub. This allows Jenkins to read the configuration from the repo.
Copy the URL of your Jenkins server.
Go back to the GitHub repo and configure the settings to create a webhook for the project you just created.
Select Settings → Webhooks → Add webhook.
Under Payload URL, paste in the URL for your Jenkins server.
Immediately after the Jenkins server URL, add /github-webhook/. NOTE: Please be sure to include the trailing slash on github-webhook/. The field should be in a format similar to http://your-jenkins-server.com/github-webhook/.
Under Content type, select application/json.
Select Add webhook. NOTE: GitHub will ping the Jenkins server and indicate a successful connection with a green checkmark next to the webhook name. If your webhook does not indicate that it connected successfully, select Edit and confirm your settings again. If needed, delete the webhook and start over.
Select the <>Code tab.
Edit the file algorithm.sh. Update the contents of the file as directed by the comments.
Select Commit changes and commit the changes directly to the main branch.
Go to the Jenkins server and observe the job being triggered by the change you just made in GitHub. NOTE: If your job is not triggered, review the configuration for the Jenkins job and the GitHub repo, making any adjustments as needed. If needed, start again with a new job in Jenkins or with a new webhook in GitHub.
