---
title: "Ajouter la logique m&#233;tier aux donn&#233;es XML | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-xml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "logique métier [XML]"
ms.assetid: 0877fb38-f1a2-43d8-86cf-4754be224dc1
caps.latest.revision: 18
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 18
---
# Ajouter la logique m&#233;tier aux donn&#233;es XML
  Votre logique métier peut être ajoutée aux données XML de plusieurs manières :  
  
-   Vous pouvez écrire des contraintes sur les lignes ou les colonnes de façon à imposer des contraintes propres à un domaine lors de l'insertion et de la modification des données XML.  
  
-   Vous pouvez écrire un déclencheur sur la colonne XML qui est activé lors de l'insertion ou de la mise à jour de valeurs dans la colonne. Le déclencheur peut contenir des règles de validation propres au domaine ou remplir les tables de propriétés.  
  
-   Le moteur de base de données permet l'exécution de code managé. Vous pouvez utiliser cette intégration au CLR (Common Language Runtime) pour écrire des fonctions dans le code managé auxquelles vous transmettez des valeurs XML et utiliser les capacités de traitement fournies par l’espace de noms System.Xml. Vous pouvez, par exemple, appliquer une transformation XSL aux données XML. Vous pouvez également désérialiser le code XML en une ou plusieurs classes managées et travailler sur ces classes à l'aide de code managé.  
  
-   Vous pouvez écrire des procédures stockées et des fonctions Transact-SQL pour lancer le traitement sur la colonne XML en fonction de vos besoins.  
  
## Exemple : application XSLT  
 Prenez l’exemple d’une fonction CLR **TransformXml()** qui accepte une instance de type de données **xml** et une transformation XSL stockée dans un fichier, applique la transformation aux données XML, puis retourne les données XML transformées dans le résultat. Le code suivant est un squelette de fonction écrit en C# :  
  
```  
public static SqlXml TransformXml (SqlXml XmlData, string xslPath) {  
   // Load XSL transformation  
   XslCompiledTransform xform = new XslCompiledTransform();  
   XPathDocument xslDoc = new XPathDocument (xslPath);  
   xform.Load(xslDoc);  
  
   // Load XML data   
   XPathDocument xDoc = new XPathDocument (XmlData.CreateReader());  
  
   // Return the transformed value  
   MemoryStream xsltResult = new MemoryStream();  
   xform.Transform(xDoc, null, xsltResult);  
   SqlXml retSqlXml = new SqlXml(xsltResult);  
   return (retSqlXml);  
}   
```  
  
 Après l’enregistrement de l’assembly et la création d’une fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] définie par l’utilisateur, **SqlXslTransform()** correspondant à **TransformXml()**, la fonction peut être appelée à partir de Transact-SQL, comme le montre la requête suivante :  
  
```  
SELECT SqlXslTransform (xCol, 'C:\MyFile\xsltransform.xsl')  
FROM    T  
WHERE  xCol.exist('/book/title/text()[contains(.,"custom")]') =1;  
```  
  
 Le résultat de la requête contient un ensemble de lignes pour le code XML transformé.  
  
 L’intégration CLR dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] étend les possibilités de décomposition des données XML en tables ou en promotion de propriétés, et d’interrogation des données XML en utilisant les classes managées de l’espace de noms System.Xml. Pour plus d’informations, consultez [Données XML &#40;SQL Server&#41;](../../relational-databases/xml/xml-data-sql-server.md).  
  
  