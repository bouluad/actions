This GitHub Actions workflow automates the process of building a Java application, running tests, performing code analysis with SonarQube, and pushing the artifact into a Nexus repository. This workflow is triggered on pushes to the main branch.

Prerequisites
Before setting up this workflow, ensure you have the following in place:

Maven Configuration: Your Java project should be configured with Maven. Make sure your project's pom.xml file is correctly set up.

SonarQube Configuration: Set up a SonarQube server and configure your project in SonarQube. Obtain the SonarQube project key and authentication token for analysis.

Nexus Configuration: Configure a Nexus repository to which you want to deploy your Maven artifacts. Ensure you have Nexus repository credentials.

GitHub Repository: This workflow should be set up in your GitHub repository where your Java project resides.

GitHub Secrets
To securely store sensitive information, you need to add the following secrets to your GitHub repository:

NEXUS_USERNAME: Your Nexus repository username.
NEXUS_PASSWORD: Your Nexus repository password.
SONAR_TOKEN: Your SonarQube authentication token (for SonarQube analysis).
Workflow Steps
1. Checkout Code
This step checks out your Java project's code from the repository.

2. Set up JDK
Sets up the Java Development Kit (JDK). In this example, it uses Java 11, but you can modify the java-version as needed.

3. Build with Maven
This step builds your Java application using Maven by running mvn clean install.

4. Run Tests
Runs tests on your Java application using Maven by running mvn test.

5. SonarQube Scan
Performs a SonarQube analysis on your code using Maven. Replace the placeholders with your SonarQube project key, organization, instance URL, and authentication token.

6. Publish to Nexus
Publishes the artifact to the Nexus repository. Replace the Nexus repository URL (https://your-nexus-repo-url/repository/maven-releases), nexus, NEXUS_USERNAME, and NEXUS_PASSWORD with your Nexus repository details.

Workflow Execution
When you push changes to the main branch, this workflow is automatically triggered.

It checks out the code, sets up the JDK, builds the Java application, runs tests, and performs a SonarQube analysis.

If all steps are successful, the artifact is published to your Nexus repository.

Configuring Maven
Ensure your Maven settings.xml file and pom.xml are configured correctly with your Nexus repository credentials and SonarQube project details.

That's it! With this GitHub Actions workflow, you can automate the entire process of building, testing, analyzing, and deploying your Java application.
