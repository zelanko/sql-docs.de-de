---
title: Azure Active Directory | Microsoft-Dokumentation
ms.date: 02/25/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- azure active directory, authentication, access token
author: david-puglielli
ms.author: v-dapugl
manager: v-mabarw
ms.openlocfilehash: 8712681a244e969d230b0b7099acd4aa56334f11
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "68265179"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Herstellen einer Verbindung mithilfe der Azure Active Directory-Authentifizierung
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) ist eine zentrale Technologie zur Verwaltung von Benutzer-IDs, die als Alternative zur [SQL Server-Authentifizierung](../../connect/php/how-to-connect-using-sql-server-authentication.md) fungiert. Azure AD ermöglicht Verbindungen mit Microsoft Azure SQL-Datenbank und SQL Data Warehouse mit Verbundidentitäten in Azure AD unter Verwendung eines Benutzernamens und Kennworts, der integrierten Windows-Authentifizierung oder einem Azure AD-Zugriffstoken. Die PHP-Treiber für SQL Server unterstützen diese Features teilweise.

Wenn Sie Azure AD nutzen möchten, verwenden Sie die Schlüsselwörter **Authentication** oder **AccessToken** (diese schließen sich gegenseitig aus), wie in der folgenden Tabelle gezeigt. Weitere technische Details finden Sie unter [Verwenden von Azure Active Directory mit dem ODBC Driver](../../connect/odbc/using-azure-active-directory.md).

|Schlüsselwort|Werte|Beschreibung|
|-|-|-|
|**AccessToken**|Nicht festgelegt (Standardeinstellung)|Der Authentifizierungsmodus wird durch andere Schlüsselwörter bestimmt. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md). |
||Eine Bytezeichenfolge|Das aus einer OAuth-JSON-Antwort extrahierte Azure AD-Zugriffstoken. Die Verbindungszeichenfolge darf weder eine Benutzer-ID noch ein Kennwort noch das Schlüsselwort „Authentication“ enthalten (erfordert die ODBC-Treiberversion 17 oder höher unter Linux oder macOS). |
|**Authentifizierung**|Nicht festgelegt (Standardeinstellung)|Der Authentifizierungsmodus wird durch andere Schlüsselwörter bestimmt. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|Direkte Authentifizierung bei einer SQL Server-Instanz (dies kann eine Azure-Instanz sein) unter Verwendung eines Benutzernamens und eines Kennworts. Benutzername und Kennwort müssen mit den Schlüsselwörtern **UID** und **PWD** an die Verbindungszeichenfolge übergeben werden. |
||`ActiveDirectoryPassword`|Authentifizierung mit einer Azure Active Directory-Identität unter Verwendung eines Benutzernamens und eines Kennworts. Benutzername und Kennwort müssen mit den Schlüsselwörtern **UID** und **PWD** an die Verbindungszeichenfolge übergeben werden. |
||`ActiveDirectoryMsi`|Authentifizierung über eine vom System oder vom Benutzer zugewiesene verwaltete Identität (erfordert die ODBC-Treiberversion 17.3.1.1 oder höher). Eine Übersicht und Tutorials finden Sie unter [Was sind verwaltete Identitäten für Azure-Ressourcen?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview).|

Das Schlüsselwort **Authentication** wirkt sich auf die Einstellungen der Verbindungssicherheit aus. Wenn dieses Schlüsselwort in der Verbindungszeichenfolge festgelegt ist, wird das Schlüsselwort **Encrypt** standardmäßig auf „true“ festgelegt. Das bedeutet, dass der Client eine Verschlüsselung anfordert. Darüber hinaus wird unabhängig von der Verschlüsselungseinstellung das Serverzertifikat überprüft, sofern nicht **TrustServerCertificate** auf „true“ festgelegt wird (die Standardeinstellung ist **false**). Dieses Feature unterscheidet sich von der alten, weniger sicheren Anmeldemethode, bei der das Serverzertifikat nur dann überprüft wird, wenn die Verschlüsselung in der Verbindungszeichenfolge explizit angefordert wird.

Wenn Sie Azure AD mit den PHP-Treibern für SQL Server unter Windows verwenden, werden Sie möglicherweise aufgefordert, den [Microsoft Online Services-Anmeldeassistenten](https://www.microsoft.com/download/details.aspx?id=41950) zu installieren (für ODBC-Version 17 und höher nicht erforderlich).

#### <a name="limitations"></a>Einschränkungen

Unter Windows unterstützt der zugrunde liegende ODBC-Treiber einen weiteren Wert für das Schlüsselwort **Authentication**: **ActiveDirectoryIntegrated**. Allerdings unterstützen die PHP-Treiber diesen Wert auf keiner Plattform.

## <a name="example---connect-using-sqlpassword-and-activedirectorypassword"></a>Beispiel: Herstellen einer Verbindung mithilfe von SqlPassword und ActiveDirectoryPassword

```php
<?php
// First connect to a local SQL Server instance by setting Authentication to SqlPassword
$serverName = "myserver.mydomain";

$connectionInfo = array("UID"=>$myusername, "PWD"=>$mypassword, "Authentication"=>'SqlPassword');

$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
    echo "Could not connect with Authentication=SqlPassword.\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Authentication=SqlPassword.\n";
    sqlsrv_close($conn);
}

// Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
$azureServer = "myazureserver.database.windows.net";
$azureDatabase = "myazuredatabase";
$azureUsername = "myuid";
$azurePassword = "mypassword";
$connectionInfo = array("Database"=>$azureDatabase,
                        "UID"=>$azureUsername,
                        "PWD"=>$azurePassword,
                        "Authentication"=>'ActiveDirectoryPassword');

$conn = sqlsrv_connect($azureServer, $connectionInfo);
if ($conn === false) {
    echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
    sqlsrv_close($conn);
}

?>
```

## <a name="example---connect-using-the-pdo_sqlsrv-driver"></a>Beispiel: Herstellen einer Verbindung mithilfe des PDO_SQLSRV-Treibers

```php
<?php
// First connect to a local SQL Server instance by setting Authentication to SqlPassword
$serverName = "myserver.mydomain";

$connectionInfo = "Database = $databaseName; Authentication = SqlPassword;";

try {
    $conn = new PDO("sqlsrv:server = $serverName ; $connectionInfo", $myusername, $mypassword);
    echo "Connected successfully with Authentication=SqlPassword.\n";
    $conn = null;
} catch (PDOException $e) {
    echo "Could not connect with Authentication=SqlPassword.\n";
    print_r($e->getMessage());
    echo "\n";
}

// Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
$azureServer = "myazureserver.database.windows.net";
$azureDatabase = "myazuredatabase";
$azureUsername = "myuid";
$azurePassword = "mypassword";
$connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryPassword;";

try {
    $conn = new PDO("sqlsrv:server = $azureServer ; $connectionInfo", $azureUsername, $azurePassword);
    echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
    unset($conn);
} catch (PDOException $e) {
    echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
    print_r($e->getMessage());
    echo "\n";
}
?>
```

## <a name="example---connect-using-azure-ad-access-token"></a>Beispiel: Herstellen einer Verbindung mithilfe eines Azure AD-Zugriffstokens

### <a name="sqlsrv-driver"></a>SQLSRV-Treiber

```php
<?php
// Using an access token to connect: do not use UID or PWD connection options
// Assume $accToken is the valid byte string extracted from an OAuth JSON response
$connectionInfo = array("Database"=>$azureAdDatabase, "AccessToken"=>$accToken);
$conn = sqlsrv_connect($azureAdServer, $connectionInfo);
if ($conn === false) {
    echo "Could not connect with Azure AD Access Token.\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Azure AD Access Token.\n";
    sqlsrv_close($conn);
}
?>
```

### <a name="pdo_sqlsrv-driver"></a>PDO_SQLSRV-Treiber

```php
<?php
try {
    // Using an access token to connect: do not pass in $uid or $pwd
    // Assume $accToken is the valid byte string extracted from an OAuth JSON response
    $connectionInfo = "Database = $azureAdDatabase; AccessToken = $accToken;";
    $conn = new PDO("sqlsrv:server = $azureAdServer; $connectionInfo");
    echo "Connected successfully with Azure AD Access Token\n";
    unset($conn);
} catch (PDOException $e) {
    echo "Could not connect with Azure AD Access Token.\n";
    print_r($e->getMessage());
    echo "\n";
}
?>
```

## <a name="example---connect-using-managed-identities-for-azure-resources"></a>Beispiel: Herstellen einer Verbindung mithilfe von verwalteten Identitäten für Azure-Ressourcen

### <a name="using-the-system-assigned-managed-identity-with-sqlsrv-driver"></a>Verwenden der vom System zugewiesenen verwalteten Identität mit dem SQLSRV-Treiber

Wenn Sie mithilfe der vom System zugewiesenen verwalteten Identität eine Verbindung herstellen, verwenden Sie nicht die Optionen UID und PWD.

```php
<?php

$azureServer = 'myazureserver.database.windows.net';
$azureDatabase = 'myazuredatabase';
$connectionInfo = array('Database'=>$azureDatabase,
                        'Authentication'=>'ActiveDirectoryMsi');
$conn = sqlsrv_connect($azureServer, $connectionInfo);

if ($conn === false) {
    echo "Could not connect with Authentication=ActiveDirectoryMsi (system-assigned).\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Authentication=ActiveDirectoryMsi (system-assigned).\n";
    
    $tsql = "SELECT @@Version AS SQL_VERSION";
    $stmt = sqlsrv_query($conn, $tsql);
    if ($stmt === false) {
        echo "Failed to run the simple query (system-assigned).\n";
        print_r(sqlsrv_errors());
    } else {
        while ($row = sqlsrv_fetch_array($stmt, SQLSRV_FETCH_ASSOC)) {
            echo $row['SQL_VERSION'] . PHP_EOL;
        }

        sqlsrv_free_stmt($stmt);
    }
    
    sqlsrv_close($conn);
}
?>
```

### <a name="using-the-user-assigned-managed-identity-with-pdo_sqlsrv-driver"></a>Verwenden der vom Benutzer zugewiesenen verwalteten Identität mit dem PDO_SQLSRV-Treiber

Eine vom Benutzer zugewiesene verwaltete Identität wird als eigenständige Azure-Ressource erstellt. Azure erstellt eine Identität in dem Azure AD-Mandanten, der vom verwendeten Abonnement als vertrauenswürdig eingestuft wird. Nachdem die Identität erstellt wurde, kann sie einer oder mehreren Azure-Dienstinstanzen zugewiesen werden. Kopieren Sie die `Object ID` dieser Identität, und legen Sie sie als Benutzernamen in der Verbindungszeichenfolge fest. 

Geben Sie beim Herstellen einer Verbindung mithilfe der vom Benutzer zugewiesenen verwalteten Identität die Objekt-ID als Benutzernamen an, lassen Sie aber das Kennwort weg.

```php
<?php

$azureServer = 'myazureserver.database.windows.net';
$azureDatabase = 'myazuredatabase';
$azureUser = '2d68f56e-9547-4dae-aee8-f3g28ab9674x';    // Object ID of the identity
$connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryMsi;";

try {
    $conn = new PDO("sqlsrv:server = $azureServer; $connectionInfo", $azureUser);
    echo "Connected successfully with Authentication=ActiveDirectoryMsi (user-assigned).\n";
    
    $tsql = "SELECT @@Version AS SQL_VERSION";
    
    try {
        $stmt = $conn->query($tsql);
        $result = $stmt->fetchall(PDO::FETCH_ASSOC);
        print_r($result);

        unset($stmt);
    } catch (PDOException $e) {
        echo "Failed to run the simple query (user-assigned).\n";
    }
    unset($conn);
} catch (PDOException $e) {
    echo "Could not connect with Authentication=ActiveDirectoryMsi (user-assigned).\n";
    print_r($e->getMessage());
    echo "\n";
}
?>
```

## <a name="see-also"></a>Weitere Informationen
[Verwenden von Azure Active Directory mit dem ODBC-Treiber](https://docs.microsoft.com/sql/connect/odbc/using-azure-active-directory)

[Was sind verwaltete Identitäten für Azure-Ressourcen?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview)
