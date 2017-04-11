---
title: "R&#233;f&#233;rence de l&#39;interface utilisateur de l&#39;Assistant Configuration de package | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.configwizard.finishdtsconfiguration.f1"
  - "sql13.dts.configwizard.selectobjects.f1"
  - "sql13.dts.configwizard.selecconfigtype.f1"
  - "sql13.dts.configwizard.welcome.f1"
ms.assetid: adca6938-6d5a-40ec-950e-dceb79d044fe
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# R&#233;f&#233;rence de l&#39;interface utilisateur de l&#39;Assistant Configuration de package
  **L’Assistant Configuration de package** vous permet de créer des configurations chargées de mettre à jour les propriétés d’un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ainsi que les objets qui s’y rattachent au moment de l’exécution. Cet Assistant s’exécute quand vous ajoutez une nouvelle configuration ou modifiez une configuration existante dans la boîte de dialogue **Bibliothèque des configurations du package**. Pour ouvrir la boîte de dialogue **Bibliothèque des configurations du package**, sélectionnez **Configurations du package** dans le menu **SSIS** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations, consultez [Créer des configurations de package](../../integration-services/packages/create-package-configurations.md).  
  
> **REMARQUE :** des configurations sont disponibles pour le modèle de déploiement de package. Les paramètres sont utilisés à la place des configurations pour le modèle de déploiement de projet. Le modèle de déploiement de projet vous permet de déployer des projets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Pour plus d'informations sur les modèles de déploiement, consultez [Deployment of Projects and Packages](https://msdn.microsoft.com/library/hh213290.aspx).  
  
 Les sections suivantes décrivent les pages de l'Assistant.  
  
## Page Assistant Configuration de package  
 **L’Assistant de configuration de SSIS** vous permet de créer des configurations chargées de mettre à jour les propriétés d’un package ainsi que les objets qui s’y rattachent au moment de l’exécution du programme.  
  
### Options  
 **Ne plus afficher cette page**  
 Option permettant d'ignorer cette page d'accueil la prochaine fois que vous ouvrez l'Assistant.  
  
 **Suivant**  
 Permet de passer à la page suivante de l’Assistant.  
  
## Page Sélectionner le type de configuration  
 La page **Sélectionner le type de configuration** permet de spécifier le type de configuration à créer.  
  
 Si vous souhaitez obtenir des informations supplémentaires pour déterminer quel type de configuration utiliser, consultez [Configurations de package](../../integration-services/packages/package-configurations.md).  
  
### Options statiques  
 **Type de configuration**  
 Sélectionnez le type de source dans lequel stocker la configuration, à l'aide des options suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Fichier de configuration XML**|Stocke la configuration sous forme de fichier XML. Si cette valeur est sélectionnée, les options dynamiques s’affichent dans la section **Type de configuration**.|  
|**Variable d'environnement**|Stocke la configuration dans une des variables d'environnement. Si cette valeur est sélectionnée, les options dynamiques s’affichent dans la section **Type de configuration**.|  
|**Entrée de Registre**|Stocke la configuration dans le Registre. Si cette valeur est sélectionnée, les options dynamiques s’affichent dans la section **Type de configuration**.|  
|**Variable de package parent**|Stocke la configuration en tant que variable dans le package qui contient la tâche.  Si cette valeur est sélectionnée, les options dynamiques s’affichent dans la section **Type de configuration**.|  
|**SQL Server**|Stocke la configuration dans une table de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si cette valeur est sélectionnée, les options dynamiques s’affichent dans la section **Type de configuration**.|  
  
 **Suivant**  
 Affiche la page suivante de l'Assistant.  
  
### Options dynamiques  
  
#### Option Type de configuration = Fichier de configuration XML  
 **Spécifier directement les paramètres de configuration**  
 Permet de spécifier directement les paramètres.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Nom du fichier de configuration**|Tapez le chemin d'accès du fichier de configuration généré par l'Assistant.|  
|**Parcourir**|La boîte de dialogue **Sélectionner l’emplacement du fichier de configuration** permet de spécifier le chemin d’accès au fichier de configuration généré par l’Assistant. Si le fichier n'existe pas, l'Assistant le crée.|  
  
 **L'emplacement de la configuration est stocké dans une variable d'environnement**  
 Permet de spécifier la variable d’environnement dans laquelle stocker la configuration.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Variable d'environnement**|Permet de sélectionner une variable d'environnement dans la liste.|  
  
#### Option Type de configuration = Variable d'environnement  
 **Variable d'environnement**  
 Permet de sélectionner la variable d'environnement qui contient les informations de configuration.  
  
#### Option Type de configuration = Entrée de Registre  
 **Spécifier directement les paramètres de configuration**  
 Permet de spécifier directement les paramètres.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Entrée de Registre**|Tapez la clé de Registre qui contient les informations de configuration. Le format est \<clé de Registre>.<br /><br /> La clé de Registre doit déjà exister dans HKEY_CURRENT_USER et porter une valeur nommée Value. Cette valeur peut être de type DWORD ou une chaîne.<br /><br /> Pour utiliser une clé de Registre qui ne se trouve pas à la racine de HKEY_CURRENT_USER, recourez au format \<clé de Registre\clé de Registre\\...> pour identifier la clé.|  
  
 **L'emplacement de la configuration est stocké dans une variable d'environnement**  
 Permet de spécifier la variable d’environnement dans laquelle stocker la configuration.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Variable d'environnement**|Permet de sélectionner une variable d'environnement dans la liste.|  
  
#### Option Type de configuration = Variable de package parent  
 **Spécifier directement les paramètres de configuration**  
 Permet de spécifier directement les paramètres.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Variable parent**|Permet de spécifier la variable dans le package parent qui contient les informations de configuration.|  
  
 **L'emplacement de la configuration est stocké dans une variable d'environnement**  
 Permet de spécifier la variable d’environnement dans laquelle stocker la configuration.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Variable d'environnement**|Permet de sélectionner une variable d'environnement dans la liste.|  
  
#### Options Type de configuration = SQL Server  
 **Spécifier directement les paramètres de configuration**  
 Permet de spécifier directement les paramètres.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Connexion**|Permet de sélectionner une connexion dans la liste ou de cliquer sur **Nouvelle** pour créer une connexion.|  
|**Table de configuration**|Permet de sélectionner une table existante ou de cliquer sur **Nouvelle** pour écrire une instruction SQL qui crée une table.|  
|**Filtre de la configuration**|Permet de sélectionner le nom d'une configuration existante ou de taper un nouveau nom.<br /><br /> Un grand nombre de configurations SQL Server peuvent être stockées dans la même table et chacune d'entre elles peut inclure plusieurs éléments de configuration.<br /><br /> La valeur définie par l'utilisateur est stockée dans la table pour identifier les éléments de configuration qui appartiennent à une configuration particulière.|  
  
 **L'emplacement de la configuration est stocké dans une variable d'environnement**  
 Permet de spécifier la variable d'environnement dans laquelle stocker la configuration.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Variable d'environnement**|Permet de sélectionner une variable d'environnement dans la liste.|  
  
## Page Sélectionner des objets à exporter  
 Utilisez la page **Sélectionner la propriété cible ou Sélectionner les propriétés à exporter** pour définir les propriétés des objets que contient la configuration. La sélection de plusieurs propriétés n'est possible que si vous sélectionnez le type de configuration XML.  
  
### Options  
 **Objets**  
 Développe la hiérarchie du package et sélectionne les propriétés à exporter.  
  
 **Attributs de la propriété**  
 Affiche les attributs d'une propriété.  
  
 **Suivant**  
 Permet de passer à la page suivante de l'Assistant.  
  
## Page Fin de l’Assistant  
 Utilisez la page **Fin de l’Assistant** pour nommer les paramètres de configuration et d’affichage utilisés par l’Assistant pour créer la configuration. Quand l’Assistant est terminé, la **Bibliothèque des configurations du package** affiche la liste de toutes les configurations du package.  
  
### Options  
 **Nom de la configuration**  
 Tapez le nom de la configuration.  
  
 **Aperçu**  
 Affiche les paramètres utilisés par l'Assistant pour créer la configuration.  
  
 **Terminer**  
 Crée la configuration et quitte **l’Assistant Configuration de package**.  
  
## Voir aussi  
 [Créer des configurations de package](../../integration-services/packages/create-package-configurations.md)  
  
  