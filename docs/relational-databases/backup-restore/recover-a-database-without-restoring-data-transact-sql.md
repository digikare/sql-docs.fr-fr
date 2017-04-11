---
title: "R&#233;cup&#233;rer une base de donn&#233;es sans restaurer les donn&#233;es (Transact-SQL) | Microsoft Docs"
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
  - "restauration [réplication SQL Server], récupération seule"
  - "scénario de récupération seule [SQL Server]"
  - "restauration des bases de données [SQL Server], récupération seule"
  - "récupération [SQL Server], récupération seule"
  - "récupération de base de données [SQL Server]"
  - "restaurations de base de données [SQL Server], récupération seule"
  - "récupération [SQL Server], sans restauration des données"
ms.assetid: 7e8fa620-315d-4e10-a718-23fa5171c09e
caps.latest.revision: 39
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 39
---
# R&#233;cup&#233;rer une base de donn&#233;es sans restaurer les donn&#233;es (Transact-SQL)
  En général, toutes les données dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont restaurées avant que la base de données ne soit récupérée. Toutefois, une opération de restauration peut récupérer une base de données sans réellement restaurer une sauvegarde, par exemple lors de la récupération d'un fichier en lecture seule qui est cohérent avec la base de données. Il s’agit d’une *restauration avec récupération uniquement*. Lorsque des données hors ligne sont déjà cohérentes avec la base de données et doivent uniquement être rendues disponibles, une restauration avec récupération uniquement termine la récupération de la base de données et met les données en ligne.  
  
 Une restauration avec récupération uniquement peut se produire pour une base de données entière ou pour un ou plusieurs fichiers ou groupes de fichiers.  
  
## Restauration de base de données avec récupération uniquement  
 Une restauration de base de données avec récupération uniquement est utile dans les situations suivantes :  
  
-   Vous n'avez pas récupéré la base de données lors de la restauration de la dernière sauvegarde au cours d'une séquence de restauration, et vous voulez à présent récupérer cette base de données pour la mettre en ligne.  
  
-   La base de données est en mode veille, et vous voulez qu'elle puisse être mise à jour sans appliquer une autre sauvegarde de journal.  
  
 La syntaxe [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) pour une restauration de base de données avec récupération uniquement est la suivante :  
  
 RESTORE DATABASE *nom_base_de_données* WITH RECOVERY  
  
> [!NOTE]  
>  La clause FROM **=** \<*unité_de_sauvegarde>* n’est pas destinée aux restaurations avec récupération uniquement, car aucune sauvegarde n’est nécessaire.  
  
 **Exemple**  
  
 L'exemple suivant récupère l'exemple de base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] dans le cadre d'une opération de restauration sans restaurer les données.  
  
```  
-- Restore database using WITH RECOVERY.  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY  
```  
  
## Restauration de fichier avec récupération uniquement  
 Une restauration de fichier avec récupération uniquement est utile dans la situation suivante :  
  
 Une base de données est restaurée par fragments. Une fois le groupe de fichiers primaire restauré, un ou plusieurs des fichiers non restaurés sont cohérents avec le nouvel état de la base de données, peut-être pour avoir été en lecture seule un moment. Ces fichiers doivent seulement être récupérés ; la copie des données n'est pas nécessaire.  
  
 Une opération de restauration avec récupération uniquement met en ligne les données du groupe de fichiers hors connexion ; aucune phase de copie des données ni d'annulation ou de restauration par progression n'est effectuée. Pour plus d’informations sur les phases de restauration, consultez [Vue d’ensemble de la restauration et de la récupération &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-and-recovery-overview-sql-server.md).  
  
 La syntaxe [RESTORE](../Topic/RESTORE%20\(Transact-SQL\).md) pour une restauration de fichier avec récupération uniquement est la suivante :  
  
 RESTORE DATABASE *nom_base_de_données* { FILE **=***nom_fichier_logique* | FILEGROUP **=***nom_groupe_fichiers_logique* } [ **,**...*n* ] WITH RECOVERY  
  
 **Exemple**  
  
 L'exemple suivant illustre une restauration de fichier avec récupération uniquement des fichiers dans un groupe de fichiers secondaire, `SalesGroup2`, dans la base de données `Sales`. Le groupe de fichiers primaire a déjà été restauré au cours de l'étape initiale d'une restauration fragmentaire, et `SalesGroup2` est cohérent avec le groupe de fichiers primaire restauré. La récupération de ce groupe de fichiers et sa mise en ligne ne requièrent qu'une seule instruction.  
  
```  
RESTORE DATABASE Sales FILEGROUP=SalesGroup2 WITH RECOVERY;  
```  
  
## Exemples de finalisation d'un scénario de restauration fragmentaire à l'aide d'une restauration avec récupération uniquement  
 **Mode de récupération simple**  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-simple-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire de quelques groupes de fichiers uniquement &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-simple-recovery-model.md)  
  
 **Mode de restauration complète**  
  
-   [Exemple : restauration fragmentaire d’une base de données &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-database-full-recovery-model.md)  
  
-   [Exemple : restauration fragmentaire de quelques groupes de fichiers &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/example-piecemeal-restore-of-only-some-filegroups-full-recovery-model.md)  
  
-   <xref:Microsoft.SqlServer.Management.Smo.Restore.SqlRestore%2A>  
  
## Voir aussi  
 [Restauration en ligne &#40;SQL Server&#41;](../../relational-databases/backup-restore/online-restore-sql-server.md)   
 [Restaurations fragmentaires &#40;SQL Server&#41;](../../relational-databases/backup-restore/piecemeal-restores-sql-server.md)   
 [Restauration de fichiers &#40;mode de récupération simple&#41;](../../relational-databases/backup-restore/file-restores-simple-recovery-model.md)   
 [Restaurations de fichiers &#40;mode de récupération complète&#41;](../../relational-databases/backup-restore/file-restores-full-recovery-model.md)   
 [RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)  
  
  