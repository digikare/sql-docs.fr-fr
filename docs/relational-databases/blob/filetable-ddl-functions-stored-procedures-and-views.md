---
title: "DDL, fonctions, proc&#233;dures stock&#233;es et vues FileTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-blob"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "FileTables [SQL Server], objets de base de données"
ms.assetid: 7e2e0f7f-94a8-4178-8bc7-d2e14ac8528c
caps.latest.revision: 13
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# DDL, fonctions, proc&#233;dures stock&#233;es et vues FileTable
  Répertorie les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] et les objets de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui ont été ajoutés ou modifiés afin de prendre en charge la fonctionnalité FileTable dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 La colonne d'état dans les tableaux suivants indique si l'élément est nouveau dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], ou bien s'il était présent dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mais a été modifié dans [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] pour prendre en charge la recherche sémantique.  
  
 Pour obtenir la liste des instructions et des objets de base de données qui prennent en charge FILESTREAM, consultez [FILESTREAM DDL, Functions, Stored Procedures, and Views](../../relational-databases/blob/filestream-ddl-functions-stored-procedures-and-views.md).  
  
##  <a name="ddl"></a> Instructions DDL (Data Definition Language, langage de définition de données) Transact-SQL  
  
|Objet|État|Informations supplémentaires|  
|------------|------------|----------------------|  
|[ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)<br /><br /> [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](../Topic/ALTER%20DATABASE%20SET%20Options%20\(Transact-SQL\).md)|Modifié|[Activer les conditions préalables pour les FileTables](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)<br /><br /> [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
|[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)|Modifié|[Créer, modifier et supprimer des FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)<br /><br /> [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
|[CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)|Modifié|[Activer les conditions préalables pour les FileTables](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)|  
|[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)|Modifié|[Créer, modifier et supprimer des FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)|  
|[RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20\(Transact-SQL\).md)<br /><br /> [Arguments RESTORE &#40;Transact-SQL&#41;](../Topic/RESTORE%20Arguments%20\(Transact-SQL\).md)|Modifié||  
  
##  <a name="func"></a> Fonctions  
  
|Objet|État|Informations supplémentaires|  
|------------|------------|----------------------|  
|[FileTableRootPath &#40;Transact-SQL&#41;](../../relational-databases/system-functions/filetablerootpath-transact-sql.md)|**Ajouté**|[Travailler avec des répertoires et des chemins d'accès dans FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)|  
|[GetFileNamespacePath &#40;Transact-SQL&#41;](../../relational-databases/system-functions/getfilenamespacepath-transact-sql.md)|**Ajouté**|[Travailler avec des répertoires et des chemins d'accès dans FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)|  
|[GetPathLocator &#40;Transact-SQL&#41;](../../relational-databases/system-functions/getpathlocator-transact-sql.md)|**Ajouté**|[Travailler avec des répertoires et des chemins d'accès dans FileTables](../../relational-databases/blob/work-with-directories-and-paths-in-filetables.md)|  
  
##  <a name="sproc"></a> Procédures stockées  
  
|Objet|État|Informations supplémentaires|  
|------------|------------|----------------------|  
|[sp_kill_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../Topic/sp_kill_filestream_non_transacted_handles%20\(Transact-SQL\).md)|**Ajouté**|[Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
  
##  <a name="cv"></a> Affichages catalogue  
  
|Objet|État|Informations supplémentaires|  
|------------|------------|----------------------|  
|[sys.database_filestream_options &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-filestream-options-transact-sql.md)|**Ajouté**|[Activer les conditions préalables pour les FileTables](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)|  
|[sys.filetable_system_defined_objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filetable-system-defined-objects-transact-sql.md)|**Ajouté**|[Créer, modifier et supprimer des FileTables](../../relational-databases/blob/create-alter-and-drop-filetables.md)<br /><br /> [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
|[sys.filetables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filetables-transact-sql.md)|**Ajouté**|[Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
|[sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)|Modifié|[Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
  
##  <a name="dmv"></a> Vues de gestion dynamique  
  
|Objet|État|Informations supplémentaires|  
|------------|------------|----------------------|  
|[sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md)|**Ajouté**|[Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)|  
  
## Voir aussi  
 [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)  
  
  