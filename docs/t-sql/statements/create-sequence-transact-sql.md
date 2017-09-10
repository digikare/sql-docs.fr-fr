---
title: "CRÉER la séquence (Transact-SQL) | Documents Microsoft"
ms.custom: 
ms.date: 04/11/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SEQUENCE
- CREATE SEQUENCE
- SEQUENCE_TSQL
- CREATE_SEQUENCE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CREATE SEQUENCE statement
- sequence number object, creating
- sequence object
- number, sequence
ms.assetid: 419f907b-8a72-4d6c-80cb-301df44c24c1
caps.latest.revision: 40
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 89a96d101c17f528b9ff14ca523e5dc41ada2f4c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="create-sequence-transact-sql"></a>CREATE SEQUENCE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Crée un objet séquence et spécifie ses propriétés. Une séquence est un objet lié par schéma défini par l'utilisateur qui génère une séquence de valeurs numériques d'après la spécification avec laquelle la séquence a été créée. La séquence de valeurs numériques est générée dans un ordre croissant ou décroissant à un intervalle défini et peut être configurée pour redémarrer (cycle) lorsque épuisée. Les séquences, contrairement aux colonnes d'identité, ne sont pas associées aux tables spécifiques. Les applications font référence à un objet séquence pour extraire sa valeur suivante. La relation entre les séquences et les tables est contrôlée par l'application. Les applications utilisateur peuvent référencer un objet séquence et coordonner les valeurs sur plusieurs lignes et tables.  
  
 Contrairement aux valeurs de colonnes d’identité qui sont générés lorsque des lignes sont insérées, une application peut obtenir le numéro séquentiel suivant sans insérer la ligne en appelant le [fonction NEXT VALUE FOR](../../t-sql/functions/next-value-for-transact-sql.md). Utilisez [sp_sequence_get_range](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md) pour obtenir plusieurs numéros séquentiels à la fois.  
  
 Pour obtenir des informations et des scénarios qui utilisent à la fois **CREATE SEQUENCE** et la fonction **NEXT VALUE FOR** , consultez [Numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CREATE SEQUENCE [schema_name . ] sequence_name  
    [ AS [ built_in_integer_type | user-defined_integer_type ] ]  
    [ START WITH <constant> ]  
    [ INCREMENT BY <constant> ]  
    [ { MINVALUE [ <constant> ] } | { NO MINVALUE } ]  
    [ { MAXVALUE [ <constant> ] } | { NO MAXVALUE } ]  
    [ CYCLE | { NO CYCLE } ]  
    [ { CACHE [ <constant> ] } | { NO CACHE } ]  
    [ ; ]  
```  
  
## <a name="arguments"></a>Arguments  
 *sequence_name*  
 Spécifie le nom unique sous lequel la séquence est connue dans la base de données. Est de type **sysname**.  
  
 [ built_in_integer_type | user-defined_integer_type  
 Une séquence peut être définie comme tout type entier. Les types suivants sont autorisés.  
  
-   **tinyint** -plage comprise entre 0 et 255  
  
-   **smallint** -plage de-32 768 à 32 767  
  
-   **int** -plage allant de -2,147,483,648 à 2 147 483 647  
  
-   **bigint** -plage de -9,223,372,036,854,775,808 à 9,223,372,036,854,775,807  
  
-   **décimal** et **numérique** avec une échelle de 0.  
  
-   Tout type de données défini par l'utilisateur (type d'alias) basé sur l'un des types autorisés.  
  
 Si aucun type de données n’est fourni, le **bigint** type de données est utilisé en tant que la valeur par défaut.  
  
 START WITH \<constante >  
 Première valeur retournée par l'objet séquence. Le **Démarrer** valeur doit être une valeur inférieure ou égale à la valeur maximale et supérieure ou égale à la valeur minimale de l’objet séquence. La valeur de début par défaut d'un nouvel objet séquence correspond à la valeur minimale pour un objet séquence croissant et à la valeur maximale pour un objet séquence décroissant.  
  
 INCREMENT BY \<constante >  
 Valeur utilisée pour incrémenter (ou décrémenter le cas de valeurs négatives) la valeur de l’objet de séquence pour chaque appel à la **NEXT VALUE FOR** (fonction). Si l'incrément est une valeur négative, l'objet séquence décroît ; sinon, il croît. L'incrément ne peut pas avoir la valeur 0. L'incrément par défaut pour un nouvel objet séquence est 1.  
  
 [MINVALUE \<constante > | **Aucun MINVALUE** ]  
 Spécifie les limites de l'objet séquence. La valeur minimale par défaut d'un nouvel objet séquence correspond à la valeur minimale du type de données de l'objet séquence. Il s’agit de zéro pour le type de données **tinyint** et d’un nombre négatif pour tous les autres types de données.  
  
 [MAXVALUE \<constante > | **Aucun MAXVALUE**  
 Spécifie les limites de l'objet séquence. La valeur maximale par défaut d'un nouvel objet séquence correspond à la valeur maximale du type de données de l'objet séquence.  
  
 [CYCLE | **AUCUN CYCLE** ]  
 Propriété qui spécifie si l'objet séquence doit redémarrer de la valeur minimale (ou maximale pour les objets de séquence décroissante) ou générer une exception lorsque sa valeur minimale ou maximale est dépassée. L'option de cycle par défaut pour les nouveaux objets séquences est NO CYCLE.  
  
 Notez que l'itération redémarre à partir de la valeur minimale ou maximale, et non de la valeur de début.  
  
 [ **CACHE** [\<constante >] | AUCUN CACHE]  
 Augmente la performance des applications qui utilisent des objets séquences en réduisant le nombre d'E/S sur le disque requises pour générer des numéros séquentiels. Paramètres par défaut sur CACHE.  
  
 Par exemple, si vous choisissez une taille de cache de 50, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne conserve pas 50 valeurs individuelles en cache. Il met uniquement en cache la valeur actuelle et le nombre de valeurs restées dans le cache. Cela signifie que la quantité de mémoire requise pour stocker le cache correspond toujours à deux instances du type de données de l'objet séquence.  
  
> [!NOTE]  
>  Si l'option de cache est activée sans spécifier une taille du cache, le moteur de base de données en sélectionne une automatiquement. Toutefois, les utilisateurs ne doivent pas compter sur une sélection cohérente. [!INCLUDE[msCoName](../../includes/msconame-md.md)] peut modifier la méthode de calcul de la taille du cache sans préavis.  
  
 Lors de la création avec le **CACHE** option, un arrêt inattendu (par exemple, une panne de courant) peut entraîner la perte des numéros séquentiels qui restent dans le cache.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Les numéros séquentiels sont générés à l'extérieur de l'étendue de la transaction actuelle. Ils sont utilisés si la transaction à l'aide du numéro séquentiel est validée ou restaurée.  
  
### <a name="cache-management"></a>Gestion du cache  
 Pour améliorer les performances, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pré-alloue le nombre de numéros de séquence spécifiés par le **CACHE** argument.  
  
 Par exemple, une nouvelle séquence est créée avec une valeur de départ de 1 et une taille du cache de 15. Lorsque la première valeur est exigée, les valeurs 1 à 15 sont rendues disponibles à partir de la mémoire. La dernière valeur mise en cache (15) est écrite dans les tables système sur le disque. Lorsque les 15 nombres sont utilisés, la demande suivante (pour le nombre 16) entraînera une nouvelle allocation du cache. La nouvelle et dernière valeur mise en cache (30) sera écrite dans les tables système.  
  
 Si la [!INCLUDE[ssDE](../../includes/ssde-md.md)] est arrêtée après avoir utilisé 22 nombres, la prochaine destiné numéro de séquence en mémoire (23) est écrit dans les tables système, en remplaçant le nombre précédemment stocké.  
  
 Après le redémarrage de SQL Server, un numéro séquentiel est exigé ; le nombre initial est lu à partir des tables système (23). Le montant de cache de 15 nombres (23-38) est alloué à la mémoire et le numéro de non-cache suivant (39) est écrit dans les tables système.  
  
 Si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] s’arrête anormalement pour un événement tel qu’une panne de courant, la séquence redémarre avec le nombre lu à partir des tables système (39). N’importe quelle séquence numéros alloués à la mémoire (mais jamais demandés par un utilisateur ou une application) sont perdues. Cette fonctionnalité peut laisser des espaces vides, mais garantit que la même valeur ne sera jamais émise deux fois pour un objet séquence unique, sauf si elle est définie comme **CYCLE** ou est redémarré manuellement.  
  
 Le cache est maintenu en mémoire en suivant la valeur actuelle (la dernière valeur émise) et le nombre de valeurs restées dans le cache. Par conséquent, la quantité de mémoire utilisée par le cache correspond toujours à deux instances du type de données de l'objet séquence.  
  
 Si l’argument de cache **NO CACHE** écrit la valeur de la séquence actuelle dans les tables système chaque fois qu’une séquence est utilisée. Cela peut ralentir les performances en augmentant l'accès au disque, mais réduit les risques d'espaces vides non désirés. Intervalles peuvent encore se produire si les nombres sont demandés à l’aide de la **NEXT VALUE FOR** ou **sp_sequence_get_range** fonctions, mais les numéros ne sont pas utilisés ou sont utilisés dans les transactions non validées.  
  
 Lorsqu’un objet séquence utilise le **CACHE** option, si vous redémarrez l’objet séquence, ou modifiez la **INCRÉMENT**, **CYCLE**, **MINVALUE**, **MAXVALUE**, ou les propriétés de taille du cache, elle entraîne le cache d’écriture sur les tables système avant le changement se produit. Puis, le cache est rechargé en commençant par la valeur actuelle (autrement dit, aucun nombre n'est ignoré). Toute modification apportée à la taille du cache prend effet immédiatement.  
  
 **Option CACHE lorsque les valeurs mises en cache sont disponibles**  
  
 Le processus suivant se produit chaque fois qu’un objet séquence est demandé pour générer la valeur suivante de la **CACHE** option si les valeurs inutilisées sont disponibles dans le cache en mémoire pour l’objet séquence.  
  
1.  La valeur suivante de l'objet séquence est calculée.  
  
2.  La nouvelle valeur actuelle de l'objet séquence est mise à jour en mémoire.  
  
3.  La valeur calculée est retournée à l'instruction appelante.  
  
 **Option CACHE lorsque le cache est épuisé**  
  
 Le processus suivant se produit chaque fois qu’un objet séquence est demandé pour générer la valeur suivante de la **CACHE** option si le cache est épuisé :  
  
1.  La valeur suivante de l'objet séquence est calculée.  
  
2.  La dernière valeur du nouveau cache est calculée.  
  
3.  La ligne de table système pour l'objet séquence est verrouillée, et la valeur calculée à l'étape 2 (dernière valeur) est écrite dans la table système. Un xevent de cache épuisé est déclenché pour notifier l'utilisateur de la nouvelle valeur rendue persistante.  
  
 **AUCUNE option de CACHE**  
  
 Le processus suivant se produit chaque fois qu’un objet séquence est demandé pour générer la valeur suivante de la **NO CACHE** option :  
  
1.  La valeur suivante de l'objet séquence est calculée.  
  
2.  La nouvelle valeur actuelle de l'objet séquence est écrite dans la table système.  
  
3.  La valeur calculée est retournée à l'instruction appelante.  
  
## <a name="metadata"></a>Métadonnées  
 Pour plus d’informations sur les séquences, interrogez [sys.sequences](../../relational-databases/system-catalog-views/sys-sequences-transact-sql.md).  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Permissions  
 Nécessite l’autorisation **CREATE SEQUENCE**, **ALTER**ou **CONTROL** sur le SCHEMA.  
  
-   Membres de db_owner et db_ddladmin de base de données fixé peuvent créer, modifier et supprimer des objets de la séquence.  
  
-   Membres de db_owner et db_datawriter, rôle de base de données fixé peuvent mettre à jour les objets séquences en leur faisant générer des nombres.  
  
 L’exemple suivant accorde l’autorisation AdventureWorks\Larry pour créer des séquences dans le schéma de Test de l’utilisateur.  
  
```  
GRANT CREATE SEQUENCE ON SCHEMA::Test TO [AdventureWorks\Larry]  
```  
  
 La propriété d’un objet séquence peut être transférée à l’aide de la **ALTER AUTHORIZATION** instruction.  
  
 Si une séquence utilise un type de données défini par l'utilisateur, le créateur de la séquence doit avoir l'autorisation REFERENCES sur le type.  
  
### <a name="audit"></a>Audit  
 Pour auditer **créer une séquence**, analyse le **SCHEMA_OBJECT_CHANGE_GROUP**.  
  
## <a name="examples"></a>Exemples  
 Pour obtenir des exemples de création de séquences et à l’aide de la **NEXT VALUE FOR** afin de générer des numéros de séquence, consultez [numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
 La plupart des exemples suivants créent des objets séquences dans un schéma nommé Test.  
  
 Pour créer le schéma de Test, exécutez l’instruction suivante.  
  
```  
CREATE SCHEMA Test ;  
GO  
```  
  
### <a name="a-creating-a-sequence-that-increases-by-1"></a>A. Création d'une séquence qui augmente de 1  
 Dans l’exemple suivant, Thierry crée une séquence nommée CountBy1 qui augmente d’une unité chaque fois qu’elle est utilisée.  
  
```  
CREATE SEQUENCE Test.CountBy1  
    START WITH 1  
    INCREMENT BY 1 ;  
GO  
```  
  
### <a name="b-creating-a-sequence-that-decreases-by-1"></a>B. Création d'une séquence qui décroît de 1  
 L'exemple suivant démarre à 0 et décroît d'une valeur négative chaque fois qu'il est utilisé.  
  
```  
CREATE SEQUENCE Test.CountByNeg1  
    START WITH 0  
    INCREMENT BY -1 ;  
GO  
```  
  
### <a name="c-creating-a-sequence-that-increases-by-5"></a>C. Création d'une séquence qui augmente de 5  
 L'exemple suivant crée une séquence qui augmente de 5 chaque fois qu'elle est utilisée.  
  
```  
CREATE SEQUENCE Test.CountBy1  
    START WITH 5  
    INCREMENT BY 5 ;  
GO  
```  
  
### <a name="d-creating-a-sequence-that-starts-with-a-designated-number"></a>D. Création d'une séquence qui démarre avec un nombre désigné  
 Après avoir importé une table, Thierry remarque que le numéro d'ID le plus élevé utilisé est 24 328. Thierry a besoin d'une séquence qui générera des nombres qui démarrent à 24 329. Le code suivant crée une séquence qui démarre à 24 329 et est incrémentée de 1.  
  
```  
CREATE SEQUENCE Test.ID_Seq  
    START WITH 24329  
    INCREMENT BY 1 ;  
GO  
```  
  
### <a name="e-creating-a-sequence-using-default-values"></a>E. Création d'une séquence à l'aide de valeurs par défaut  
 L'exemple suivant crée une séquence à l'aide des valeurs par défaut.  
  
```  
CREATE SEQUENCE Test.TestSequence ;  
```  
  
 Exécutez l'instruction suivante pour consulter les propriétés de la séquence.  
  
```  
SELECT * FROM sys.sequences WHERE name = 'TestSequence' ;  
```  
  
 Une liste partielle de la sortie montre les valeurs par défaut.  
  
|||  
|-|-|  
|`start_value`|`-9223372036854775808`|  
|`increment`|`1`|  
|`mimimum_value`|`-9223372036854775808`|  
|`maximum_value`|`9223372036854775807`|  
|`is_cycling`|`0`|  
|`is_cached`|`1`|  
|`current_value`|`-9223372036854775808`|  
  
### <a name="f-creating-a-sequence-with-a-specific-data-type"></a>F. Création d'une séquence avec un type de données spécifique  
 L’exemple suivant crée une séquence à l’aide de la **smallint** type de données, avec une plage comprise entre-32 768 à 32 767.  
  
```  
CREATE SEQUENCE SmallSeq  
    AS smallint ;  
```  
  
### <a name="g-creating-a-sequence-using-all-arguments"></a>G. Création d'une séquence à l'aide de tous les arguments  
 L’exemple suivant crée une séquence nommée à l’aide de DecSeq les **décimal** type de données, avec une plage comprise entre 0 et 255. La séquence démarre à 125 et est incrémentée de 25 chaque fois qu'un nombre est généré. Étant donné que la séquence est configurée pour se répéter lorsque la valeur dépasse la valeur maximale de 200, la séquence redémarre à la valeur minimale de 100.  
  
```  
CREATE SEQUENCE Test.DecSeq  
    AS decimal(3,0)   
    START WITH 125  
    INCREMENT BY 25  
    MINVALUE 100  
    MAXVALUE 200  
    CYCLE  
    CACHE 3  
;  
```  
  
 Exécutez l'instruction suivante pour consulter la première valeur ; l'option `START WITH` de 125.  
  
```  
SELECT NEXT VALUE FOR Test.DecSeq;  
```  
  
 Exécutez l'instruction trois autres fois pour retourner 150, 175 et 200.  
  
 Exécutez une nouvelle fois l'instruction pour voir comment la valeur de début revient en arrière à l'option `MINVALUE` de 100.  
  
 Exécutez le code suivant pour confirmer la taille du cache et consulter la valeur actuelle.  
  
```  
SELECT cache_size, current_value   
FROM sys.sequences  
WHERE name = 'DecSeq' ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [ALTER SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [DROP SEQUENCE &#40; Transact-SQL &#41;](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [VALEUR suivante de &#40; Transact-SQL &#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [Numéros de séquence](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  
