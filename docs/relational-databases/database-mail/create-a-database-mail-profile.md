---
title: "Cr&#233;er un profil de messagerie de base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "08/01/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "messagerie de base de données [SQL Server], profils publics"
  - "profils [SQL Server], messagerie de base de données"
  - "profils publics [messagerie de base de données]"
ms.assetid: 58ae749d-6ada-4f9c-bf00-de7c7a992a2d
caps.latest.revision: 34
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 34
---
# Cr&#233;er un profil de messagerie de base de donn&#233;es
  Utilisez l' **Assistant Configuration de la messagerie de base de données** ou [!INCLUDE[tsql](../../includes/tsql-md.md)] pour créer des profils privés et publics de messagerie de base de données. Pour plus d’informations sur les profils de messagerie, consultez [Profil de messagerie de base de données](https://msdn.microsoft.com/library/ms175100.aspx#Anchor_2).
  
-   **Avant de commencer :** [Configuration requise](#Prerequisites), [Sécurité](#Security)  
  
-   **Pour créer un profil privé de messagerie de base de données en utilisant :**  [Assistant Configuration de la messagerie de base de données](#SSMSProcedure), [Transact-SQL](#PrivateProfile)  
  
-   **Pour créer un profil public de messagerie de base de données en utilisant :**  [Assistant Configuration de la messagerie de base de données](#SSMSProcedure), [Transact-SQL](#PublicProfile)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Configuration requise  
 Créez un ou plusieurs comptes de messagerie de base de données pour le profil. Pour plus d’informations sur la création de comptes de messagerie de base de données, consultez [Créer un compte de messagerie de base de données](../../relational-databases/database-mail/create-a-database-mail-account.md).  
  
###  <a name="Security"></a> Sécurité  
 Un profil public permet à tout utilisateur ayant accès à la base de données **msdb** d’envoyer des e-mails à l’aide de ce profil. Un profil privé peut être utilisé par un utilisateur ou par un rôle. Accorder l'accès de rôles aux profils permet de créer une architecture plus facile à maintenir. Pour envoyer du courrier, vous devez être membre du rôle **DatabaseMailUserRole** de la base de données **msdb** et disposer d'au moins un accès à un profil de messagerie de base de données.  
  
####  <a name="Permissions"></a> Autorisations  
 L'utilisateur qui crée les comptes de profils et exécute des procédures stockées doit être membre du rôle serveur fixe sysadmin.  
  
##  <a name="SSMSProcedure"></a> Utilisation de l'Assistant Configuration de la messagerie de base de données  
 **Pour créer un profil de messagerie de base de données**  
  
-   Dans l'Explorateur d'objets, connectez-vous à l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sur laquelle vous voulez configurer la messagerie de base de données, puis développez l'arborescence du serveur.  
  
-   Développez le nœud **Gestion** .  
  
-   Double-cliquez sur Messagerie de base de données pour ouvrir l'Assistant Configuration de la messagerie de base de données.  
  
-   Dans la page **Sélectionner une tâche de configuration** , sélectionnez l'option **Gérer les comptes et les profils de messagerie de base de données** , puis cliquez sur **Suivant**.  
  
-   Dans la page **Gérer les profils et les comptes** , sélectionnez l'option **Créer un nouveau profil** , puis cliquez sur **Suivant**.  
  
-   Dans la page **Nouveau profil** , spécifiez le nom de profil et la description, et ajoutez des comptes à inclure dans le profil, puis cliquez sur **Suivant**.  
  
-   Dans la page **Terminer l'Assistant** , examinez les actions à exécuter, puis cliquez sur **Terminer** pour terminer la création du nouveau profil.  
  
-   **Pour configurer un profil privé de messagerie de base de données :**  
  
    -   Ouvrez l'Assistant Configuration de la messagerie de base de données.  
  
    -   Dans la page **Sélectionner une tâche de configuration** , sélectionnez l'option **Gérer les comptes et les profils de messagerie de base de données** , puis cliquez sur **Suivant**.  
  
    -   Dans la page **Gérer les profils et les comptes** , sélectionnez l'option **Gérer la sécurité des profils** , puis cliquez sur **Suivant**.  
  
    -   Sous l'onglet **Profils privés** , activez la case à cocher du profil que vous souhaitez configurer et cliquez sur **Suivant**.  
  
    -   Dans la page **Terminer l'Assistant** , examinez les actions à exécuter, puis cliquez sur **Terminer** pour terminer la configuration du profil.  
  
-   **Pour configurer un profil public de messagerie de base de données :**  
  
    -   Ouvrez l'Assistant Configuration de la messagerie de base de données.  
  
    -   Dans la page **Sélectionner une tâche de configuration** , sélectionnez l'option **Gérer les comptes et les profils de messagerie de base de données** , puis cliquez sur **Suivant**.  
  
    -   Dans la page **Gérer les profils et les comptes** , sélectionnez l'option **Gérer la sécurité des profils** , puis cliquez sur **Suivant**.  
  
    -   Sous l'onglet **Profils publics** , activez la case à cocher du profil que vous souhaitez configurer et cliquez sur **Suivant**.  
  
    -   Dans la page **Terminer l'Assistant** , examinez les actions à exécuter, puis cliquez sur **Terminer** pour terminer la configuration du profil.  
  
## Utilisation de Transact-SQL  
  
###  <a name="PrivateProfile"></a> Pour créer un profil privé de messagerie de base de données  
  
-   Connectez-vous à l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Pour créer un profil, exécutez la procédure stockée système [sysmail_add_profile_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql.md) comme suit :  
  
     **EXECUTEmsdb.dbo.sysmail_add_profile_sp**  
  
     *@profile_name* = '*nom_de_profil*'  
  
     *@description* = '*description*'  
  
     où *@profile_name* est le nom du profil, et *@description* est la description du profil. Ce paramètre est facultatif.  
  
-   Pour chaque compte, exécutez la procédure stockée [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql.md) comme suit :  
  
     **EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**  
  
     *@profile_name* = '*nom_de_profil*'  
  
     *@account_name* = '*nom_de_compte*'  
  
     *@sequence_number* = '*numéro_de_séquence_du_compte_dans_le_profil* '  
  
     où *@profile_name* est le nom du profil, *@account_name* est le nom du compte à ajouter au profil, et *@sequence_number* détermine l’ordre dans lequel les comptes sont utilisés dans le profil.  
  
-   Octroyez une autorisation d'accès au profil à chaque rôle de base de données ou à chaque utilisateur qui enverra des messages électroniques via ce profil. Pour ce faire, exécutez la procédure stockée [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql.md) comme suit :  
  
     **EXECUTEmsdb.sysmail_add_principalprofile_sp**  
  
     *@profile_name* = ’*nom_de_profil*’  
  
     *@ principal_name* = ’*nom_de_l’utilisateur_de_base_de_données_ou_rôle*’  
  
     *@is_default* = ’*état_du_profil_par_défaut*’  
  
     où *@profile_name* est le nom du profil, *@principal_name* est le nom du rôle ou de l’utilisateur de base de données, et *@is_default* détermine si ce profil est ou non le paramètre par défaut pour le rôle ou l’utilisateur de base de données.  
  
 L'exemple suivant crée un compte et un profil privé de messagerie de base de données, puis ajoute le compte au profil et octroie au rôle de base de données **DBMailUsers** dans la base de données **msdb** l'accès à ce profil.  
  
```  
-- Create a Database Mail account  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @replyto_address = 'danw@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
  
-- Create a Database Mail profile  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @description = 'Profile used for administrative mail.' ;  
  
-- Add the account to the profile  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @account_name = 'AdventureWorks Administrator',  
    @sequence_number =1 ;  
  
-- Grant access to the profile to the DBMailUsers role  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @principal_name = 'ApplicationUser',  
    @is_default = 1 ;  
```  
  
###  <a name="PublicProfile"></a> Pour créer un profil public de messagerie de base de données  
  
-   Connectez-vous à l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Pour créer un profil, exécutez la procédure stockée système [sysmail_add_profile_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql.md) comme suit :  
  
     **EXECUTEmsdb.dbo.sysmail_add_profile_sp**  
  
     *@profile_name* = '*nom_de_profil*'  
  
     *@description* = '*description*'  
  
     où *@profile_name* est le nom du profil, et *@description* est la description du profil. Ce paramètre est facultatif.  
  
-   Pour chaque compte, exécutez la procédure stockée [sysmail_add_profileaccount_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql.md) comme suit :  
  
     **EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**  
  
     *@profile_name* = '*nom_de_profil*'  
  
     *@account_name* = '*nom_de_compte*'  
  
     *@sequence_number* = '*numéro_de_séquence_du_compte_dans_le_profil* '  
  
     où *@profile_name* est le nom du profil, *@account_name* est le nom du compte à ajouter au profil, et *@sequence_number* détermine l’ordre dans lequel les comptes sont utilisés dans le profil.  
  
-   Pour accorder un accès public, exécutez la procédure stockée [sysmail_add_principalprofile_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql.md) comme suit :  
  
     **EXECUTEmsdb.sysmail_add_principalprofile_sp**  
  
     *@profile_name* = '*nom_de_profil*'  
  
     *@ principal_name* = '**public** ou **0**'  
  
     *@is_default* = '*état_du_profil_par_défaut*'  
  
     où *@profile_name* est le nom du profil, *@principal_name* indique s’il s’agit d’un profil public, et *@is_default* détermine si ce profil est ou non le paramètre par défaut pour le rôle ou l’utilisateur de base de données.  
  
 L'exemple suivant crée un compte et un profil privé de messagerie de base de données, puis ajoute le compte au profil et octroie l'accès public au profil.  
  
```  
-- Create a Database Mail account  
  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Public Account',  
    @description = 'Mail account for use by all database users.',  
    @email_address = 'db_users@Adventure-Works.com',  
    @replyto_address = 'danw@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
  
-- Create a Database Mail profile  
  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @description = 'Profile used for administrative mail.' ;  
  
-- Add the account to the profile  
  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @account_name = 'AdventureWorks Public Account',  
    @sequence_number =1 ;  
  
-- Grant access to the profile to all users in the msdb database  
  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @principal_name = 'public',  
    @is_default = 1 ;  
```  
  
  