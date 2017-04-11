---
title: "Configurer les propri&#233;t&#233;s d’ex&#233;cution d’un rapport (Gestionnaire de rapports) | Microsoft Docs"
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
helpviewer_keywords: 
  - "propriétés relatives à l'exécution des rapports [Reporting Services]"
  - "rapports [Reporting Services], propriétés"
  - "rapports [Reporting Services], options d’exécution"
ms.assetid: 73cc8dcc-ef80-40d7-9739-d33bba0eb28a
caps.latest.revision: 41
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 41
---
# Configurer les propri&#233;t&#233;s d’ex&#233;cution d’un rapport (Gestionnaire de rapports)
  Vous pouvez définir les options de traitement d'un rapport afin de spécifier le moment où les données d'un rapport sont récupérées. Il est utile de planifier le traitement des données d'un rapport si la source de données externe est actualisée à des heures spécifiques (par exemple un entrepôt de données actualisé chaque jour ou chaque semaine) et si vous souhaitez éviter le temps de traitement lié à la récupération des mêmes données chaque fois qu'un rapport est demandé. La planification du traitement des données est également utile lorsque vous souhaitez contrôler la charge de traitement du serveur de base de données externe, ou lorsque vous souhaitez fournir des résultats cohérents pour plusieurs utilisateurs qui doivent travailler avec des jeux de données identiques. Avec des données volatiles, un rapport à la demande peut produire des résultats différents en l'espace d'une minute. En revanche, un instantané de rapport vous permet d'effectuer des comparaisons valides par rapport à d'autres rapports ou peut servir d'outil d'analyse contenant des données toutes datées d'un même point dans le temps.  
  
 Un instantané de rapport est un rapport qui contient des instructions de mise en page et des résultats de requêtes récupérés à un moment précis. Contrairement aux rapports à la demande, qui récupèrent les résultats des requêtes récentes lorsque vous les sélectionnez, les instantanés de rapport sont traités par planification, puis enregistrés sur un serveur de rapports. Lorsque vous sélectionnez un instantané de rapport pour le visualiser, le serveur de rapports récupère le rapport stocké dans la base de données du serveur de rapports, puis affiche les données et la mise en page telles qu'elles étaient lors de la création de l'instantané.  
  
 Les instantanés de rapport ne sont pas enregistrés dans un format de rendu particulier. Ils sont générés dans un format d'affichage final (par exemple, au format HTML) uniquement à la demande d'un utilisateur ou d'une application. Le rendu différé permet de disposer d'un instantané portable. Le rendu du rapport peut être effectué dans le format approprié pour le périphérique ou le navigateur Web à l'origine de la demande.  
  
### Pour configurer les options de traitement d'un rapport  
  
1.  Démarrez le [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md).  
  
2.  Accédez au rapport dont vous souhaitez définir les options de traitement et ouvrez-le.  
  
 Pointez sur le rapport et cliquez sur la flèche déroulante.  
  
1.  Dans le menu déroulant, cliquez sur **Gérer**, puis sélectionnez l’onglet **Options de traitement**.  
  
2.  Cliquez sur **Effectuer le rendu de ce rapport à partir d’un instantané d’exécution, puis sélectionnez l’une des options suivantes :**  
  
    -   Si vous voulez créer un instantané, sélectionnez l’option **Utiliser la planification suivante pour créer des instantanés d’exécution du rapport**, puis définissez une planification spécifique aux rapports ou sélectionnez-en une dans la liste **Planification partagée**.  
  
    -   Si vous voulez créer immédiatement un instantané, sélectionnez l’option **Créer un instantané du rapport lorsque vous cliquez sur le bouton Appliquer de cette page**.  
  
3.  Cliquez sur **Appliquer**.  
  
## Voir aussi  
 [Définir les propriétés de traitement d'un rapport](../../reporting-services/report-server/set-report-processing-properties.md)   
 [Ouvrir et fermer un rapport &#40;Gestionnaire de rapports&#41;](../../reporting-services/reports/open-and-close-a-report-report-manager.md)   
 [Page Contenu &#40;Gestionnaire de rapports&#41;](../Topic/Contents%20Page%20\(Report%20Manager\).md)   
 [Gestion du contenu du serveur de rapports &#40;SSRS en mode natif&#41;](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Page de propriétés Options de traitement &#40;Gestionnaire de rapports&#41;](../Topic/Processing%20Options%20Properties%20Page%20\(Report%20Manager\).md)  
  
  