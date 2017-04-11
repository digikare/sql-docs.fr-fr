---
title: "Validation (Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98eb49e7-b190-4a21-8316-08c07cde14ed
caps.latest.revision: 12
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 12
---
# Validation (Master Data Services)
  Dans [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], les données sont validées pour en garantir l'exactitude. Une partie de la validation s'effectue automatiquement, tandis qu'une autre partie est basée sur des règles d'entreprise créées par les administrateurs.  
  
## Occurrences de la validation des données  
 La validation se produit à différents moments et s'affiche de différentes manières dans l'application Web [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
|Type de validation|Standards déterminés par|Lorsqu'elle se produit|Affichée dans l'interface utilisateur Web du gestionnaire de MasterData en tant que|Affichée dans le complément pour Excel en tant que|Les données sont-elles enregistrées dans le référentiel MDS ?|  
|---------------------|-----------------------------|--------------------|---------------------------------------------------|-------------------------------------------|------------------------------------------|  
|Validation de la règle d'entreprise|Administrateur MDS|Automatiquement lorsqu'un utilisateur ajoute ou modifie des données.<br /><br /> Manuellement lorsqu'un utilisateur applique des règles d'entreprise.<br /><br /> Manuellement, lorsqu'un administrateur dans la zone fonctionnelle **Gestion des versions** de l'application Web [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] valide une version par rapport aux règles d'entreprise.|Erreurs de validation|ValidationStatus|Oui|  
|Validation de type de données et de contenu|Un administrateur MDS, en créant des objets de modèle (par exemple, la longueur ou le type de données d'un attribut)|Automatiquement lorsqu'un utilisateur ajoute ou modifie des données.|Erreurs d'entrée|InputStatus|Non|  
|Validation de type de données et de contenu|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ou [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|Automatiquement lorsqu'un utilisateur ajoute ou modifie des données.|Erreurs d'entrée|InputStatus|Non|  
  
## Tâches associées  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Créer et publier des règles d'entreprise par rapport auxquelles valider des données.|[Créer et publier une règle d’entreprise &#40;Master Data Services&#41;](../master-data-services/create-and-publish-a-business-rule-master-data-services.md)|  
|Valider une version des données par rapport aux règles d'entreprise. Administrateurs uniquement.|[Valider une version par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)|  
|Valider des sous-ensembles de données spécifiques par rapport aux règles d'entreprise. Tous les utilisateurs autorisés à accéder à la zone fonctionnelle **Explorateur** .|[Valider des membres spécifiques par rapport aux règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)|  
|Valider des sous-ensembles de données spécifiques par rapport aux règles d'entreprise. Tous les utilisateurs autorisés à accéder à la zone fonctionnelle **Explorateur** et utilisant [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].|[Appliquer des règles d’entreprise &#40;Complément MDS pour Excel&#41;](../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
  
## Voir aussi  
 [Règles d’entreprise &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  