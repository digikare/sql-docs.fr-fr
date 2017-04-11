---
title: "Ajouter des emplacements personnalis&#233;s &#224; une carte (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MICROSOFT.REPORTDESIGNER.MAPPOINT.POINTTEMPLATE"
ms.assetid: 7d36faae-5bcc-446a-9eba-f42349cafacb
caps.latest.revision: 10
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 10
---
# Ajouter des emplacements personnalis&#233;s &#224; une carte (G&#233;n&#233;rateur de rapports et SSRS)
  Après avoir ajouté une carte à un rapport paginé [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)], vous pouvez ajouter vos propres emplacements de points.  
  
 Les propriétés d'affichage de tous les points d'une couche sont contrôlées en définissant des options pour les propriétés des points de la couche. Pour un point incorporé sélectionné, vous pouvez remplacer les propriétés d'affichage.  
  
> [!NOTE]  
>  Lorsque vous remplacez les propriétés d'affichage de couche pour le point incorporé, les modifications que vous apportez ne sont pas réversibles.  
  
 Pour plus d’informations, consultez [Modifier l’affichage des polygones, des lignes et des points à l’aide de règles et de données analytiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/vary polygon, line, and point display by rules and analytical data.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Pour ajouter une couche de points  
  
1.  Sur l'aire de conception du rapport, cliquez sur la carte pour la sélectionner et afficher le volet Carte.  
  
2.  Dans la barre d’outils, cliquez sur **Ajouter une couche**.  
  
3.  Dans la liste déroulante, cliquez sur **Ajouter une couche de points**. Une couche de points sans points est ajoutée à la carte. Par défaut, la couche de points est prête pour que vous ajoutiez des points incorporés.  
  
## Pour ajouter un point personnalisé  
  
1.  Sur l'aire de conception du rapport, cliquez sur la carte pour la sélectionner et afficher le volet Carte.  
  
2.  Dans le volet Carte, cliquez avec le bouton droit sur une couche de points de type **Incorporé**, puis cliquez sur **Ajouter un point**. Le curseur se transforme en croix.  
  
3.  Pour ajouter un point, cliquez sur un emplacement sur la carte. Un point incorporé est ajouté à la couche sélectionnée à l'emplacement où vous cliquez.  
  
## Pour personnaliser l'affichage pour un point incorporé  
  
1.  Cliquez avec le bouton droit sur le point, puis cliquez sur **Propriétés des points**. La boîte de dialogue **Propriétés des points incorporés de la carte** s’ouvre.  
  
2.  Cliquez sur **Remplacer les options de point pour cette couche**. Plusieurs pages de propriétés s'affichent dans le volet gauche.  
  
3.  Cliquez sur les pages et définissez les propriétés d'affichage que vous souhaitez appliquer à ce point.  
  
## Voir aussi  
 [Cartes &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/maps-report-builder-and-ssrs.md)   
 [Modifier l’affichage des polygones, des lignes et des points à l’aide de règles et de données analytiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/vary polygon, line, and point display by rules and analytical data.md)  
  
  