---
title: MSSQLSERVER_8443 | Microsoft Docs
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
- 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 75fb26c6ad2d49fe8a28a84cdecf8aa67564c6e8
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver8443"></a>MSSQLSERVER_8443
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|8443|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SB_DIALOG_WO_CONV_GROUP|  
|Texte du message|La conversation avec l’ID '%.*ls' et l’initiateur %d fait référence à un groupe de conversations manquant '%.\*ls'. Exécutez DBCC CHECKDB pour analyser et réparer la base de données.|  
  
## <a name="explanation"></a>Explication  
La couche de métadonnées a retourné la valeur NULL pour le groupe de conversations. La base de données a été endommagée d'une certaine façon. Une erreur de disque est une source d'endommagement possible.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez DBCC CHECKDB en mode réparation pour ramener la base de données à un état cohérent. Cela peut entraîner la suppression de messages si cela s'avère nécessaire pour restaurer la cohérence. Examinez les journaux des erreurs du système pour voir si cette erreur a été causée par une autre défaillance dans le système.  
  
