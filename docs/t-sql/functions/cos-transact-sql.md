---
title: COS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COS
- COS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- cosine
- COS function
ms.assetid: c9fa8ae1-3373-4f3e-9b97-fa05077c1040
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: a54e9376a84e42baf400e08750c72c4e14eea382
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="cos-transact-sql"></a>COS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Fonction mathématique qui renvoie le cosinus trigonométrique de l'angle spécifié, exprimé en radians, dans l'expression spécifiée.
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
COS ( float_expression )  
```  
  
## <a name="arguments"></a>Arguments  
*float_expression*  
[Expression](../../t-sql/language-elements/expressions-transact-sql.md) de type **float**.
  
## <a name="return-types"></a>Types de retour
**float**
  
## <a name="examples"></a>Exemples  
L'exemple suivant renvoie le cosinus de l'angle indiqué.
  
```sql
DECLARE @angle float;  
SET @angle = 14.78;  
SELECT 'The COS of the angle is: ' + CONVERT(varchar,COS(@angle));  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
The COS of the angle is: -0.599465                        
  
(1 row(s) affected)  
```  

## <a name="examples"></a>Exemples
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  


L'exemple suivant renvoie le cosinus de l'angle indiqué.
  
```sql
SELECT COS(14.76) AS cosCalc1, COS(-0.1472738) AS cosCalc2;   
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
cosCalc1  cosCalc2
--------  --------
-0.58     0.99
```
  
## <a name="see-also"></a>Voir aussi
[Fonctions mathématiques &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)
  
  

