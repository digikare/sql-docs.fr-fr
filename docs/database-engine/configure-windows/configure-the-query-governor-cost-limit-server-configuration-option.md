---
title: "Configurer l&#39;option de configuration du serveur Limite de co&#251;t de l&#39;Administrateur de requ&#234;tes | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "requêtes [SQL Server], temps d'exécution"
  - "limite de coût de l'Administrateur de requêtes (option) [SQL Server]"
  - "temps [SQL Server], temps d'exécution de requête"
ms.assetid: e7b8f084-1052-4133-959b-cebf4add790f
caps.latest.revision: 28
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 28
---
# Configurer l&#39;option de configuration du serveur Limite de co&#251;t de l&#39;Administrateur de requ&#234;tes
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette rubrique explique comment configurer l'option de configuration de serveur **Limite de coût de l'Administrateur de requêtes** dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. L’option de limite de coût de l’Administrateur de requêtes spécifie une limite supérieure de durée d’exécution d’une requête. Le coût d'une requête correspond à la durée (en secondes) estimée nécessaire à l'exécution complète d'une requête dans une configuration matérielle donnée. La valeur par défaut de cette option est 0, laquelle désactive l'Administrateur de requêtes. Cela permet l'exécution de toutes les requêtes sans limitation de temps. Si vous spécifiez une valeur positive et différente de zéro, l'Administrateur de requêtes n'autorise pas l'exécution de requêtes dont le coût estimé excède cette valeur.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour configurer l'option Limite de coût de l'Administrateur de requêtes, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré l'option Limite de coût de l'Administrateur de requêtes](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Cette option avancée ne doit être modifiée que par un administrateur de base de données qualifié ou un technicien agréé [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Pour modifier la valeur de l’option Limite de coût de l’Administrateur de requêtes pour chaque connexion, utilisez l’instruction [SET QUERY_GOVERNOR_COST_LIMIT](../../t-sql/statements/set-query-governor-cost-limit-transact-sql.md).  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Les autorisations d’exécution de **sp_configure**, sans paramètre ou avec le premier paramètre uniquement, sont accordées par défaut à tous les utilisateurs. Pour exécuter **sp_configure** avec les deux paramètres afin de modifier une option de configuration ou d’exécuter l’instruction RECONFIGURE, un utilisateur doit disposer de l’autorisation de niveau serveur ALTER SETTINGS. L'autorisation ALTER SETTINGS est implicitement détenue par les rôles serveur fixes **sysadmin** et **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour configurer l'option Limite de coût de l'Administrateur de requêtes  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur et sélectionnez **Propriétés**.  
  
2.  Cliquez sur la page **Connexions** .  
  
3.  Cochez ou décochez la case **Utiliser l’Administrateur de requêtes pour empêcher les requêtes longues**.  
  
     Si vous activez cette case à cocher, spécifiez dans la zone située en-dessous une valeur positive, que l'Administrateur de requêtes utilise pour interdire l'exécution de toutes les requêtes dont la durée d'exécution dépasse cette valeur.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour configurer l'option Limite de coût de l'Administrateur de requêtes  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) pour attribuer à l’option `query governor cost limit` une valeur de `120` secondes.  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'query governor cost limit', 120 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Pour plus d’informations, consultez [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré l'option Limite de coût de l'Administrateur de requêtes  
 Le paramètre prend effet immédiatement sans redémarrage du serveur.  
  
## Voir aussi  
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [SET QUERY_GOVERNOR_COST_LIMIT &#40;Transact-SQL&#41;](../../t-sql/statements/set-query-governor-cost-limit-transact-sql.md)   
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  