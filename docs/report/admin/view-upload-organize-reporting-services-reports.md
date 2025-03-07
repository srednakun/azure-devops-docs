---
title: View, upload, and organize Reporting Services reports
titleSuffix: Azure DevOps Server
description: View, upload, and organize Reporting Services reports to analyze the progress and quality of the project.
ms.technology: devops-analytics
ms.topic: conceptual
ms.assetid: 6368a79e-32d4-4451-89de-0975530e3d17
ms.author: kaelli
author: KathrynEE
ms.date: 09/23/2021
---

# View, upload, and organize Reporting Services reports

[!INCLUDE [version-lt-azure-devops](../../includes/version-lt-azure-devops.md)]

You can analyze the progress and quality of your project by viewing the reports in SQL Server Reporting Services.  

> [!NOTE]  
> This article applies to TFS-2017 and earlier versions. Starting with TFS-2018, the integration of SQL Reporting Services and Team Explorer was deprecated. 
  
 The ![Report](media/icon_reportte.png "Icon_reportTE")**Reports** page in Team Explorer provides a tree view of the reports defined for your team project. To open a report, choose it and press Enter.  
  
> [!NOTE]
>  The ![Report](media/icon_reportte.png "Icon_reportTE") **Reports** option appears only when the team project collection that contains your team project is provisioned with Reporting Services. For more information, see [Add a Report Server to a Team Project Collection](../admin/add-reports-to-a-team-project.md).  
  
 The ![Report](media/icon_reportte.png "Icon_reportTE")**Reports** page for your team project shows the reports and organizes them under a set of folders. The default set of reports is based on the process template that was used to create the team project. You can manage these reports using Report Manager. For more information, see [Report Server Content (Native Mode)](/previous-versions/azure/devops/reference/upgrade/new-features-added).  
  
 The reports that TFS provides with the default process templates provide a view of the current state of your project. They do so by aggregating and summarizing the metrics from:
- Work items.
- Version control.
- Test results.
- Builds.

You can use the default reports, or you can customize each report to fit your specific needs.  
  
 Most of these reports provide filters that you can use to specify contents to include in the report. Filters include time period, iteration and area paths, work item types, and work item states. The questions that they answer relate to all types of work items such as user stories, test cases, tasks, and bugs. For more information about the purpose, layout, or use of each report, see [Reporting Services Reports](../sql-reports/reporting-services-reports.md).  
  
 Team project reports are stored in Reporting Services, and you can access them through Team Explorer or Report Manager. As the number of reports listed on the **Reports** page increases, you may want to create subfolders for grouping or organizing the reports.  
  
 You use Report Manager to manage reports and report folders. To access the team report site from Team Web Access, on the Home page, select ![Report](media/icon_reportte.png "Icon_reportTE") **Reports**.  
  
 **Requirements**  
  
-   To open a report from Team Explorer, your **View project-level information** permission on the team project must be set to **Allow**. You must also be a member of the SQL Server Reporting Services **Browser** role.  
  
-   To manage reports from Report Manager, you must be a member of the SQL Server Reporting Services **Team Foundation Content Manager** role. For more information, see [Grant permissions to view or create reports in TFS](../admin/grant-permissions-to-reports.md).  
  
    > [!NOTE]
    >  If you are running Windows Server 2008 or Windows Vista, you might have trouble opening Web pages or sites from Team Explorer. For example, you might not be able to open the project portal by right-clicking a team project in Team Explorer and then clicking **Show Project Portal**. For more information about access issues that may occur with Windows Server 2008 or Windows Vista, see the following page on the Microsoft Web site: [User Account Control](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772207(v=ws.10)).  
  
## Viewing

### To view a report from Team Explorer  
  
1.  From the ![Home icon](media/alm_te_home_icon.png "ALM_TE_Home_Icon") home page in Team Explorer, choose ![Report](media/icon_reportte.png "Icon_reportTE")**Reports**.  
  
    > [!NOTE]
    >  If a red X icon appears next to ![Report](media/icon_reportte.png "Icon_reportTE")**Reports**, you might not have permissions to access the reports, or Team Explorer might have lost communication with the server that hosts Reporting Services. In these instances, check with your project administrator to make sure that you have permissions to access the reports and that the server that hosts Reporting Services is running.  
  
    Also, a red X icon might appear next to **Reports** if both of the following conditions are true:  
  
    - Team Explorer is running on the same computer as Reporting Services.  
  
    - You aren't signed in as an administrator, or enhanced security is enabled for Internet Explorer.  
  
    To correct this issue, sign in to your computer as an administrator, or open Internet Explorer, open Internet Options, choose the **Security** tab, and clear the **Enabled Protected Mode** check box.  
  
1.  Choose the report and then press Enter.  
  
     A web browser window opens and shows the report.  
  
2.  At the top of the report, specify your filter parameters, and then choose **View Report**.  
  
### To view a report from Report Manager
  
1.  From the ![Home icon](media/alm_te_home_icon.png "ALM_TE_Home_Icon") home page in Team Explorer, choose  ![Report](media/icon_reportte.png "Icon_reportTE")**Reports**, and then choose the **Go to site** link.  
  
     Or, choose **Team, Show Report Site** from the Visual Studio toolbar.  
  
2.  In **Report Manager**, choose the folder that contains the report you want to view.  
  
3.  Choose the report that you want to open.  
  
4.  At the top of the report, specify your filter parameters, and then choose **View Report**.  
  
## Related notes
-  [Reporting Services Reports](../sql-reports/reporting-services-reports.md)   
-  [Create and manage Reporting Services reports](../sql-reports/create-and-manage-reporting-services-reports.md)