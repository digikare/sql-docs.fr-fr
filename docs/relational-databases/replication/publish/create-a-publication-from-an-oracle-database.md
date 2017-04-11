---
title: "Cr&#233;er une publication &#224; partir d&#39;une base de donn&#233;es Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "publications [SQL Server replication], Oracle databases"
  - "publication Oracle [réplication SQL Server], configuration"
ms.assetid: b3812746-14b0-4b22-809e-b4a95e1c8083
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Cr&#233;er une publication &#224; partir d&#39;une base de donn&#233;es Oracle
  Cette rubrique explique comment créer une publication Oracle dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Conditions préalables](#Prerequisites)  
  
-   **Pour créer une publication à partir d'une base de données Oracle à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   Avant de créer une publication, vous devez installer le logiciel Oracle sur le serveur de distribution [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et configurer la base de données Oracle. Pour plus d’informations, consultez [configurer un serveur de publication Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Créez une publication transactionnelle ou d'instantané à partir d'une base de données Oracle à l'aide de l'Assistant Nouvelle publication.  
  
 La première fois que vous créez une publication à partir d'une base de données Oracle, vous devez identifier le serveur de publication Oracle sur le serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (ce ne sera plus nécessaire pour les publications suivantes effectuées à partir de la même base de données). Identifier le serveur de publication Oracle peut être effectuée à partir de l’Assistant Nouvelle Publication ou le **Propriétés du serveur de distribution - \< serveur de distribution>** boîte de dialogue ; cette rubrique montre les **Propriétés du serveur de distribution - \< distributeur>** boîte de dialogue.  
  
#### Pour identifier le serveur de publication Oracle sur le serveur de distribution SQL Server  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], connectez-vous à l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que le serveur de publication Oracle utilisera comme serveur de distribution puis développez le nœud du serveur.  
  
2.  Avec le bouton droit le **réplication** puis cliquez sur **des propriétés de serveur de distribution**.  
  
3.  Sur le **éditeurs** page de le **Propriétés du serveur de distribution - \< serveur de distribution>** boîte de dialogue, cliquez sur **Ajouter**, puis cliquez sur **Ajouter le serveur de publication Oracle**.  
  
4.  Dans la boîte de dialogue **Se connecter au serveur** , cliquez sur le bouton **Options** .  
  
5.  Dans l'onglet **Connexion** :  
  
    1.  Entrez le nom de l'instance de base de données Oracle ou sélectionnez **Parcourir** dans la zone de liste déroulante **Instance de serveur** .  
  
    2.  Sélectionnez **l’authentification Standard Oracle** (recommandé) ou **l’authentification Windows**.  
  
         Si vous sélectionnez **l’authentification Windows**: le serveur Oracle doit être configuré pour autoriser les connexions à l’aide des informations d’identification Windows (pour plus d’informations, consultez la documentation Oracle) et vous devez être actuellement connecté avec le même [!INCLUDE[msCoName](../../../includes/msconame-md.md)] compte Windows spécifié pour le schéma utilisateur administratif de réplication.  
  
    3.  Si vous sélectionnez **Authentification standard Oracle**, entrez le nom de connexion et le mot de passe du schéma utilisateur d'administration de réplication créé sur le serveur de publication Oracle pendant la configuration.  
  
6.  Dans l'onglet **Propriétés de la connexion** , sélectionnez un type de serveur de publication ( **Passerelle** ou **Complet**).  
  
     L’option **Complet** est conçue pour fournir des publications transactionnelles et d’instantané avec l’ensemble complet de fonctionnalités prises en charge pour la publication Oracle. L’option **Passerelle** fournit des optimisations de conception spécifiques pour améliorer les performances dans les cas où la réplication sert de passerelle entre les systèmes. L’option **Passerelle** ne peut pas être utilisée si vous avez l’intention de publier la même table dans plusieurs publications transactionnelles. Une table peut apparaître au maximum dans une publication transactionnelle et dans une ou plusieurs publications d'instantané si vous sélectionnez **Passerelle**.  
  
7.  Cliquez sur **Se connecter**, qui crée une connexion au serveur de publication Oracle et le configure pour la réplication. Le **se connecter au serveur** boîte de dialogue se ferme et vous revenez à la **des propriétés de serveur de distribution - \< serveur de distribution>** boîte de dialogue.  
  
    > [!NOTE]  
    >  En cas de problème lié à la configuration réseau, vous recevrez un message d'erreur à ce stade. Si vous rencontrez des difficultés pour vous connecter à la base de données Oracle, consultez la section « Connexion impossible du serveur de distribution SQL Server à l'instance de base de données Oracle » dans [Troubleshooting Oracle Publishers](../../../relational-databases/replication/non-sql/troubleshooting-oracle-publishers.md).  
  
8.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### Pour créer une publication à partir d'une base de données Oracle  
  
1.  Connectez-vous à l'instance [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que le serveur de publication Oracle utilisera comme serveur de distribution puis développez le nœud du serveur.  
  
2.  Développez le dossier **Réplication** .  
  
3.  Cliquez sur le **Publications locales** puis cliquez sur **nouvelle Publication Oracle**.  
  
4.  Dans la page **Serveur de publication Oracle** de l'Assistant Nouvelle publication, sélectionnez le serveur de publication Oracle. S'il ne s'affiche pas, cliquez sur **Ajouter un serveur de publication Oracle**, puis suivez les étapes décrites dans la procédure précédente.  
  
5.  Dans la page **Type de publication** , sélectionnez **Publication d'instantané** ou **Publication transactionnelle**.  
  
6.  Dans la page **Articles** , sélectionnez les objets de base de données à publier.  
  
     Retirez éventuellement des colonnes de table en développant une table et en désactivant la case à cocher d'une ou plusieurs colonnes. Cliquez sur **Propriétés de l'article** pour afficher et modifier les propriétés de l'article et spécifier, le cas échéant, d'autres mappages de types de données. Pour plus d’informations sur les mappages de type de données, consultez la page [spécifier des mappages de types de données pour un serveur de publication Oracle](../../../relational-databases/replication/publish/specify-data-type-mappings-for-an-oracle-publisher.md).  
  
7.  Dans la page **Filtrer les lignes de la table** , appliquez éventuellement des filtres pour publier un sous-ensemble de données d'une ou plusieurs tables.  
  
8.  Dans la page **Agent d'instantané** , désactivez **Créer un instantané immédiatement** uniquement si vous avez créé tous les objets et ajouté toutes les données requises dans la base de données d'abonnement.  
  
9. Sur le **sécurité de l’Agent** spécifiez les informations d’identification de l’Agent d’instantané (pour toutes les publications) et l’Agent de lecture du journal (pour les publications transactionnelles). Les Agents s'exécutent et se connectent au serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à l'aide du contexte du compte [!INCLUDE[msCoName](../../../includes/msconame-md.md)] spécifié. Les Agents se connectent à la base de données Oracle avec le contexte du compte spécifié comme schéma utilisateur d'administration de réplication. Pour plus d’informations, consultez [configurer un serveur de publication Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
     Pour plus d'informations sur les autorisations requises par chaque Agent, consultez [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) et [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md).  
  
10. Dans la page **Actions de l'Assistant** , créez éventuellement un script de la publication. Pour plus d’informations, consultez [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
11. Dans la page **Terminer l'Assistant** , spécifiez un nom pour la publication.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Une fois la base de données Oracle a été configuré comme serveur de publication, vous pouvez créer une publication transactionnelle ou de capture instantanée de la même manière que vous le feriez à partir un [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] serveur de publication, à l’aide du système de procédures stockées.  
  
#### Pour créer une publication Oracle  
  
1.  Configurez la base de données Oracle en tant que serveur de publication. Pour plus d’informations, consultez [configurer un serveur de publication Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
2.  S'il n'existe pas de serveur de distribution distant, configurez-en un. Pour plus d’informations, consultez [Configure Publishing and Distribution](../../../relational-databases/replication/configure-publishing-and-distribution.md).  
  
3.  Sur le serveur de distribution distant qui utilise le serveur de publication Oracle, exécutez [sp_adddistpublisher & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md). Spécifiez le nom de réseau TNS (Transparent Substrate) de l’instance de base de données Oracle pour **@publisher** et la valeur **ORACLE** ou **ORACLE GATEWAY** pour **@publisher_type**. `Specify` le mode de sécurité utilisé lors de la connexion entre le Serveur de publication Oracle et le serveur de distribution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] distant parmi les modes suivants :  
  
    -   Pour utiliser l’authentification Standard Oracle, la valeur par défaut, spécifiez la valeur **0** pour **@security_mode**, la connexion du schéma utilisateur administratif réplication créé sur le serveur de publication Oracle au cours de la configuration de **@login**, et le mot de passe **@password**.  
  
        > [!IMPORTANT]  
        >  Lorsque c'est possible, demande aux utilisateurs de fournir les informations d'identification au moment de l'exécution. Si vous stockez des informations d'identification dans un fichier de script, vous devez sécuriser le fichier pour empêcher tout accès non autorisé.  
  
    -   Pour utiliser l’authentification Windows, spécifiez la valeur **1** pour **@security_mode**.  
  
        > [!NOTE]  
        >  Pour utiliser l'authentification Windows, le serveur Oracle doit être configuré pour autoriser les connexions à l'aide des informations d'identification Windows (pour plus d'informations, consultez la documentation Oracle) et vous devez être actuellement connecté avec le même compte Microsoft Windows que celui spécifié pour le schéma utilisateur d'administration de réplication.  
  
4.  Créez un travail de l'Agent de lecture du journal pour la base de données de publication.  
  
    -   Si vous ne savez pas si un travail d’Agent de lecture du journal existe pour une base de données publiée, exécutez [sp_helplogreader_agent & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-helplogreader-agent-transact-sql.md) serveur de distribution utilisé par le serveur de publication Oracle sur la base de données de distribution. Spécifiez le nom du serveur de publication Oracle pour **@publisher**. Si le jeu de résultats est vide, un travail de l'Agent de lecture du journal doit être créé.  
  
    -   Si un travail de l'Agent de lecture du journal existe déjà pour la base de données de publication, passez à l'étape 5.  
  
    -   Sur le serveur de distribution utilisé par le serveur de publication Oracle sur la base de données de distribution, exécutez [sp_addlogreader_agent & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md). Spécifiez les informations d’identification Windows sous lequel l’agent s’exécute pour **@job_login** et **@job_password**.  
  
        > [!NOTE]  
        >  Le **@job_login** paramètre doit correspondre à la connexion fournie à l’étape 3. Ne fournissez pas d'informations de sécurité pour le serveur de publication. L'Agent de lecture du journal se connecte au serveur de publication à l'aide des informations de sécurité fournies à l'étape 3.  
  
5.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_addpublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md) Pour créer la publication. Pour plus d'informations, voir [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
6.  Sur le serveur de distribution sur la base de données de distribution, exécutez [sp_addpublication_snapshot & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md). Spécifiez le nom de publication utilisé à l’étape 4 pour **@publication** et les informations d’identification Windows sous lequel l’Agent de capture instantanée s’exécute pour **@job_name** et **@password**. Pour utiliser l’authentification Standard Oracle lors de la connexion au serveur de publication, vous devez également spécifier une valeur de **0** pour **@publisher_security_mode** et les informations de connexion Oracle **@publisher_login** et **@publisher_password**. Il s'ensuit la création d'un travail de l'Agent d'instantané pour la publication.  
  
## Voir aussi  
 [Configurer un serveur de publication Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Publier des données et des objets de base de données](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Configurer le travail du jeu de transactions pour un serveur de publication Oracle & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/administration/configure the transaction set job for an oracle publisher.md)   
 [Présentation de la publication Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)   
 [Script pour l'attribution d'autorisations Oracle](../../../relational-databases/replication/non-sql/script-to-grant-oracle-permissions.md)  
  
  