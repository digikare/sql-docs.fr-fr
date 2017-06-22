---
title: "Installer Reporting et Internet Information Services côte-à-côte | Documents Microsoft"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [Reporting Services], IIS
ms.assetid: 9b651fa5-f582-4f18-a77d-0dde95d9d211
caps.latest.revision: 40
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 1818a4b076dd6e1c81c0a9b39b781516bdf718e0
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---

# <a name="install-reporting-and-internet-information-services-side-by-side"></a>Installer Reporting et Internet Information Services côte à côte

[!INCLUDE[ssrs-appliesto-sql2016-preview](../../includes/ssrs-appliesto-sql2016-preview.md)]

  Vous pouvez installer et exécuter SQL Server Reporting Services (SSRS) et Internet Information Services (IIS) sur le même ordinateur. La version des services IIS (Internet Information Services) que vous utilisez détermine les problèmes d'interopérabilité que vous devez traiter.  
  
|Version des services IIS (Internet Information Services)|Problèmes|Description|  
|-----------------|------------|-----------------|  
|8.0, 8.5|Les requêtes prévues pour une application sont acceptées par une autre application.<br /><br /> HTTP.SYS applique des règles de priorité pour les réservations d'URL. Les requêtes envoyées aux applications qui ont le même nom de répertoire virtuel et qui surveillent conjointement le port 80 risquent de ne pas atteindre la cible prévue si la réservation d'URL est faible par rapport à la réservation d'URL d'une autre application.|Dans certaines conditions, un point de terminaison inscrit qui remplace un autre point de terminaison d'URL dans le schéma de réservation d'URL peut recevoir des requêtes HTTP destinées à l'autre application.<br /><br /> L’utilisation de noms de répertoires virtuels uniques pour le service Web Report Server et le [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] vous aide à éviter ce conflit.<br /><br /> Des informations détaillées sur ce scénario sont fournies dans cette rubrique.|  
  
## <a name="precedence-rules-for-url-reservations"></a>Règles de priorité pour les réservations d'URL  
 Avant de pouvoir traiter les problèmes d'interopérabilité entre les services IIS (Internet Information Services) et [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous devez comprendre le fonctionnement des règles de priorité pour la réservation d'URL. Les règles de priorité peuvent être généralisées à l'aide de la formule suivante : la réservation d'URL dont la définition des valeurs est la plus explicite est la première à recevoir les requêtes qui correspondent à l'URL.  
  
-   Une réservation d'URL qui spécifie un répertoire virtuel est plus explicite qu'une réservation d'URL qui omet un répertoire virtuel.  
  
-   Une réservation d'URL qui spécifie une adresse unique (via une adresse IP, un nom de domaine complet, un nom d'ordinateur réseau ou un nom d'hôte) est plus explicite qu'un caractère générique.  
  
-   Une réservation d'URL qui spécifie un caractère générique fort est plus explicite qu'un caractère générique faible.  
  
 Les exemples suivants illustrent une plage de réservations d'URL, de la plus explicite à la moins explicite :  
  
|Exemple|Demande|  
|-------------|-------------|  
|`http://123.234.345.456:80/reports`|Reçoit toutes les requêtes sont envoyées à `http://123.234.345.456/reports` ou `http://\<computername>/reports` si un service de nom de domaine peut résoudre l’adresse IP pour ce nom d’hôte.|  
|`http://+:80/reports`|Reçoit toutes les requêtes envoyées à une adresse IP ou un nom d'hôte valide pour cet ordinateur, tant que l'URL contient le nom de répertoire virtuel « reports ».|  
|`http://123.234.345.456:80`|Reçoit les requêtes qui spécifient `http://123.234.345.456` ou `http://\<computername>` si un service de nom de domaine peut résoudre l’adresse IP pour ce nom d’hôte.|  
|`http://+:80`|Reçoit les requêtes qui ne sont pas déjà reçues par d'autres applications, pour tous les points de terminaison d'application mappés à **Assigné**.|  
|`http://*:80`|Reçoit les requêtes qui ne sont pas déjà reçues par d'autres applications, pour les points de terminaison d'application mappés à **Non assigné**.|  
  
 Le message d'erreur suivant indique un conflit de ports : « System.IO.FileLoadException : Le processus ne peut pas accéder au fichier, car il est utilisé par un autre processus. (Exception de HRESULT : 0x80070020). »  
  
## <a name="url-reservations-for-iis-80-85-with-sql-server-reporting-services"></a>Réservations d’URL pour IIS 8.0, 8.5 avec SQL Server Reporting Services  
 Grâce aux règles de priorité décrites dans la section précédente, vous pouvez comprendre comment les réservations d'URL définies pour Reporting Services et les services IIS (Internet Information Services) favorisent l'interopérabilité. Reporting Services reçoit des requêtes qui spécifient explicitement les noms de répertoires virtuels de ses applications ; les services IIS (Internet Information Services) reçoivent toutes les requêtes restantes, lesquelles peuvent être adressées ensuite aux applications qui s'exécutent dans le cadre du modèle de processus IIS.  
  
|Application|Réservation d'URL|Description|Réception de requête|  
|-----------------|---------------------|-----------------|---------------------|  
|Serveur de rapports|`http://+:80/ReportServer`|Caractère générique fort sur le port 80, avec le répertoire virtuel du serveur de rapports.|Reçoit toutes les requêtes sur le port 80 qui spécifient le répertoire virtuel du serveur de rapports. Le service Web Report Server reçoit toutes les requêtes vers http://\<nom_ordinateur > / reportserver.|  
|Portail web|`http://+:80/Reports`|Caractère générique fort sur le port 80, avec le répertoire virtuel Reports.|Reçoit toutes les requêtes sur le port 80 qui spécifient le répertoire virtuel reports. Le [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] reçoit toutes les requêtes vers http://\<nom_ordinateur > /Reports.|  
|IIS|`http://*:80/`|Caractère générique faible sur le port 80.|Reçoit toutes les requêtes restantes sur le port 80, qui ne sont pas reçues par une autre application.|  

## <a name="side-by-side-deployments-of-sql-server-reporting-services-on-iis-80-85"></a>Déploiements côte à côte de SQL Server Reporting Services sur IIS 8.0, 8.5

 Des problèmes d'interopérabilité entre les services IIS (Internet Information Services) et Reporting Services se produisent lorsque les sites Web IIS ont des noms de répertoires virtuels identiques à ceux utilisés par Reporting Services. Prenons l'exemple de la configuration suivante :  
  
-   Site Web IIS assigné au port 80 et répertoire virtuel nommé « Reports ».  
  
-   Une instance de serveur de rapports installée dans la configuration par défaut, où la réservation d’URL spécifie également le port 80 et le [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] application utilise également « Reports » pour le nom de répertoire virtuel.  
  
 Avec cette configuration, une demande est envoyée à http://\<nom_ordinateur > : 80/reports sera reçues par le [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)]. L’application qui est accessible via le répertoire virtuel de Reports dans IIS ne recevra plus les demandes après l’installation de l’instance de serveur de rapports.  
  
 Si vous exécutez des déploiements côte à côte de versions plus anciennes et plus récentes de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], vous risquez de rencontrer le problème de routage qui vient d'être décrit. En effet, toutes les versions de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] utilisent « ReportServer » et « Reports » comme noms de répertoires virtuels pour le serveur de rapports et les applications [!INCLUDE[ssRSWebPortal-Non-Markdown](../../includes/ssrswebportal-non-markdown-md.md)] , ce qui augmente le risque d’avoir des répertoires virtuels « reports » et « reportserver » dans IIS.  
  
 Pour vous assurer que toutes les applications reçoivent des requêtes, suivez ces instructions :  
  
-   Pour les installations Reporting Services, choisissez des noms de répertoires virtuels qui ne sont pas déjà utilisés par un site Web IIS sur le même port que Reporting Services. En cas de conflit, installez Reporting Services en mode « fichiers uniquement » (via le programme d'installation, mais ne configurez pas l'option serveur dans l'Assistant Installation) afin de pouvoir configurer les répertoires virtuels, une fois l'installation terminée. Le message d'erreur suivant indique un conflit au niveau de votre configuration : « System.IO.FileLoadException : Le processus ne peut pas accéder au fichier, car il est utilisé par un autre processus. (Exception de HRESULT : 0x80070020). »  
  
-   Pour les installations que vous configurez manuellement, adoptez les conventions d'affectation des noms par défaut dans les URL de configuration. Si vous installez [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] en tant qu'instance nommée, incluez le nom de l'instance lors de la création d'un répertoire virtuel.  

## <a name="next-steps"></a>Étapes suivantes

[Configurer des URL de serveur de rapports](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)   
[Configurer une URL](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
[Installer le serveur de rapports Reporting Services en Mode natif](../../reporting-services/install-windows/install-reporting-services-native-mode-report-server.md)  

D’autres questions ? [Essayez de poser le forum Reporting Services](http://go.microsoft.com/fwlink/?LinkId=620231)