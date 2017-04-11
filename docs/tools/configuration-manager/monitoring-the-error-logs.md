---
title: "Surveillance des journaux d&#39;erreurs | Microsoft Docs"
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
  - "journaux [SQL Server]"
  - "performances des bases de données [SQL Server], erreurs"
  - "journaux des applications Windows [SQL Server]"
  - "surveillance des performances [SQL Server], erreurs"
  - "performances du serveur [SQL Server], erreurs"
  - "comparaison des sorties des journaux d'erreurs et des applications"
  - "erreurs [SQL Server], journaux"
  - "paramétrage des bases de données [SQL Server], erreurs"
  - "surveillance des bases de données [SQL Server], erreurs"
  - "journal des erreurs de SQL Server"
  - "journaux [SQL Server], journaux d'erreurs SQL Server"
  - "journaux d'erreurs [SQL Server]"
  - "journaux [SQL Server], journaux des applications Windows"
ms.assetid: e250336b-0695-44f6-a42f-23222f94e377
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Surveillance des journaux d&#39;erreurs
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] enregistre certains événements système ainsi que des événements définis par l’utilisateur dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le journal des applications [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. Tous les événements consignés dans ces deux journaux sont automatiquement datés. Utilisez les informations du journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour résoudre des problèmes liés à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le journal des applications Windows fournit une vue d'ensemble des événements survenus dans le système d'exploitation Windows, ainsi que des événements survenus dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et dans l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Utilisez l'Observateur d'événements Windows pour afficher le journal des applications Windows et filtrer les informations. Par exemple, vous pouvez filtrer des d'événements, comme les informations, les avertissements, les erreurs, les audits de succès et les audits d'échecs.  
  
## Comparaison des sorties des journaux d'erreurs et des applications  
 Vous pouvez utiliser le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et le journal des applications Windows pour identifier les causes des problèmes. Par exemple, pendant la surveillance du journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous pouvez rencontrer des messages d'erreur qui ne contiennent pas d'informations sur la cause. En comparant les dates et les heures des événements intervenus entre ces journaux, vous pouvez réduire la liste des causes possibles. La visionneuse du fichier journal de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] permet d'intégrer l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les journaux Windows dans une même liste, facilitant ainsi la compréhension d'événements serveur et d'événements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] liés. Pour plus d'informations, consultez la rubrique relative à la visionneuse du fichier journal dans la documentation en ligne de SQL Server.  
  
## Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Consultation du journal des erreurs de SQL Server](../../tools/configuration-manager/viewing-the-sql-server-error-log.md)|Contient des informations sur le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et la procédure pour l'afficher.|  
|[Affichage du journal des applications Windows](../../tools/configuration-manager/viewing-the-windows-application-log.md)|Contient des informations sur le journal des applications Windows et la procédure pour l'afficher.|  
  
  