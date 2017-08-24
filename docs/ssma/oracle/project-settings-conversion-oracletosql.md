---
title: "Paramètres (Conversion) (OracleToSQL) du projet | Documents Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016 Preview
ms.assetid: a98a5e07-eb5e-47b9-a6f2-e2cb3a18309c
caps.latest.revision: 15
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: afd652370653f4642162fb596bdab88313366354
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="project-settings-conversion-oracletosql"></a>Paramètres du projet (Conversion) (OracleToSQL)
La page de Conversion de la **les paramètres de projet** boîte de dialogue contient des paramètres permettant de personnaliser comment SSMA convertit la syntaxe Oracle [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] syntaxe.  
  
Le volet de la Conversion est disponible dans le **les paramètres de projet** et **les paramètres de projet par défaut** boîtes de dialogue :  
  
-   Pour spécifier les paramètres pour tous les projets SSMA, sur le **outils** menu, cliquez sur **les paramètres de projet par défaut**, sélectionnez le type de projet de migration pour lequel les paramètres sont requis pour être affichées ou modifiées à partir de **Version cible de la Migration** liste déroulante, puis cliquez sur **général** au bas de la gauche, puis cliquez sur **Conversion**.  
  
-   Pour spécifier les paramètres pour le projet actuel, sur le **outils** menu, cliquez sur **les paramètres de projet**, puis cliquez sur **général** au bas de la gauche, puis cliquez sur **Conversion**.  
  
## <a name="conversion-messages"></a>Messages de conversion  
  
|||  
|-|-|  
|Terme|Définition|  
|**Générer des messages sur les problèmes appliquées**|Spécifie si SSMA génère des messages d’information pendant la conversion, les affiche dans le volet de sortie et les ajoute au code converti.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste :** N°<br /><br />**Mode complet :** N°|  
  
## <a name="miscellaneous-options"></a>Options diverses  
  
|||  
|-|-|  
|Terme|Définition|  
|**Expressions de cast ROWNUM en tant qu’entiers**|Lorsque SSMA convertit les expressions ROWNUM, il convertit l’expression dans une clause TOP, suivie par l’expression. L’exemple suivant montre ROWNUM dans une instruction DELETE d’Oracle :<br /><br />`DELETE FROM Table1`<br /><br />`WHERE ROWNUM < expression and Field1 >= 2`<br /><br />L’exemple suivant montre le qui en résulte [!INCLUDE[tsql](../../includes/tsql_md.md)]:<br /><br />`DELETE TOP (expression-1)`<br /><br />`FROM Table1`<br /><br />`WHERE Field1>=2`<br /><br />HAUT nécessite que l’expression TOP clauses correspond à un entier. Si l’entier est négatif, l’instruction génère une erreur.<br /><br />Si vous sélectionnez **Oui**, SSMA effectue un cast de l’expression en tant qu’entier.<br /><br />Si vous sélectionnez **non**, SSMA marque toutes les expressions de type non entier comme une erreur dans le code converti.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/complet :** N°<br /><br />**Mode optimisé :** Oui|  
|**Mappage de schéma par défaut**|Ce paramètre spécifie comment les schémas d’Oracle sont mappés à des schémas de SQL Server. Deux options sont disponibles pour ce paramètre :<br /><br />**Schéma de base de données :** dans ce mode, Oracle, schéma 'sch1' sera mappé par défaut pour le schéma de SQL Server « dbo » dans la base de données de SQL Server 'sch1'.<br /><br />**Schéma au schéma :**dans ce mode, Oracle, schéma 'sch1' sera mappé par défaut pour le schéma de SQL Server 'sch1' dans la base de données SQL Server par défaut fourni dans la boîte de dialogue de connexion.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/Optimistic/complet :** schéma de la base de données|  
|**Méthodes de conversion de l’instruction MERGE**|Si vous sélectionnez **à l’aide de INSERT, UPDATE, instruction DELETE**, SSMA convertit l’instruction de fusion dans INSERT, UPDATE, supprimer les instructions.<br /><br />Si vous sélectionnez **de fusion à l’aide de l’instruction**, SSMA convertit l’instruction de fusion dans une instruction MERGE dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].<br /><br />**Remarque :** cette option de configuration de projet est uniquement disponible dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2008, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2012, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 2014.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/Optimistic/complet :** Using fusion instruction|  
|**Convertir les appels des sous-programmes qui utilisent des arguments par défaut**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]les fonctions ne gèrent pas l’omission des paramètres dans l’appel de fonction. En outre, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] fonctions et procédures ne gèrent pas les expressions en tant que valeurs de paramètre par défaut.<br /><br />Si vous sélectionnez **Oui** et un appel de fonction omet les paramètres, SSMA insère le mot clé **par défaut** dans la fonction et l’appel à la position correcte. Ensuite, il marque l’appel avec un avertissement.<br /><br />Si vous sélectionnez **non**, SSMA marque les appels de fonction en tant qu’erreurs.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Oui|  
|**Convertir la fonction COUNT pour COUNT_BIG**|Si votre nombre de fonctions sont susceptibles de renvoyer les valeurs supérieure à 2 147 483 647, qui est de 2<sup>31</sup>-1, vous devez convertir les fonctions COUNT_BIG.<br /><br />Si vous sélectionnez **Oui**, SSMA convertit toutes les utilisations du nombre COUNT_BIG.<br /><br />Si vous sélectionnez **non**, les fonctions restent en tant que nombre. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Retourne une erreur si la fonction retourne une valeur supérieure à 2<sup>31</sup>-1.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/complet :** Oui<br /><br />**Mode optimisé :** N°|  
|**Convertir FORALL instruction WHILE instruction**|Définit comment SSMA traitera FORALL boucles sur les éléments de la collection PL/SQL.<br /><br />Si vous sélectionnez **Oui**, SSMA crée une boucle WHILE dans laquelle les éléments de collection sont récupérés un par un.<br /><br />Si vous sélectionnez **non**, SSMA génère un ensemble de lignes à partir de la collection à l’aide de la méthode de nœuds () et l’utilise en tant qu’une seule table. Cela est plus efficace, mais rend le code de sortie moins lisible.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste :** N°<br /><br />**Mode complet :** Oui|  
|**Clés étrangères de CONVERT avec l’action référentielle SET NULL sur la colonne qui est non NULL**|Oracle autorise la création de contraintes de clé étrangère, où une action SET NULL pas pu éventuellement être effectuée car les valeurs NULL ne sont pas autorisées dans la colonne référencée. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]n’autorise pas cette configuration de clé étrangère.<br /><br />Si vous sélectionnez **Oui**, SSMA générera des actions d’intégrité référentielle comme dans Oracle, mais vous devrez apporter les modifications manuelles apportées avant le chargement de la contrainte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Par exemple, vous pouvez choisir de NO ACTION au lieu de valeur NULL.<br /><br />Si vous sélectionnez **non**, la contrainte sera marquée comme une erreur.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** N°|  
|**Convertir les appels de fonction pour les appels de procédure**|Certaines fonctions Oracle sont définies en tant que transactions autonomes ou contiennent des instructions qui ne seraient pas valides dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Dans ces cas, SSMA crée une procédure et une fonction qui est un wrapper pour la procédure. La fonction convertie appelle la procédure d’implémentation.<br /><br />SSMA peut convertir les appels à la fonction wrapper en appels à la procédure. Cela crée un code plus lisible et peut améliorer les performances. Toutefois, le contexte ne permettre pas toujours ; par exemple, vous ne peut pas remplacer un appel de fonction dans la liste de sélection avec un appel de procédure. SSMA présente quelques options pour couvrir les cas courants :<br /><br />Si vous sélectionnez **toujours**, SSMA essaie de convertir les appels de fonction de wrapper dans les appels de procédure. Si le contexte actuel n’autorise pas cette conversion, un message d’erreur est généré. Ainsi, aucun appel de fonction n’est laissées dans le code généré.<br /><br />Si vous sélectionnez **lorsque cela est possible**, SSMA effectue un déplacement aux appels de procédure uniquement si la fonction a des paramètres de sortie. Lorsque le déplacement n’est pas possible, l’attribut de sortie du paramètre est supprimé. Dans tous les autres cas SSMA laisse les appels de fonction.<br /><br />Si vous sélectionnez **jamais**, SSMA laisse tous les appels de fonction comme appels de fonction. Ce choix peut parfois être inacceptable pour des raisons de performances.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/Optimistic/complet :** lorsque cela est possible|  
|**Convertir les instructions de la TABLE de verrouillage**|SSMA peut convertir de nombreuses instructions de la TABLE de verrouillage dans les indicateurs de table. SSMA ne peut pas convertir les instructions de la TABLE de verrouillage qui contiennent une PARTITION, SUBPARTITION, @dblinket des clauses NOWAIT et marque ces instructions avec des messages d’erreur de conversion.<br /><br />Si vous sélectionnez **Oui**, SSMA convertira les instructions LOCK TABLE prises en charge les indicateurs de table.<br /><br />Si vous sélectionnez **non**, SSMA marque toutes les instructions de TABLE de verrouillage avec les messages d’erreur de conversion.<br /><br />Le tableau suivant montre comment SSMA convertit les modes de verrouillage Oracle :<br /><br />**Mode de verrouillage Oracle**<br /><br />PARTAGE DE LA LIGNE<br /><br />LIGNE EXCLUSIF<br /><br />MISE À JOUR DU PARTAGE = PARTAGE DE LIGNE<br /><br />PARTAGER<br /><br />PARTAGER<br /><br />EXCLUSIF<br /><br />**Indicateur de Table SQL Server**<br /><br />ROWLOCK, HOLDLOCK<br /><br />ROWLOCK, XLOCK, HOLDLOCK<br /><br />ROWLOCK, HOLDLOCK<br /><br />TABLOCK, HOLDLOCK<br /><br />TABLOCK, XLOCK, HOLDLOCK<br /><br />TABLOCKX, HOLDLOCK<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Oui|  
|**Convertir les instructions OPEN-FOR pour les paramètres REF CURSOR OUT**|Dans Oracle, l’instruction OPEN-FOR peut être utilisée pour retourner un jeu de résultats à un sous-programme à un paramètre de type REF CURSOR. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], des procédures stockées directement les résultats d’instructions SELECT.<br /><br />SSMA peut convertir de nombreuses instructions FOR de l’ouvrir dans les instructions SELECT.<br /><br />Si vous sélectionnez **Oui**, SSMA convertit l’instruction OPEN-pour une instruction SELECT, qui retourne le jeu de résultats pour le client.<br /><br />Si vous sélectionnez **non**, SSMA génère un message d’erreur dans le code converti, puis dans le volet de sortie.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Oui|  
|**Convertir l’enregistrement sous forme de liste de variables de sépare**|SSMA peut convertir les enregistrements d’Oracle dans des variables de sépare et dans des variables de XML avec une structure spécifique.<br /><br />Si vous sélectionnez **Oui**, SSMA convertit l’enregistrement dans une liste de variables sépare lorsque cela est possible.<br /><br />Si vous sélectionnez **non**, SSMA convertit l’enregistrement de variables XML avec une structure spécifique.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Oui|  
|**Convertir les appels de fonction SUBSTR aux appels de fonction SUBSTRING**|SSMA peut convertir les appels de fonction Oracle SUBSTR dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **sous-chaîne** appels, en fonction du nombre de paramètres de fonction. Si SSMA ne peut pas convertir un appel de fonction SUBSTR ou le nombre de paramètres n’est pas pris en charge, SSMA convertira l’appel de fonction SUBSTR en un appel de fonction SSMA personnalisé.<br /><br />Si vous sélectionnez **Oui**, SSMA convertira les appels de fonction SUBSTR qui utilisent des trois paramètres dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] **sous-chaîne**. Autres fonctions SUBSTR seront converties pour appeler la fonction SSMA personnalisée.<br /><br />Si vous sélectionnez **non**, SSMA convertira l’appel de fonction SUBSTR en un appel de fonction SSMA personnalisé.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste :** Oui<br /><br />**Mode complet :** N°|  
|**Convertir les sous-types**|SSMA peut convertir des sous-types de PL/SQL de deux manières :<br /><br />Si vous sélectionnez **Oui**, SSMA créera [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] définie par l’utilisateur à partir d’un sous-type de type et l’utiliser pour chaque variable de ce sous-type.<br /><br />Si vous sélectionnez **non**, SSMA sera remplacer toutes les déclarations de source du sous-type avec le type sous-jacent et convertir le résultat comme d’habitude. Dans ce cas, aucun des types supplémentaires ne sont créés dans[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** N°|  
|**Convertir des synonymes**|Les synonymes pour les objets Oracle suivants peuvent être migrés vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]:<br /><br />Tables et des tables d’objets<br /><br />Vues et les vues de l’objet<br /><br />Fonctions et procédures stockées<br /><br />Vues matérialisées<br /><br />**Les synonymes pour les éléments suivants** objets Oracle peuvent être remplacés par des références directes aux objets :<br /><br />Séquences<br /><br />.<br /><br />Objets de schéma de classe Java<br /><br />Types d’objet défini par l’utilisateur<br /><br />Synonymes ne peuvent pas être migrés. SSMA génère des messages d’erreur pour le synonyme et toutes les références qui utilisent le synonyme.<br /><br />Si vous sélectionnez **Oui**, SSMA créera [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] synonymes et des références d’objet direct selon les listes précédentes.<br /><br />Si vous sélectionnez **non**, SSMA crée des références d’objet direct pour tous les synonymes sont répertoriées ici.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Oui|  
|**Convertir TO_CHAR (date, format)**|SSMA peut convertir Oracle TO_CHAR(date, format) dans les procédures de base de données sysdb.<br /><br />Si vous sélectionnez **(fonction) à l’aide de TO_CHAR_DATE**, SSMA convertit le TO_CHAR_DATE fonction à l’aide de la langue anglaise pour la conversion de la TO_CHAR (date, format).<br /><br />Si vous sélectionnez **(fonction) à l’aide de TO_CHAR_DATE_LS (NLS soins)**, SSMA convertit le TO_CHAR_DATE_LS fonction à l’aide de la langue de session pour la conversion de la TO_CHAR (date, format)<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/Optimistic :** Using TO_CHAR_DATE (fonction)<br /><br />**Mode complet :** Using TO_CHAR_DATE_LS (fonction) (NLS soins)|  
|**Convertir les instructions de traitement de transaction**|SSMA peut convertir les instructions de traitement de transaction Oracle :<br /><br />Si vous sélectionnez **Oui**, SSMA convertit les instructions de traitement de transaction Oracle à [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] instructions.<br /><br />Si vous sélectionnez **non**, SSMA marque la transaction du traitement d’instructions en tant qu’erreurs de conversion.<br /><br />**Remarque :** Oracle ouvre implicitement des transactions. Pour émuler ce comportement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], vous devez ajouter les instructions BEGIN TRANSACTION manuellement où vous souhaitez que vos transactions pour démarrer. Vous pouvez aussi exécuter la commande SET IMPLICIT_TRANSACTIONS ON au début de votre session. SSMA ajoute automatiquement SET IMPLICIT_TRANSACTIONS ON lors de la conversion des sous-routines avec transactions autonomes.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Oui|  
|**Émuler le comportement de null Oracle dans des clauses ORDER BY**|Les valeurs NULL sont ordonnées différemment dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] et Oracle :<br /><br />Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], NULL les valeurs sont les valeurs les plus basses d’une liste ordonnée. Dans une liste croissante, les valeurs NULL apparaît en premier.<br /><br />Dans Oracle, les valeurs NULL sont les valeurs les plus élevées dans une liste ordonnée. Par défaut, les valeurs NULL apparaissent en derniers dans une liste en ordre croissant.<br /><br />Oracle a des clauses de valeurs NULL et les valeurs NULL prénom, qui vous permet de modifier la façon dont Oracle trie les valeurs NULL.<br /><br />SSMA peut émuler le comportement Oracle ORDER BY en recherchant les valeurs NULL. Il puis tout d’abord des commandes par les valeurs NULL dans l’ordre spécifié et les commandes par d’autres valeurs.<br /><br />Si vous sélectionnez **Oui**, SSMA convertira l’instruction Oracle d’une manière qui émule le comportement Oracle ORDER BY.<br /><br />Si vous sélectionnez **non**, SSMA ignore les règles d’Oracle et générer un message d’erreur quand il rencontre les clauses de valeurs NULL et les valeurs NULL prénom.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste :** N°<br /><br />**Mode complet :** Oui|  
|**Émuler des exceptions de nombre de lignes dans SELECT**|Si une instruction SELECT avec une clause INTO ne retourne pas de toutes les lignes, Oracle déclenche une exception NO_DATA_FOUND. Si l’instruction retourne deux ou plusieurs lignes, l’exception TOO_MANY_ROWS est déclenchée. L’instruction convertie dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ne déclenche pas une exception si le nombre de lignes est différent d’un.<br /><br />Si vous sélectionnez **Oui**, SSMA ajoute un appel à sysdb procédure db_error_exact_one_row_check après chaque instruction SELECT. Cette procédure émule les exceptions NO_DATA_FOUND et TOO_MANY_ROWS. Ceci est la valeur par défaut et vous permet de reproduire le comportement d’Oracle aussi proche que possible. Vous devez toujours choisir **Oui** si le code source a des gestionnaires d’exceptions qui traitent de ces erreurs. Notez que si l’instruction SELECT se produit à l’intérieur d’une fonction définie par l’utilisateur, ce module sera converti en une procédure stockée, car l’exécution des procédures stockées et le déclenchement d’exceptions n’est pas compatible avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] contexte de la fonction.<br /><br />Si vous sélectionnez **non**, aucune exception ne sera générée. Qui peut être utile lorsque SSMA convertit une fonction définie par l’utilisateur et que vous souhaitez qu’il reste une fonction dans[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Oui|  
|**Génère l’erreur pour DBMS_SQL. ANALYSE**|Si vous sélectionnez **erreur**, SSMA générer d’erreur à la conversion DBMS_SQL. ANALYSE.<br /><br />Si vous sélectionnez **avertissement**, SSMA génèrent un avertissement à la conversion DBMS_SQL. ANALYSE.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** erreur|  
|**Générer la colonne ROWID**|Lorsque SSMA crée des tables dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], il peut créer une colonne de ligne ROWID. Lors de la migration des données, chaque ligne Obtient une nouvelle valeur UNIQUEIDENTIFIER générée par la fonction newid().<br /><br />Si vous sélectionnez **Oui**, la colonne ROWID est créée sur toutes les tables et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] génère des GUID lorsque vous insérez des valeurs. Choisissez toujours **Oui** si vous envisagez d’utiliser le testeur de SSMA.<br /><br />Si vous sélectionnez **non**, les colonnes ROWID ne sont pas ajoutées aux tables.<br /><br />**Ajouter une colonne d’ID de ligne pour les tables avec des déclencheurs** ajouter ROWID pour les tables contenant des déclencheurs.<br /><br />**Remarque :** paramètre par défaut dans le cas de SQL Server 2005, SQL Server 2008 et SQL Server 2012 et 2014 est **colonne ROWID d’ajouter des tables avec des déclencheurs**.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/Optimistic :** ajouter la colonne ROWID pour les tables avec des déclencheurs<br /><br />**Mode complet :** Oui|  
|**Générer un index unique sur la colonne d’ID de ligne**|Spécifie si SSMA génère une colonne d’index unique sur la colonne ROWID généré ou non. Si l’option est définie sur « Oui », l’index unique est généré et s’il est défini sur « Non », index unique n’est pas généré sur la colonne de ligne ROWID.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Oui|  
|**Conversion de modules locaux**|Définit le type de conversion de sous-programme (déclaré dans la procédure d’autonome stockée ou fonction) d’oracle imbriqué.<br /><br />Si vous sélectionnez **Inline**, les appels imbriqués sous-programme seront remplacés par son corps.<br /><br />Si vous sélectionnez **des procédures stockées**sous-programme imbriquée sera convertie en une procédure stockée SQL Server et seront remplacés ses appels sur cet appel de procédure.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Inline|  
|**Utilisation de ISNULL dans la concaténation de chaînes**|Oracle et [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] retournent des résultats différents lorsque les concaténations de chaînes incluent des valeurs NULL. Oracle considère la valeur NULL comme un jeu de caractères vide. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Retourne la valeur NULL.<br /><br />Si vous sélectionnez **Oui**, SSMA remplace le caractère de concaténation Oracle (&#124; &#124;) avec le [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] caractère de concaténation (+). SSMA vérifie également les expressions des deux côtés de la concaténation des valeurs NULL.<br /><br />Si vous sélectionnez **non**, SSMA remplace les caractères de concaténation, mais ne vérifie pas les valeurs NULL.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Oui|  
|**Utilisation de ISNULL dans les appels de fonction REPLACE**|Instruction de ISNULL est utilisée dans les appels de fonction REPLACE pour émuler le comportement d’Oracle. Les options suivantes sont présentes pour ce paramètre :<br /><br />YES<br /><br />Non<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste :** N°<br /><br />**Mode complet :** Oui|  
|**Utilisation de ISNULL dans les appels de fonction CONCAT**|Instruction de ISNULL est utilisée dans les appels de fonction CONCAT pour émuler le comportement d’Oracle. Les options suivantes sont présentes pour ce paramètre :<br /><br />YES<br /><br />Non<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste :** N°<br /><br />**Mode complet :** Oui|  
|**Utiliser la fonction convert natif lorsque cela est possible**|Si vous sélectionnez **Oui**, SSMA convertit le TO_CHAR (date, format) en fonction convert natif lorsque cela est possible.<br /><br />Si vous sélectionnez **non**, SSMA convertit le TO_CHAR (date, format) TO_CHAR_DATE ou TO_CHAR_DATE_LS (défini par les options de « Convertir TO_CHAR(date, format) »).<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste :** Oui<br /><br />**Mode complet :** N°|  
|**Utiliser l’instruction SELECT... FOR XML lors de la conversion, sélectionnez... INTO pour la variable d’enregistrement**|Spécifie s’il faut générer un résultat XML défini lorsque vous sélectionnez dans une variable d’enregistrement.<br /><br />Si vous sélectionnez **Oui**, l’instruction SELECT renvoie le code XML.<br /><br />Si vous sélectionnez **non**, l’instruction SELECT renvoie un jeu de résultats.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** N°|  
  
## <a name="returning-clause-conversion"></a>Conversion de la Clause de retour  
  
|||  
|-|-|  
|Terme|Définition|  
|**Convertir de clause RETURNING dans l’instruction DELETE en sortie**|Oracle fournit une clause RETURNING comme un moyen d’obtenir immédiatement les valeurs supprimées. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]fournit cette fonctionnalité avec la clause OUTPUT.<br /><br />Si vous sélectionnez **Oui**, SSMA convertira les clauses de retour dans les instructions DELETE aux clauses de sortie. Étant donné que les déclencheurs sur une table peuvent modifier les valeurs, la valeur retournée peut être différente dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] qu’il l’était dans Oracle.<br /><br />Si vous sélectionnez **non**, SSMA génère une instruction SELECT avant de supprimer les instructions pour extraire des valeurs retournées.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Oui|  
|**Convertir en sortie clause RETURNING dans l’instruction INSERT**|Oracle fournit une clause RETURNING comme un moyen d’obtenir immédiatement les valeurs insérées. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]fournit cette fonctionnalité avec la clause OUTPUT.<br /><br />Si vous sélectionnez **Oui**, SSMA convertira une clause RETURNING dans une instruction INSERT en sortie. Étant donné que les déclencheurs sur une table peuvent modifier les valeurs, la valeur retournée peut être différente dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] qu’il l’était dans Oracle.<br /><br />Si vous sélectionnez **non**, SSMA émule la fonctionnalité Oracle en insérant, puis en sélectionnant les valeurs dans une table de référence.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Oui|  
|**Convertir la clause RETURNING dans l’instruction de mise à jour à la sortie**|Oracle fournit une clause RETURNING comme un moyen d’obtenir immédiatement les valeurs mises à jour. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]fournit cette fonctionnalité avec la clause OUTPUT.<br /><br />Si vous sélectionnez **Oui**, SSMA convertira les clauses de retour dans les instructions de mise à jour pour les clauses de sortie. Étant donné que les déclencheurs sur une table peuvent modifier les valeurs, la valeur retournée peut être différente dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] qu’il l’était dans Oracle.<br /><br />Si vous sélectionnez **non**, SSMA génère des instructions SELECT après les instructions de mise à jour pour récupérer les valeurs de retour.<br /><br />Lorsque vous sélectionnez un mode de conversion dans le **Mode** zone, SSMA s’applique le paramètre suivant :<br /><br />**Le Mode par défaut/optimiste/complet :** Oui|  
  
## <a name="sequence-conversion"></a>Conversion de séquence  
  
|||  
|-|-|  
|Terme|Définition|  
|**Convertir le Générateur de séquence**|Dans Oracle, vous pouvez utiliser une séquence pour générer des identificateurs uniques.<br /><br />SSMA peut convertir des séquences à ce qui suit.<br /><br />À l’aide du Générateur de séquence de SQL Server (cette option est uniquement disponible lors de la conversion de SQL Server 2012 et SQL Server 2014).<br /><br />À l’aide du Générateur de séquence de SSMA.<br /><br />À l’aide d’identité de colonne.<br /><br />L’option par défaut lors de la conversion de SQL Server 2012 ou SQL Server 2014 est d’utiliser le Générateur de séquence de SQL Server. Toutefois, SQL Server 2012 et SQL Server 2014 ne prend pas en charge obtenir la valeur actuelle de la séquence (telle que celle de la méthode currval de séquence Oracle). Reportez-vous au site de blog de l’équipe SSMA pour obtenir des conseils sur la méthode de currval de séquence Oracle migration.<br /><br />SSMA fournit également une option permettant de convertir une séquence d’Oracle émulateur de séquence SSMA. Cette option est la valeur par défaut lorsque vous convertissez vers SQL Server antérieures à 2012<br /><br />Enfin, vous pouvez également convertir séquence assigné à une colonne de table pour les valeurs d’identité SQL Server. Vous devez spécifier le mappage entre les séquences pour une colonne d’identité sur Oracle **Table** onglet|  
|**Convertir CURRVAL en dehors de déclencheurs**|Visible uniquement lorsque le Générateur de séquence convertir est défini sur **à l’aide d’identité de colonne**. Séquences Oracle étant des objets séparés des tables, de nombreuses tables qui utilisent des séquences utilisent un déclencheur pour générer et insérer une nouvelle valeur de la séquence. SSMA commente ces instructions et les marque comme des erreurs lors de la sortie de commentaire génèrent des erreurs.<br /><br />Si vous sélectionnez **Oui**, SSMA marque toutes les références pour en dehors de déclencheurs sur la séquence CURRVAL avec un avertissement.<br /><br />Si vous sélectionnez **non**, SSMA marque toutes les références pour en dehors de déclencheurs sur la séquence CURRVAL avec une erreur.|  
  
## <a name="see-also"></a>Voir aussi  
[Référence de l’Interface utilisateur &#40; OracleToSQL &#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  
