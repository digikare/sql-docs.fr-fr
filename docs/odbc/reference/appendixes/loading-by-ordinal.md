---
title: Le chargement par Ordinal | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ef22486a7cbd9932c90069f461b83358c2db8fd4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="loading-by-ordinal"></a>Chargement par Ordinal
Dans ODBC 2. *x*, le chargement par ordinal pu être effectué pour améliorer les performances du processus de connexion. Une application ODBC 2. *x* pilote exporte une fonction factice avec l’ordinal 199 ; lorsque le Gestionnaire de pilote détecte, il résout les adresses des fonctions ODBC par ordinal, et non par nom. Cette fonctionnalité est toujours pris en charge pour ODBC 2. *x* pilotes mais n’est ne pas pris en charge pour ODBC 3*.x* pilotes.