# **DAY-4 | JENKINS**

Jenkins is an open-source automation server that allows you to automate various tasks in your software development workflow, such as building, testing, and deploying applications. It provides a web-based interface and supports a wide range of plugins for integrating with different tools and technologies.

#### Click Below to watch the video Tutorial
[![Watch the video](https://img.youtube.com/vi/zQpDnuUuff4/maxresdefault.jpg)](https://www.youtube.com/watch?v=zQpDnuUuff4)

###  REAL WORLD SCENARIO  ###
Let's consider a real-world scenario where Jenkins is used in a typical software development workflow:

1. **Version Control**: Developers commit their code changes to a version control system like Git.

2. **Continuous Integration**: Jenkins is set up to monitor the version control system for changes. Whenever a new commit is made, Jenkins automatically triggers a build process.

3. **Build**: Jenkins checks out the latest code from the repository and performs a build process. This typically involves tasks such as compiling the code, running unit tests, and generating build artifacts.

4. **Automated Testing**: After the build is successful, Jenkins triggers automated tests. These tests can include unit tests, integration tests, functional tests, and more, depending on the project's requirements.

5. **Code Quality Analysis**: Jenkins can integrate with code analysis tools like SonarQube or Checkstyle to perform static code analysis and generate reports on code quality, coding standards, and potential issues.

6. **Artifact Storage**: Jenkins archives the build artifacts, including compiled binaries, documentation, and other relevant files.

7. **Deployment**: Jenkins can deploy the built artifacts to various environments, such as staging or production servers. This can involve tasks like deploying to application servers, configuring databases, or setting up infrastructure.

8. **Notification and Reporting**: Jenkins sends notifications to relevant stakeholders, such as developers, testers, or project managers, about the build status, test results, and any issues encountered. It can also generate reports and metrics for monitoring and tracking the progress of the software development process.

9. **Continuous Deployment**: Jenkins can be configured to automate the deployment process to production environments based on predefined conditions and approvals. This ensures that code changes are seamlessly delivered to users without manual intervention.

10. **Monitoring and Scaling**: Jenkins can integrate with monitoring and alerting tools to track the performance and health of deployed applications. It can also scale the application infrastructure based on predefined rules or triggers.

11. **Scheduled Jobs**: Jenkins allows the scheduling of jobs for recurring tasks such as backups, database cleanups, or periodic maintenance tasks.

By leveraging Jenkins in this scenario, teams can achieve continuous integration, automated testing, code quality analysis, and streamlined deployment processes. Jenkins helps to automate repetitive tasks, ensure code stability, and improve collaboration among team members. Additionally, it provides visibility into the entire software development lifecycle, enabling efficient management and monitoring of the project.

## **Ways To Install Jenkins on Windows & Linux**

### **--- INSTALL JENKINS  ON LINUX METHOD -1 ---**

```shell
sudo apt update -y
sudo apt install openjdk-11-jre -y

curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update -y 
sudo apt-get install jenkins -y

sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```

### **--- INSTALL JENKINS ON LINUX METHOD -2 ---**

```shell
sudo apt update -y
sudo apt install openjdk-11-jre -y
sudo wget https://updates.jenkins.io/download/war/2.387.3/jenkins.war
java -jar Jenkins.war  --httpPort=8082
```
### **--- INSTALL JENKINS ON WINDOWS ---**

Follow these step-by-step instructions to install Jenkins on your Windows machine:

1. Visit the official Jenkins website at [https://www.jenkins.io/](https://www.jenkins.io/) and go to the "Download" section.

2. Click on the "Windows" tab and download the latest stable release of Jenkins for Windows as a "Generic Java package (.war)" file.

3. Once the download is finished, navigate to the location where you saved the Jenkins ".war" file.

4. Open a command prompt by pressing "Win + R" and typing "cmd", then hit Enter.

5. In the command prompt, navigate to the directory where you saved the Jenkins ".war" file using the `cd` command. For example, if you saved the file in the "Downloads" folder, you would use the command: `cd C:\Users\YourUsername\Downloads`.

6. Once you're in the correct directory, run the following command to start Jenkins: `java -jar jenkins.war`.

7. Jenkins will start initializing, and you'll see some log output in the command prompt.

8. Open a web browser and go to [http://localhost:8080/](http://localhost:8080/). This is the default URL for accessing the Jenkins web interface.

9. On the Jenkins web page, you'll be prompted to enter the initial administrator password. To obtain the password, go back to the command prompt where Jenkins is running and look for the line that says "Please unlock Jenkins". Copy the alphanumeric password from there.

10. Paste the administrator password into the Jenkins web interface and click "Continue".

11. On the next screen, choose the option "Install suggested plugins" to install the recommended set of plugins. This will enable basic functionality in Jenkins.

12. Wait for the plugin installation to complete. Once done, you'll be prompted to create an admin user. Fill in the required details and click "Save and Continue".

13. Finally, you'll see the Jenkins dashboard, where you can start setting up your projects and automation workflows.

That's it! You have successfully installed Jenkins on your Windows machine. Feel free to explore the various features and capabilities offered by Jenkins for continuous integration and delivery.

## Jenkins Guide: Installing Plugins, Global Tool Configuration, Configure System, and Adding Credentials

In this guide, we will walk you through the process of installing plugins, configuring global tools, setting up system configurations, and adding credentials in Jenkins. Let's get started!

### Installing Plugins

1. From the Jenkins dashboard, click on "Manage Jenkins" in the left sidebar.
2. Select "Manage Plugins" to access the plugin installation page.
3. In the "Available" tab, you can browse and search for plugins you want to install.
4. Check the box next to the plugin(s) you want to install.
5. Click on the "Install without restart" button to install the selected plugin(s).
6. Wait for the installation process to complete. You can view the progress on the Jenkins console.
7. Once the installation is finished, you may be prompted to restart Jenkins. If required, click on the "Restart Jenkins when installation is complete and no jobs are running" checkbox and then click "Continue."

### Global Tool Configuration

1. From the Jenkins dashboard, click on "Manage Jenkins" in the left sidebar.
2. Select "Global Tool Configuration" to access the tool configuration page.
3. Scroll down to the section corresponding to the tool you want to configure (e.g., JDK, Git, Maven).
4. Click on the "Add JDK"/"Add Git"/"Add Maven" button to configure each tool individually.
5. Provide the necessary details such as name, path, version, etc., depending on the tool you are configuring.
6. Click on "Save" to save the global tool configuration.

### Configure System

1. From the Jenkins dashboard, click on "Manage Jenkins" in the left sidebar.
2. Select "Configure System" to access the system configuration page.
3. Here, you can modify various system-wide settings and configurations.
4. Review and update the configuration options based on your requirements. Some common configurations include:

- Jenkins URL: Set the Jenkins URL to access the Jenkins server.
- System Message: Add a system message to display on the Jenkins dashboard.
- E-mail Notification: Configure the email settings for Jenkins notifications.
- Security Settings: Configure security options like access control, user management, and authorization strategies.

5. Click on "Save" to save the system configuration.

### Adding Credentials

1. From the Jenkins dashboard, click on "Credentials" in the left sidebar.
2. Select "System" to access the system credentials page.
3. Click on "Global credentials (unrestricted)" or a specific domain to add credentials.
4. Click on the "Add Credentials" link to add a new credential entry.
5. Choose the credential type from the available options (e.g., Username and Password, SSH Username with Private Key, Secret Text, etc.).
6. Fill in the required fields for the selected credential type, such as username, password, private key, etc.
7. Provide an optional description to help identify the credential entry.
8. Click on "OK" to save the credential entry.

That's it! You have now installed plugins, configured global tools, set up system configurations, and added credentials in Jenkins. These configurations will enable you to enhance the capabilities of your Jenkins environment and customize it to meet your specific needs.

🚀 **Start automating your software development workflow with Jenkins!** 🚀

## **Jenkins Job Tutorial**

In this tutorial, we'll walk you through the process of creating three types of Jenkins jobs: Freestyle, Pipeline, and Multibranch. Each job will have stages for Git checkout, Maven compile, Maven package, and deploying to Tomcat. Let's get started!

### **Freestyle Job**

1. From the Jenkins dashboard, click on "New Item" to create a new job.
2. Enter a name for the job and select "Freestyle project" as the job type.
3. In the job configuration page, go to the "Source Code Management" section and choose your Git repository. Configure the branch or repository URL as per your requirements.
4. In the "Build" section, click on "Add build step" and select "Execute shell" from the dropdown.
5. In the shell script section, enter the following commands:

```shell
#!/bin/bash

# Git checkout
git checkout <branch_name>

# Maven compile
mvn compile

# Maven package
mvn package

# Deploy to Tomcat
# Replace 'webapp.war' with your generated WAR file name and adjust the Tomcat server details
cp target/webapp.war /path/to/tomcat/webapps/
```

6. Click on "Save" to save the job configuration.

### **Pipeline Job**

1. From the Jenkins dashboard, click on "New Item" to create a new job.
2. Enter a name for the job and select "Pipeline" as the job type.
3. In the job configuration page, scroll down to the "Pipeline" section.
4. Choose the "Pipeline script" option and enter the following script:

```groovy
pipeline {
  agent any
  
  tools{
        jdk 'jdk11'
        maven 'maven3'
        }
  
  stages {
    stage('Git Checkout') {
      steps {
        // Git checkout
        git branch: '<branch_name>', url: '<git_repository_url>'
      }
    }
    
    stage('Maven Compile') {
      steps {
        // Maven compile
        sh 'mvn compile'
      }
    }
    
    stage('Maven Package') {
      steps {
        // Maven package
        sh 'mvn package'
      }
    }
    
    stage('Deploy to Tomcat') {
      steps {
        // Deploy to Tomcat
        sh 'cp target/webapp.war /path/to/tomcat/webapps/'
      }
    }
  }
}
```

5. Click on "Save" to save the job configuration.

### **Multibranch Job**

1. From the Jenkins dashboard, click on "New Item" to create a new job.
2. Enter a name for the job and select "Multibranch Pipeline" as the job type.
3. In the job configuration page, go to the "Branch Sources" section.
4. Configure the source for your Git repository, such as GitHub or Bitbucket, and provide the necessary credentials and repository details.
5. In the "Build Configuration" section, click on "Add build step" and select "Pipeline script" from the dropdown.
6. Enter the same pipeline script mentioned in the Pipeline Job section.
7. Click on "Save" to save the job configuration.

That's it! You have now created three Jenkins jobs: Freestyle, Pipeline, and Multibranch, with stages for Git checkout, Maven compile, Maven package, and deploying to Tomcat. You can trigger these jobs manually or configure them to run automatically based on your requirements.
