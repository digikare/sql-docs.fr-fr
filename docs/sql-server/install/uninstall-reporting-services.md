---
title: "D&#233;sinstaller Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5c764a00-d4bc-465d-b32e-e4efce052ce4
caps.latest.revision: 7
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "erikre"
caps.handback.revision: 7
---
# D&#233;sinstaller Reporting Services
  La désinstallation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne supprime pas le contenu que vous avez créé ou la configuration que vous avez modifiée. Toutefois, s'il existe du contenu dont vous avez besoin une fois la désinstallation terminée, il est recommandé de faire des copies de contenu avant de commencer le processus de désinstallation.  
  
## Désinstaller en mode SharePoint  
 Lorsque vous désinstallez le mode SharePoint de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , les éléments suivants sont supprimés :  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et proxy de service.  
  
-   fichiers utilisés pour l'installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Les applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ne sont pas supprimées. Si vous ne souhaitez plus utiliser les applications de service, supprimez-les à l'aide de Windows PowerShell ou de l'Administration centrale de SharePoint.  
  
 Les éléments de rapport et les métadonnées associées ne sont pas supprimés. Ces informations sont contenues dans les bases de données de contenu et de configuration liées aux applications de service [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Les bases de données ne sont pas supprimées. Migrez-les manuellement vers une autre installation de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode SharePoint. Toutefois, si vous ne voulez plus des informations, vous devez supprimer ces bases de données. Pour plus d'informations, consultez [Upgrade and Migrate Reporting Services](../../reporting-services/install-windows/upgrade-and-migrate-reporting-services.md).  
  
 Voici des exemples de noms des trois bases de données [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui ne sont pas supprimées.  
  
-   **Base de données du serveur de rapports :** ReportingService_7f616e2d253040e8ab5653b3c09a065e  
  
-   **Base de données temporaire du serveur de rapports :** ReportingService_7f616e2d253040e8ab5653b3c09a065eTempDB  
  
-   **Base de données des alertes du serveur de rapports :** ReportingService_7f616e2d253040e8ab5653b3c09a065e_Alerting  
  
### Désinstallez le complément pour les produits SharePoint.  
 Lorsque vous désinstallez le complément sur un ordinateur, vous pouvez choisir de désinstaller uniquement les fichiers ou de supprimer également la fonctionnalité [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] de la batterie de serveurs. Pour plus d’informations sur la désinstallation du complément [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] pour les produits SharePoint, consultez [Installer ou désinstaller le complément Reporting Services pour SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md).  
  
## Désinstaller en mode natif  
 Lorsque vous désinstallez en mode natif [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , tout ce qui **a été créé** ou **modifié** après l'installation est laissé en place. Par exemple, les fichiers de base de données, les fichiers journaux, les fichiers de configuration [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] et les éléments de contenu tels que des rapports et des fichiers de source de données.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] est une fonctionnalité d'instance et par conséquent, elle n'est pas répertoriée dans le Panneau de configuration Windows sous Programmes et fonctionnalités. Pour désinstaller [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] en mode natif :  
  
1.  Dans le Panneau de configuration Windows, cliquez sur **Programmes et fonctionnalités**.  
  
2.  Dans **Programmes et fonctionnalités** , sélectionnez **Microsoft SQL Server 2012**.  
  
3.  Dans l'Assistant Désinstallation, sélectionnez l'instance qui inclut la fonctionnalité d'instance [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **RS**.  
  
     ![rs_nativemode_uninstall_selectinstance](../../sql-server/install/media/rs-nativemode-uninstall-selectinstance.gif "rs_nativemode_uninstall_selectinstance")  
  
4.  Après avoir sélectionné l'instance, sélectionnez la fonctionnalité [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
     ![rs_nativemode_uninstall_selectfeatures](../../sql-server/install/media/rs-nativemode-uninstall-selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")  
  
5.  Terminez l'Assistant.  
  
## Voir aussi  
 [Désinstaller une instance existante de SQL Server &#40;programme d’installation&#41;](../../sql-server/install/uninstall-an-existing-instance-of-sql-server-setup.md)   
 [Installer ou désinstaller le complément Power Pivot pour SharePoint &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md)   
 [Installer ou désinstaller le complément Reporting Services pour SharePoint](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  