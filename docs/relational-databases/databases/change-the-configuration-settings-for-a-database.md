---
title: "Modifier les param&#232;tres de configuration d&#39;une base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "configuration d'une base de données [SQL Server]"
  - "options de configuration [SQL Server], bases de données"
  - "modification des paramètres de configuration d'une base de données"
ms.assetid: c29c3385-5043-400f-bb4e-044a4c9a9a4b
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Modifier les param&#232;tres de configuration d&#39;une base de donn&#233;es
  Cette rubrique explique comment modifier les options de base de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Ces options sont spécifiques à chaque base de données et n'affectent pas les autres.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour modifier les paramètres d'option d'une base de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Seuls l’administrateur système, le propriétaire de la base de données, les membres des rôles serveur fixes **sysadmin** et **dbcreator** et des rôles de base de données fixes **db_owner** peuvent modifier ces options.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l'autorisation ALTER sur la base de données.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour modifier les paramètres d'option d'une base de données  
  
1.  Dans l’Explorateur d’objets, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)], développez le serveur, puis **Bases de données**, cliquez avec le bouton droit sur une base de données, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Propriétés de la base de données** , cliquez sur **Options** pour accéder à la plupart des paramètres de configuration. Les configurations de fichiers et de groupes de fichiers, la mise en miroir et la copie des journaux de transactions sont sur leurs pages respectives.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour modifier les paramètres d'option d'une base de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple définit les options de mode de récupération et de vérification de pages de données pour l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
 [!code-sql[DatabaseDDL#AlterDatabase7](../../relational-databases/databases/codesnippet/tsql/change-the-configuration_1.sql)]  
  
 Pour plus d’exemples, consultez [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md).  
  
## Voir aussi  
 [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Compatibility%20Level%20\(Transact-SQL\).md)   
 [Mise en miroir de bases de données ALTER DATABASE &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20Database%20Mirroring%20\(Transact-SQL\).md)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20HADR%20\(Transact-SQL\).md)   
 [Modifier le nom d'une base de données](../../relational-databases/databases/rename-a-database.md)   
 [Réduire une base de données](../../relational-databases/databases/shrink-a-database.md)  
  
  