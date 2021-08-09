# Step 0 (Optional): GCP Setup
If you'd like to host HiGlass on GCP, follow these steps to create a GCP instance with the features necessary to host HiGlass.

## Create a project
If you want to host HiGlass on a new project, first open your GCP home page and select the projects menu.
![](https://user-images.githubusercontent.com/29579245/128775701-fcfe601e-09d9-476b-b00b-f88f10bf4712.png)
Click on "New Project" and select a name for your project. Make sure it is made in the correct organization.
![](https://user-images.githubusercontent.com/29579245/128775296-56f836c5-c4f8-4dec-8580-342190ec006a.png)

If you're adding HiGlass to an existing GCP project, ignore this step.

## Creating a VM
You will need a virtual machine to host HiGlass. Click on the menu in the top left corner and select Compute Engine → VM instances. (You may need to enable Compute Engine first - just click "Enable" when you see the prompt. You will need a billing account connected to enable it.)

![](https://user-images.githubusercontent.com/29579245/128776356-f01b28b8-6136-4f42-94df-a3f74e379bd6.png)

After you reach the VM instances page, click "Create instance".
![](https://user-images.githubusercontent.com/29579245/128776923-5ad5620f-e549-466f-b6dc-825ee194efa6.png)

You should be able to leave most of the settings at their defaults. You can change the name to whatever you'd like to name the VM, and you can configure the VM size if you'd like (though the default of 2 vCPUs and 4GB of memory should be more than enough.)

However, make sure to configure the boot disk. You should use the most recent Ubuntu LTS version available (at the time of writing, Ubuntu 20.04 LTS). Additionally, you may want to increase the amount of space available from 10GB if you expect to be hosting a large dataset.

![](https://user-images.githubusercontent.com/29579245/128777660-b7c4dc1a-bbed-477b-a13f-c72f6317cbe0.png)

Also, tick both the "Allow HTTP traffic" and "Allow HTTPS traffic" boxes under the "Firewall" section.

## Accessing the shell
When you see your VM appear in the instance list, click the "SSH" button to open up an SSH session with the VM in your browser. A terminal-like window should pop up, and in it you can type the commands you need to install and set up HiGlass.

![](https://user-images.githubusercontent.com/29579245/128778001-fcaf1d8a-0ebe-487c-a230-e037e172b13f.png)

Follow the steps in the [installation guide](./1-installation.md) to continue.