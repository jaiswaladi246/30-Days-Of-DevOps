# DAY-12 | Azure Pipelines

#### Click Below to watch the video Tutorial
[![Watch the video](https://img.youtube.com/vi/coWZWmlfzKM/0.jpg)](https://www.youtube.com/watch?v=coWZWmlfzKM)

## Azure Pipelines with Classic Editor

Azure Pipelines is a powerful continuous integration and delivery (CI/CD) platform provided by Microsoft Azure. The Classic Editor in Azure Pipelines allows you to define your build and release pipelines using a graphical interface. This guide will walk you through the steps to set up and configure Azure Pipelines using the Classic Editor.

### Prerequisites

Before getting started, make sure you have the following:

1. An Azure DevOps organization: You need an Azure DevOps organization to create and manage your pipelines. If you don't have one, you can create a new organization or use an existing one.

2. A repository with your source code: Azure Pipelines integrates with various source control systems like Git, GitHub, Azure Repos, and more. Make sure your source code repository is set up and accessible.

### Creating an Azure Pipeline

To create an Azure Pipeline using the Classic Editor, follow these steps:

1. Open your Azure DevOps organization and navigate to the project where you want to create the pipeline.

2. Go to the Pipelines section and click on the **New pipeline** button.

3. Select your source code repository and choose the branch you want to build.

4. Azure Pipelines provides several pipeline templates for popular application types. You can choose a template or start with an empty pipeline. Click on **Apply** to proceed.

5. The Classic Editor will open, displaying a graphical interface to define your pipeline. The editor consists of various stages and tasks that you can configure.

6. Define your pipeline stages by clicking on the **Add stage** button. Each stage represents a logical division in your CI/CD process, such as build, test, and deployment.

7. Within each stage, you can add tasks by clicking on the **+** icon. Tasks are individual actions performed within a stage, such as compiling code, running tests, or deploying applications.

8. Configure each task by providing the necessary inputs and parameters. You can specify things like the target platform, script files, command-line arguments, and more.

9. Use the control flow options to manage the execution of your pipeline. You can add conditions, parallelize tasks, and control the overall flow based on success or failure.

10. Once you have defined your pipeline stages and tasks, click on the **Save & queue** button to save your pipeline configuration.

![alt text](https://github.com/jaiswaladi246/30-Days-Of-DevOps/blob/main/Images/10.png?raw=true)

### Running the Pipeline

To run your Azure Pipeline, follow these steps:

1. After saving your pipeline configuration, you will be redirected to the pipeline overview page.

2. Click on the **Run** button to manually trigger a pipeline run. You can also set up triggers to automatically start the pipeline on events like code commits or pull requests.

3. Monitor the progress of your pipeline as it executes. You can view the logs, check the status of each stage, and identify any issues that occur during the process.

4. Once the pipeline run is complete, you can review the results and any generated artifacts or build outputs.

### Conclusion

Congratulations! You have successfully set up and executed an Azure Pipeline using the Classic Editor. Azure Pipelines provides extensive capabilities for building, testing, and deploying your applications, helping you streamline your software development process. Explore the Azure Pipelines documentation for more advanced features and customization options.

For more information and detailed documentation on Azure Pipelines using the Classic Editor, refer to the official [Azure Pipelines documentation](https://docs.microsoft.com/azure/devops/pipelines/?view=azure-devops-2022) provided by Microsoft.

