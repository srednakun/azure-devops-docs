---
title: Differences between provisioned and published wiki
titleSuffix: Azure DevOps
description: Understand the differences of updating a provisioned wiki for a team project versus files you publish from a Git repository in Azure DevOps 
ms.technology: devops-collab
ms.custom: wiki
ms.topic: conceptual
ms.assetid:
ms.author: chcomley
ms.reviewer: gopinach
author: chcomley
monikerRange: '>= tfs-2018'
ms.date: 06/07/2021  
---

# Provisioned wikis vs. published code as a wiki

[!INCLUDE [version-gt-eq-2018](../../includes/version-gt-eq-2018.md)] 

<!--- Supports https://go.microsoft.com/fwlink/?linkid=866310 -->

In Azure DevOps, you have the following options for maintaining wiki content.

- [Provision a wiki for your team project](wiki-create-repo.md). This option supports only one wiki for the team project.
- [Publish Markdown files defined in a Git repository to a wiki](publish-repo-to-wiki.md). With this option, you can maintain several versioned wikis to support your content needs, although it's available only if Azure Repos is enabled.

While both options maintain the wiki content in Git repositories, the way you add, update, and manage the wiki content differs.

> [!NOTE]  
> The publish code as wiki feature is currently available on Azure DevOps Server 2018 and later versions. For older versions, you can only [provision a wiki for your team project](wiki-create-repo.md).  

## Wiki page menu options

With a *provisioned wiki*, you add and edit pages directly within the **Wiki**. All content updates to a *provisioned wiki* occur within the **Wiki**.

With a publish code as wiki, you add, edit, and update content from **Repos** or **Code**.

The unavailable menu options for the wiki pages are shown in the following illustration. As you can see, several options aren't supported for the **publish as code wiki** pages.

**Provisioned wiki**

:::image type="content" source="media/wiki/diff-menu-options-provisioned.png" alt-text="Provisioned wiki page menu options"::: 

**Publish code as wiki**

:::image type="content" source="media/wiki/diff-menu-options.png" alt-text="Publish code page menu options":::

For example, the **Edit in Repos** option for the publish code as wiki takes you to the **Repo** page to edit that specific page. Updates you make to a page in the branch you selected for the wiki get automatically published to the wiki.

## Supported features and operational differences

*Provisioned wikis* and *publish as code wikis* support the following features:

- [Markdown format](markdown-guidance.md)
- [HTML tags](wiki-markdown-guidance.md#html-tag-support-in-wiki-pages)
- [Insert and resize images](markdown-guidance.md#images)
- [Mathematical notation and characters](markdown-guidance.md#mathematical-notation)
- [Link to work items using #](wiki-markdown-guidance.md#link-to-work-items-from-a-wiki-page)
- [Attach files](markdown-guidance.md#attach)
- [Filter Wiki contents](filter-print-wiki.md)
- [Print a Wiki page](filter-print-wiki.md)
- [Update content offline](wiki-update-offline.md)
- [Add or edit pages from the Wiki](add-edit-wiki.md)

The following table summarizes those operations or features that may differ, depending on the wiki type.  

> [!div class="mx-tdCol2BreakAll"]
> |Operation |    Provisioned wiki    | Publish code as wiki |
> |--------|--------------|--------------|  
> |[Support multiple wikis, name wiki](publish-repo-to-wiki.md)  |  | ✔️|
> |[Add or edit pages from **Repos** > **Files** or **Code** > **Files**](publish-repo-to-wiki.md) |  |✔️ |
> |[Revert to an earlier revision from the **Wiki**](wiki-view-history.md#revert-provision) |✔️ |  |
> |[Revert to an earlier revision from **Repos** or **Code**](wiki-view-history.md#revert-publish) |✔️ |✔️ |
> |[Maintain versioned wikis](#versioning) |  | ✔️ |
> |[Select a wiki version](wiki-select-unpublish-versions.md) |  | ✔️ |
> |[Unpublish a wiki](wiki-select-unpublish-versions.md) |  | ✔️ |

<a id="add-pages"></a>

## Add pages

For a *provisioned wiki* or *publish code as wiki*, select **New page** or **Add subpage**. To learn more, see [Add and edit wiki pages](add-edit-wiki.md#add-a-wiki-page).

<a id="toc"></a>

## Page sequence and page list in navigation pane

The *provisioned wiki* manages the page sequence and page list automatically as you add or move pages within the navigation pane.

To structure the list of pages in the navigation pane for a *publish code as wiki*, define the **.order** file at the root, and for each subfolder or parent page that contains subpages.

Both types of wikis follow the same file structure, it's just that the publish code as wiki requires you to maintain the page sequence manually.

To learn more about working with **.order** files, see [Wiki Git repository files and file structure](wiki-file-structure.md#order-file).

<a id="revisions"></a>

## Page revisions and reverting to a previous version

From the **Wiki**, you can view the revisions of any wiki page by choosing **Revisions** or selecting the **View revisions** menu option.

However, the revert process differs depending on the wiki page type.  

- For a *provisioned wiki* page, select **Revert**, as described in [Revert a commit to a provisioned wiki page](wiki-view-history.md#revert-provision)
- For a *publish as code wiki* page, work from a local branch and submit a pull request to update the branch you're working from.

<a id="versioning"></a>

## Versioning and unpublishing a wiki

With versioning, you can publish different content versions to distinct wikis, based on a versioned branch of a Git repo. Versioning and unpublishing content you've previously published to a wiki, is supported only for wikis that you've created by publishing code to a wiki.

To learn more, see [Version, select, or unpublish a published wiki](wiki-select-unpublish-versions.md).

## Delete project wiki

Deleting a project wiki isn't supported with wiki APIs, but you can delete the wiki repository by completing the following steps.

1. Clone the wiki repository to make a backup of all of its content. Select the context menu, and then select **Clone wiki**, copying the clone URL.

   :::image type="content" source="media/wiki/clone-wiki.png" alt-text="Clone the wiki repository":::

2. Get the git repository ID that is backing this wiki. Use [this REST API](/rest/api/azure/devops/wiki/wikis/get) to get all the wikis in the project.
   
   For example: GET https://dev.azure.com/fabrikam/_apis/wiki/wikis?api-version=4.1
   This returns all the wikis in the project, "sampleProject". Here you can get the repository ID of the wiki that you want to delete.

   :::image type="content" source="media/wiki/clone-repository.png" alt-text="Clone the wiki repository, copy the URL":::

3. Use the following REST API to delete the git repository.
	
    For example: DELETE https://dev.azure.com/fabrikam/_apis/git/repositories/{repositoryId}?api-version=4.1
	Use the repository ID of the project wiki found using the previous step. Ensure that the repository ID matches the project wiki that you want to remove.

## Update a wiki by working offline

You can work offline or in a local branch to update content for a  *provisioned wiki* and *publish as code wiki*. To learn more, see [Clone and update wiki pages offline](wiki-update-offline.md).

## Related articles

- [Create a wiki for your team project](./wiki-create-repo.md)
- [Wiki Git repository files and file structure](wiki-file-structure.md)
- [Publish a Git repository to a wiki](publish-repo-to-wiki.md)
- [Get Started with Git](../../repos/git/gitquickstart.md)
