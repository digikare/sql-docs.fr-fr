---
title: "Activer l&#39;option Lock Pages in Memory (Windows) | Microsoft Docs"
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
  - "lock pages in memory (option)"
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Activer l&#39;option Lock Pages in Memory (Windows)
  Cette stratégie Windows détermine quels comptes peuvent utiliser un processus destiné à conserver les données en mémoire physique pour éviter leur pagination en mémoire virtuelle sur le disque.  
  
> [!NOTE]  
>  Le verrouillage des pages en mémoire permet d'optimiser les performances lorsque la pagination de la mémoire sur disque est prévue.  
  
 L'outil Stratégie de groupe de Windows (gpedit.msc) vous permet d'activer cette stratégie pour le compte utilisé par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous devez être administrateur système pour modifier cette stratégie.  
  
### Pour activer l'option Verrouiller les pages en mémoire  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**. Dans la zone **Ouvrir** , tapez **gpedit.msc**.  
  
2.  Sur la console **Éditeur de stratégie de groupe locale** , développez **Configuration ordinateur**, puis **Paramètres Windows**.  
  
3.  Développez **Paramètres de sécurité**, puis **Stratégies locales**.  
  
4.  Sélectionnez le dossier **Attribution des droits utilisateur** .  
  
     Les stratégies s'affichent dans le volet Détails.  
  
5.  Dans le volet, double-cliquez sur **Verrouiller les pages en mémoire**.  
  
6.  Dans la boîte de dialogue **Paramètre de sécurité locale – Verrouiller les pages en mémoire** , cliquez sur **Ajouter un utilisateur ou un groupe**.  
  
7.  Dans la boîte de dialogue **Sélectionner des utilisateurs, des comptes de service ou des groupes** , ajoutez un compte avec les privilèges nécessaires pour exécuter sqlservr.exe.  
  
8.  Fermez la session, puis rouvrez-la pour que cette modification prenne effet.  
  
## Voir aussi  
 [Mémoire du serveur (option de configuration de serveur)](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  