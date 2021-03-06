---
title: sqlsrv_commit | Documents Microsoft
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- sqlsrv_commit
apitype: NA
helpviewer_keywords:
- transaction support
- API Reference, sqlsrv_commit
- sqlsrv_commit
ms.assetid: bad67571-61ad-45b5-b4ff-677e3544f809
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 05f3c5710cfcf308073a91fd752eb1abbff8b9d4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsrvcommit"></a>sqlsrv_commit
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Valide la transaction actuelle sur la connexion spécifiée et retourne la connexion au mode de validation automatique. La transaction actuelle contient toutes les instructions sur la connexion spécifiée qui ont été exécutées après l’appel à [sqlsrv_begin_transaction](../../connect/php/sqlsrv-begin-transaction.md) et avant tous les appels à [sqlsrv_rollback](../../connect/php/sqlsrv-rollback.md) ou **sqlsrv_commit**.  
  
> [!NOTE]  
> Le [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] est en mode de validation automatique par défaut. Cela signifie que toutes les requêtes sont validées automatiquement en cas de réussite, sauf si elles ont été désignées comme faisant partie d’une transaction explicite à l’aide de **sqlsrv_begin_transaction**.  
  
> [!NOTE]  
> Si **sqlsrv_commit** est appelé sur une connexion qui n’est pas dans une transaction active et qui a été lancée avec **sqlsrv_begin_transaction**, l’appel retourne **false** et une erreur *Pas dans la transaction* est ajoutée à la collection d’erreurs.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sqlsrv_commit( resource $conn )  
```  
  
#### <a name="parameters"></a>Paramètres  
*$conn*: connexion sur laquelle la transaction est active.  
  
## <a name="return-value"></a>Valeur retournée  
Valeur booléenne : **true** si la transaction a été correctement validée. Dans le cas contraire, la valeur est **false**.  
  
## <a name="example"></a>Exemple  
L’exemple ci-après exécute deux requêtes dans le cadre d’une transaction. Si les deux requêtes réussissent, la transaction est validée. Si l’une des requêtes (ou les deux) échoue, la transaction est annulée.  
  
La première requête de l’exemple insère une nouvelle commande dans la table *Sales.SalesOrderDetail* de la base de données AdventureWorks. La commande concerne cinq unités du produit dont l’ID est 709. La seconde requête réduit de cinq unités la quantité de stock du produit dont l’ID est 709. Ces requêtes sont incluses dans une transaction, car elles doivent toutes les deux réussir pour que la base de données reflète avec exactitude l’état des commandes et la disponibilité du produit.  
  
L’exemple part du principe que SQL Server et le [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) base de données sont installés sur l’ordinateur local. Toute la sortie est écrite dans la console quand l’exemple est exécuté à partir de la ligne de commande.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initiate transaction. */  
/* Exit script if transaction cannot be initiated. */  
if (sqlsrv_begin_transaction( $conn) === false)  
{  
     echo "Could not begin transaction.\n";  
     die( print_r( sqlsrv_errors(), true ));  
}  
  
/* Initialize parameter values. */  
$orderId = 43659; $qty = 5; $productId = 709;  
$offerId = 1; $price = 5.70;  
  
/* Set up and execute the first query. */  
$tsql1 = "INSERT INTO Sales.SalesOrderDetail   
                     (SalesOrderID,   
                      OrderQty,   
                      ProductID,   
                      SpecialOfferID,   
                      UnitPrice)  
          VALUES (?, ?, ?, ?, ?)";  
$params1 = array( $orderId, $qty, $productId, $offerId, $price);  
$stmt1 = sqlsrv_query( $conn, $tsql1, $params1 );  
  
/* Set up and execute the second query. */  
$tsql2 = "UPDATE Production.ProductInventory   
          SET Quantity = (Quantity - ?)   
          WHERE ProductID = ?";  
$params2 = array($qty, $productId);  
$stmt2 = sqlsrv_query( $conn, $tsql2, $params2 );  
  
/* If both queries were successful, commit the transaction. */  
/* Otherwise, rollback the transaction. */  
if( $stmt1 && $stmt2 )  
{  
     sqlsrv_commit( $conn );  
     echo "Transaction was committed.\n";  
}  
else  
{  
     sqlsrv_rollback( $conn );  
     echo "Transaction was rolled back.\n";  
}  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt1);  
sqlsrv_free_stmt( $stmt2);  
sqlsrv_close( $conn);  
?>  
```  
  
Pour mieux mettre l’accent sur le comportement de la transaction, aucune recommandation en matière de gestion des erreurs n’est incluse dans l’exemple précédent. Pour une application de production, nous vous recommandons de vérifier s’il existe des erreurs et de les gérer en conséquence dans tout appel à la fonction **sqlsrv** .  
  
> [!NOTE]  
> N’utilisez pas Transact-SQL incorporé pour effectuer des transactions. Par exemple, n’exécutez pas une instruction avec “BEGIN TRANSACTION” en tant que requête Transact-SQL pour commencer une transaction. Le comportement transactionnel attendu ne peut pas être garanti lors de l’utilisation de Transact-SQL incorporé pour effectuer des transactions.  
  
## <a name="see-also"></a>Voir aussi  
[Informations de référence sur l’API du pilote SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)

[Guide pratique pour effectuer des transactions](../../connect/php/how-to-perform-transactions.md)

[Vue d’ensemble des pilotes Microsoft SQL Server pour PHP](../../connect/php/overview-of-the-php-sql-driver.md)
  
