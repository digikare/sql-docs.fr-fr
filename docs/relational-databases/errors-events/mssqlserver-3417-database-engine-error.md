---
title: MSSQLSERVER_3417 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d67f08ab21e634823011dd5a0e96005e97f2839c
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver3417"></a>MSSQLSERVER_3417
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3417|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|REC_BADMASTER|  
|Texte du message|Impossible de récupérer la base de données master. Impossible d'exécuter SQL Server. Restaurez la base master à partir d'une sauvegarde complète, réparez-la ou reconstruisez-la. Pour plus d'informations sur la façon de reconstruire la base de données master, consultez la documentation en ligne de SQL Server.|  
  
## <a name="explanation"></a>Explication  
SQL Server ne peut pas démarrer la base de données **MASTER**. Si les bases de données **MASTER** ou **tempdb** ne peuvent pas être mises en ligne, SQL Server ne peut pas s’exécuter. Cette erreur est généralement précédée d'autres erreurs. Étudiez les journaux d'erreurs pour trouver la racine du problème.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Restaurez la sauvegarde de la base de données ou réparez la base de données.  
  
