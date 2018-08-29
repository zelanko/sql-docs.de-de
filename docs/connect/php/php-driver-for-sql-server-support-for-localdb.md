---
title: Unterstützung für LocalDB | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d315ad6a-0d50-4093-80c2-2f11217237c2
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f408cb1f6cb82610cfa74a4d59a3ce15e4307e64
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42784409"
---
# <a name="support-for-localdb"></a>Unterstützung für LocalDB

[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

LocalDB ist eine Basisversion der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die ist seit verfügbar [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. In diesem Thema wird erläutert, wie in einer LocalDB-Instanz eine Verbindung mit einer Datenbank hergestellt wird.

## <a name="remarks"></a>Remarks

Weitere Informationen zu LocalDB, wie Sie LocalDB installieren und Konfigurieren der LocalDB-Instanz finden Sie unter den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Thema der Onlinedokumentation auf [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Express LocalDB.

Kurz gesagt, erlaubt LocalDB Ihnen:

-   Verwenden Sie **sqllocaldb.exe i** , um den Namen der Standardinstanz zu ermitteln.

-   Verwenden Sie das Schlüsselwort der **AttachDBFilename** -Verbindungszeichenfolge, um anzugeben, welche Datenbankdatei der Server anfügen soll. Wenn Sie **AttachDBFilename**verwenden und den Namen der Datenbank nicht mit dem Schlüsselwort der **Database** -Verbindungszeichenfolge angeben, wird die Datenbank aus der LocalDB-Instanz entfernt, wenn die Anwendung geschlossen wird.

-   Geben Sie in der Verbindungszeichenfolge eine LocalDB-Instanz an: Hier ist z. B. eine Beispiel-SQLSRV-Verbindungszeichenfolge:

    ```php
    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array( 'Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF','Database'=>'myData'));

    $conn = sqlsrv_connect( '(localdb)\\v11.0',
        array('AttachDBFileName'=>'c:\\myData.MDF'));
    ```

    Als Nächstes wird eine Beispiel PDO_SQLSRV-Verbindungszeichenfolge:  

    ```php
    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'Database=myData', NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF;Database=myData ',
        NULL, NULL);

    $conn = new PDO( 'sqlsrv:server=(localdb)\\v11.0;'
        . 'AttachDBFileName=c:\\myData.MDF', NULL, NULL);  
    ```

Falls notwendig können Sie eine LocalDB-Instanz mit "sqllocaldb.exe" erstellen. Sie können auch "sqlcmd.exe" verwenden, um Datenbanken in einer LocalDB-Instanz hinzuzufügen und zu ändern. Beispiel: `sqlcmd -S (localdb)\v11.0`. (Wenn in IIS ausgeführt wird, müssen Sie für die Ausführung unter dem richtigen Konto auf die gleichen Ergebnisse, die beim Ausführen an der Befehlszeile; finden Sie unter [Verwenden von LocalDB mit vollständigem IIS, Teil 2: Instanz den Besitz](http://blogs.msdn.com/b/sqlexpress/archive/2011/12/09/using-localdb-with-full-iis-part-2-instance-ownership.aspx) für Weitere Informationen.)

Im folgenden sind Beispiele für Verbindungszeichenfolgen mit dem SQLSRV-Treiber, die Verbindung mit einer Datenbank in eine benannte Instanz, die Bezeichnung "MyInstance" LocalDB:

```php
$conn = sqlsrv_connect( '(localdb)\\myInstance',
    array( 'Database'=>'myData'));
```

Im folgenden sind Beispiele für Verbindungszeichenfolgen mit dem PDO_SQLSRV-Treiber, die Verbindung mit einer Datenbank in eine benannte Instanz, die Bezeichnung "MyInstance" LocalDB:  
  
```php
$conn = new PDO( 'sqlsrv:server=(localdb)\\myInstance;'
    . 'database=myData', NULL, NULL);
```

Anweisungen zum Installieren von LocalDB finden Sie die [LocalDB Dokumentation](../../database-engine/configure-windows/sql-server-2016-express-localdb.md). Wenn Sie sqlcmd.exe verwenden, um Daten in der LocalDB-Instanz ändern, müssen Sie die [Hilfsprogramms "Sqlcmd"](../../tools/sqlcmd-utility.md).

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Verbinden mit dem Server](../../connect/php/connecting-to-the-server.md)
