---
title: Azure Active Directory | Microsoft-Dokumentation
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.openlocfilehash: 67f32c2c48188b3bcff50e22ca66bf2f563b1704
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814828"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Herstellen einer Verbindung mithilfe der Azure Active Directory-Authentifizierung
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) ist eine zentrale Benutzer-ID-Management-Technologie, die als Alternative zur funktioniert [SQL Server-Authentifizierung](../../connect/php/how-to-connect-using-sql-server-authentication.md). Azure AD ermöglicht Verbindungen mit Microsoft Azure SQL-Datenbank und SQL Data Warehouse mit verbundidentitäten in Azure AD mit einem Benutzernamen und Kennwort, integrierte Windows-Authentifizierung oder ein Azure AD-Zugriffstoken wird; die PHP-Treiber für SQL Server bieten teilweise Unterstützung für diese Funktionen.

Um Azure AD verwenden möchten, verwenden die **Authentifizierung** Schlüsselwort. Die Werte, die **Authentifizierung** können auf in der folgenden Tabelle beschrieben sind.

|Schlüsselwort|Werte|und Beschreibung|
|-|-|-|
|**Authentifizierung**|Nicht festgelegt (Standard)|Der Authentifizierungsmodus durch andere Schlüsselwörter bestimmt. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|Authentifizieren Sie sich direkt bei einer SQL Server-Instanz (die eine Azure-Instanz sein kann). mithilfe eines Benutzernamens und Kennworts. Benutzername und Kennwort müssen in die Verbindungszeichenfolge mithilfe übergeben werden die **UID** und **PWD** Schlüsselwörter. |
||`ActiveDirectoryPassword`|Authentifizieren Sie mit einer Azure Active Directory-Identität mit einem Benutzernamen und Kennwort ein. Benutzername und Kennwort müssen in die Verbindungszeichenfolge mithilfe übergeben werden die **UID** und **PWD** Schlüsselwörter. |

Die **Authentifizierung** Schlüsselwort hat Einfluss auf die Einstellungen der verbindungssicherheit. Wenn sie in der Verbindungszeichenfolge aus, und klicken Sie dann in der Standardeinstellung festgelegt ist die **verschlüsseln** Schlüsselwort auf "true", damit der Client die Verschlüsselung anfordert, festgelegt ist. Das Serverzertifikat wird außerdem unabhängig von der die verschlüsselungseinstellung überprüft werden, es sei denn, **TrustServerCertificate** wird festgelegt auf "true". Dies wird unterschieden, aus der alten und weniger sichere, Login-Methode, in dem das Serverzertifikat nicht überprüft wird, wenn die Verschlüsselung in der Verbindungszeichenfolge explizit angefordert wird.

Bevor Sie mithilfe von Azure AD mit den PHP-Treibern für SQL Server unter Windows, stellen Sie sicher, dass Sie installiert haben die [Microsoft Online Services-Anmeldeassistent](https://www.microsoft.com/download/details.aspx?id=41950) (nicht für Linux und MacOS erforderlich).

#### <a name="limitations"></a>Einschränkungen

Auf Windows, die zugrunde liegenden ODBC-Treiber unterstützt einen Mehrwert für die **Authentifizierung** Schlüsselwort **ActiveDirectoryIntegrated**, aber die PHP-Treiber unterstützen diesen Wert auf jeder Plattform und somit auch Azure AD-Token-basierter Authentifizierung nicht unterstützt.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie eine Verbindung herstellen mit **"sqlpassword"** und **ActiveDirectoryPassword**.

```php
    <?php
    // First connect to a local SQL Server instance by setting Authentication to SqlPassword
    $serverName = "myserver.mydomain";

    $connectionInfo = array( "UID"=>$myusername, "PWD"=>$mypassword, "Authentication"=>'SqlPassword' );

    $conn = sqlsrv_connect( $serverName, $connectionInfo );
    if( $conn === false )
    {
        echo "Could not connect with Authentication=SqlPassword.\n";
        print_r( sqlsrv_errors() );
    }
    else
    {
        echo "Connected successfully with Authentication=SqlPassword.\n";
        sqlsrv_close( $conn );
    }

    // Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
    $azureServer = "myazureserver.database.windows.net";
    $azureDatabase = "myazuredatabase";
    $azureUsername = "myuid";
    $azurePassword = "mypassword";
    $connectionInfo = array( "Database"=>$azureDatabase, "UID"=>$azureUsername, "PWD"=>$azurePassword,
                             "Authentication"=>'ActiveDirectoryPassword' );

    $conn = sqlsrv_connect( $azureServer, $connectionInfo );
    if( $conn === false )
    {
        echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
        print_r( sqlsrv_errors() );
    }
    else
    {
        echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
        sqlsrv_close( $conn );
    }

    ?>
```

Im folgende Beispiel wird der gleiche wie oben mit dem PDO_SQLSRV-Treiber.

```php
    <?php
    // First connect to a local SQL Server instance by setting Authentication to SqlPassword
    $serverName = "myserver.mydomain";

    $connectionInfo = "Database = $databaseName; Authentication = SqlPassword;";

    try
    {
        $conn = new PDO( "sqlsrv:server = $serverName ; $connectionInfo", $myusername, $mypassword );
        echo "Connected successfully with Authentication=SqlPassword.\n";
        $conn = null;
    }
    catch( PDOException $e )
    {
        echo "Could not connect with Authentication=SqlPassword.\n";
        print_r( $e->getMessage() );
        echo "\n";
    }

    // Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
    $azureServer = "myazureserver.database.windows.net";
    $azureDatabase = "myazuredatabase";
    $azureUsername = "myuid";
    $azurePassword = "mypassword";
    $connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryPassword;";

    try
    {
        $conn = new PDO( "sqlsrv:server = $azureServer ; $connectionInfo", $azureUsername, $azurePassword );
        echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
        $conn = null;
    }
    catch( PDOException $e )
    {
        echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
        print_r( $e->getMessage() );
        echo "\n";
    }

    ?>
```
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Verwenden von Azure Active Directory mit dem ODBC-Treiber](https://docs.microsoft.com/sql/connect/odbc/using-azure-active-directory)
