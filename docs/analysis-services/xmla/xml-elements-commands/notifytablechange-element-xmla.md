---
title: Élément NotifyTableChange (XMLA) | Documents Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6b379fde8b0561af0af41cabcef1b91adf459a26
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="notifytablechange-element-xmla"></a>Élément NotifyTableChange (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  Notifie une instance de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] qu'une modification a été apportée à des tables dans une source de données spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
  
<Command>  
   <NotifyTableChange>  
      <Object>...</Object>  
      <TableNotifications>...</TableNotifications>  
   </NotifyTableChange>  
</Command>  
```  
  
## <a name="element-characteristics"></a>Caractéristiques de l'élément  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Type de données et longueur|Aucune|  
|Valeur par défaut|Aucune|  
|Cardinalité|0-n : élément facultatif pouvant apparaître plusieurs fois.|  
  
## <a name="element-relationships"></a>Relations entre les éléments  
  
|Relation|Élément|  
|------------------|-------------|  
|Éléments parents|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|Éléments enfants|[Object](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md), [TableNotifications](../../../analysis-services/xmla/xml-elements-properties/tablenotifications-element-xmla.md)|  
  
## <a name="remarks"></a>Notes  
 Le **NotifyTableChange** commande permet à une application cliente notifier explicitement une [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] de l’instance que l’une ou plusieurs tables contenues dans une source de données ont été modifiés. Pour la mise en cache proactive, cette notification indique que les objets OLAP relationnels (ROLAP) basés sur ces tables doivent être examinés et mis à jour.  
  
 Cette méthode de notification convient le mieux aux objets ROLAP basés sur des vues ou des requêtes nommées définies dans une vue de source de données dont les modifications peuvent être délicates à détecter et suivre.  
  
 Le **objet** doit faire référence à une source de données dans le [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] base de données. Si l'élément **Object** fait référence à un objet autre qu'une source de données, une erreur survient.  
  
 Pour plus d’informations sur la mise en cache proactive, consultez [Mise en cache proactive &#40;partitions&#41;](../../../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes & #40 ; XMLA & #41 ;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
