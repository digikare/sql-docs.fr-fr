---
title: Resync, méthode-exemple (VB) | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Resync method [ADO], Visual Basic example
ms.assetid: ab95315c-fe15-458c-9e0c-937ae5596592
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0722fb59229cef08f8e93a2d7bf13ca3c2a8d83
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="resync-method-example-vb"></a>Resync, méthode-exemple (VB)
Cet exemple montre comment utiliser le [Resync](../../../ado/reference/ado-api/resync-method.md) méthode pour actualiser les données dans un jeu d’enregistrements statique.  
  
```  
'BeginResyncVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection strings  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'connection and recordset variables  
    Dim Cnxn As ADODB.Connection  
    Dim rstTitles As ADODB.Recordset  
    Dim strCnxn As String  
    Dim strSQLTitles As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Open recordset using object refs to set properties  
    ' that allow for updates to the database  
    Set rstTitles = New ADODB.Recordset  
    Set rstTitles.ActiveConnection = Cnxn  
    rstTitles.CursorType = adOpenKeyset  
    rstTitles.LockType = adLockOptimistic  
  
    strSQLTitles = "titles"  
    rstTitles.Open strSQLTitles  
  
    'rstTitles.Open strSQLTitles, Cnxn, adOpenKeyset, adLockPessimistic, adCmdTable  
    'the above line of code passes the same refs as the object refs listed above  
  
    ' Change the type of the first title in the recordset  
    rstTitles!Type = "database"  
  
    ' Display the results of the change  
    MsgBox "Before resync: " & vbCr & vbCr & _  
        "Title - " & rstTitles!Title & vbCr & _  
        "Type - " & rstTitles!Type  
  
    ' Resync with database and redisplay results  
    rstTitles.Resync  
    MsgBox "After resync: " & vbCr & vbCr & _  
        "Title - " & rstTitles!Title & vbCr & _  
        "Type - " & rstTitles!Type  
  
    ' clean up  
    rstTitles.CancelBatch  
    rstTitles.Close  
    Cnxn.Close  
    Set rstTitles = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstTitles Is Nothing Then  
        If rstTitles.State = adStateOpen Then  
            rstTitles.CancelBatch  
            rstTitles.Close  
        End If  
    End If  
    Set rstTitles = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndResyncVB  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Objet Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Resync, méthode](../../../ado/reference/ado-api/resync-method.md)
