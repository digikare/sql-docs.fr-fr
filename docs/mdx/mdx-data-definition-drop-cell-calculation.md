---
title: Instruction DROP CELL CALCULATION (MDX) | Documents Microsoft
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
- Calculation
- DROP
- DROP_CELL_CALCULATION
- CELL CALCULATION
- DROP CELL
- cell
- DROP CELL CALCULATION
dev_langs:
- kbMDX
helpviewer_keywords:
- deleting calculations
- dropping calculations
- removing calculations
- DROP CELL CALCULATION statement
- calculations [SQL Server]
- cubes [Analysis Services], calculations
ms.assetid: 77caedf4-dd96-4eac-a5e4-fd82148a44a7
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b1b5f11a1a2a827b7e7f1a607254220956298a4e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---drop-cell-calculation"></a>Définition de données MDX - DROP CELL CALCULATION
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Supprime le calcul de cellule spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP [ SESSION ] CELL CALCULATION CURRENTCUBE | Cube_Name.CellCalc_Name  
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Chaîne d'expression valide qui précise le nom d'une expression de cube.  
  
 *CellCalc_Name*  
 Chaîne d'expression valide qui précise le nom d'un calcul de cellule à supprimer.  
  
## <a name="see-also"></a>Voir aussi  
 [CRÉER une instruction de calcul de cellule & #40 ; MDX & #41 ;](../mdx/mdx-data-definition-create-cell-calculation.md)   
 [Instructions MDX de définition de données &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
