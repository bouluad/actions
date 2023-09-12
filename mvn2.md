1. Checkout Code
yaml
Copy code
- name: Checkout code
  uses: actions/checkout@v2
This step uses the actions/checkout GitHub Action to clone your repository's code into the GitHub Actions runner environment. It ensures that the subsequent steps have access to your project's source code.

2. Set up JDK
yaml
Copy code
- name: Set up JDK
  uses: actions/setup-java@v2
  with:
    java-version: '11'
This step sets up the Java Development Kit (JDK) in the GitHub Actions runner environment. In this example, it installs JDK version 11, which can be configured to match your project's Java version requirements.

3. Build with Maven
yaml
Copy code
- name: Build with Maven
  run: mvn clean install
This step uses Maven to build your Java application. The mvn clean install command cleans any previous build artifacts, compiles your code, runs tests, and packages your application into a JAR or WAR file.

4. Run Tests
yaml
Copy code
- name: Run Tests
  run: mvn test
Here, Maven is used to execute the tests for your Java application. It ensures that your code behaves correctly and meets the defined test cases.

5. SonarQube Scan
yaml
Copy code
- name: SonarQube Scan
  run: mvn sonar:sonar -Dsonar.projectKey=your_project_key -Dsonar.organization=your_organization -Dsonar.host.url=https://your-sonarqube-instance -Dsonar.login=your-sonar-token
This step performs a SonarQube code analysis on your Java application. You need to replace the placeholders with your specific SonarQube configuration details:

your_project_key: The unique key for your SonarQube project.
your_organization: The organization name in your SonarQube setup.
https://your-sonarqube-instance: The URL of your SonarQube server.
your-sonar-token: An authentication token or username/password for SonarQube access.
SonarQube analysis provides insights into code quality, security, and maintainability.

6. Publish to Nexus
yaml
Copy code
- name: Publish to Nexus
  run: mvn deploy -DrepositoryId=nexus -Durl=https://your-nexus-repo-url/repository/maven-releases -Drepository.url=https://your-nexus-repo-url/repository/maven-releases -Drepository.username=$NEXUS_USERNAME -Drepository.password=$NEXUS_PASSWORD
This step deploys your Maven artifact (e.g., JAR or WAR file) to a Nexus repository. Replace the placeholders with your Nexus repository details:

https://your-nexus-repo-url/repository/maven-releases: The URL of your Nexus repository.
nexus: The repository ID for Nexus (configured in your settings.xml).
$NEXUS_USERNAME and $NEXUS_PASSWORD: These environment variables are set using GitHub Secrets and provide the necessary authentication credentials for Nexus repository access.
This step ensures that your built artifact is stored in your Nexus repository for distribution and version control.
