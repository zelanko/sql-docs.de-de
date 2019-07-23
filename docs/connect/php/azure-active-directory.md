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
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265179"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Herstellen einer Verbindung mithilfe der Azure Active Directory-Authentifizierung
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) ist eine zentrale Benutzer-ID-Verwaltungs Technologie, die als Alternative zur [SQL Server Authentifizierung](../../connect/php/how-to-connect-using-sql-server-authentication.md)fungiert. Azure AD ermöglicht Verbindungen mit Microsoft Azure SQL-Datenbank und SQL Data Warehouse mit Verbund Identitäten in Azure AD mit einem Benutzernamen und einem Kennwort, integrierter Windows-Authentifizierung oder einem Azure AD Zugriffs Token. Die PHP-Treiber für SQL Server bieten partielle Unterstützung für diese Features.

Um Azure AD zu verwenden, verwenden Sie die Schlüsselwörter " **Authentication** " oder " **accesstoken** " (die sich gegenseitig ausschließen), wie in der folgenden Tabelle dargestellt. Weitere technische Informationen finden Sie unter [Verwenden von Azure Active Directory mit dem ODBC-Treiber](../../connect/odbc/using-azure-active-directory.md).

|Schlüsselwort|Werte|und Beschreibung|
|-|-|-|
|**AccessToken**|Nicht festgelegt (Standard)|Der Authentifizierungsmodus, der durch andere Schlüsselwörter bestimmt wird. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md). |
||Eine Byte Zeichenfolge|Das Azure AD Zugriffs Token, das aus einer OAuth-JSON-Antwort extrahiert wurde. Die Verbindungs Zeichenfolge darf nicht die Benutzer-ID, das Kennwort oder das Authentifizierungs Schlüsselwort enthalten (erfordert den ODBC-Treiber Version 17 oder höher unter Linux oder macOS). |
|**Authentifizierung**|Nicht festgelegt (Standard)|Der Authentifizierungsmodus, der durch andere Schlüsselwörter bestimmt wird. Weitere Informationen finden Sie unter [Connection Options](../../connect/php/connection-options.md). |
||`SqlPassword`|Direktes Authentifizieren bei einer SQL Server Instanz (bei der es sich um eine Azure-Instanz handeln kann) mithilfe eines Benutzernamens und Kennworts. Der Benutzername und das Kennwort müssen mithilfe der Schlüsselwörter **UID** und **pwd** in die Verbindungs Zeichenfolge übergeben werden. |
||`ActiveDirectoryPassword`|Authentifizieren Sie sich mit einer Azure Active Directory Identität mithilfe eines Benutzernamens und Kennworts. Der Benutzername und das Kennwort müssen mithilfe der Schlüsselwörter **UID** und **pwd** in die Verbindungs Zeichenfolge übergeben werden. |
||`ActiveDirectoryMsi`|Authentifizieren Sie sich entweder über eine vom System zugewiesene verwaltete Identität oder eine vom Benutzer zugewiesene verwaltete Identität (erfordert den ODBC-Treiber Version 17.3.1.1 oder höher). Eine Übersicht und Tutorials finden Sie unter [Was sind verwaltete Identitäten für Azure-Ressourcen?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview).|

Das **Authentifizierungs** Schlüsselwort wirkt sich auf die Verbindungs Sicherheitseinstellungen aus. Wenn Sie in der Verbindungs Zeichenfolge festgelegt ist, wird **das Schlüsselwort** Encryption standardmäßig auf true festgelegt. Dies bedeutet, dass der Client die Verschlüsselung anfordert. Außerdem wird das Serverzertifikat unabhängig von der Verschlüsselungs Einstellung überprüft, es sei denn, " **TrustServerCertificate** " ist auf "true" festgelegt (standardmäßig "**false** "). Diese Funktion unterscheidet sich von der alten, weniger sicheren Anmelde Methode, bei der das Serverzertifikat nur überprüft wird, wenn die Verschlüsselung in der Verbindungs Zeichenfolge ausdrücklich angefordert wird.

Wenn Sie Azure AD mit den PHP-Treibern für SQL Server unter Windows verwenden, werden Sie möglicherweise aufgefordert, den [Microsoft Online Services-Anmelde-Assistenten](https://www.microsoft.com/download/details.aspx?id=41950) zu installieren (nicht erforderlich für ODBC 17 und höher).

#### <a name="limitations"></a>Einschränkungen

Unter Windows unterstützt der zugrunde liegende ODBC-Treiber einen weiteren Wert für das **Authentifizierungs** Schlüsselwort **activedirectoryintegrated**, aber die PHP-Treiber unterstützen diesen Wert auf keiner Plattform.

## <a name="example---connect-using-sqlpassword-and-activedirectorypassword"></a>Beispiel: Herstellen einer Verbindung mithilfe von sqlpassword und activedirectoriypassword

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

## <a name="example---connect-using-the-pdosqlsrv-driver"></a>Beispiel: Herstellen einer Verbindung mithilfe des PDO_SQLSRV-Treibers

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

## <a name="example---connect-using-azure-ad-access-token"></a>Beispiel: Herstellen einer Verbindung mithilfe Azure AD Zugriffs Tokens

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

## <a name="example---connect-using-managed-identities-for-azure-resources"></a>Beispiel: Verbinden mit verwalteten Identitäten für Azure-Ressourcen

### <a name="using-the-system-assigned-managed-identity-with-sqlsrv-driver"></a>Verwenden der vom System zugewiesenen verwalteten Identität mit dem sqlsrv-Treiber

Verwenden Sie beim Herstellen einer Verbindung mithilfe der vom System zugewiesenen verwalteten Identität nicht die UID-oder PWD-Optionen.

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

### <a name="using-the-user-assigned-managed-identity-with-pdosqlsrv-driver"></a>Verwenden der vom Benutzer zugewiesenen verwalteten Identität mit dem PDO_SQLSRV-Treiber

Eine vom Benutzer zugewiesene verwaltete Identität wird als eigenständige Azure-Ressource erstellt. Azure erstellt eine Identität in dem Azure AD Mandanten, der vom verwendeten Abonnement als vertrauenswürdig eingestuft wird. Nachdem die Identität erstellt wurde, kann die Identität mindestens einer Azure-Dienst Instanz zugewiesen werden. Kopieren Sie `Object ID` die dieser Identität, und legen Sie Sie als Benutzernamen in der Verbindungs Zeichenfolge fest. 

Wenn Sie also eine Verbindung mit der vom Benutzer zugewiesenen verwalteten Identität herstellen, geben Sie die Objekt-ID als Benutzernamen an, und lassen Sie das Kennwort aus.

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
