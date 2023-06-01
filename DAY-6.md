

# DAY-6 | OWASP Dependency Check

OWASP Dependency Check is a software composition analysis (SCA) tool that identifies project dependencies with known vulnerabilities. It helps developers and security professionals identify and mitigate potential risks associated with using vulnerable libraries and components.

## Installation

You can install OWASP Dependency Check using various methods:

### Option 1: Downloading the Standalone JAR

1. Go to the [OWASP Dependency Check releases page](https://github.com/jeremylong/DependencyCheck/releases).
2. Download the latest version of the standalone JAR file (`dependency-check.jar`).
3. Ensure you have Java 8 or higher installed on your system.
4. Run the tool using the following command:
   ```
   java -jar dependency-check.jar --project <project-name> --scan <path-to-project>
   ```

### Option 2: Using Package Managers

OWASP Dependency Check is available in popular package managers:

- **Maven**: Add the following plugin to your `pom.xml` file:
  ```xml
  <build>
    <plugins>
      <plugin>
        <groupId>org.owasp</groupId>
        <artifactId>dependency-check-maven</artifactId>
        <version>INSERT_VERSION_HERE</version>
        <executions>
          <execution>
            <goals>
              <goal>check</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
  ```
  Run `mvn dependency-check:check` to analyze your project.



## Usage

Once you have OWASP Dependency Check installed, you can run it against your project to identify vulnerabilities in dependencies.

- For the standalone JAR:
  ```
  java -jar dependency-check.jar --project <project-name> --scan <path-to-project>
  ```

- For Maven:
  ```
  mvn dependency-check:check
  ```


Make sure to replace `<project-name>` with the name of your project and `<path-to-project>` with the path to your project's directory.

## Configuration

OWASP Dependency Check offers various configuration options to customize its behavior. Refer to the [Configuration Guide](link-to-configuration-guide) for detailed information on how to configure the tool according to your needs.

## Reporting

OWASP Dependency Check generates comprehensive reports about the vulnerabilities identified in your project's dependencies. You can find the generated reports in the following locations:

- For the standalone JAR: `<path-to-project>/target/dependency-check-report.html`
- For Maven: `<path-to-project>/target/dependency-check-report.html`
- For Gradle: `<path-to-project>/build/reports/dependency-check-report.html`

Open the HTML report in your web browser to view the vulnerability details.

## Contributing

If you encounter any issues or would like to contribute to OWASP Dependency Check, please refer to the [Contributing Guidelines](link-to-contributing-guidelines) for instructions on how to get involved.

## Resources

- [OWASP Dependency Check GitHub Repository](https://github.com/jeremylong/DependencyCheck)
- [OWASP Dependency Check Official Website](https://owasp.org/www-project-dependency-check/)

## With Pipeline 

```groovy
pipeline {
    agent any
    
    tools {
        jdk 'jdk11'
        maven 'maven3'
    }
    
    environment {
        SCANNER_HOME = tool 'sonar-scanner'
    }
    
    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/jaiswaladi246/Petclinic.git'
            }
        }
        
        stage('Compile') {
            steps {
               sh "mvn clean compile"
            }
        }
        
        stage('Test cases') {
            steps {
               sh "mvn test"
            }
        }
        
        stage('Sonarqube Analysis') {
            steps {
               sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.url=http://13.235.115.91:9000/ -Dsonar.login=squ_0dbe68dbee1fb33ebf9d46975a892aee5d414927 -Dsonar.projectName=Petclinic \
                    -Dsonar.java.binaries=. \
                    -Dsonar.projectKey=Petclinic '''
            }
        }
        
        stage('Build') {
            steps {
               sh "mvn clean package "
            }
        }
        
        stage('OWASP Dependency Check') {
            steps {
                dependencyCheck additionalArguments: '--scan target/', odcInstallation: 'owasp'
            }
        }
        
        stage('Publish OWASP Dependency Check Report') {
            steps {
                publishHTML(target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: 'target',
                    reportFiles: 'dependency-check-report.html',
                    reportName: 'OWASP Dependency Check Report'
                ])
            }
        }
        
        stage('Tomcat Deploy') {
            steps {
               sh "sudo cp target/petclinic.war /opt/apache-tomcat-9.0.65/webapps "
            }
        }
    }
}
```

