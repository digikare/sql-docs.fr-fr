---
title: Sys.dm_db_file_space_usage (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_db_file_space_usage
- sys.dm_db_file_space_usage_TSQL
- sys.dm_db_file_space_usage
- dm_db_file_space_usage_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_db_file_space_usage dynamic management view
ms.assetid: 148a5276-a8d5-49d2-8146-3c63d24c2144
caps.latest.revision: "45"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: da7c61f339c0d8d66c8c0bcd00514a6ecf58286f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmdbfilespaceusage-transact-sql"></a>sys.dm_db_file_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne des informations sur l'utilisation de l'espace pour chaque fichier de la base de données.  
  
> [!NOTE]  
>  Pour appeler cette de [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] ou [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], utilisez le nom **sys.dm_pdw_nodes_db_file_space_usage**.  
  
|Nom de colonne|Type de données| Description|  
|-----------------|---------------|-----------------|  
|database_id|**smallint**|ID de la base de données.|  
|file_id|**smallint**|ID de fichier.<br /><br /> FILE_ID correspond à file_id dans [sys.dm_io_virtual_file_stats](../../relational-databases/system-dynamic-management-views/sys-dm-io-virtual-file-stats-transact-sql.md) et à fileid dans [sys.sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md).|  
|filegroup_id|**smallint**|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> ID de groupe de fichiers.|  
|total_page_count|**bigint**|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Nombre total de pages dans le fichier.|  
|allocated_extent_page_count|**bigint**|**S'applique à**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Nombre total de pages dans les étendues allouées du fichier.|  
|unallocated_extent_page_count|**bigint**|Nombre total de pages dans les étendues non allouées du fichier.<br /><br /> Cette valeur ne comprend pas les pages inutilisées dans les étendues allouées.|  
|version_store_reserved_page_count|**bigint**|Nombre total de pages dans les étendues uniformes allouées pour le magasin de versions. Les pages du magasin de versions ne sont jamais allouées à partir d'étendues mixtes.<br /><br /> Les pages IAM ne sont pas incluses parce qu'elles sont toujours allouées à partir d'étendues mixtes. Les pages PFS sont incluses si elles sont allouées à partir d'une étendue uniforme.<br /><br /> Pour plus d’informations, consultez [sys.dm_tran_version_store &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md).|  
|user_object_reserved_page_count|**bigint**|Nombre total de pages allouées à partir d'étendues uniformes pour les objets utilisateur de la base de données. Ce nombre inclut les pages non utilisées provenant d'une étendue allouée.<br /><br /> Les pages IAM ne sont pas incluses parce qu'elles sont toujours allouées à partir d'étendues mixtes. Les pages PFS sont incluses si elles sont allouées à partir d'une étendue uniforme.<br /><br /> Vous pouvez utiliser la colonne total_pages le [sys.allocation_units](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md) catalogue pour retourner le nombre de pages réservées de chaque unité d’allocation de l’objet utilisateur. Notez toutefois que la colonne total_pages inclut les pages IAM.|  
|internal_object_reserved_page_count|**bigint**|Nombre total de pages d'étendues uniformes allouées pour des objets internes dans le fichier. Ce nombre inclut les pages non utilisées provenant d'une étendue allouée.<br /><br /> Les pages IAM ne sont pas incluses parce qu'elles sont toujours allouées à partir d'étendues mixtes. Les pages PFS sont incluses si elles sont allouées à partir d'une étendue uniforme.<br /><br /> Il n'existe pas d'affichage catalogue ni d'objet de gestion dynamique qui retourne le nombre de pages de chaque objet interne.|  
|mixed_extent_page_count|**bigint**|Nombre total de pages allouées et non allouées dans les étendues mixtes allouées du fichier. Les étendues mixtes contiennent des pages allouées à différents objets. Ce nombre comprend toutes les pages IAM du fichier.|
|modified_extent_page_count|**bigint**|**À partir de**:[!INCLUDE[sssqlv14-md](../../includes/sssqlv14-md.md)]<br /><br />Nombre total de pages modifiées dans allouée étendues du fichier depuis la dernière sauvegarde de base de données complète. Le nombre de pages modifiées peut être utilisé pour effectuer le suivi des modifications différentielles de la base de données depuis la dernière sauvegarde complète pour décider s’il est préférable d’effectuer la sauvegarde différentielle.|
|pdw_node_id|**int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> L’identificateur du nœud qui se trouve sur cette distribution.|  
|distribution_id|**int**|**S’applique aux**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Id numérique unique associée à la distribution.|  
  
## <a name="remarks"></a>Notes  
 Le nombre de pages se situe toujours au niveau des étendues. Les nombres de pages sont donc toujours des multiples de huit. Les étendues qui contiennent des pages d'allocation GAM (Global Allocation Map) et SGAM (Shared Global Allocation Map) sont des étendues uniformes allouées. Elles ne sont pas incluses dans les nombres de pages décrits précédemment.  
  
 Le contenu de la banque des versions en cours est dans [sys.dm_tran_version_store](../../relational-databases/system-dynamic-management-views/sys-dm-tran-version-store-transact-sql.md). Le suivi des pages du magasin de versions n'est pas effectué au niveau des sessions et des tâches, mais au niveau des fichiers. En effet, il s'agit de ressources globales. Une session peut générer des versions, mais ces dernières ne peuvent pas être supprimées lorsque la session se termine. Le nettoyage du magasin de versions doit considérer la transaction la plus longue ayant besoin d'accéder à une version particulière. La transaction en cours d’exécution plus longue pour la version nettoyage du magasin peut être détectée en consultant la colonne elapsed_time_seconds dans [sys.dm_tran_active_snapshot_database_transactions](../../relational-databases/system-dynamic-management-views/sys-dm-tran-active-snapshot-database-transactions-transact-sql.md).  
  
 Des modifications fréquentes dans la colonne mixed_extent_page_count peuvent indiquer une utilisation importante de pages SGAM. Le cas échéant, vous risquez d'observer un grand nombre d'attentes PAGELATCH_UP dans lesquelles la ressource d'attente est une page SGAM. Pour plus d’informations, consultez [sys.dm_os_waiting_tasks &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-waiting-tasks-transact-sql.md), [sys.dm_os_wait_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md), et [sys.dm_os_latch_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-latch-stats-transact-sql.md).  
  
## <a name="user-objects"></a>Objets utilisateur  
 Les objets suivants sont compris dans les compteurs de pages des objets utilisateurs :  
  
-   les tables et les index définis par l'utilisateur ;  
  
-   les tables et les index système ;  
  
-   les tables temporaires globales et les index ;  
  
-   les tables temporaires locales et les index ;  
  
-   les variables de tables ;  
  
-   les tables renvoyées dans les fonctions table.  
  
## <a name="internal-objects"></a>Objets internes  
 Les objets internes se trouvent uniquement dans tempdb. Les objets suivants sont compris dans les compteurs de pages des objets internes :  
  
-   les tables de travail des opérations de curseur ou de mise en attente et le stockage temporaire d'objets LOB ;  
  
-   les fichiers de travail des opérations telles que les jointures de hachage ;  
  
-   Tris  
  
## <a name="relationship-cardinalities"></a>Cardinalités de la relation  
  
|De|Pour|Relation|  
|----------|--------|------------------|  
|sys.dm_db_file_space_usage.database_id, file_id|sys.dm_io_virtual_file_stats.database_id, file_id|Un à un|  
  
## <a name="permissions"></a>Permissions  
 Sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requiert l’autorisation VIEW SERVER STATE sur le serveur.  
  
 Sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] niveaux Premium requiert l’autorisation VIEW DATABASE STATE dans la base de données. Sur [!INCLUDE[ssSDS](../../includes/sssds-md.md)] Standard et les niveaux de base nécessite le [!INCLUDE[ssSDS](../../includes/sssds-md.md)] compte d’administrateur.  
  
## <a name="examples"></a>Exemples  
  
### <a name="determing-the-amount-of-free-space-in-tempdb"></a>Détermination de la quantité d'espace disponible dans tempdb  
 La requête suivante retourne le nombre total de pages disponibles et l’espace libre total en mégaoctets (Mo) disponibles dans tous les fichiers de **tempdb**.  
  
```tsql
USE tempdb;  
GO  
SELECT SUM(unallocated_extent_page_count) AS [free pages],   
(SUM(unallocated_extent_page_count)*1.0/128) AS [free space in MB]  
FROM sys.dm_db_file_space_usage;  
```  

### <a name="determining-the-amount-of-space-used-by-user-objects"></a>Détermination de la quantité d'espace utilisée par les objets utilisateur  
 La requête ci-dessous retourne le nombre total de pages utilisées par les objets utilisateur et l'espace total en Mo utilisé par les objets utilisateur dans tempdb.  
  
```tsql  
USE tempdb;  
GO  
SELECT SUM(user_object_reserved_page_count) AS [user object pages used],  
(SUM(user_object_reserved_page_count)*1.0/128) AS [user object space in MB]  
FROM sys.dm_db_file_space_usage;
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions et vues de gestion dynamique &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Base de données associés des vues de gestion dynamique &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [Sys.dm_db_task_space_usage &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
 [sys.dm_db_session_space_usage &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-session-space-usage-transact-sql.md)  