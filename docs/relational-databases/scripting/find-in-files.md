---
title: "Rechercher dans les fichiers | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findreplace.findinfiles"
  - "vs.findinfiles"
helpviewer_keywords: 
  - "Rechercher dans les fichiers (boîte de dialogue)"
ms.assetid: bf92770a-33df-43ef-85ad-5a9223649b98
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Rechercher dans les fichiers
  L’onglet **Rechercher dans les fichiers** de la fenêtre Rechercher et remplacer vous permet de rechercher une chaîne ou une expression dans le code d’un ensemble de fichiers spécifié. Les concordances trouvées et les actions exécutées sont répertoriées dans la fenêtre Résultats de la recherche, sélectionnée dans **Options de résultat**.  
  
 Vous pouvez également ouvrir la boîte de dialogue **Rechercher et remplacer** à l’aide de boutons de la barre d’outils et de touches de raccourci.  
  
 Les sections ci-après répertorient les commandes disponibles sous l’onglet **Rechercher dans les fichiers**.  
  
## Rechercher  
 Ces commandes sous l’onglet **Rechercher dans les fichiers** vous permettent de spécifier la chaîne ou l’expression qui doit concorder.  
  
 **Rechercher**  
 Tapez le texte à rechercher. La boîte de dialogue tente de fournir le texte recherché, à l'aide du texte sélectionné avec le curseur avant l'ouverture de la boîte de dialogue, d'un texte proche ou d'un texte qui a fait l'objet d'une recherche antérieure. Vous pouvez réutiliser une des 20 dernières chaînes de recherche en la sélectionnant dans cette liste déroulante.  
  
 **[chaînes contenant des caractères génériques]**  
 Si vous souhaitez inclure des caractères génériques tels que des astérisques (`*`) et des points d’interrogation (`?`) dans votre chaîne de recherche, cochez la case **Utiliser** sous **Options de recherche**, puis cliquez sur **Caractères génériques**.  
  
 **[expression régulière]**  
 Pour forcer le moteur de recherche à interpréter votre chaîne de recherche comme une expression régulière, cochez la case **Utiliser** sous **Options de recherche**, puis cliquez sur **Expressions régulières**.  
  
 **Générateur d'expressions**  
 Ce bouton triangulaire en regard de la zone **Rechercher** est disponible quand la case **Utiliser** est cochée sous **Options de recherche**. Cliquez sur ce bouton pour afficher la liste des caractères génériques ou des expressions régulières, selon l’option **Utiliser** qui est sélectionnée. Tout élément sélectionné dans cette liste est ajouté à la chaîne **Rechercher**.  
  
## Regarder dans  
 L’option sélectionnée dans la liste déroulante **Regarder dans** détermine si l’option **Rechercher dans les fichiers** limite la recherche aux fichiers qui sont actuellement actifs ou l’étend à tous les fichiers stockés dans certains dossiers. Sélectionnez l’étendue de la recherche dans la liste, tapez le chemin d’un dossier ou cliquez sur le bouton **...** pour afficher la boîte de dialogue **Choisir des dossiers de recherche** et choisir un ensemble de dossiers pour la recherche.  
  
> [!NOTE]  
>  Si l’option **Regarder dans** sélectionnée applique la recherche à un fichier que vous avez extrait du contrôle du code source, celle-ci se limite à la version du fichier qui a été téléchargée sur votre ordinateur local.  
  
 **Regarder dans**  
 Sélectionnez une étendue de recherche prédéfinie dans cette liste ou entrez votre propre ensemble de répertoires à l’aide de la boîte de dialogue **Choisir des dossiers de recherche**.  
  
 **Document actif**  
 Cette option est disponible lorsqu'un document est ouvert dans un éditeur. Elle recherche la chaîne spécifiée dans **Rechercher** dans le document actif uniquement.  
  
 **Tous les documents ouverts**  
 Effectue la recherche dans tous les fichiers actuellement ouverts à des fins d'édition.  
  
 **Projet en cours**  
 Effectue la recherche dans tous les fichiers du projet en cours.  
  
 **Solution complète**  
 Effectue la recherche dans tous les fichiers de la solution active.  
  
 **Inclure les sous-dossiers**  
 Indique que les sous-dossiers du dossier spécifié dans **Regarder dans** doivent être inclus dans la recherche. Cette option requiert un ensemble de répertoires personnalisé.  
  
 **Parcourir**  
 Cliquez sur ce bouton pour afficher la boîte de dialogue **Choisir des dossiers de recherche**, qui vous permet d’assembler, de modifier, d’enregistrer et de sélectionner des ensembles nommés de répertoires à entrer dans la zone **Regarder dans**.  
  
## Options de recherche  
 Vous pouvez développer ou réduire la section **Options de recherche**. Les options ci-après peuvent être activées ou désactivées.  
  
 **Respecter la casse**  
 Lorsque cette case est cochée, les fenêtres de résultats de la recherche n’affichent que les instances de la chaîne spécifiée dans **Rechercher** qui concordent avec le contenu et la casse. Par exemple, une recherche de **MyObject** lorsque la case **Respecter la casse** est cochée retourne « MyObject », mais pas « myobject », ni « MYOBJECT ».  
  
 **Mot entier**  
 Quand cette case est cochée, les fenêtres de résultats de la recherche n’affichent que les instances de la chaîne spécifiée dans **Rechercher** qui concordent avec les mots entiers. Si vous recherchez **MonObjet**, par exemple, « MonObject » est retourné comme résultat, mais pas « CMonObjet » ou « MonObjetC ».  
  
 **Utiliser**  
 Indique comment interpréter les caractères spéciaux qui sont entrés dans les zones de texte **Rechercher** et **Remplacer par**. Les options comprennent **Caractères génériques** et **Expressions régulières**.  
  
 **Expressions régulières**  
 Des notations spéciales définissent des modèles de texte pour les concordances. Pour obtenir la liste, consultez [Rechercher du texte avec des expressions régulières](../../relational-databases/scripting/search-text-with-regular-expressions.md).  
  
 **Caractères génériques**  
 Les caractères spéciaux tels que les astérisques (`*`) et les points d'interrogation (`?`) représentent un ou plusieurs caractères. Pour obtenir la liste, consultez [Rechercher du texte avec des caractères génériques](../../relational-databases/scripting/search-text-with-wildcards.md).  
  
 **Examiner ces types de fichiers**  
 Cette liste indique les types de fichiers auxquels la recherche doit être appliquée dans les répertoires spécifiés dans **Regarder dans**. Si ce champ est vide, la recherche est étendue à tous les fichiers des répertoires spécifiés dans **Regarder dans**.  
  
```  
*.[ext]; *.[ext] (manual)  
```  
  
 Pour effectuer une recherche dans des fichiers d'un type particulier, entrez un astérisque (`*`) pour le nom de fichier, suivi d'un point (`.`) et de l'extension de fichier. Pour spécifier plusieurs types de fichiers, entrez plusieurs chaînes de recherche séparées par un point-virgule (`;`).  
  
```  
*.[ext]; *.[ext] (from list)  
```  
  
 Sélectionnez n'importe quel élément dans la liste pour entrer une chaîne de recherche préconfigurée qui retrouvera des fichiers de types particuliers.  
  
## Options de résultat  
 Détermine l’emplacement des résultats lorsque vous cliquez sur **Rechercher tout**. Vous pouvez développer ou réduire la section **Options de résultat**. Les options ci-après peuvent être activées ou désactivées.  
  
 **Fen. Résultats de la recherche 1**  
 Lorsque cette case à cocher est activée, les résultats de la recherche actuelle sont ajoutés au contenu de la fenêtre Résultats de la recherche 1. Cette fenêtre s'ouvre automatiquement pour afficher vos résultats de recherche. Pour l’ouvrir manuellement, cliquez sur **Autres fenêtres** dans le menu **Affichage**, puis cliquez sur **Résultats de la recherche 1**.  
  
 **Fen. Résultats de la recherche 2**  
 Lorsque cette case à cocher est activée, les résultats de la recherche actuelle sont ajoutés au contenu de la fenêtre Résultats de la recherche 2. Cette fenêtre s'ouvre automatiquement pour afficher vos résultats de recherche. Pour l’ouvrir manuellement, cliquez sur **Autres fenêtres** dans le menu **Affichage**, puis cliquez sur **Résultats de la recherche 2**.  
  
 **Afficher les noms des fichiers seulement**  
 Affiche une entrée par fichier contenant une concordance plutôt qu'une entrée par concordance dans la fenêtre Résultats de la recherche 1 ou Résultats de la recherche 2. Cette option n'est pas disponible dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 **Conserver les fichiers modifiés ouverts après un remplacement global**  
 Lorsque cette option est activée, tous les fichiers dans lesquels des remplacements ont été effectués restent ouverts afin que vous puissiez annuler ou enregistrer ces modifications. Les contraintes de mémoire peuvent limiter le nombre de fichiers qui peuvent rester ouverts suite à une opération de remplacement.  
  
> [!CAUTION]  
>  Vous ne pouvez utiliser la commande **Annuler** qu’avec les fichiers qui restent ouverts à des fins d’édition. Si vous n’activez pas cette option, les fichiers qui n’étaient pas ouverts à des fins d’édition restent fermés et l’option **Annuler** n’est pas disponible pour ces fichiers.  
  
## Vues Rechercher et remplacer  
 Les onglets situés en haut de la fenêtre Rechercher et remplacer comprennent les menus **Affichage**. Ces menus vous permettent de choisir un ensemble de champs à afficher dans le volet actif. Vous pouvez laisser la fenêtre Rechercher et remplacer ancrée à un endroit qui vous convient, puis effectuer des modifications au niveau des onglets et des vues pour exécuter tout type d'opération de recherche ou de remplacement.  
  
 **Recherche rapide**  
 Cet onglet de barre d’outils remplace la boîte de dialogue par celle intitulée **Recherche rapide**.  
  
 **Rechercher dans les fichiers**  
 Cet onglet de barre d’outils remplace la boîte de dialogue par celle intitulée **Rechercher dans les fichiers**.  
  
 **Rechercher un symbole**  
 Cet onglet de barre d’outils remplace la boîte de dialogue par celle intitulée **Rechercher un symbole**.  
  
## Voir aussi  
 [Raccourcis clavier dans SQL Server Management Studio](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md)  
  
  