---
title: "Méthode getBlob (int) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerCallableStatement.getBlob (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bef3ef12-cdda-4a18-90d6-4a501b8e30f0
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7de04a59b86448deabf7d2ffb3bcfa0668e699ab
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getblob-method-int"></a>Méthode getBlob (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du paramètre BLOB JDBC désigné en tant qu’objet Blob dans le langage de programmation Java fonction de l’index de paramètre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Blob getBlob(int index)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 Un **int** qui indique l’index de paramètre.  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet Blob.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getBlob est spécifiée par la méthode getBlob dans l’interface java.sql.CallableStatement.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getBlob &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getblob-method-sqlservercallablestatement.md)   
 [Membres de SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement, classe](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  