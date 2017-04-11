---
title: "Effectuer une recherche dans des documents &#224; l&#39;aide des listes de r&#233;sultats | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "recherches [SQL Server Management Studio], listes de résultats"
  - "recherches à l'aide de listes de résultats [SQL Server Management Studio]"
  - "recherches [SQL Server Management Studio], plusieurs fichiers"
  - "éditeur de requêtes [SQL Server Management Studio], recherche dans plusieurs fichiers"
ms.assetid: 275e1b6c-fbd0-4408-af77-35903f90657c
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Effectuer une recherche dans des documents &#224; l&#39;aide des listes de r&#233;sultats
  À l’aide de la boîte de dialogue **Rechercher et remplacer**, vous pouvez rechercher et remplacer du texte dans tous les fichiers d’un projet, d’une solution ou d’un dossier du système de fichiers, même s’ils ne sont pas ouverts dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Les occurrences trouvées lors d’une recherche effectuée dans la boîte de dialogue **Rechercher et remplacer** s’affichent dans les fenêtres Résultats de la recherche 1 et Résultats de la recherche 2, ce qui vous permet de voir le texte exact de la ligne contenant le résultat.  
  
### Pour effectuer une recherche dans plusieurs fichiers  
  
1.  Dans le menu **Edition**, pointez sur **Rechercher et remplacer**, puis cliquez sur **Rechercher dans les fichiers**.  
  
2.  Dans la zone de texte **Rechercher**, entrez le texte à rechercher.  
  
3.  Dans la liste **Regarder dans**, cliquez sur **Tous les documents ouverts**, **Projet en cours**, **Solution complète** ou tapez un chemin de répertoire.  
  
4.  Dans la liste **Types de fichiers**, sélectionnez l’un des jeux d’extensions de fichier répertoriés ou entrez les extensions correspondant aux types de fichiers à analyser en les séparant par des points-virgules. Spécifiez \*\* pour effectuer la recherche dans tous les fichiers du répertoire sélectionné dans la liste déroulante **Regarder dans**.  
  
5.  Sélectionnez d'autres options pour affiner la recherche.  
  
6.  Cliquez sur **Rechercher** pour commencer la recherche.  
  
 Les résultats de la recherche s'affichent par défaut dans la fenêtre Résultats de la recherche 1. Vous pouvez parcourir les résultats de la recherche en double-cliquant sur chaque entrée de la fenêtre Résultats de la recherche 1. Pour afficher les résultats de la recherche dans une nouvelle fenêtre, cochez la case **Afficher dans Rechercher 2**.  
  
#### Pour effectuer un remplacement dans plusieurs fichiers ou dossiers  
  
1.  Dans le menu **Edition**, pointez sur **Rechercher et remplacer**, puis cliquez sur **Remplacer dans les fichiers**.  
  
2.  Dans la zone de texte **Rechercher**, entrez le texte à rechercher.  
  
3.  Dans la zone de texte **Remplacer par**, entrez le texte qui doit remplacer le texte recherché.  
  
4.  Dans la liste **Regarder dans**, cliquez sur **Tous les documents ouverts**, **Projet en cours**, **Solution complète** ou tapez un chemin de répertoire.  
  
5.  Cliquez sur **Remplacer** pour remplacer le résultat de la recherche en cours par le texte spécifié dans la zone **Remplacer par**. Vous pouvez ignorer une occurrence isolée en cliquant sur **Suivant** ou l’ensemble d’un fichier en cliquant sur **Ignorer le fichier**.  
  
     \- ou -  
  
     Cliquez sur **Remplacer tout** pour remplacer toutes les occurrences trouvées par le texte spécifié dans la zone **Remplacer par**. Cochez la case **Conserver les fichiers modifiés ouverts après un remplacement global** si vous souhaitez annuler certains remplacements à un autre moment.  
  
    > [!NOTE]  
    > La commande  **Remplacer tout** remplace toutes les occurrences trouvées, notamment celles que vous avez ignorées en cliquant sur le bouton **Ignorer le fichier** ou **Suivant**. Vous pouvez utiliser **Annuler** uniquement pour les remplacements effectués dans des fichiers restant ouverts après cette opération.  
  
 Les informations relatives aux remplacements s'affichent par défaut dans la fenêtre Résultats de la recherche 1. Vous pouvez parcourir les remplacements en double-cliquant sur chaque entrée de la fenêtre Résultats de la recherche 1.  
  
## Voir aussi  
 [Recherche et remplacement](../../relational-databases/scripting/search-and-replace.md)   
 [Effectuer une recherche de façon interactive dans des documents](../../relational-databases/scripting/search-documents-interactively.md)   
 [Rechercher du texte avec des caractères génériques](../../relational-databases/scripting/search-text-with-wildcards.md)   
 [Rechercher du texte avec des expressions régulières](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  