---
title: "Acc&#232;s de navigation (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "accès de navigation [Master Data Services]"
  - "sécurité [Master Data Services], accès de navigation"
ms.assetid: 3403b7b0-44e2-48c3-a1b7-9c4612b874b8
caps.latest.revision: 5
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 5
---
# Acc&#232;s de navigation (Master Data Services)
  L’accès de navigation s’applique à la sécurité de l’objet modèle, affectée sous l’onglet **Modèles**.  
  
 L'accès de navigation désigne l'accès aux niveaux supérieurs par rapport à ceux auxquels vous avez affecté une sécurité.  
  
 Dans cet exemple, les autorisations sont affectées à une entité, et donc l'accès de navigation est accordé au niveau du modèle.  
  
 ![mds_conc_inheritance_model](../master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")  
  
 **Entités**  
  
 Lorsque vous affectez une autorisation à une entité, ses membres feuilles ou ses membres consolidés, l'accès de navigation signifie que vous pouvez lire ou mettre à jour le nom et le code de tous les membres. Vous pouvez également lire le nom du modèle.  
  
 **Attributs**  
  
 Lorsque vous affectez une autorisation à un attribut, l'accès de navigation signifie que vous pouvez lire ou mettre à jour le nom et le code de tous les membres dans l'entité. Vous pouvez également lire le nom du modèle.  
  
 **Collections**  
  
 Lorsque vous affectez des autorisations aux collections, vous pouvez lire ou mettre à jour le nom, le code, la description et l'ID de propriétaire. Vous pouvez également lire le nom du modèle.  
  
## Voir aussi  
 [Mode de détermination des autorisations &#40;Master Data Services&#41;](../master-data-services/how-permissions-are-determined-master-data-services.md)  
  
  