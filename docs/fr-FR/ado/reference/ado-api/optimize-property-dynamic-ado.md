---
title: Optimiser la propriété dynamique (ADO) | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Optimize property [ADO]
ms.assetid: a491c4ce-2b04-4c84-be83-3846bde8d16b
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3512f1a63ae92ce75990f63caabf80a83099c149
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="optimize-property-dynamic-ado"></a>Optimiser la propriété dynamique (ADO)
Spécifie si un index doit être créé sur un [champ](../../../ado/reference/ado-api/field-object.md).  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **booléenne** valeur qui indique si un index doit être créé.  
  
## <a name="remarks"></a>Notes  
 Un index peut améliorer les performances des opérations de recherche ou de trier les valeurs dans une [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md). L’index est interne à ADO ; Vous ne peut pas explicitement accéder ou l’utiliser dans votre application.  
  
 Pour créer un index sur un champ, définissez la **optimiser** propriété **True**. Pour supprimer l’index, définissez cette propriété sur **False**.  
  
 **Optimiser** est une propriété dynamique ajoutée à la [champ](../../../ado/reference/ado-api/field-object.md) objet [propriétés](../../../ado/reference/ado-api/properties-collection-ado.md) collection lorsque le [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) est définie sur **adUseClient**.  
  
## <a name="usage"></a>Utilisation  
  
```  
Dim rs As New Recordset  
Dim fld As Field  
rs.CursorLocation = adUseClient      'Enable index creation  
rs.Fields.Append "Field1", adChar, 35, adFldIsNullable  
rs.Open  
Set fld = rs.Fields(0)  
fld.Properties("Optimize") = True    'Create an index  
fld.Properties("Optimize") = False   'Delete an index  
```  
  
## <a name="applies-to"></a>S'applique à  
 [Field, objet](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Optimiser la propriété Exemple (VB)](../../../ado/reference/ado-api/optimize-property-example-vb.md)   
 [Optimiser l’exemple de propriété (VC ++)](../../../ado/reference/ado-api/optimize-property-example-vc.md)   
 [Filter, propriété](../../../ado/reference/ado-api/filter-property.md)   
 [Find (méthode) (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Sort, propriété](../../../ado/reference/ado-api/sort-property.md)
