---
title: sqlsrv_connect | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_connect
apitype: NA
helpviewer_keywords:
- connecting to the server
- API Reference, sqlsrv_connect
- connection pooling support
- sqlsrv_connect
ms.assetid: 37836b49-258e-45ce-9549-b8bd85d6952d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 11da2b4eca130eafe93a01315aaa1f6d9919632c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015038"
---
# <a name="sqlsrv_connect"></a>sqlsrv_connect
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Erstellt eine Verbindungsressource und öffnet eine Verbindung. Standardmäßig wird versucht, die Verbindung unter Verwendung der Windows-Authentifizierung herzustellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sqlsrv_connect( string $serverName [, array $connectionInfo])  
```  
  
#### <a name="parameters"></a>Parameter  
*$serverName*: Eine Zeichenfolge, die den Namen des Servers angibt, zu dem eine Verbindung erstellt werden soll. Ein Instanzname (z. B. „MeinServer\InstanzName“) oder Port (z. B. „MeinServer, 1521“) kann als Teil dieser Zeichenfolge enthalten sein. Eine vollständige Beschreibung der Optionen für diesen Parameter finden Sie im Abschnitt „Server-Schlüsselwort in den Kennwörtern der Verbindungszeichenfolgen des ODCB-Treibers“. Diesen finden Sie unter [Verwenden von Schlüsselwörtern für Verbindungszeichenfolgen mit SQL Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
Ab Version 3.0 der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]können Sie auch eine LocalDB-Instanz mit `"(localdb)\instancename"`angeben. Weitere Informationen finden Sie [unter Unterstützung für localdb](../../connect/php/php-driver-for-sql-server-support-for-localdb.md).  
  
Zusätzlich können Sie ab der Version 3.0 der [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]einen virtuellen Netzwerknamen angeben, um sich mit einer AlwaysOn-Verfügbarkeitsgruppe zu verbinden. Weitere Informationen [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] zur-Unterstützung [!INCLUDE[ssHADR](../../includes/sshadr_md.md)]für finden Sie [unter Unterstützung für hohe Verfügbarkeit, Notfall Wiederherstellung](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).  
  
*$connectionInfo* (optional): ein assoziatives **Array**, das Verbindungsattribute enthält (z.B. **array**("Database" => "AdventureWorks")). Unter [Connection Options](../../connect/php/connection-options.md) finden Sie eine Liste der unterstützten Schlüssel für das Array.  
  
## <a name="return-value"></a>Rückgabewert  
Eine PHP-Verbindungsressource. Wenn eine Verbindung nicht erfolgreich erstellt und geöffnet werden kann, wird **false** zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
Wenn im optionalen *$connectionInfo* -Parameter keine Werte für die Schlüssel *UID* und *PWD* angegeben sind, wird versucht, die Verbindung mithilfe der Windows-Authentifizierung herzustellen. Weitere Informationen zur Herstellung einer Verbindung mit dem Server finden Sie unter [How to: Connect Using Windows Authentication](../../connect/php/how-to-connect-using-windows-authentication.md) und [How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md).  
  
## <a name="example"></a>Beispiel  
Das folgende Beispiel erstellt und öffnet eine Verbindung mit Windows-Authentifizierung. Das Beispiel setzt voraus, dass SQL Server und die [AdventureWorks-Datenbank](https://www.codeplex.com/SqlServerSamples) auf dem lokalen Computer installiert sind. Wenn das Beispiel über die Befehlszeile ausgeführt wird, werden alle Ausgaben in die Konsole geschrieben.  
  
```  
<?php  
/*  
Connect to the local server using Windows Authentication and specify  
the AdventureWorks database as the database in use. To connect using  
SQL Server Authentication, set values for the "UID" and "PWD"  
 attributes in the $connectionInfo parameter. For example:  
$connectionInfo = array("UID" => $uid, "PWD" => $pwd, "Database"=>"AdventureWorks");  
*/  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if( $conn )  
{  
     echo "Connection established.\n";  
}  
else  
{  
     echo "Connection could not be established.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
//-----------------------------------------------  
// Perform operations with connection.  
//-----------------------------------------------  
  
/* Close the connection. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>Weitere Informationen  
[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)

[Connecting to the Server](../../connect/php/connecting-to-the-server.md)

[Informationen zu den Codebeispielen in der Dokumentation](../../connect/php/about-code-examples-in-the-documentation.md)  
  
