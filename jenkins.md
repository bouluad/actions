In this version, we're using an if statement to check if the jenkins-job-parameters input is empty or not. If it's empty, we trigger the Jenkins job without parameters using the /build endpoint. If it's not empty, we trigger the Jenkins job with parameters using the /buildWithParameters endpoint.

Note that we're also using the -H "Jenkins-Crumb: do-not-crumb" option in the second curl command to disable CSRF protection. If your Jenkins server has CSRF protection enabled, you may need to modify this option or include additional steps to retrieve and include the correct CSRF crumb in the request headers.

To use this updated composite action in a workflow with parameters, you would pass the parameters as a string in key=value format:

```
jobs:
  example-job:
    runs-on: ubuntu-latest
    steps:
      - name: Trigger Jenkins Job
        uses: your-username/trigger-jenkins-job@main
        with:
          jenkins-url: 'https://your-jenkins-server.com'
          jenkins-username: 'your-jenkins-username'
          jenkins-api-token: ${{ secrets.JENKINS_API_TOKEN }}
          jenkins-job-name: 'your-jenkins-job-name'
          jenkins-job-parameters: 'param1=value1&param2=value2'
```
