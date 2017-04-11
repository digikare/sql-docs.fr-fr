---
title: "Rep&#232;res de plan | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-plan-guides"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TEMPLATE, repère de plan"
  - "repères de plan SQL"
  - "OPTIMIZE FOR, indicateur de requête"
  - "RECOMPILE, indicateur de requête"
  - "OBJECT, repère de plan"
  - "repères de plan [SQL Server], à propos des repères de plan"
  - "OPTION (clause)"
  - "repères de plan [SQL Server]"
  - "USE PLAN, indicateur de requête"
ms.assetid: bfc97632-c14c-4768-9dc5-a9c512f6b2bd
caps.latest.revision: 52
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 52
---
# Rep&#232;res de plan
  Les repères de plan vous permettent d'optimiser les performances des requêtes lorsque vous ne pouvez pas ou ne souhaitez pas modifier directement le texte de la requête réelle dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Les repères de plan influencent l'optimisation des requêtes en attachant des indicateurs de requête ou un plan fixe de requête à celles-ci. Les repères de plan s'avèrent utiles lorsqu'un petit sous-ensemble de requêtes d'une application de base de données fournie par un tiers ne fonctionne pas comme prévu. Dans le repère de plan, vous spécifiez l'instruction Transact-SQL que vous voulez optimiser et une clause OPTION contenant les indicateurs de requête ou un plan de requête spécifique à utiliser pour optimiser la requête. Lorsque la requête s'exécute, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fait correspondre l'instruction Transact-SQL au repère de plan et attache la clause OPTION à la requête au moment de l'exécution ou fait appel au plan de requête spécifié.  
  
 Le nombre total de repères de plan que vous pouvez créer est uniquement tributaire des ressources système disponibles. Toutefois, les repères de plan doivent se limiter au traitement des requêtes critiques ciblées à des fins d'amélioration ou de stabilisation des performances. Les repères de plan ne doivent pas influencer la majeure partie de la charge de requête d'une application déployée.  
  
> [!NOTE]  
>  Les repères de plan ne peuvent pas être utilisés dans toutes les éditions de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour obtenir la liste des fonctionnalités prises en charge par les éditions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Fonctionnalités prises en charge par les éditions de SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md). Les repères de plan sont visibles dans n'importe quelle édition. En outre, vous pouvez attacher une base de données qui contient des repères de plan à n'importe quelle édition. Les repères de plan demeurent intacts lorsque vous restaurez ou attachez une base de données à une version mise à niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## Types de repères de plan  
 Il est possible de créer les types de repères de plan suivants.  
  
 OBJECT, repère de plan  
 Un repère de plan OBJECT correspond à des requêtes qui s'exécutent dans le contexte de procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)], de fonctions scalaires définies par l'utilisateur, de fonctions table à instructions multiples définies par l'utilisateur et de déclencheurs DML.  
  
 Supposons que la procédure stockée suivante, qui accepte le paramètre `@Country`_`region`, figure dans une application de base de données déployée dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] :  
  
```  
CREATE PROCEDURE Sales.GetSalesOrderByCountry (@Country_region nvarchar(60))  
AS  
BEGIN  
    SELECT *  
    FROM Sales.SalesOrderHeader AS h, Sales.Customer AS c,   
        Sales.SalesTerritory AS t  
    WHERE h.CustomerID = c.CustomerID  
        AND c.TerritoryID = t.TerritoryID  
        AND CountryRegionCode = @Country_region  
END;  
```  
  
 Supposons que cette procédure stockée a été compilée et optimisée pour `@Country`_`region = N'AU'` (Australie). Toutefois, comme il y a relativement peu de commandes client qui proviennent d'Australie, les performances diminuent lorsque la requête s'exécute à l'aide de valeurs de paramètre de pays contenant plus de commandes client. Dans la mesure où les États-Unis constituent le pays qui arrive en première position en termes de commandes remportées, un plan de requête généré pour `@Country`\_`region = N'US'` obtiendrait de meilleures performances pour toutes les valeurs possibles du paramètre `@Country`\_`region`.  
  
 Vous pouvez résoudre ce problème en modifiant la procédure stockée pour ajouter l'indicateur de requête `OPTIMIZE FOR` à la requête. Toutefois, étant donné que la procédure stockée se trouve dans une application déployée, vous ne pouvez pas modifier directement le code de cette dernière. Vous pouvez en revanche créer le repère de plan suivant dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT *FROM Sales.SalesOrderHeader AS h,  
        Sales.Customer AS c,  
        Sales.SalesTerritory AS t  
        WHERE h.CustomerID = c.CustomerID   
            AND c.TerritoryID = t.TerritoryID  
            AND CountryRegionCode = @Country_region',  
@type = N'OBJECT',  
@module_or_batch = N'Sales.GetSalesOrderByCountry',  
@params = NULL,  
@hints = N'OPTION (OPTIMIZE FOR (@Country_region = N''US''))';  
```  
  
 Lorsque la requête spécifiée dans l'instruction `sp_create_plan_guide` s'exécute, elle est modifiée avant l'optimisation de façon à inclure la clause `OPTIMIZE FOR (@Country = N''US'')`.  
  
 Repère de plan SQL  
 Un repère de plan SQL correspond à des requêtes qui s'exécutent dans le contexte de lots et d'instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] autonomes ne faisant pas partie d'un objet de base de données. Les repères de plan SQL peuvent également être employés pour les requêtes paramétrables au format spécifié. Les repères de plan SQL s'appliquent aux instructions et aux lots [!INCLUDE[tsql](../../includes/tsql-md.md)] autonomes. Le plus souvent, ces instructions sont envoyées par une application à l’aide de la procédure stockée système [sp_executesql](../../relational-databases/system-stored-procedures/sp-executesql-transact-sql.md). Imaginons par exemple le traitement autonome suivant :  
  
```  
SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC;  
```  
  
 Pour empêcher la génération d'un plan d'exécution parallèle sur cette requête, créez le repère de plan suivant et affectez à l'indicateur de requête `MAXDOP` la valeur `1` dans le paramètre `@hints`.  
  
```  
sp_create_plan_guide   
@name = N'Guide2',   
@stmt = N'SELECT TOP 1 * FROM Sales.SalesOrderHeader ORDER BY OrderDate DESC',  
@type = N'SQL',  
@module_or_batch = NULL,   
@params = NULL,   
@hints = N'OPTION (MAXDOP 1)';  
```  
  
> [!IMPORTANT]  
>  Les valeurs fournies pour les arguments `@module_or_batch` et `@params` de l'instruction `sp_create_plan guide` doivent correspondre au texte correspondant soumis dans la requête réelle. Pour plus d’informations, consultez [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md) et [Utiliser le Générateur de profils SQL Server pour créer et tester des repères de plan](../../relational-databases/performance/use-sql-server-profiler-to-create-and-test-plan-guides.md).  
  
 Les repères de plan SQL peuvent aussi être créés sur des requêtes paramétrables au même format lorsque l'option de base de données PARAMETERIZATION a la valeur FORCED ou lorsqu'un repère de plan TEMPLATE est créé pour spécifier qu'une classe de requête est paramétrable.  
  
 TEMPLATE, repère de plan  
 Un repère de plan TEMPLATE correspond à des requêtes autonomes paramétrables au format spécifié. Il s'emploie pour remplacer l'option de base de données PARAMETERIZATION par une classe de requêtes.  
  
 Vous pouvez créer un repère de plan TEMPLATE dans l'une des circonstances suivantes :  
  
-   lorsque l'option de base de données PARAMETERIZATION est définie à FORCED, mais qu'il y a des requêtes que vous voulez compiler selon les règles du paramétrage simple ;  
  
-   lorsque l'option de base de données PARAMETERIZATION est définie à SIMPLE (l'option par défaut), mais que vous voulez appliquer une tentative de paramétrage forcé à une classe de requêtes.  
  
## Paramétrage de la mise en correspondance du repère de plan  
 Les repères de plan sont limités à la base de données dans laquelle ils sont créés. Par conséquent, seuls les repères de plan existant dans la base de données qui est active lors de l'exécution d'une requête peuvent être mis en correspondance avec cette requête. Supposons que [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] est la base de données active et que la requête suivante est exécutée :  
  
 `SELECT FirstName, LastName FROM Person.Person;`  
  
 Seuls les repères de plan de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] peuvent être mis en correspondance avec cette requête. Supposons maintenant que [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] est la base de données active et que les instructions suivantes sont exécutées :  
  
 `USE DB1;`  
  
 `SELECT FirstName, LastName FROM Person.Person;`  
  
 Seuls les repères de plan de `DB1` peuvent être mis en correspondance avec la requête, car celle-ci s'exécute dans le contexte de `DB1`.  
  
 Pour les repères de plan basés sur SQL ou TEMPLATE, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fait correspondre les valeurs pour les arguments @module_or_batch et @params avec une requête en comparant les deux valeurs caractère par caractère. Cela signifie que vous devez fournir le texte exactement tel que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le reçoit dans le traitement réel.  
  
 Lorsque @type = 'SQL' et @module_or_batch ont la valeur NULL, la valeur de @module_or_batch a la valeur de @stmt. Autrement dit, la valeur de *statement_text* doit être fournie dans un format identique (au caractère près) à celui utilisé lors de son envoi à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Aucune conversion interne n'est effectuée pour faciliter cette correspondance.  
  
 Lorsqu'un repère de plan normal (SQL ou OBJECT) et un repère de plan TEMPLATE peuvent s'appliquer tous les deux à une instruction, seul le repère de plan normal est utilisé.  
  
> [!NOTE]  
>  Le traitement qui contient l’instruction sur laquelle vous souhaitez créer un repère de plan ne peut pas contenir une instruction de *base de données* USE.  
  
## Effet du repère de plan sur le cache du plan  
 La création d'un repère de plan sur un module supprime le plan de requête pour ce module du cache du plan. La création d'un repère de plan de type OBJET ou SQL sur un lot supprime le plan de requête pour un lot qui a la même valeur de hachage. La création d'un repère de plan de type TEMPLATE supprime tous les lots comprenant une instruction unique du cache du plan dans cette base de données.  
  
## Tâches associées  
  
|Tâche|Rubrique|  
|----------|-----------|  
|Explique comment créer un repère de plan.|[Créer un repère de plan](../../relational-databases/performance/create-a-new-plan-guide.md)|  
|Explique comment créer un repère de plan pour les requêtes paramétrables.|[Créer un repère de plan pour les requêtes paramétrables](../../relational-databases/performance/create-a-plan-guide-for-parameterized-queries.md)|  
|Explique comment contrôler le comportement du paramétrage de requête à l'aide de repères de plan.|[Spécifier le comportement du paramétrage de requêtes grâce aux repères de plan](../../relational-databases/performance/specify-query-parameterization-behavior-by-using-plan-guides.md)|  
|Explique comment inclure un plan de requête fixe dans un repère de plan.|[Appliquer un plan de requête fixe à un repère de plan](../../relational-databases/performance/apply-a-fixed-query-plan-to-a-plan-guide.md)|  
|Explique comment spécifier des indicateurs de requête dans un repère de plan.|[Attacher des indicateurs de requête à un repère de plan](../../relational-databases/performance/attach-query-hints-to-a-plan-guide.md)|  
|Explique comment afficher les propriétés d'un repère de plan.|[Afficher les propriétés du repère de plan](../../relational-databases/performance/view-plan-guide-properties.md)|  
|Explique comment utiliser SQL Server Profiler pour créer et tester des repères de plan.|[Utiliser le Générateur de profils SQL Server pour créer et tester des repères de plan](../../relational-databases/performance/use-sql-server-profiler-to-create-and-test-plan-guides.md)|  
|Explique comment valider des repères de plan.|[Valider des repères de plan après la mise à niveau](../../relational-databases/performance/validate-plan-guides-after-upgrade.md)|  
  
## Voir aussi  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)   
 [sp_control_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-control-plan-guide-transact-sql.md)   
 [sys.plan_guides &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-plan-guides-transact-sql.md)   
 [sys.fn_validate_plan_guide &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md)  
  
  