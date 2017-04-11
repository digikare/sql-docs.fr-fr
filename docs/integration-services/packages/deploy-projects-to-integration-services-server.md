---
title: "D&#233;ployer des projets sur le serveur Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/06/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e9402f4-4d50-49ff-820d-65a77829c4a5
caps.latest.revision: 22
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 22
---
# D&#233;ployer des projets sur le serveur Integration Services
  Dans la version actuelle d’[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez déployer vos projets sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] vous permet de gérer les packages, d'exécuter les packages et de configurer les valeurs d'exécution des packages à l'aide d'environnements.  
  
 Pour plus d’informations sur les environnements, consultez [Créer et mapper un environnement serveur](../../integration-services/packages/create-and-map-a-server-environment.md).  
  
> [!NOTE]  
>  À l’instar des versions antérieures d’[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], la version actuelle vous permet aussi de déployer vos packages sur une instance de SQL Server et d’utiliser le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] pour exécuter et gérer les packages. Utilisez le modèle de déploiement de package. Pour plus d’informations, consultez [Déploiement de packages hérités &#40;SSIS&#41;](../../integration-services/packages/legacy-package-deployment-ssis.md).  
  
 Pour déployer un projet sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], effectuez les tâches suivantes :  
  
1.  Créez un catalogue SSISDB, si vous ne l'avez pas encore fait. Pour plus d’informations, consultez [Créer le catalogue SSIS](../../integration-services/service/create-the-ssis-catalog.md).  
  
2.  Convertissez le projet en modèle de déploiement de projet en exécutant **l’Assistant Conversion de projet Integration Services**. Pour plus d’informations, consultez les instructions ci-dessous : [Pour convertir un projet en modèle de déploiement de projet](#convert).  
  
    -   Si vous avez créé le projet dans [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)], par défaut, le projet utilise le modèle de déploiement de projet.  
  
    -   Si vous avez créé le projet dans une version précédente de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], après avoir ouvert le fichier projet dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], convertissez le projet en modèle de déploiement de projet.  
  
        > [!NOTE]  
        >  Si le projet contient une ou plusieurs sources de données, les sources de données sont supprimées à l’issue de la conversion du projet. Pour créer une connexion à une source de données que les packages du projet peuvent partager, ajoutez un gestionnaire de connexions au niveau du projet. Pour plus d’informations, consultez [Ajouter, supprimer ou partager un gestionnaire de connexions dans un package](../Topic/Add,%20Delete,%20or%20Share%20a%20Connection%20Manager%20in%20a%20Package.md).  
  
         Selon que vous exécutez **l’Assistant Conversion de projet Integration Services** à partir de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], l’Assistant effectue différentes tâches de conversion.  
  
        -   Si vous exécutez l'Assistant à partir de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], les packages contenus dans le projet sont convertis de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 2005, 2008 ou 2008 R2 vers le format utilisé par la version en cours de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Les fichiers du projet d'origine (.dtproj) et de package (.dtsx) sont mis à niveau.  
  
        -   Si vous exécutez l’Assistant à partir de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], l’Assistant génère un fichier de déploiement de projet (.ispac) à partir des packages et des configurations contenus dans le projet. Les fichiers de package d'origine (.dtsx) ne sont pas mis à niveau.  
  
             Vous pouvez sélectionner un fichier existant ou en créer un dans la page **Destination de la sélection** de l’Assistant.  
  
             Pour mettre à niveau des fichiers de package pendant la conversion d’un projet, exécutez **l’Assistant Conversion de projet Integration Services** à partir de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Pour mettre à niveau des fichiers de package en dehors d’une conversion de projet, exécutez **l’Assistant Conversion de projet Integration Services** à partir de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], puis exécutez **l’Assistant Mise à niveau de packages SSIS**. Si vous mettez à niveau les fichiers de package séparément, assurez-vous d'enregistrer les modifications. À défaut, lorsque vous convertissez le projet en modèle de déploiement de projet, les modifications non enregistrées dans le package ne sont pas converties.  
  
     Pour plus d’informations sur la mise à niveau des packages, consultez [Mettre à niveau des packages Integration Services](../../integration-services/install-windows/upgrade-integration-services-packages.md) et [Mettre à niveau des packages Integration Services à l’aide de l’Assistant Mise à niveau de packages SSIS](../../integration-services/install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).  
  
3.  Déployez le projet sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Pour plus d’informations, consultez les instructions ci-dessous : [Pour déployer un projet sur le serveur Integration Services](#deploy).  
  
4.  (Facultatif) Créez un environnement pour le projet déployé. Pour plus d’informations, consultez [Créer et mapper un environnement serveur](../../integration-services/packages/create-and-map-a-server-environment.md).  
  
##  <a name="convert"></a> Pour convertir un projet en modèle de déploiement de projet  
  
1.  Ouvrez le projet dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] puis, dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et cliquez sur **Convertir en modèle de déploiement de projet**.  
  
     -ou-  
  
     Dans l’Explorateur d’objets de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], cliquez avec le bouton droit sur le nœud **Projets** et sélectionnez **Importer les packages**.  
  
2.  Terminez l'Assistant. Pour plus d’informations, consultez [Assistant Conversion de projet Integration Services](../../integration-services/packages/integration-services-project-conversion-wizard.md).  
  
##  <a name="deploy"></a> Pour déployer un projet sur le serveur Integration Services  
  
1.  Ouvrez le projet dans [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] puis, dans le menu **Projet**, sélectionnez **Déployer** pour lancer **l’Assistant Déploiement d’Integration Services**.  
  
     -ou-  
  
     Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], développez le nœud [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] > **SSISDB** dans l’Explorateur d’objets, puis recherchez le dossier du projet que vous souhaitez déployer. Cliquez avec le bouton droit sur le dossier des **projets**, puis cliquez sur **Déployer le projet**.  
  
     -ou-  
  
     À l’invite de commandes, exécutez **isdeploymentwizard.exe** à partir de **%ProgramFiles%\Microsoft SQL Server\110\DTS\Binn**. Sur les ordinateurs 64 bits, il existe aussi une version 32 bits de l’outil dans **%ProgramFiles(x86)%\Microsoft SQL Server\100\DTS\Binn**.  
  
2.  Dans la page **Sélectionner une source**, cliquez sur **Fichier de déploiement de projet** pour sélectionner le fichier de déploiement du projet.  
  
     -OU-  
  
     Cliquez sur **Catalogue Integration Services** pour sélectionner un projet qui a déjà été déployé dans le catalogue SSISDB.  
  
3.  Terminez l'Assistant. Pour plus d’informations, consultez [Assistant Déploiement d’Integration Services](../../integration-services/packages/integration-services-deployment-wizard.md).  
  
  