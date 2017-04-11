---
title: "D&#233;sactiver des contraintes de validation lors de la r&#233;plication | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Contraintes CHECK, désactivation"
  - "contraintes [SQL Server], désactivation"
  - "désactivation des contraintes"
  - "contraintes [SQL Server], validation"
ms.assetid: af98fc70-24dd-4bd3-a0a3-f701dfa67b2c
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# D&#233;sactiver des contraintes de validation lors de la r&#233;plication
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  Vous pouvez désactiver des contrainte de validation dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)]. Vous pouvez également choisir expressément de désactiver les contraintes de validation pour la réplication, ce qui est parfois très utile si vous publiez des données issues d'une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Si une table est publiée à l'aide du processus de réplication, les contraintes de validation sont automatiquement désactivées lors des opérations effectuées par les agents de réplication. Lorsqu'un Agent de réplication effectue une requête Insert, Update ou Delete vers un abonné, la contrainte n'est pas vérifiée ; si c'est un utilisateur qui effectue la requête Insert, Update ou Delete, la contrainte est vérifiée. La contrainte est désactivée pour l'Agent de réplication, car elle était déjà vérifiée au niveau de l'éditeur lorsque les données ont été insérées, mises à jour ou supprimées à l'origine. Pour plus d’informations, consultez [Spécifier des options de schéma](../../relational-databases/replication/publish/specify-schema-options.md).  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert une autorisation ALTER sur la table.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### Pour désactiver une contrainte de validation lors de la réplication  
  
1.  Dans l' **Explorateur d'objets**, développez la table avec la contrainte que vous souhaitez modifier, puis développez le dossier **Contraintes** .  
  
2.  Cliquez avec le bouton droit sur la contrainte de validation à modifier, puis cliquez sur **Modifier**.  
  
3.  Dans la boîte de dialogue **Contraintes de validation** , sous **Concepteur de tables**, sélectionnez la valeur **Non** pour **Appliquer la réplication**.  
  
4.  Cliquez sur **Fermer**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### Pour désactiver une contrainte de validation lors de la réplication  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. L'exemple crée une table avec une colonne IDENTITY et une contrainte CHECK sur la table. Il supprime ensuite la contrainte et la recrée en spécifiant la clause NOT FOR REPLICATION.  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    CREATE TABLE dbo.doc_exd (column_a int IDENTITY (1,1)   
    CONSTRAINT exd_check CHECK (column_a > 1))   
  
    ALTER TABLE dbo.doc_exd   
    DROP CONSTRAINT exd_check;   
    GO  
    ALTER TABLE dbo.doc_exd    
    ADD CONSTRAINT exd_check CHECK NOT FOR REPLICATION (column_a > 1);  
    ```  
  
 Pour plus d’informations, consultez [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md).  
  
###  <a name="TsqlExample"></a>   
## Voir aussi  
 [Spécifier des options de schéma](../../relational-databases/replication/publish/specify-schema-options.md)  
  
  