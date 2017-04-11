---
title: "Exemple&#160;: restauration en ligne d’un fichier en lecture/&#233;criture (mode de r&#233;cup&#233;ration compl&#232;te) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-backup-restore"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mode de récupération complète [SQL Server], exemple RESTORE"
  - "restaurations en ligne [SQL Server], mode de récupération complète"
  - "séquences de restauration [SQL Server], en ligne"
ms.assetid: 0dbeda81-1464-44ba-9011-914900096368
caps.latest.revision: 33
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 33
---
# Exemple&#160;: restauration en ligne d’un fichier en lecture/&#233;criture (mode de r&#233;cup&#233;ration compl&#232;te)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique concerne les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui relèvent du mode de récupération complète et qui contiennent plusieurs fichiers ou groupes de fichiers.  
  
 Dans cet exemple, une base de données appelée `adb` qui utilise le mode de restauration complète, contient trois groupes de fichiers. Le groupe de fichiers `A` est en lecture-écriture, et les groupes de fichiers `B` et `C` sont en lecture seule. Au départ, tous les groupes de fichiers sont en ligne.  
  
 Le fichier `a1` du groupe de fichiers `A` est endommagé et l’administrateur de la base de données décide de le restaurer pendant que la base de données est en ligne.  
  
> [!NOTE]  
>  En mode de récupération simple, la restauration en ligne des données en lecture-écriture n'est pas autorisée.  
  
## Séquences de restauration  
  
> [!NOTE]  
>  La syntaxe pour une séquence de restauration en ligne est la même que pour une séquence de restauration hors connexion.  
  
1.  Restauration en ligne du fichier `a1`.  
  
    ```  
    RESTORE DATABASE adb FILE='a1' FROM backup   
    WITH NORECOVERY;  
    ```  
  
     À ce stade, le fichier a1 est dans l'état RESTORING et le groupe de fichiers A est hors ligne.  
  
2.  Après avoir restauré le fichier, l'administrateur de base de données effectue une nouvelle sauvegarde de fichier journal afin de s'assurer que le point auquel le fichier a été mis hors connexion est capturé.  
  
    ```  
    BACKUP LOG adb TO log_backup3;   
    ```  
  
3.  Restauration en ligne des sauvegardes de fichiers journaux.  
  
     L’administrateur restaure toutes les sauvegardes de journaux effectuées depuis la restauration de la sauvegarde de fichiers, en terminant par la sauvegarde de fichier journal la plus récente (*log_backup3*, effectuée à l’étape 2). Une fois restaurée la dernière sauvegarde, la base de données est récupérée.  
  
    ```  
    RESTORE LOG adb FROM log_backup1 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup2 WITH NORECOVERY;  
    RESTORE LOG adb FROM log_backup3 WITH NORECOVERY;  
    RESTORE LOG adb WITH RECOVERY;  
    ```  
  
     Le fichier `a1` est désormais en ligne.  
  
## Autres exemples  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire de quelques groupes de fichiers uniquement &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
-   [Exemple : restauration en ligne d’un fichier en lecture seule &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-simple-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;mode de restauration complète&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire de quelques groupes de fichiers &#40;mode de restauration complète&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   [Exemple : restauration en ligne d’un fichier en lecture seule &#40;mode de restauration complète&#41;](../../relational-databases/backup-restore/example-online-restore-of-a-read-only-file-full-recovery-model.md)  
  
## Voir aussi  
 [Restauration en ligne &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Restaurations fragmentaires &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [Vue d’ensemble de la restauration et de la récupération &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md)   
 [Appliquer les sauvegardes du journal de transactions &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  