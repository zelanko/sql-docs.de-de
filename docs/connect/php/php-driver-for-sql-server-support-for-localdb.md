---
title: Unterstützung für LocalDB | Microsoft-Dokumentation
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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "67935957"
---
# <a name="support-for-localdb"></a>Unterstützung für LocalDB

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

LocalDB ist eine vereinfachte Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], die seit [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] verfügbar ist. In diesem Thema wird erläutert, wie in einer LocalDB-Instanz eine Verbindung mit einer Datenbank hergestellt wird.

## <a name="remarks"></a>Bemerkungen

Weitere Informationen zu LocalDB, einschließlich Informationen zur Installation von LocalDB und zur Konfiguration der LocalDB-Instanz, finden Sie in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Onlinedokumentation im Thema zu [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Express LocalDB.

Kurz gesagt ermöglicht LocalDB Folgendes:

-   Verwenden Sie **sqllocaldb.exe i** , um den Namen der Standardinstanz zu ermitteln.

-   Verwenden Sie das Schlüsselwort der **AttachDBFilename** -Verbindungszeichenfolge, um anzugeben, welche Datenbankdatei der Server anfügen soll. Wenn Sie **AttachDBFilename**verwenden und den Namen der Datenbank nicht mit dem Schlüsselwort der **Database** -Verbindungszeichenfolge angeben, wird die Datenbank aus der LocalDB-Instanz entfernt, wenn die Anwendung geschlossen wird.

-   Geben Sie in der Verbindungszeichenfolge eine LocalDB-Instanz an: Im Folgenden finden Sie z. B. ein Beispiel für eine SQLSRV-Verbindungszeichenfolge:

    ```php
    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array( 'Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF','Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF'));
    ```

    Als Nächstes folgt ein Beispiel für eine PDO_SQLSRV-Verbindungszeichenfolge:  

    ```php
    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'Database=myData', NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF;Database=myData ',
        NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF', NULL, NULL);  
    ```

Falls notwendig können Sie eine LocalDB-Instanz mit "sqllocaldb.exe" erstellen. Sie können auch "sqlcmd.exe" verwenden, um Datenbanken in einer LocalDB-Instanz hinzuzufügen und zu ändern. Beispiel: `sqlcmd -S (localdb)\v11.0`. (Bei der Ausführung in IIS müssen Sie unter dem richtigen Konto ausführen, um die gleichen Ergebnisse wie bei der Ausführung in der Befehlszeile zu erhalten. Weitere Informationen finden Sie im Artikel zum [Verwenden von LocalDB mit vollständigem IIS, Teil 2: Instanzbesitz](https://blogs.msdn.com/b/sqlexpress/archive/2011/12/09/using-localdb-with-full-iis-part-2-instance-ownership.aspx)).

Im Folgenden finden Sie Beispiele für Verbindungszeichenfolgen, die den SQLSRV-Treiber verwenden und eine Verbindung mit einer Datenbank in einer benannten LocalDB-Instanz mit dem Namen „myInstance“ herstellen:

```php
$conn = sqlsrv_connect( '(localdb)\\myInstance',
    array( 'Database'=>'myData'));
```

Im Folgenden finden Sie Beispiele für Verbindungszeichenfolgen, die den PDO_SQLSRV-Treiber verwenden und eine Verbindung mit einer Datenbank in einer benannten LocalDB-Instanz mit dem Namen „myInstance“ herstellen:  
  
```php
$conn = new PDO( 'sqlsrv:server=(localdb)\\myInstance;'
    . 'database=myData', NULL, NULL);
```

Anweisungen zum Installieren von LocalDB finden Sie in der [LocalDB-Dokumentation](../../database-engine/configure-windows/sql-server-2016-express-localdb.md). Wenn Sie „sqlcmd.exe“ verwenden, um Daten in ihrer LocalDB-Instanz zu ändern, benötigen Sie das [sqlcmd-Hilfsprogramm](../../tools/sqlcmd-utility.md).

## <a name="see-also"></a>Weitere Informationen

[Verbinden mit dem Server](../../connect/php/connecting-to-the-server.md)
