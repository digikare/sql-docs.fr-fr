---
title: "Étape 5 : Test de la leçon 4 du Package du didacticiel | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 5f18df92-0248-4858-836b-c8b02f0e0439
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 68e4545ee2eae96664007a8dc69c9953c0351107
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="lesson-4-5---testing-the-lesson-4-tutorial-package"></a>Leçon 4-5-test de la leçon 4 du Package du didacticiel
Au moment de l'exécution, le fichier corrompu, Currency_BAD.txt, ne parvient pas à générer une correspondance avec la transformation de recherche Currency Key. Du fait que la sortie d'erreur de la transformation de recherche Currency Key a été configurée en vue de réacheminer les lignes qui ont échoué vers une nouvelle destination de lignes échouées, le composant n'échoue pas et le package s'exécute correctement. Toutes les lignes qui ont échoué sont enregistrées dans le fichier ErrorOutput.txt.  
  
Au cours de cette tâche, vous allez tester la configuration de sortie d'erreur révisée en exécutant le package. Une fois le package exécuté, vous visualiserez le contenu du fichier ErrorOutput.txt.  
  
> [!NOTE]  
> Pour éviter l'accumulation de lignes d'erreur dans le fichier ErrorOutput.txt, vous devez manuellement supprimer le contenu du fichier entre chaque exécution du package.  
  
## <a name="checking-the-package-layout"></a>Vérification de la disposition du package  
Avant de tester le package, vous devez vérifier que le flux de contrôle et le flux de données dans le package de la leçon 4 contiennent les objets affichés dans les diagrammes suivants. Le flux de contrôle doit être identique au flux de contrôle des leçons 2 à 4.  
  
**Flux de contrôle**  
  
![Contrôler le flux de package](../integration-services/media/task4lesson2control.gif "contrôler le flux de package")  
  
**Flux de données**  
  
![Flux de données dans le package](../integration-services/media/task5lesson5data.gif "dans le package de flux de données")  
  
### <a name="to-run-the-lesson-4-tutorial-package"></a>Pour exécuter le package du didacticiel Lesson 4  
  
1.  Dans le menu **Déboguer** , cliquez sur **Démarrer le débogage**.  
  
2.  Une fois l'exécution du package terminée, dans le menu **Déboguer** , cliquez sur **Arrêter le débogage**.  
  
### <a name="to-verify-the-contents-of-the-erroroutputtxt-file"></a>Pour vérifier le contenu du fichier ErrorOutput.txt  
  
-   Dans le Bloc-notes ou un autre éditeur de texte, ouvrez le fichier ErrorOutput.txt. L'ordre par défaut des colonnes est le suivant : AverageRate, CurrencyID, CurrencyDate, EndOfDateRate, ErrorCode, ErrorColumn, ErrorDescription.  
  
    Notez que toutes les lignes du fichier contiennent la valeur CurrencyID non appariée définie à BAD, la valeur ErrorCode définie à -1071607778, la valeur ErrorColumn définie à 0 et la valeur ErrorDescription dévoilant le message « Aucune correspondance de ligne trouvée au cours de la recherche ». La valeur de ErrorColumn est définie à 0 puisque l'erreur n'est pas liée à une colonne. C'est l'opération de recherche qui a échoué. .  
  
  
  
