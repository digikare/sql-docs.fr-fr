---
title: Annotations XSD (SQLXML 4.0) | Documents Microsoft
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- annotated XSD schemas, annotations listed
- XSD schemas [SQLXML], annotations
ms.assetid: c62a6785-8d66-40a2-9c5d-80c73d600a3b
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 329cf82052fe6bb6f90bbc0ca858f21b3a16a69a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="xsd-annotations-sqlxml-40"></a>Annotations XSD (SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]Le tableau suivant répertorie les annotations XSD introduites dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]et les compare avec les annotations XDR introduites dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
|Annotation XSD| Description|Lien de rubrique|Annotation XDR|  
|--------------------|-----------------|----------------|--------------------|  
|**SQL : encoder**|Lorsqu'un élément ou un attribut XML est mappé à une colonne BLOB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], autorise la demande d'un URI de référence. Cet URI peut être utilisé ultérieurement pour retourner les données BLOB.|[Demande de références URL à des données d’objet BLOB à l’aide de sql : encode &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/requesting-url-references-to-blob-data-using-sql-encode-sqlxml-4-0.md)|**URL-encode**|  
|**SQL : GUID**|Vous permet de spécifier s'il convient d'utiliser une valeur GUID générée par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d'utiliser la valeur fournie dans le code de mise à jour (updategram) pour cette colonne.|[Utilisation des annotations sql:identity et sql:guid](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Non pris en charge|  
|**SQL : Hide**|Masque l'élément ou l'attribut spécifié dans le schéma dans le document XML résultant.|[Masquage d’éléments et d’attributs à l’aide de sql:hide](../../relational-databases/sqlxml-annotated-xsd-schemas-using/hiding-elements-and-attributes-by-using-sql-hide.md)|Non pris en charge|  
|**SQL : Identity**|Peut être spécifié sur un nœud quelconque qui est mappé à une colonne de base de données de type IDENTITY. La valeur spécifiée pour cette annotation définit comment la colonne de type IDENTITY correspondante dans la base de données est mise à jour.|[Utilisation des annotations sql:identity et sql:guid](../../relational-databases/sqlxml-annotated-xsd-schemas-using/using-the-sql-identity-and-sql-guid-annotations.md)|Non pris en charge|  
|**SQL : inverse**|Fait en sorte que la logique de mise à jour d’inverser son interprétation de la relation parent-enfant qui a été spécifiée à l’aide de  **\<SQL : Relationship >**.|[Spécification de l’attribut SQL : inverse sur SQL : Relationship &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-the-sql-inverse-attribute-on-sql-relationship-sqlxml-4-0.md)|Non pris en charge|  
|**SQL : constante est**|Crée un élément XML qui n'est mappé à aucune table. L'élément apparaît dans le résultat de la requête.|[Création d’éléments constants à l’aide de sql : constante est &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-constant-elements-using-sql-is-constant-sqlxml-4-0.md)|Identique|  
|**SQL : Key-champs**|Permet de spécifier une ou des colonnes qui identifient de façon unique les lignes d'une table.|[Identification des colonnes de clés à l’aide de SQL : Key-champs &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/identifying-key-columns-using-sql-key-fields-sqlxml-4-0.md)|Identique|  
|**SQL : limit-champ**<br /><br /> **SQL : limit-valeur**|Permet de limiter les valeurs retournées en fonction d'une valeur de limitation.|[Filtrage des valeurs à l’aide de SQL : limit-champ et SQL : limit-value &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/filtering-values-using-sql-limit-field-and-sql-limit-value-sqlxml-4-0.md)|Identique|  
|**SQL : mappé**|Permet à des éléments de schéma d'être exclus du résultat.|[Exclusion d’éléments de schéma du Document XML résultant avec sql : mappé &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/excluding-schema-elements-from-the-xml-document-using-sql-mapped.md)|**champ de la carte**|  
|**SQL : max-depth**|Vous permet de spécifier la profondeur dans les relations récursives spécifiées dans le schéma.|[Spécification de la profondeur dans les relations récursives à l’aide de sql:max-depth](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-depth-in-recursive-relationships-by-using-sql-max-depth.md)|Non pris en charge|  
|**SQL : Overflow-champ**|Identifie la colonne de la base de données qui contient les données de dépassement.|[La récupération des données à l’aide de SQL : Overflow-champ &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/retrieving-unconsumed-data-using-the-sql-overflow-field-sqlxml-4-0.md)|Identique|  
|**SQL : Prefix**|Crée des attributs ID, IDREF et IDREFS XML valides. Ajoute les valeurs des attributs ID, IDREF et IDREFS avec une chaîne.|[Création de SQL : Prefix valide ID, IDREF et à l’aide des attributs de Type IDREFS &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-valid-id-idref-and-idrefs-type-attributes-using-sql-prefix-sqlxml-4-0.md)|Identique|  
|**SQL : Relationship**|Spécifie des relations entre des éléments XML. Le **parent**, **enfant**, **clé parente**, et **clé enfant** attributs sont utilisés pour établir la relation.|[Spécification de relations à l’aide de SQL : Relationship &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-relationships-using-sql-relationship-sqlxml-4-0.md)|Les noms des attributs sont différents :<br /><br /> **relation de clé**<br /><br /> **relation étrangère**<br /><br /> **clé**<br /><br /> **clé étrangère**|  
|**SQL : use-cdata**|Permet de spécifier les sections CDATA à utiliser pour certains éléments dans le document XML.|[Création à l’aide des Sections CDATA de SQL : use-cdata &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/creating-cdata-sections-using-sql-use-cdata-sqlxml-4-0.md)|Identique|  
  
> [!NOTE]  
>  Natif XSD **targetNamespace** attribut remplace le **espace de noms cible** annotation a été introduite dans le [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] schéma de mappage XDR.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification d’une cible Namespace à l’aide de l’attribut targetNamespace &#40; SQLXML 4.0 &#41;](../../relational-databases/sqlxml-annotated-xsd-schemas-using/specifying-a-target-namespace-using-the-targetnamespace-attribute-sqlxml-4-0.md)  
  
  