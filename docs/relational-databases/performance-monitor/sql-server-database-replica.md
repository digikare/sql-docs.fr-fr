---
title: "SQL Server, r&#233;plica de base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "08/24/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "groupes de disponibilité [SQL Server], analyse"
  - "SQLServer : réplica de base de données"
  - "compteurs de performance [SQL Server], groupes de disponibilité AlwaysOn"
  - "groupes de disponibilité [SQL Server], compteurs de performance"
ms.assetid: a5f6bdce-2b13-4924-aaeb-b50b57d624d8
caps.latest.revision: 27
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 27
---
# SQL Server, r&#233;plica de base de donn&#233;es
  L’objet de performance **SQLServer:Database Replica** contient des compteurs de performances qui communiquent des informations sur les bases de données secondaires d’un groupe de disponibilité Always On dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Cet objet est valide uniquement sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui héberge un réplica secondaire.  
  
|Nom du compteur|Description|Vue sur…|  
|------------------|-----------------|--------------|  
|**Octets de fichier reçus/s**|Quantité de données FILESTREAM reçue par le réplica secondaire pour la base de données secondaire au cours de la dernière seconde.|Réplica secondaire|  
|**File des blocs du journal en attente d’application**|Nombre de blocs de journal en attente d’application au réplica de base de données.|Réplica secondaire|
|**File des blocs du journal prêts pour application**|Nombre de blocs de journal en attente, qui sont prêts à être appliqués au réplica de base de données.|Réplica secondaire| 
|**Octets de journal reçus/s**|Quantité d'enregistrements du journal reçue par le réplica secondaire pour la base de données au cours de la dernière seconde.|Réplica secondaire|  
|**Taille de journal restante pour l'annulation**|Quantité de journal en kilo-octets restant pour terminer la phase de restauration.|Réplica secondaire|  
|**File d'attente d'envoi du journal**|Quantité d'enregistrements du journal dans les fichiers journaux de la base de données primaire, en kilo-octets, qui n'a pas encore été envoyée au réplica secondaire. Cette valeur est envoyée au réplica secondaire à partir du réplica principal. La taille de file d'attente n'inclut pas les fichiers FILESTREAM envoyés à un réplica secondaire.|Réplica secondaire|  
|**Transactions d'écriture en miroir/s**|Nombre de transactions qui ont été écrites dans la base de données primaire et qui ont ensuite attendu que le journal soit envoyé à la base de données secondaire pour être validées, au cours de la dernière seconde.|Réplica principal|  
|**File de récupération**|Quantité d'enregistrements du journal dans les fichiers journaux du réplica secondaire qui n'a pas encore été réexécutée.|Réplica secondaire|  
|**Restauration par progression bloquée/s**|Nombre de fois que le thread de restauration est bloqué sur des verrous détenus par les lecteurs de la base de données.|Réplica secondaire|  
|**Octets restants de restauration par progression**|Taille de journal restante, en kilo-octets, avant la fin de la phase de restauration.|Réplica secondaire|  
|**Octets réexécutés/s**|Quantité d'enregistrements du journal réexécutée sur la base de données secondaire au cours de la dernière seconde.|Réplica secondaire|  
|**Taille totale de journal nécessitant une annulation**|Nombre total de kilo-octets du journal qui doivent être annulés.|Réplica secondaire|  
|**Délai de transaction**|Délai d'attente d'accusé de réception non terminé, en millisecondes.|Réplica principal|  
  
## Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)   
 [SQL Server, réplica de disponibilité](../../relational-databases/performance-monitor/sql-server-availability-replica.md)   
 [SQL Server, objet Databases](../../relational-databases/performance-monitor/sql-server-databases-object.md)   
 [Groupes de disponibilité Always On &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  