---
title: Dimensions (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Dimensions
dev_langs:
- kbMDX
helpviewer_keywords:
- Dimensions function
ms.assetid: 64f63aa0-ef74-4415-a0c9-8acc6cd81739
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 2f0c3ea111eafd55f4fc1f0a0eacc0993ef0d713
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="dimensions-mdx"></a>Dimensions (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne la hiérarchie spécifiée par une expression numérique ou de chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Numeric expression syntax  
Dimensions(Hierarchy_Number)  
  
String expression syntax  
Dimensions(Hierarchy_Name)  
```  
  
## <a name="arguments"></a>Arguments  
 *Hierarchy_Number*  
 Expression numérique valide qui spécifie un numéro de hiérarchie.  
  
 *Hierarchy_Name*  
 Expression de chaîne valide qui spécifie un nom de hiérarchie.  
  
## <a name="remarks"></a>Notes  
 Si un numéro de hiérarchie est spécifié, la **Dimensions** fonction retourne une hiérarchie dont la position de base zéro dans le cube est spécifiée de numéro de hiérarchie.  
  
 Si un nom de hiérarchie est spécifié, la **Dimensions** fonction retourne la hiérarchie spécifiée. En général, vous utilisez cette version de chaîne de la **Dimensions** fonction avec les fonctions définies par l’utilisateur.  
  
> [!NOTE]  
>  Le **mesures** dimension est toujours représentée par `Dimensions(0)`.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants utilisent le **Dimensions** fonction pour retourner le nom, le nombre de niveaux et le nombre de membres d’une hiérarchie spécifiée, à l’aide d’une expression numérique et une expression de chaîne.  
  
```  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Levels.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions  
   ('[Product].[Product Model Lines]').Members.Count  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Name  
SELECT Measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Levels.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
  
WITH MEMBER Measures.x AS Dimensions(0).Members.Count  
SELECT measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)  
  
  
