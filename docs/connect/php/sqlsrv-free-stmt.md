---
title: sqlsrv_free_stmt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_free_stmt
apitype: NA
helpviewer_keywords:
- sqlsrv_free_stmt
- API Reference, sqlsrv_free_stmt
ms.assetid: 3c71f432-36ad-41e1-8ac7-587c82539448
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fb937b9477be3a18f14960c3ed9d142aacbe7452
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922765"
---
# <a name="sqlsrv_free_stmt"></a>sqlsrv_free_stmt
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Gibt alle der angegebenen Anweisung zugeordneten Ressourcen frei. Die Anweisung kann nicht erneut verwendet werden, nachdem diese Funktion aufgerufen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlsrv_free_stmt( resource $stmt)  
```  
  
#### <a name="parameters"></a>Parameter  
*$stmt*: Die Anweisung, die geschlossen werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
Der boolesche Wert **true** , außer die Funktion wird mit einem ungültigen Parameter aufgerufen. Wenn die Funktion mit einem ungültigen Parameter aufgerufen wird, wird **false** zurückgegeben.  
  
> [!NOTE]  
> **NULL** ist ein gültiger Parameter für diese Funktion. Dadurch kann die Funktion mehrmals in einem Skript aufgerufen werden. Wenn Sie z.B. eine Verbindung in einem Fehlerzustand freigeben und sie erneut am Ende des Skripts freigeben, gibt der zweite Aufruf von **sqlsrv_free_stmt** den Wert **TRUE** zurück, da der erste Aufruf von **sqlsrv_free_stmt** (im Fehlerzustand) die Verbindungsressource auf **NULL** festlegt.  
  
## <a name="example"></a>Beispiel  
Das folgende Beispiel erstellt eine Anwendungsressource, führt eine einfache Abfrage durch und ruft **sqlsrv_free_stmt** auf, um alle der Anweisung zugeordneten Ressourcen freizugeben. Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks-Datenbank](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) auf dem lokalen Computer installiert sind. Wenn das Beispiel über die Befehlszeile ausgeführt wird, werden alle Ausgaben in die Konsole geschrieben.  
  
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
     die( print_r( sqlsrv_errors(), true));  
}  
  
$stmt = sqlsrv_query( $conn, "SELECT * FROM Person.Contact");  
if( $stmt )  
{  
     echo "Statement executed.\n";  
}  
else  
{  
     echo "Query could not be executed.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/*-------------------------------  
     Process query results here.  
-------------------------------*/  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)  

[Informationen zu den Codebeispielen in der Dokumentation](../../connect/php/about-code-examples-in-the-documentation.md)  

[sqlsrv_cancel](../../connect/php/sqlsrv-cancel.md)  
  
