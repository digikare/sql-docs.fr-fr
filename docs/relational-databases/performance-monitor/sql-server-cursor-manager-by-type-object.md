---
title: "Objet SQLServer:Cursor Manager by Type | Microsoft Docs"
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
  - "Cursor Manager by Type (objet)"
  - "SQLServer:Cursor Manager by Type"
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Objet SQLServer:Cursor Manager by Type
  L'objet **SQLServer:Cursor Manager by Type** fournit des compteurs pour surveiller les curseurs, groupés par type.  
  
 Le tableau ci-dessous décrit les compteurs **Cursor Manager by Type** de SQL Server.  
  
|Compteurs Cursor Manager by Type|Description|  
|-------------------------------------|-----------------|  
|**Curseurs actifs**|Nombre de curseurs actifs.|  
|**Taux d'accès au cache**|Rapport entre les présences dans le cache et les recherches.|  
|**Base du taux d’accès au cache**|À usage interne uniquement| 
|**Nombres de curseurs mis en cache**|Nombre de curseurs d'un type donné dans le cache.|  
|**Nombre d'utilisations du cache de curseurs/s**|Nombre d'utilisations de chaque type de curseur en cache.|  
|**Mémoire utilisée par les curseurs**|Quantité de mémoire consommée par les curseurs en kilo-octets (Ko).|  
|**Requêtes de curseurs/s**|Nombre de requêtes de curseurs SQL reçues par le serveur.|  
|**Tables de travail utilisées par les curseurs**|Nombre de tables de travail utilisées par les curseurs.|  
|**Nombre de plans de curseurs actifs**|Nombre de plans de curseurs.|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Instance Cursor Manager|Description|  
|-----------------------------|-----------------|  
|**_Total**|Informations pour tous les curseurs.|  
|**API Cursor**|Informations sur le curseur API uniquement.|  
|**TSQL Global Cursor**|Informations sur le curseur global [!INCLUDE[tsql](../../includes/tsql-md.md)] uniquement.|  
|**TSQL Local Cursor**|Informations sur le curseur local [!INCLUDE[tsql](../../includes/tsql-md.md)] uniquement.|  
  
## Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  