---
title: "Supprimer un mod&#232;le (Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "suppression de modèles [Master Data Services]"
  - "modèles [Master Data Services], suppression de modèles"
ms.assetid: f0ad3cc4-aed7-47c8-94bc-2971fe9fe871
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# Supprimer un mod&#232;le (Master Data Services)
  Supprimez un modèle afin de supprimer le modèle et toutes ses données de [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)].  
  
> [!NOTE]  
>  Lorsque vous effectuez cette procédure, tous les objets et toutes les données de toutes les versions du modèle sont supprimés définitivement.  
  
## Conditions préalables  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Administration de système** .  
  
-   Vous devez être administrateur de modèle. Pour plus d’informations, consultez [Administrateurs &#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md).  
  
### Pour supprimer un modèle  
  
1.  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], cliquez sur **Administration de système**.  
  
2.  Dans la page **Vue du modèle** , dans la barre de menus, pointez sur **Gérer** , puis cliquez sur **Modèles**.  
  
3.  Dans la grille de la page **Gérer les modèles** , sélectionnez la ligne du modèle à supprimer.  
  
4.  Cliquez sur **Supprimer**.  
  
5.  Dans la boîte de dialogue de confirmation, cliquez sur **OK**.  
  
6.  Dans la boîte de dialogue de confirmation supplémentaire, cliquez sur **OK**.  
  
 La colonne **État** de la grille affiche l’état de l’opération sur le modèle. Lorsque vous cliquez sur le bouton **Enregistrer le modèle**, l’image ![Updating](../master-data-services/media/mds-model-status-updating.png "Updating") s’affiche, ce qui signifie que le modèle est en cours de mise à jour. En cas d’erreur lors de la création ou de la modification d’un modèle, l’image ![Error](../master-data-services/media/mds-model-status-error.png "Error") apparaît. Dans le cas contraire, le statut est OK et l’image ![OK](../master-data-services/media/mds-model-status-ok.png "OK") s’affiche.  
  
## Voir aussi  
 [Modèles &#40;Master Data Services&#41;](../master-data-services/models-master-data-services.md)   
 [Créer un modèle &#40;Master Data Services&#41;](../master-data-services/create-a-model-master-data-services.md)  
  
  