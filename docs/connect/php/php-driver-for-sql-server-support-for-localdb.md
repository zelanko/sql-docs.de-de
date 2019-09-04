---
title: Unterstützung für localdb | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d315ad6a-0d50-4093-80c2-2f11217237c2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6da7f1aed956c8b2f5c71496c9c121f6006eabb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935957"
---
# <a name="support-for-localdb"></a>Unterstützung für LocalDB

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Localdb ist eine vereinfachte Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , die seit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]verfügbar ist. In diesem Thema wird erläutert, wie in einer LocalDB-Instanz eine Verbindung mit einer Datenbank hergestellt wird.

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zu localdb, einschließlich der Installation von localdb und der Konfiguration der localdb-Instanz, finden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Sie im Thema der [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Online Dokumentation zu Express localdb.

Kurz gesagt ermöglicht localdb Folgendes:

-   Verwenden Sie **sqllocaldb.exe i** , um den Namen der Standardinstanz zu ermitteln.

-   Verwenden Sie das Schlüsselwort der **AttachDBFilename** -Verbindungszeichenfolge, um anzugeben, welche Datenbankdatei der Server anfügen soll. Wenn Sie **AttachDBFilename**verwenden und den Namen der Datenbank nicht mit dem Schlüsselwort der **Database** -Verbindungszeichenfolge angeben, wird die Datenbank aus der LocalDB-Instanz entfernt, wenn die Anwendung geschlossen wird.

-   Geben Sie in der Verbindungszeichenfolge eine LocalDB-Instanz an: Im folgenden finden Sie ein Beispiel für eine sqlsrv-Verbindungs Zeichenfolge:

    ```php
    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array( 'Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF','Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF'));
    ```

    Als nächstes folgt eine PDO_SQLSRV-Beispiel Verbindungs Zeichenfolge:  

    ```php
    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'Database=myData', NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF;Database=myData ',
        NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF', NULL, NULL);  
    ```

Falls notwendig können Sie eine LocalDB-Instanz mit "sqllocaldb.exe" erstellen. Sie können auch "sqlcmd.exe" verwenden, um Datenbanken in einer LocalDB-Instanz hinzuzufügen und zu ändern. Beispiel: `sqlcmd -S (localdb)\v11.0`. (Bei der Ausführung in IIS müssen Sie unter dem richtigen Konto ausgeführt werden, um die gleichen Ergebnisse wie bei der Ausführung in der Befehlszeile zu erhalten. Weitere Informationen finden Sie unter [Verwenden von localdb mit vollständigem IIS, Teil 2: instanzbesitz](https://blogs.msdn.com/b/sqlexpress/archive/2011/12/09/using-localdb-with-full-iis-part-2-instance-ownership.aspx) .)

Im folgenden finden Sie Beispiel Verbindungs Zeichenfolgen, die den sqlsrv-Treiber verwenden, der eine Verbindung mit einer Datenbank in einer benannten localdb-Instanz namens MyInstance herstellt:

```php
$conn = sqlsrv_connect( '(localdb)\\myInstance',
    array( 'Database'=>'myData'));
```

Im folgenden finden Sie Beispiel Verbindungs Zeichenfolgen, die den PDO_SQLSRV-Treiber verwenden, der eine Verbindung mit einer Datenbank in einer benannten localdb-Instanz namens MyInstance herstellt  
  
```php
$conn = new PDO( 'sqlsrv:server=(localdb)\\myInstance;'
    . 'database=myData', NULL, NULL);
```

Anweisungen zum Installieren von localdb finden Sie in der [Dokumentation zu localdb](../../database-engine/configure-windows/sql-server-2016-express-localdb.md). Wenn Sie sqlcmd. exe verwenden, um Daten in der localdb-Instanz zu ändern, benötigen Sie das [Hilfsprogramm sqlcmd](../../tools/sqlcmd-utility.md).

## <a name="see-also"></a>Weitere Informationen

[Verbinden mit dem Server](../../connect/php/connecting-to-the-server.md)
