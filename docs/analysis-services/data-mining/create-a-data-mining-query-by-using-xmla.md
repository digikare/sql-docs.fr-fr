---
title: "Cr&#233;er une requ&#234;te d’exploration de donn&#233;es en utilisant XMLA | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "requêtes de contenu [DMX]"
ms.assetid: 8f6b6008-006c-4792-9bd1-64c30dc3fd41
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 11
---
# Cr&#233;er une requ&#234;te d’exploration de donn&#233;es en utilisant XMLA
  Vous pouvez créer diverses requêtes sur les objets d'exploration de données en utilisant AMO, DMX ou XML/A.  
  
 XML est utilisé pour les communications entre le serveur Analysis Services et tous les clients. Par conséquent, bien qu'il soit en général beaucoup plus facile de créer des requêtes de contenu à l'aide de DMX, vous pouvez écrire des requêtes à l'aide des instructions DISCOVER et COMMAND en XML/A, en utilisant un client qui prend en charge le protocole SOAP ou en créant une requête XML/A dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Cette rubrique explique comment utiliser les modèles XML/A qui sont disponibles dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer une requête de contenu du modèle sur un modèle d’exploration de données stocké sur le serveur actuel.  
  
## Interrogation des ensembles de lignes de schéma d'exploration de données à l'aide de XML/A  
  
#### Pour ouvrir un modèle XML/A  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], dans le menu **Affichage** , cliquez sur **Explorateur de modèles**.  
  
2.  Cliquez sur l'icône du cube pour ouvrir la liste des modèles d'Analysis Services.  
  
3.  Dans la liste des catégories de modèles, développez **XMLA**, développez **Ensembles de lignes de schéma**, puis double-cliquez sur **Découvrir les ensembles de lignes du schéma** pour ouvrir le modèle dans l’éditeur de code approprié.  
  
4.  Dans la boîte de dialogue **Se connecter à Analysis Services** , fournissez les informations de connexion, puis cliquez sur **Se connecter**. Une nouvelle fenêtre de l'éditeur de requête s'affiche avec le modèle **Découvrir les ensembles de lignes du schéma** .  
  
#### Pour découvrir les noms des colonnes à partir de l'ensemble de lignes de schéma MINING MODEL CONTENT  
  
1.  Avec le modèle **Découvrir les ensembles de lignes du schéma** ouvert, cliquez **Exécuter**.  
  
     Une liste d'ensembles de lignes de schéma est retournée dans le volet **Résultats** qui contient les noms et les colonnes des ensembles de lignes disponibles sur l'instance actuelle.  
  
2.  Dans le volet **Requête**, placez le curseur après **\<Liste de restrictions>** et appuyez sur Entrée pour ajouter une nouvelle ligne.  
  
3.  Placez le curseur sur la ligne vide et tapez **\<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT\</SchemaName>**  
  
     La section complète relative aux restrictions doit s'afficher comme suit :  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<SchemaName>DMSCHEMA_MINING_MODEL_CONTENT</SchemaName>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
4.  Cliquez sur **Exécuter**.  
  
     Le volet **Résultats** affiche une liste de noms de colonnes pour l'ensemble de lignes de schéma spécifié.  
  
#### Pour créer une requête de contenu à partir de l'ensemble de lignes de schéma MINING MODEL CONTENT  
  
1.  Dans le modèle **Découvrir les ensembles de lignes du schéma** , modifiez le type de requête en remplaçant le texte à l'intérieur des balises de type de requête.  
  
     Remplacez cette ligne :  
  
     `<RequestType>DISCOVER_SCHEMA_ROWSETS</RequestType>`  
  
     par la ligne suivante :  
  
     **\<RequestType>DMSCHEMA_MINING_MODEL_CONTENT\</RequestType>**  
  
2.  Modifiez la liste de restriction pour spécifier un modèle d'exploration de données par nom, en ajoutant une nouvelle condition aux listes de restriction.  
  
3.  Dans le modèle, placez le curseur après `<Restriction List>` et appuyez sur Entrée pour ajouter une nouvelle ligne.  
  
4.  Placez le curseur sur la ligne vide et tapez **<MODEL_NAME>Mon nom de modèle</MODEL_NAME>**  
  
     La section complète relative aux restrictions doit s'afficher comme suit :  
  
     `<Restrictions>`  
  
     `<RestrictionList>`  
  
     `<MODEL_NAME>My model name</MODEL_NAME>`  
  
     `</RestrictionList>`  
  
     `</Restrictions>`  
  
5.  Cliquez sur **Exécuter**.  
  
     Le volet Résultats affiche la définition de schéma ainsi que les valeurs du modèle spécifié.  
  
## Voir aussi  
 [Contenu du modèle d’exploration &#40;Analysis Services - Exploration de données&#41;](../../analysis-services/data-mining/mining-model-content-analysis-services-data-mining.md)   
 [Ensembles de lignes de schéma d'exploration de données](../../analysis-services/schema-rowsets/data-mining/data-mining-schema-rowsets.md)  
  
  