---
title: Méthode SetEOS | Documents Microsoft
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
f1_keywords:
- _Stream::raw_SetEOS
- _Stream::SetEOS
helpviewer_keywords:
- SetEOS method [ADO]
ms.assetid: 707c18ca-6a56-4970-bbd6-ae1fb86a0b8a
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3506ae0c62172461633df100c32bec73ea4af9f5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="seteos-method"></a>SetEOS, méthode
Définit la position qui représente la fin du flux de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.SetEOS  
```  
  
## <a name="remarks"></a>Notes  
 **SetEOS** met à jour la valeur de la [fin du support](../../../ado/reference/ado-api/eos-property.md) propriété, en rendant actuel [Position](../../../ado/reference/ado-api/position-property-ado.md) la fin du flux de données. Tous les octets ou caractères après la position actuelle sont tronqués.  
  
 Étant donné que [écrire](../../../ado/reference/ado-api/write-method.md), [WriteText](../../../ado/reference/ado-api/writetext-method.md), et [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) ne pas tronquer les valeurs supplémentaires existant **flux** des objets, vous pouvez tronquer ces octets ou caractères en définissant la nouvelle position de fin de flux avec **SetEOS**.  
  
> [!CAUTION]
>  Si vous définissez **fin du support** à une position avant la fin du flux de données, vous perdrez toutes les données une fois que le nouvel **fin du support** position.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
