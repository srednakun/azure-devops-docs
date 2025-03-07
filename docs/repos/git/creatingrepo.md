---
title: Create a new Git repo
titleSuffix: Azure Repos
description: Create new Git repos using Visual Studio or command line init 
ms.assetid: 83c20dac-85c6-4fa0-93b5-912d5477246a
ms.technology: devops-code-git 
ms.topic: tutorial
ms.date: 09/10/2018
monikerRange: '<= azure-devops'
---


#  Create a new Git repo

[!INCLUDE [version-lt-eq-azure-devops](../../includes/version-lt-eq-azure-devops.md)]
[!INCLUDE [version-vs-gt-2015](../../includes/version-vs-gt-2015.md)]

A Git repository, or repo, is a folder that you've told Git to help you track file changes in. 
You can have any number of repos on your computer, each stored in their own folder. 
Each Git repo on your system is independent, so changes saved in one Git repo don't affect the contents of another.

A Git repo contains every version of every file saved in the repo. Git saves these files very efficiently, so having a large number of versions doesn't mean that it uses a lot of disk space.
Storing each version of your files helps Git merge code better and makes working with multiple versions of your code quick and easy.

In this tutorial you learn how to:

> [!div class="checklist"]
> * Create a new Git repo

## Create a new repo

Manage any folder with source code or Visual Studio solution in Git by creating a repo for them. 
Later you can connect this Git repo to a remote Git repo to share your work with others. 

#### [Visual Studio](#tab/visual-studio/)

[!INCLUDE [temp](includes/note-new-git-tool.md)]  

### Create a repo 

* [Create a repo from a new solution](#from-a-new-solution)
* [Create a repo from an existing solution](#from-an-existing-solution)
* [Create a repo in an empty folder](#in-an-empty-folder)
* [Connect a local repo to a remote](#remotes)

### From a new solution

Create a new Git repo for your new Visual Studio solution by selecting **Create new Git repository** when creating the solution:

![Select Create new Git repository when creating a new solution](media/vscreategitrepo.png) 

### From an existing solution

To create a repo from an existing solution not in version control, select the **Publish** button in the bottom-right of the lower status bar ![Visual Studio publish button](media/share-your-code-in-git-vs/publish_status_bar.png).
This creates a new Git repo in the same directory as your solution and opens up the **Publish** view in Team Explorer so you can [push](pushing.md) your code to Azure Repos or 
another remote Git repository.

![Publishing a solution to a new remote Git repository in Visual Studio Team Explorer](media/vspublish.gif)

### In an empty folder

1. Open the **Connect** view in Team Explorer by choosing **Projects** then **Manage Connections** from the context menu. 
2. Under **Local Git Repositories**, select **New** and enter a folder where the repo will be created. This directory must be empty.  
3. Select **Create** to create the repo.

   ![Creating a new local Git repository in Visual Studio Team Explorer](media/CreateNewRepoVS.png)</ol>

<a name="remotes"></a>

### Connect a local repo to a remote

To connect a local repository to a hosted remote Git repository to share your work, go the **Settings** page in Team Explorer. Select **Repository Settings**.
Under **Remotes**, select **Add**.    

![Add a remote for a repo in Visual Studio Team Explorer](media/add_remote_vs.png)

Enter `origin` in the **Name** field and enter the [clone URL](clone.md#clone_url) for your repo in the **Fetch** field. 
Make sure that **Push matches fetch** is checked and select **Save**. 

#### [Command Line](#tab/command-line/)
Open up a command prompt and navigate to the top-level folder containing your project's code, or a new folder if you are starting from scratch. 
Create the Git repository using the `init` command as shown in the following example. After the repo is created, you'll see a confirmation like `Initialized empty Git repository in current directory`. 

```
git init .
```

Work in [branches](./create-branch.md) to keep track of your work and create [commits](commits.md) to snapshot your changes into Git.   

Once you are ready to share your code, [get the clone URL](clone.md#clone_url) for the repository you want to connect to and then set up a remote relationship (in this case, `origin`) so your repo 
can [push](pushing.md) changes to a shared repo.

```
git remote add origin https://dev.azure.com/fabrikam/Fabrikam/_git/FabrikamFiber
```

[Push](pushing.md) your changes to the `origin` repository to share with others:

```
git push origin users/frank/feature
```

> [!NOTE]
> You can also create and get repos from the command line or scripts using the [Azure DevOps Services CLI](/cli/azure/).

* * *


## Next steps

> [!div class="nextstepaction"]
> [Save work with commits](commits.md)