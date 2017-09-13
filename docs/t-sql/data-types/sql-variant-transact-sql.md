---
title: sql_variant (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/23/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sql_variant
- sql_variant_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sql_variant comparisons
- storing data [SQL Server], sql_variant
- sql_variant data type
- storage [SQL Server], sql_variant
ms.assetid: 01229779-8bc1-4c7d-890a-8246d4899250
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4eb946d5b6ed5a9c6d33789166327bd2dd25d7c1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="sqlvariant-transact-sql"></a>sql_variant (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Type de données qui stocke les valeurs de divers types de données pris en charge par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
**S’applique aux**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] via [version actuelle](http://go.microsoft.com/fwlink/p/?LinkId=299658)),[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]
  
![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntaxe  
  
```sql
sql_variant  
```  
  
## <a name="remarks"></a>Notes  
**sql_variant** peut être utilisé dans des colonnes, des paramètres, des variables et des valeurs de retour des fonctions définies par l’utilisateur. **sql_variant** permet à ces objets de base de données prendre en charge les valeurs des autres types de données.
  
Une colonne de type **sql_variant** peut contenir des lignes de différents types de données. Par exemple, une colonne définie en tant que **sql_variant** peut stocker **int**, **binaire**, et **char** valeurs.
  
**sql_variant** peut avoir une longueur maximale de 8 016 octets. Cela inclut les informations du type de base et la valeur du type de base. La longueur maximale de la valeur de type de base réelle est de 8 000 octets.
  
A **sql_variant** type de données doit tout d’abord être converti à sa valeur de type de base de données avant de participer aux opérations telles que l’addition et la soustraction.
  
**sql_variant** peut être affectée à une valeur par défaut. Ce type de données accepte également les valeurs NULL comme valeurs sous-jacentes, mais ces dernières ne seront pas associées à un type de base. En outre, **sql_variant** ne peut pas avoir une autre **sql_variant** comme type de base.
  
Une clé unique, primaire ou étrangère peut inclure des colonnes de type **sql_variant**, mais la longueur totale des valeurs de données qui composent la clé d’une ligne spécifique ne doit pas être supérieure à la longueur maximale d’un index. Cette longueur est de 900 octets.
  
Une table peut avoir un nombre quelconque de **sql_variant** colonnes.
  
**sql_variant** ne peut pas être utilisé dans CONTAINSTABLE et FREETEXTTABLE.
  
ODBC ne prennent pas en charge **sql_variant**. Par conséquent, les requêtes de **sql_variant** colonnes sont retournées en tant que données binaires lorsque vous utilisez fournisseur Microsoft OLE DB pour ODBC (MSDASQL). Par exemple, un **sql_variant** colonne qui contient les données de chaîne de caractères « PS2091 » est retournée sous la forme 0 x 505332303931.
  
## <a name="comparing-sqlvariant-values"></a>Comparaison des valeurs sql_variant  
Le **sql_variant** type de données situé tout en haut de la liste de hiérarchie de type de données pour la conversion. Pour **sql_variant** les comparaisons, les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ordre de hiérarchie de type de données est regroupé dans des familles de types de données.
  
|Hiérarchie des types de données|Famille de types de données|  
|---|---|
|**sql_variant**|**sql_variant**|  
|**datetime2**|Date et heure|  
|**datetimeoffset**|Date et heure|  
|**datetime**|Date et heure|  
|**smalldatetime**|Date et heure|  
|**date**|Date et heure|  
|**time**|Date et heure|  
|**float**|Valeur numérique approchée|  
|**real**|Valeur numérique approchée|  
|**decimal**|Valeur numérique exacte|  
|**money**|Valeur numérique exacte|  
|**smallmoney**|Valeur numérique exacte|  
|**bigint**|Valeur numérique exacte|  
|**int**|Valeur numérique exacte|  
|**smallint**|Valeur numérique exacte|  
|**tinyint**|Valeur numérique exacte|  
|**bit**|Valeur numérique exacte|  
|**nvarchar**|Unicode|  
|**nchar**|Unicode|  
|**varchar**|Unicode|  
|**char**|Unicode|  
|**varbinary**|Binaire|  
|**binaire**|Binaire|  
|**uniqueidentifier**|**Uniqueidentifier**|  
  
Les règles suivantes s’appliquent aux **sql_variant** comparaisons :
-   Lorsque **sql_variant** les valeurs des types de données de base différentes sont comparées et les types de base de données sont des données différentes familles de types, la valeur dont famille de type de données est le plus élevé dans la hiérarchie est considérée comme la plus grande des deux valeurs.  
-   Lorsque **sql_variant** les valeurs des types de données de base différentes sont comparées et les types de base de données sont dans la même famille de type de données, la valeur dont le type de données de base est inférieur dans la hiérarchie est implicitement convertie au type de données et la comparaison est alors effectuée.  
-   Lorsque **sql_variant** les valeurs de la **char**, **varchar**, **nchar**, ou **nvarchar** des types de données sont comparées, leurs classements sont d’abord comparés en fonction des critères suivants : LCID, version LCID, indicateurs de comparaison et tri ID. Chacun de ces critères est comparé en tant que valeur entières, dans l'ordre indiqué. Si tous ces critères sont égaux, les valeurs de chaîne réelles sont comparées d'après le classement.  
  
## <a name="converting-sqlvariant-data"></a>Conversion de données sql_variant  
Lors du traitement de la **sql_variant** type de données, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge les conversions implicites d’objets avec d’autres types de données pour le **sql_variant** type. Toutefois, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne prend pas en charge les conversions implicites de **sql_variant** données à un objet avec un autre type de données.
  
## <a name="restrictions"></a>Restrictions  
Le tableau suivant répertorie les types de valeurs qui ne peut pas être stockés à l’aide de **sql_variant**:
  
|||  
|-|-|  
|**varchar(max)**|**varbinary(max)**|  
|**nvarchar(max)**|**xml**|  
|**text**|**ntext**|  
|**image**|**rowversion** (**timestamp**)|  
|**sql_variant**|**geography**|  
|**hierarchyid**|**geometry**|  
|Types définis par l'utilisateur|**datetimeoffset**|  
  
## <a name="see-also"></a>Voir aussi
[CAST et CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[SQL_VARIANT_PROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sql-variant-property-transact-sql.md)
  
  
