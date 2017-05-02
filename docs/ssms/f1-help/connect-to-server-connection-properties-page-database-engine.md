---
title: "Se connecter au serveur (page Propriétés de connexion) — Moteur de base de données | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connecttoce.connectionproperties.f1
- sql13.swb.connecttosqlserver.connectionproperties.f1
ms.assetid: edc1143c-6a47-4b02-92ab-441bdea8ea8a
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 22cef3465036947ad6389b41c4c80bfc5ef965cb
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-connection-properties-page-database-engine"></a>Se connecter au serveur (page Propriétés de connexion) — Moteur de base de données
Utilisez cet onglet pour afficher ou spécifier les options de connexion à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)] [!INCLUDE[msCoName](../../includes/msconame_md.md)] ou d’inscription du [!INCLUDE[ssDE](../../includes/ssde_md.md)] dans **Serveurs inscrits**. **Se connecter** et **Options** ne s’affichent dans cette boîte de dialogue que quand vous vous connectez à une instance du [!INCLUDE[ssDE](../../includes/ssde_md.md)]. **Tester** et **Enregistrer** s’affichent uniquement dans cette boîte de dialogue lors de l’inscription du [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
## <a name="options"></a>Options  
**Se connecter à la base de données**  
Dans la liste, sélectionnez une base de données à laquelle se connecter. Si vous sélectionnez **<default>**, c’est à la base de données par défaut pour ce serveur que vous serez connecté. Si vous sélectionnez **<Browse server>**, vous pouvez parcourir l’arborescence du serveur à la recherche de la base de données à laquelle vous souhaitez vous connecter.  
  
Quand vous vous connectez à une instance du moteur de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] par le biais de [!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)], vous devez utiliser l’authentification [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et spécifier une base de données dans la boîte de dialogue **Se connecter au serveur** , sous l’onglet **Propriétés de connexion** . Vérifiez que vous avez coché la case **Chiffrer la connexion** .  
  
Par défaut, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] se connecte à **master**. Si vous spécifiez une base de données utilisateur, vous ne verrez que la base de données et ses objets dans l'Explorateur d'objets. Si vous vous connectez à **master**, vous pouvez consulter toutes les bases de données. Pour plus d’informations, consultez [Présentation de la base de données SQL Azure Windows](http://go.microsoft.com/fwlink/?LinkId=163948).  
  
**Protocole réseau**  
Sélectionnez un protocole dans la liste. Les protocoles client disponibles sont ceux que vous avez configurés à l'aide de la configuration du réseau client dans Gestion de l'ordinateur.  
  
**Taille du paquet réseau**  
Entrez la taille des paquets à envoyer. La valeur par défaut est 4096 octets.  
  
**Délai de connexion**  
Spécifiez le délai d'expiration imparti, en secondes, pour qu'une connexion soit établie. La valeur par défaut est 15 secondes.  
  
**Délai d’exécution**  
Entrez le nombre de secondes que peut prendre l'exécution d'une tâche sur le serveur. La valeur par défaut est égale à zéro seconde, ce qui définit un délai d'attente illimité.  
  
**Chiffrer la connexion**  
Force le chiffrement de la connexion.  
  
**Utiliser une couleur personnalisée**  
Sélectionnez cette option pour spécifier la couleur d'arrière-plan de la barre d'état dans une fenêtre de l'éditeur de requête du [!INCLUDE[ssDE](../../includes/ssde_md.md)] . Pour spécifier la couleur, cliquez sur **Sélectionner**. Dans la boîte de dialogue **Couleur** , sélectionnez une couleur prédéfinie dans la grille **Couleurs de base** ou cliquez sur **Définir les couleurs personnalisées** pour définir et utiliser une couleur personnalisée.  
  
-   Quand vous spécifiez une couleur pour une entrée de serveur dans le volet **Explorateur d’objets** , cette couleur est utilisée quand vous ouvrez une fenêtre de l’éditeur de requête. Pour ouvrir une fenêtre de l’éditeur de requête, cliquez avec le bouton droit sur l’entrée de serveur et sélectionnez **Nouvelle requête**; ou bien, quand le volet **Explorateur d’objets** est actif et que le focus est sur ce serveur, cliquez sur **Nouvelle requête** dans la barre d’outils.  
  
-   Quand vous spécifiez une couleur pour une entrée de serveur dans le volet **Serveurs inscrits** , cette couleur est utilisée quand vous ouvrez une fenêtre de l’éditeur de requête. Pour ouvrir une fenêtre de l’éditeur de requête, cliquez avec le bouton droit sur l’entrée de serveur et sélectionnez **Nouvelle requête**; ou bien, quand le volet **Serveurs inscrits** est actif et que le focus est sur ce serveur, cliquez sur **Nouvelle requête** dans la barre d’outils.  
  
-   Dans le menu **Fichier** , quand vous cliquez sur **Nouveau** puis sur **Requête de moteur de base de données**, la couleur que vous spécifiez dans la boîte de dialogue **Se connecter au serveur** s’applique à cette fenêtre de l’éditeur de requête.  
  
**Réinitialiser tout**  
Remplace toutes les valeurs des propriétés de connexion spécifiées manuellement par les valeurs par défaut.  
  
**Se connecter**  
Tente d'établir une connexion à l'aide des valeurs indiquées.  
  
**Options**  
Cliquez sur cette option pour modifier l’apparence de la boîte de dialogue en masquant les options de connexion serveur supplémentaires, comme la mémorisation du mot de passe.  
  
**Testerer**  
Quand vous inscrivez [!INCLUDE[ssDE](../../includes/ssde_md.md)] dans **Serveurs inscrits**, cliquez ici pour tester la connexion.  
  
**Enregistrer**  
Enregistre les paramètres dans **Serveurs inscrits**.  
  
## <a name="see-also"></a>Voir aussi  
[Boîte de dialogue Propriétés de la connexion](../../ssms/f1-help/connection-properties-dialog-box.md)  
  
