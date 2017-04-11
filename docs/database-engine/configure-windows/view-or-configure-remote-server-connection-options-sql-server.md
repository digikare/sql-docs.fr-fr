---
title: "Afficher ou configurer des options de connexion au serveur distant (SQL Server) | Microsoft Docs"
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
  - "serveurs distants [SQL Server], options de connexion"
  - "serveurs [SQL Server], distants"
  - "connexions [SQL Server], serveurs distants"
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Afficher ou configurer des options de connexion au serveur distant (SQL Server)
  Cette rubrique explique comment afficher ou configurer des options de connexion au serveur distant au niveau du serveur dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher ou configurer des options de connexion au serveur distant, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré des options de connexion au serveur distant](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 L’exécution de **sp_serveroption** nécessite l’autorisation ALTER ANY LINKED SERVER sur le serveur.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour afficher ou configurer des options de connexion au serveur distant  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Propriétés de SQL Server - \<***nom_serveur***>**, cliquez sur **Connexions**.  
  
3.  Sur la page **Connexions** , vérifiez les paramètres **Connexions au serveur distant** et au besoin modifiez-les.  
  
4.  Répétez les étapes 1 à 3 sur l'autre serveur de la paire de serveurs distants.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour afficher les options de connexion au serveur distant  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise [sp_helpserver](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md) pour retourner des informations sur tous les serveurs distants.  
  
```tsql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### Pour configurer des options de connexion au serveur distant  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_serveroption](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md) pour configurer un serveur distant. Cet exemple configure un serveur distant correspondant à une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3`, de façon à ce qu'il soit compatible avec le classement de l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```tsql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré des options de connexion au serveur distant  
 Le serveur distant doit être arrêté et redémarré pour que le paramètre puisse prendre effet.  
  
## Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Serveurs distants](../../database-engine/configure-windows/remote-servers.md)   
 [Serveurs liés &#40;moteur de base de données&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_serveroption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)  
  
  