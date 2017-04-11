---
title: "Modifier les propri&#233;t&#233;s des publications et des articles | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modification des propriétés des articles"
  - "modification des propriétés de la publication"
  - "administration de la réplication, propriétés"
  - "publications [réplication SQL Server], modification des propriétés"
  - "articles [réplication SQL Server], propriétés"
ms.assetid: f7df51ef-c088-4efc-b247-f91fb2c6ff32
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Modifier les propri&#233;t&#233;s des publications et des articles
  Quand une publication a été créée, la plupart des propriétés de la publication et des articles peuvent être modifiées, mais certaines nécessitent que l'instantané soit régénéré et/ou que les abonnements soient réinitialisés. Cette rubrique contient des informations sur toutes les propriétés qui requièrent l'une de ces actions ou les deux si elles sont modifiées.  
  
## Propriétés de la publication pour la réplication d'instantané et transactionnelle  
  
|Description|Procédure stockée|Propriétés|Spécifications|  
|-----------------|----------------------|----------------|------------------|  
|Modifier le format d'instantané.|**sp_changepublication**|**sync_method**|Nouvel instantané.|  
|Modifier l'emplacement de l'instantané.|**sp_changepublication**|**alt_snapshot_folder**<br /><br /> **snapshot_in_defaultfolder**|Nouvel instantané.|  
|Modifier l'emplacement de l'instantané.|**sp_changedistpublisher**|**working_directory**|Nouvel instantané.|  
|Modifier la compression de l'instantané.|**sp_changepublication**|**compress_snapshot**|Nouvel instantané.|  
|Modifier des options de l'instantané FTP (File Transfer Protocol).|**sp_changepublication**|**enabled_for_internet**<br /><br /> **ftp_address**<br /><br /> **ftp_login**<br /><br /> **ftp_password**<br /><br /> **ftp_port**<br /><br /> **ftp_subdirectory**|Nouvel instantané.|  
|Modifier l'emplacement du script de pré- ou de post-instantané.|**sp_changepublication**|**pre_snapshot_script**<br /><br /> **post_snapshot_script**|Nouvel instantané (également requis si vous modifiez le contenu du script).<br /><br /> La réinitialisation est requise pour appliquer le nouveau script à l'Abonné.|  
|Activer ou désactiver la prise en charge de non -[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] abonnés.|**sp_changepublication**|**is_enabled_for_het_sub**|Nouvel instantané.|  
|Modifier les rapports sur les conflits pour les abonnements mis à jour en attente|**sp_changepublication**|**centralized_conflicts**|Ne peut être modifiée qu'en l'absence d'abonnements actifs.|  
|Modifier la stratégie de résolution des conflits pour les abonnements mis à jour en attente.|**sp_changepublication**|**conflict_policy**|Ne peut être modifiée qu'en l'absence d'abonnements actifs.|  
  
## Propriétés des articles pour la réplication d'instantané et transactionnelle  
  
|Description|Procédure stockée|Propriétés|Spécifications|  
|-----------------|----------------------|----------------|------------------|  
|Supprimer un article|**sp_droparticle**|Tous les paramètres.|Les articles peuvent être supprimés avant que des abonnements soient créés. À l'aide de procédures stockées, il est possible de supprimer un abonnement à un article ; à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], l'abonnement tout entier peut être supprimé, recréé et synchronisé. Pour plus d’informations, consultez [Ajouter et supprimer des Articles de Publications existantes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).|  
|Modifier un filtre de colonne.|**sp_articlecolumn**|**@column**<br /><br /> **@operation**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Ajouter un filtre de lignes.|**sp_articlefilter**|Tous les paramètres.|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Supprimer un filtre de lignes.|**sp_articlefilter**|**@article**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Modifier un filtre de lignes.|**sp_articlefilter**|**@filter_clause**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Modifier un filtre de lignes.|**sp_changearticle**|**Filter**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Modifier des options de schéma.|**sp_changearticle**|**schema_option**|Nouvel instantané.|  
|Modifier comment les tables sont gérées sur l'Abonné avant d'appliquer l'instantané.|**sp_changearticle**|**pre_creation_cmd**|Nouvel instantané.|  
|Modifier l'état de l'article|**sp_changearticle**|**status**|Nouvel instantané.|  
|Modifier des commandes INSERT, UPDATE ou DELETE.|**sp_changearticle**|**ins_cmd**<br /><br /> **upd_cmd**<br /><br /> **del_cmd**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Modifier le nom de la table de destination|**sp_changearticle**|**dest_table**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Modifier le propriétaire de la table de destination (schéma).|**sp_changearticle**|**destination_owner**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Modifier les mappages des types de données (s'applique seulement à la publication Oracle).|**sp_changearticlecolumndatatype**|**@type**<br /><br /> **@length**<br /><br /> **@precision**<br /><br /> **@scale**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
  
## Propriétés de la publication pour la réplication de fusion  
  
|Description|Procédure stockée|Propriétés|Spécifications|  
|-----------------|----------------------|----------------|------------------|  
|Modifier le format d'instantané|**sp_changemergepublication**|**sync_mode**|Nouvel instantané.|  
|Modifier l'emplacement de l'instantané.|**sp_changemergepublication**|**alt_snapshot_folder**<br /><br /> **snapshot_in_defaultfolder**|Nouvel instantané.|  
|Modifier l'emplacement de l'instantané.|**sp_changedistpublisher**|**working_directory**|Nouvel instantané.|  
|Modifier la compression de l'instantané|**sp_changemergepublication**|**compress_snapshot**|Nouvel instantané.|  
|Modifier les options d'instantané FTP|**sp_changemergepublication**|**enabled_for_internet**<br /><br /> **ftp_address**<br /><br /> **ftp_login**<br /><br /> **ftp_password**<br /><br /> **ftp_port**<br /><br /> **ftp_subdirectory**|Nouvel instantané.|  
|Modifier les scripts de pré- ou de post-instantané.|**sp_changemergepublication**|**pre_snapshot_script**<br /><br /> **post_snapshot_script**|Nouvel instantané (également requis si vous modifiez le contenu du script).<br /><br /> La réinitialisation est requise pour appliquer le nouveau script à l'Abonné.|  
|Ajouter un filtre de jointure ou un enregistrement logique.|**sp_addmergefilter**|Tous les paramètres.|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Supprimer un filtre de jointure ou un enregistrement logique.|**sp_dropmergefilter**|Tous les paramètres.|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Modifier un filtre de jointure ou un enregistrement logique.|**sp_changemergefilter**|**@property**<br /><br /> **@value**|Nouvel instantané<br /><br /> Réinitialiser les abonnements.|  
|Désactiver l'utilisation de filtres paramétrés (l'activation de filtres paramétrés ne nécessite pas d'actions particulières).|**sp_changemergepublication**|Valeur **false** pour **dynamic_filters**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Activer ou désactiver l'utilisation de partitions précalculées.|**sp_changemergepublication**|**use_partition_groups**|Nouvel instantané.|  
|Activer ou désactiver [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] Optimisation de partition.|**sp_changemergepublication**|**keep_partition_changes**|Réinitialiser les abonnements.|  
|Activer ou désactiver la validation de partition d'Abonné.|**sp_changemergepublication**|**validate_subscriber_info**|Réinitialiser les abonnements.|  
|Modifier le niveau de compatibilité d'une publication en 80sp3 ou inférieur.|**sp_changemergepublication**|**publication_compatibility_level**|Nouvel instantané.|  
  
## Propriétés d'un article pour la réplication de fusion  
  
|Description|Procédure stockée|Propriétés|Spécifications|  
|-----------------|----------------------|----------------|------------------|  
|Supprimer un article, où l'article a le dernier filtre paramétré dans la publication.|**sp_dropmergearticle**|Tous les paramètres|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Supprimer un article, où l'article est un parent dans un filtre de jointure ou dans un enregistrement logique (ceci a comme effet de bord de supprimer la jointure).|**sp_dropmergearticle**|Tous les paramètres|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Supprimer un article, toutes les autres circonstances.|**sp_dropmergearticle**|Tous les paramètres|Nouvel instantané.|  
|Inclure un filtre de colonne qui était auparavant non publié.|**sp_mergearticlecolumn**|**@column**<br /><br /> **@operation**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Ajouter, supprimer ou modifier un filtre de lignes.|**sp_changemergearticle**|**subset_filterclause**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.<br /><br /> Si vous ajoutez, supprimez ou modifiez un filtre paramétré, les modifications en attente chez l'abonné ne peuvent pas être chargées sur le serveur de publication pendant la réinitialisation. Si vous voulez télécharger les modifications en attente, synchronisez tous les abonnements avant de modifier le filtre.<br /><br /> Si un article n'est impliqué dans aucun des filtres de jointure, vous pouvez supprimer l'article et l'ajouter à nouveau avec un autre filtre de lignes, ce qui ne nécessite pas la réinitialisation de la totalité de l'abonnement. Pour plus d’informations sur l’ajout et la suppression des articles, consultez [Ajouter et supprimer des Articles de Publications existantes](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).|  
|Modifier des options de schéma.|**sp_changemergearticle**|**schema_option**|Nouvel instantané.|  
|Modifier le suivi de niveau colonne en niveau ligne (changer le suivi de niveau ligne pour un suivi de niveau colonne ne nécessite aucune action particulière).|**sp_changemergearticle**|Valeur **false** pour **column_tracking**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Changer le fait que les autorisations sont ou non vérifiées avant l'application sur le serveur de publication d'instructions créées sur l'Abonné.|**sp_changemergearticle**|**check_permissions**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
|Activer ou désactiver les abonnements en téléchargement seul (changer d'autres options de chargement ne nécessite pas d'actions particulières).|**sp_changemergearticle**|Modification vers ou à partir d’une valeur de **2** pour **subscriber_upload_options**|Réinitialiser les abonnements.|  
|Modifier le propriétaire de la table de destination.|**sp_changemergearticle**|**destination_owner**|Nouvel instantané.<br /><br /> Réinitialiser les abonnements.|  
  
## Voir aussi  
 [Administration & #40 ; Réplication & #41 ;](../../../relational-databases/replication/administration/administration-replication.md)   
 [Créer et appliquer un instantané](../../../relational-databases/replication/create-and-apply-the-snapshot.md)   
 [Réinitialiser des abonnements](../../../relational-databases/replication/reinitialize-subscriptions.md)   
 [sp_addmergefilter & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_articlecolumn & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_articlefilter & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_changearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_changearticlecolumndatatype & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changearticlecolumndatatype-transact-sql.md)   
 [sp_changedistpublisher & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_changemergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_changemergefilter & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_changemergepublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_changepublication & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_droparticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_dropmergearticle & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [sp_dropmergefilter & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [sp_mergearticlecolumn & #40 ; Transact-SQL & #41 ;](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md)  
  
  