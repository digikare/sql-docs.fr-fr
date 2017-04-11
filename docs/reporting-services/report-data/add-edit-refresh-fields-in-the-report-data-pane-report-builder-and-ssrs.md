---
title: "ajouter, modifier ou actualiser des champs dans le volet des donn&#233;es de rapport (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2e36f0fe-8100-4513-b169-14d611646f81
caps.latest.revision: 7
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 7
---
# ajouter, modifier ou actualiser des champs dans le volet des donn&#233;es de rapport (G&#233;n&#233;rateur de rapports et SSRS)
  Les champs de dataset sont la collection intégrée de noms de champs qui représentent les données qui sont retournées lorsqu'une requête de dataset s'exécute sur une source de données externe.  
  
 Pour un dataset incorporé, les champs de dataset sont les champs créés après avoir terminé la génération d'une requête et fermé le volet Concepteur de requêtes, ainsi que les champs calculés que vous créez.  
  
 Pour un dataset partagé, les champs de dataset sont les champs de la définition du dataset partagé lorsque vous l'avez ajoutée à votre rapport. Bien que la requête depuis le dataset partagé sur le serveur de rapports soit toujours utilisée lorsque vous exécutez le rapport, la liste de champs de dataset est statique dans le rapport.  
  
 Utilisez **Actualiser les champs** pour mettre à jour la liste de champs dans le rapport afin qu'elle corresponde à la liste actuelle des champs de la requête du dataset partagé. L'actualisation de la liste de champs n'affecte pas les champs calculés que vous définissez dans votre rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### Pour ajouter un champ de requête  
  
1.  Dans le volet des données de rapport, cliquez avec le bouton droit sur le dataset, puis sélectionnez **Ajouter un champ de requête**.  
  
    > [!NOTE]  
    >  Si le volet des données de rapport n’est pas visible, cliquez sur **Données du rapport** dans le menu **Affichage**.  
  
2.  Dans la page **Champs** de la boîte de dialogue **Propriétés du dataset** , cliquez sur **Ajouter**, puis sur **Champ de requête**. Une nouvelle ligne est ajoutée au bas de la grille.  
  
3.  Dans la zone de texte **Nom du champ** , tapez le nom du champ.  
  
    > [!NOTE]  
    >  Les noms doivent être uniques dans le dataset.  
  
4.  Dans la zone de texte **Champ source** , tapez le nom d'un champ existant sur la source de données.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Pour ajouter un champ calculé  
  
1.  Dans le volet des données de rapport, cliquez avec le bouton droit sur le dataset, puis cliquez sur **Ajouter un champ calculé**.  
  
2.  Dans la page **Champs** de la boîte de dialogue **Propriétés du dataset** , cliquez sur **Ajouter**, puis sur **Champ calculé**. Une nouvelle ligne est ajoutée au bas de la grille.  
  
3.  Dans la zone de texte **Nom du champ** , tapez le nom du champ.  
  
    > [!NOTE]  
    >  Les noms doivent être uniques dans le dataset.  
  
4.  Dans la zone de texte **Champ source** , tapez l'expression du champ. Cliquez sur le bouton d’expression (**fx**) pour générer une expression.  
  
    > [!NOTE]  
    >  L'expression d'un champ calculé ne peut contenir ni agrégations, ni références à des éléments de rapport.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Pour modifier un champ de requête ou un champ de dataset  
  
1.  Dans le volet des données de rapport, cliquez avec le bouton droit sur le champ, puis cliquez sur **Propriétés du champ**.  
  
2.  Dans la page **Champs** de la boîte de dialogue **Propriétés du dataset** , cliquez sur un champ existant pour sélectionner la ligne.  
  
3.  Modifiez le nom ou la valeur du champ.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### Pour supprimer un champ de requête ou un champ calculé  
  
1.  Dans le volet des données de rapport, développez le dataset pour afficher la collection de champs.  
  
2.  Cliquez avec le bouton droit sur le champ à supprimer, puis sélectionnez **Supprimer**.  
  
### Pour actualiser la collection de champs dans le volet des données de rapport d'un dataset partagé  
  
1.  Dans le volet des données de rapport, cliquez avec le bouton droit sur le dataset, puis sélectionnez **Requête**.  
  
2.  Cliquez sur **Actualiser les champs**.  
  
     Sur le serveur de rapports, la requête du dataset partagé exécute et retourne la collection de champs actuelle.  
  
## Voir aussi  
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Jeux de données du rapport &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Concepteurs de requêtes Reporting Services](../Topic/Reporting%20Services%20Query%20Designers.md)   
 [Concepteurs de requêtes &#40;Générateur de rapports&#41;](../Topic/Query%20Designers%20\(Report%20Builder\).md)  
  
  