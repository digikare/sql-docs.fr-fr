---
title: La propriété du flux | Documents Microsoft
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
- ADOStreamConstruction::GetStream
- ADOStreamConstruction::PutStream
- ADOStreamConstruction::put_Stream
- ADOStreamConstruction::Stream
- ADOStreamConstruction::get_Stream
helpviewer_keywords:
- Stream property
ms.assetid: 4a44f9f6-0265-4c00-8def-d85b6af923b1
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd848306588cba57a25e0a8e7e8a45ab5c563766
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="stream-property"></a>Propriété de flux de données
Obtient ou définit un OLE DB **flux** objet à partir de/sur un **ADOStreamConstruction** objet.  
  
 En lecture/écriture.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT get_Stream([out, retval] IUnknown** ppStream);  
HRESULT put_Stream([in] IUnknown* pStream);  
```  
  
## <a name="parameters"></a>Paramètres  
 *ppStream*  
 Pointeur vers un OLE DB **flux** objet.  
  
 *pStream*  
 OLE DB **flux** objet.  
  
## <a name="return-values"></a>Valeurs de retour  
 Cette méthode de propriété renvoie les valeurs HRESULT standards. Cela inclut le S_OK et E_FAIL.  
  
## <a name="applies-to"></a>S'applique à  
 [ADOStreamConstruction, interface](../../../ado/reference/ado-api/adostreamconstruction-interface.md)
