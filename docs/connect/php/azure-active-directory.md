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
manager: mbarwin
ms.openlocfilehash: 30423cd7c15a920d99fad4c0ea08e074beaece0b
ms.sourcegitcommit: 8664c2452a650e1ce572651afeece2a4ab7ca4ca
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2019
ms.locfileid: "56828050"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Herstellen einer Verbindung mithilfe der Azure Active Directory-Authentifizierung
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) ist eine zentrale Benutzer-ID-Management-Technologie, die als Alternative zur funktioniert [SQL Server-Authentifizierung](../../connect/php/how-to-connect-using-sql-server-authentication.md). Azure AD ermöglicht Verbindungen mit Microsoft Azure SQL-Datenbank und SQL Data Warehouse mit verbundidentitäten in Azure AD mit einem Benutzernamen und Kennwort, integrierte Windows-Authentifizierung oder ein Azure AD-Zugriffstoken verwendet wird. Die PHP-Treiber für SQL Server bieten teilweise Unterstützung für diese Funktionen.

Um Azure AD verwenden möchten, verwenden die **Authentifizierung** oder **AccessToken** Schlüsselwörter (sie sind sich gegenseitig ausschließende), wie in der folgenden Tabelle dargestellt. Weitere technische Informationen finden Sie unter [mithilfe von Azure Active Directory mit dem ODBC-Treiber](../../connect/odbc/using-azure-active-directory.md).

|Schlüsselwort|Werte|Beschreibung|
|-|-|-|
|**AccessToken**|Nicht festgelegt (Standard)|Der Authentifizierungsmodus durch andere Schlüsselwörter bestimmt. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md). |
||Eine Byte-Zeichenfolge|Azure AD Access Token aus einem OAuth-JSON-Antwort extrahiert. Die Verbindungszeichenfolge darf keine Benutzer-ID, Kennwort oder das Schlüsselwort für die Authentifizierung (erfordert ODBC Driver, Version 17 oder höher unter Linux oder MacOS). |
|**Authentifizierung**|Nicht festgelegt (Standard)|Der Authentifizierungsmodus durch andere Schlüsselwörter bestimmt. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|Authentifizieren Sie sich direkt bei einer SQL Server-Instanz (die eine Azure-Instanz sein kann). mithilfe eines Benutzernamens und Kennworts. Benutzername und Kennwort müssen in die Verbindungszeichenfolge mithilfe übergeben werden die **UID** und **PWD** Schlüsselwörter. |
||`ActiveDirectoryPassword`|Authentifizieren Sie mit einer Azure Active Directory-Identität mit einem Benutzernamen und Kennwort ein. Benutzername und Kennwort müssen in die Verbindungszeichenfolge mithilfe übergeben werden die **UID** und **PWD** Schlüsselwörter. |
||`ActiveDirectoryMsi`|Authentifizieren mit einer vom System zugewiesene verwaltete Identität oder eine vom Benutzer zugewiesene verwaltete Identität (ODBC-Treiber Version 17.3.1.1 erfordert oder höher). Eine Übersicht über und Lernprogramme finden Sie unter [neuerungen von verwalteten Identitäten für Azure-Ressourcen?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview).|

Die **Authentifizierung** Schlüsselwort hat Einfluss auf die Einstellungen der verbindungssicherheit. Wenn sie in der Verbindungszeichenfolge aus, und klicken Sie dann in der Standardeinstellung festgelegt ist die **Encrypt** Schlüsselwort auf true festgelegt, was bedeutet, dass der Client fordert Verschlüsselung festgelegt ist. Das Serverzertifikat wird außerdem unabhängig von der die verschlüsselungseinstellung überprüft werden, es sei denn, **TrustServerCertificate** wird festgelegt auf "true" (**"false"** standardmäßig). Dieses Feature wird von der alten, weniger sichere Login-Methode, Unterschieden in der das Serverzertifikat überprüft wird, nur bei der Verschlüsselung in der Verbindungszeichenfolge explizit angefordert wird.

Bei der Verwendung von Azure AD mit den PHP-Treibern für SQL Server unter Windows möglicherweise Sie werden aufgefordert, installieren Sie die [Microsoft Online Services-Anmeldeassistent](https://www.microsoft.com/download/details.aspx?id=41950) (nicht für ODBC 17 + erforderlich).

#### <a name="limitations"></a>Einschränkungen

Auf Windows, die zugrunde liegenden ODBC-Treiber unterstützt einen Mehrwert für die **Authentifizierung** Schlüsselwort **ActiveDirectoryIntegrated**, aber die PHP-Treiber unterstützen diesen Wert auf jeder Plattform.

## <a name="example---connect-using-sqlpassword-and-activedirectorypassword"></a>Beispiel: Herstellen einer Verbindung mit "sqlpassword" und ActiveDirectoryPassword

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

## <a name="example---connect-using-the-pdosqlsrv-driver"></a>Beispiel: Herstellen einer Verbindung mit dem PDO_SQLSRV-Treiber

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

## <a name="example---connect-using-azure-ad-access-token"></a>Beispiel: Herstellen einer Verbindung mit Azure AD-Zugriffstoken

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

### <a name="pdosqlsrv-driver"></a>PDO_SQLSRV-Treiber

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

## <a name="example---connect-using-managed-identities-for-azure-resources"></a>Beispiel: Herstellen einer Verbindung mit verwalteten Identitäten für Azure-Ressourcen

### <a name="using-the-system-assigned-managed-identity-with-sqlsrv-driver"></a>Verwenden die vom System zugewiesene verwaltete Identität mit SQLSRV-Treiber

Verwenden Sie die Benutzer-ID "oder" PWD-Optionen nicht, beim Herstellen einer Verbindung mit den vom System zugewiesenen Identität verwalteten.

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

### <a name="using-the-user-assigned-managed-identity-with-pdosqlsrv-driver"></a>Verwenden die vom Benutzer zugewiesene verwaltete Identität mit PDO_SQLSRV-Treiber

Eine vom Benutzer zugewiesene verwaltete Identität wird als eigenständige Azure-Ressource erstellt. Azure erstellt eine Identität in Azure AD-Mandanten, der das verwendete Abonnement vertraut. Nachdem die Identität erstellt wurde, kann die Identität ein oder mehrere Azure-Dienstinstanzen zugewiesen werden. Kopieren der `Object ID` dieser Identität und die Gruppe als der Benutzer benennen Sie in der Verbindungszeichenfolge. 

Aus diesem Grund werden beim Herstellen einer Verbindung mit den vom Benutzer zugewiesenen Identität verwalteten Geben Sie die Objekt-ID als Benutzernamen ein, aber lassen Sie das Kennwort.

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

[Was ist die verwaltete Identitäten für Azure-Ressourcen?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview)
