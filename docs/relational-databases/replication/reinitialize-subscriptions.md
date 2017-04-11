---
title: "R&#233;initialiser des abonnements | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "initialisation d'abonnements [réplication SQL Server], réinitialisation"
  - "abonnements [réplication SQL Server], réinitialisation"
  - "réinitialisation des abonnements"
ms.assetid: fb13712b-e7ad-4f1f-b605-4554bad0cb60
caps.latest.revision: 51
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 51
---
# R&#233;initialiser des abonnements
  La réinitialisation d'un abonnement nécessite l'application d'un nouvel instantané d'un ou plusieurs articles à un ou plusieurs Abonnés : la réplication transactionnelle et la réplication d'instantané permettent à des articles individuels d'être réinitialisés ; la réplication de fusion nécessite que tous les articles soient réinitialisés. Les nœuds d'une topologie de réplication transactionnelle d'égal à égal ne peuvent pas être réinitialisés. Si vous voulez être certain qu'un nœud dispose d'une nouvelle copie des données, restaurez une sauvegarde sur le nœud. Une réinitialisation se produit pour l'une de ces deux raisons :  
  
-   Vous marquez explicitement un abonnement pour réinitialisation.  
  
-   Vous effectuez une action, par exemple une modification de propriété, qui nécessite une réinitialisation. Pour plus d’informations sur les actions qui nécessitent une réinitialisation, consultez [Publication de modification et les propriétés de l’Article](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
 Dans les deux cas, l'instantané le plus récent est appliqué à l'Abonné lors de l'exécution suivante de l'Agent de distribution ou de l'Agent de fusion. Pour la réplication d'instantané et la réplication transactionnelle, quand une réinitialisation se produit, toutes les modifications effectuées sur l'Abonné qui ne sont pas encore synchronisées avec le serveur de publication sont écrasées par l'application du nouvel instantané.  
  
 Pour la réplication de fusion, vous pouvez choisir de charger à partir de l'Abonné toutes les modifications apportées aux données avant d'appliquer l'instantané. Toutes les modifications de schéma en attente provenant du serveur de publication sont appliquées à l'Abonné, puis toutes les modifications qui ont été effectuées sur l'Abonné depuis la dernière synchronisation sont propagées vers le serveur de publication avant que l'instantané soit réappliqué. Ce comportement est contrôlé par la **upload_first** et **automatic_reinitialization_policy** Propriétés ; pour plus d’informations, consultez [Réinitialiser un abonnement](../../relational-databases/replication/reinitialize-a-subscription.md). Si vous marquez un abonnement pour réinitialisation à l’aide de SQL Server Management Studio ou le moniteur de réplication, vous disposez d’une option le **Réinitialiser les abonnements** boîte de dialogue pour télécharger les modifications.  
  
> [!IMPORTANT]  
>  Si vous ajoutez, supprimez ou modifiez un filtre paramétré dans une publication de fusion, les modifications en attente sur l'Abonné ne peuvent pas être chargées sur le serveur de publication au cours de la réinitialisation. Si vous voulez télécharger les modifications en attente, synchronisez tous les abonnements avant de modifier le filtre.  
  
 Si vous avez précisé qu'il ne fallait appliquer aucun instantané initial sur l'Abonné au moment de créer l'abonnement et marquez ensuite ce dernier en vue d'une réinitialisation, aucun instantané n'est appliqué. Pour plus d’informations, consultez [initialiser un abonnement transactionnel sans instantané](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md).  
  
 **Pour réinitialiser un abonnement**  
  
 Pour réinitialiser tous les articles d'un abonnement, utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], des procédures stockées ou Replication Management Objects. Pour réinitialiser des articles individuels dans des publications d'instantané et transactionnelles, vous devez utiliser des procédures stockées. Pour plus d’informations, consultez [Réinitialiser un abonnement](../../relational-databases/replication/reinitialize-a-subscription.md).  
  
## Voir aussi  
 [Initialiser un abonnement](../../relational-databases/replication/initialize-a-subscription.md)   
 [Expiration et désactivation des abonnements](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  