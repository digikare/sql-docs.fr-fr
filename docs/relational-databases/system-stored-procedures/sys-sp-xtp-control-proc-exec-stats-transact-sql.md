---
title: Sys.sp_xtp_control_proc_exec_stats (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_control_proc_exec_stats
- sys.sp_xtp_control_proc_exec_stats_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.sp_xtp_control_proc_exec_stats
ms.assetid: f5119808-76a1-4522-8529-9e02ee39adcb
caps.latest.revision: "15"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 721c120c200bb3142b36e06beb6e45cab1ca0805
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysspxtpcontrolprocexecstats-transact-sql"></a>sys.sp_xtp_control_proc_exec_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Active la collection de statistiques pour les procédures stockées compilées en mode natif de l'instance.  
  
 Pour activer la collection de statistiques au niveau de la requête pour les procédures stockées compilées en mode natif, consultez [sys.sp_xtp_control_query_exec_stats &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_xtp_control_proc_exec_stats [ [ @new_collection_value = ] collection_value ], [ @old_collection_value]  
```  
  
## <a name="arguments"></a>Arguments  
 @new_collection_value= *valeur*  
 Détermine si la collection de statistiques au niveau de la procédure est activée (1) ou désactivée (0).  
  
 @new_collection_valuea la valeur zéro lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou la base de données démarre.  
  
 @old_collection_value= *valeur*  
 Retourne l'état actuel.  
  
## <a name="return-code"></a>Code de retour  
 0 pour réussite. Une valeur différente de zéro pour un échec.  
  
## <a name="permissions"></a>Permissions  
 Nécessite l'appartenance au rôle sysadmin fixe.  
  
## <a name="code-samples"></a>Exemples de code  
 Pour définir @new_collection_value et la requête pour la valeur de@new_collection_value:  
  
```  
exec [sys].[sp_xtp_control_proc_exec_stats] @new_collection_value = 1  
declare @c bit  
exec sp_xtp_control_proc_exec_stats @old_collection_value=@c output  
select @c as 'collection status'  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  