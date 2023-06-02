To install Nexus on Linux, follow these steps:

1. Prerequisites:
   - Ensure that Java Development Kit (JDK) is installed on your Linux system. Nexus requires Java to run. You can check if Java is installed by running the command `java -version` in the terminal. If Java is not installed, you can install it using the package manager of your Linux distribution.

2. Download Nexus:
   - Visit the Sonatype website and go to the Nexus download page: https://www.sonatype.com/nexus/repository-oss-download
   - Download the latest version of Nexus Repository Manager OSS (Open Source Edition). Look for the "Unix/Linux" distribution package in the list.
   - Alternatively, you can use the following command in the terminal to download Nexus:
     ```
     wget https://download.sonatype.com/nexus/3/latest-unix.tar.gz
     ```

3. Extract Nexus:
   - Open a terminal and navigate to the directory where the downloaded Nexus package is located.
   - Extract the package using the following command:
     ```
     tar -xf latest-unix.tar.gz
     ```

4. Configure Nexus:
   - Open the extracted Nexus directory.
   - In the `bin` folder, you will find a script called `nexus` (or `nexus.exe` for Windows). This is the Nexus startup script.
   - Make the script executable by running the following command:
     ```
     chmod +x nexus
     ```

5. Start Nexus:
   - Start Nexus by running the following command in the terminal:
     ```
     ./nexus start
     ```

6. Access Nexus Web UI:
   - Open a web browser and navigate to `http://localhost:8081`. This is the default URL for accessing Nexus.
   - The first time you access Nexus, you will be prompted to set up the administrator credentials. Follow the on-screen instructions to create an admin user.

That's it! Nexus is now installed and running on your Linux system. You can proceed to configure Nexus, create repositories, and manage artifacts using the Nexus Web UI.

## Install Nexus using Docker

```
docker run -d --name nexus -p 8081:8081 sonatype/nexus3

```
