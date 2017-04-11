---
title: "Applet de commande&#160;PowerShell pour l’&#233;valuation de la migration | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 117250d3-9982-47fe-94fd-6f29f6159940
caps.latest.revision: 5
author: "MightyPen"
ms.author: "genemi"
manager: "jhubbard"
caps.handback.revision: 5
---
# Applet de commande&#160;PowerShell pour l’&#233;valuation de la migration
  L’applet de commande Save-SqlMigrationReport est un outil qui évalue l’aptitude à la migration de plusieurs objets dans une base de données SQL Server. Actuellement, elle se limite à l’évaluation de cette aptitude pour la fonction OLTP en mémoire. Cette applet peut être exécutée dans des environnements Windows PowerShell avec élévation des privilèges et sqlps.  
  
## Syntaxe  
  
```powershell  
Save-SqlMigrationReport [ -MigrationType OLTP ] [ -Server server -Database database [ -Object object_name ] ]  |  [ -InputObject smo_object ] -FolderPath path  
```  
  
#### Paramètres  
 Les paramètres sont décrits dans le tableau suivant.  
  
|Paramètres|Description|  
|----------------|-----------------|  
|MigrationType|Type de scénario de migration ciblé par l’applet de commande. Actuellement, la seule valeur correspond au système OLTP par défaut. Ce paramètre est facultatif.|  
|Server|Nom de l’instance SQL Server cible. Obligatoire dans l’environnement Windows Powershell lorsque le paramètre -InputObject n’est pas fourni. Facultatif dans SQLPS.|  
|Base de données|Nom de la base de données SQL Server cible. Obligatoire dans l’environnement Windows Powershell lorsque le paramètre -InputObject n’est pas fourni. Facultatif dans SQLPS.|  
|Objet|Nom de l’objet de base de données cible. Il peut s’agir d’un tableau ou d’une procédure stockée.|  
|InputObject|L’objet SMO que l’applet de commande doit cibler. Obligatoire dans l’environnement Windows Powershell lorsque les paramètres -Server et -Database ne sont pas fournis. Facultatif dans SQLPS.|  
|FolderPath|Dossier dans lequel l’applet de commande doit déposer les rapports générés. Obligatoire.|  
  
## Résultats  
 Dans le dossier spécifié dans le paramètre - FolderPath, deux noms de dossier apparaissent : Tables et Stored Procedures. Si l’objet cible est une table, son rapport se trouve dans le dossier Tables. Dans le cas contraire, il figure dans le dossier Stored Procedures.  
  
  