---
title: Affichage du journal des applications Windows | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: configuration-manager
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- application logs [SQL Server]
- Windows application logs [SQL Server]
- viewing Windows application logs
- errors [SQL Server], logs
- system logs [SQL Server]
- security logs [SQL Server]
- displaying Windows application logs
- logs [SQL Server], Windows application logs
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a88b2880ff6626dd4841a7e65764475c07ee1b04
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="viewing-the-windows-application-log"></a>Affichage du journal des applications Windows
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Lorsque [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour utiliser le journal des applications Windows, chaque session [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] écrit un nouvel événement dans ce journal. Contrairement au journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , un nouveau journal des applications n'est pas créé chaque fois que vous démarrez une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Affichez et gérez le journal des applications Windows en utilisant l'Observateur d'événements de Windows ou la Visionneuse du journal de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 Il existe trois journaux pouvant être affichés avec l’Observateur d’événements.  
  
|Type de journal Windows|Description|  
|----------------------|-----------------|  
|Journal système|Il enregistre les événements consignés par les composants du système d'exploitation Windows. L'échec du chargement d'un pilote ou d'un autre composant du système lors du démarrage, par exemple, est consigné dans le journal système.|  
|Journal de sécurité|Il enregistre les événements de sécurité comme les tentatives de connexion qui ont échoué. Cela permet de rechercher les modifications du système de sécurité et d'identifier les violations possibles de la sécurité. Par exemple, les tentatives de connexion au système doivent être enregistrées dans le journal de sécurité, en fonction des paramètres d'audit du gestionnaire des utilisateurs.<br /><br /> Seuls les membres du rôle serveur fixe **sysadmin** peuvent afficher le journal de sécurité.|  
|Journal des applications|Il enregistre les événements qui sont consignés par les applications. Par exemple, une application de base de données peut enregistrer un fichier d'erreurs dans le journal des applications.|  
  
 Pour plus d'informations sur l'utilisation de l'Observateur d'événements, la gestion du journal des applications et la signification des données qui y figurent, consultez la documentation de Windows.  
  
 **Pour consulter le journal des applications Windows**  
  
 [Afficher le journal des applications Windows &#40;Windows&#41;](../../relational-databases/performance/view-the-windows-application-log-windows-10.md)  
  
  
