##  DAY-5 | SONARQUBE  ##
SonarQube is an open-source platform that provides static code analysis and code quality management. It is designed to help developers and development teams identify and fix code issues early in the software development lifecycle. SonarQube analyzes source code for bugs, vulnerabilities, code smells, and code duplications, and provides detailed reports with actionable insights.

Here are some key features of SonarQube:

- **Static Code Analysis**: SonarQube performs static analysis on source code, analyzing its structure, syntax, and patterns to identify potential issues and violations of coding standards.

- **Code Quality Metrics**: SonarQube calculates various code quality metrics, such as code coverage, cyclomatic complexity, duplications, and maintainability index. These metrics help developers evaluate the overall quality of their codebase.

- **Issue Tracking**: SonarQube identifies and categorizes issues in the code, such as bugs, security vulnerabilities, and code smells. It provides detailed information about each issue, including the affected code snippet, severity level, and recommended fixes.

- **Continuous Inspection**: SonarQube supports continuous integration and continuous delivery (CI/CD) workflows by integrating with popular build tools and version control systems. It can be seamlessly integrated into the development pipeline to automatically analyze code with every build.

- **Custom Rules and Quality Profiles**: SonarQube allows you to define custom coding rules and quality profiles to align with your project's specific requirements and coding standards. This helps enforce consistent code quality across your development team.

- **Integrations**: SonarQube integrates with a wide range of development tools and IDEs, enabling developers to receive real-time feedback on code quality while they write code. It also integrates with popular CI/CD platforms to provide continuous inspection throughout the software development process.

By using SonarQube, development teams can proactively identify and address code issues, improve code maintainability, enhance security, and ensure adherence to coding standards. It helps foster a culture of quality within development teams and promotes the delivery of robust and reliable software.
```


--- Docker Installation ---

```shell
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg

sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo apt install docker-compose

service docker restart
sudo usermod -aG docker $USER
newgrp docker
sudo chmod 666 /var/run/docker.sock
sudo systemctl restart docker


# TO ISNTALL SONARQUBE RUN BELOW COMMAND  
docker run -d --name sonar -p 9000:9000 sonarqube:lts-community
```
```


