# DAY-15 | Azure Artifacts

Azure Artifacts is a package management solution provided by Microsoft Azure. It enables you to create, host, and share packages within your organization. These packages can include libraries, frameworks, modules, or any other components required by your software projects.

#### Click Below to watch the video Tutorial
[![Watch the video](https://img.youtube.com/vi/tiP-Z1jPax0/0.jpg)](https://www.youtube.com/watch?v=tiP-Z1jPax0)

### Getting Started

To start using Azure Artifacts and gain hands-on experience, follow these steps:

#### Step 1: Create an Azure Artifacts feed

1. Sign in to the Azure portal using your Azure account.
2. Open the Azure Artifacts service.
3. Click on "New feed" to create a new feed.
4. Provide a name for your feed, select the appropriate organization, and choose a project to associate with the feed.
5. Configure other settings such as visibility, upstream sources, etc., based on your requirements.
6. Click on "Create" to create the feed.

#### Step 2: Configure package sources

1. After creating the feed, navigate to its settings page.
2. Click on "Connect to feed" to obtain the package source URL and authentication details.
3. Make a note of the URL as you will need it for configuring your project to use the feed.

#### Step 3: Publish packages

1. Choose the package manager that aligns with your project's technology stack (e.g., npm, NuGet, Maven).
2. For npm, use the following command to publish packages to your Azure Artifacts feed:
   ```
   npm publish --registry=<feed-url> --scope=@<organization-scope>
   ```
   Replace `<feed-url>` with the package source URL obtained in the previous step and `<organization-scope>` with the appropriate scope for your organization.

#### Step 4: Consume packages

To consume packages from your Azure Artifacts feed, configure your project to use the feed as a package source. The configuration steps vary depending on the package manager:

- npm: Create or update a `.npmrc` file in your project's root directory and add the following line:
  ```
  registry=<feed-url>
  ```
  Replace `<feed-url>` with the package source URL.

- NuGet: Add a NuGet configuration file (`NuGet.config`) to your project and specify the package source as follows:
  ```xml
  <configuration>
    <packageSources>
      <add key="<source-name>" value="<feed-url>" />
    </packageSources>
  </configuration>
  ```
  Replace `<source-name>` with a name for the package source and `<feed-url>` with the package source URL.

- Maven: Add the package source to your project's `settings.xml` file, typically located in your `.m2` directory. Add the following section:
  ```xml
  <settings>
    <profiles>
      <profile>
        <repositories>
          <repository>
            <id><source-name></id>
            <url><feed-url></url>
          </repository>
        </repositories>
      </profile>
    </profiles>
  </settings>
  ```
  Replace `<source-name>` with a name for the package source and `<feed-url>` with the package source URL.

#### Step 5: Install and use packages

Once your project is configured to use Azure Artifacts as a package source, you can install and use packages from the feed. Refer to the documentation of your specific package manager for instructions on installation and usage.

Please note that these steps provide a general overview of working with Azure Artifacts and package management. The process may vary depending on your project's requirements and the package manager you are using. For more detailed instructions, consult the official documentation and guides specific to your chosen package manager and Azure Artifacts.
