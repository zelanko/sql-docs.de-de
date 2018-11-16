---
title: Laden der Microsoft-Treiber für PHP für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- loading the driver
ms.assetid: e5c114c5-8204-49c2-94eb-62ca63f5d3ec
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3dd99ffa39de48dbf8839cbe06a8bb236fffbdf3
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51606200"
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>Laden von Microsoft Drivers for PHP for SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Dieser Artikel enthält Anweisungen für das Laden der Microsoft-Treiber für PHP für SQL [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]in den PHP-Prozessbereich.  
  
Sie können die vordefinierten Treiber für Ihre Plattform aus der [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) Projektseite auf Github. Jedem Installationspaket enthält die SQLSRV- und PDO_SQLSRV-Treiber-Dateien in Threads und nicht-Thread-Varianten. Auf Windows sind sie auch in der 32-Bit und 64-Bit-Variante verfügbar. Finden Sie unter [Systemanforderungen für Microsoft Drivers for PHP for SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md) eine Liste der Treiberdateien abzurufen, die in den einzelnen Paketen enthalten sind. Die Treiberdatei muss es sich um die PHP-Version, Architektur und Threadedness Ihrer PHP-Umgebung übereinstimmen.

Unter Linux und MacOS, die Treiber können auch mit installiert werden PECL, wie in der [Tutorial zur](../../connect/php/installation-tutorial-linux-mac.md).
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Verschieben Sie die Treiberdatei in Ihr Erweiterungsverzeichnis  
Die Treiberdatei muss in einem Verzeichnis befinden, in dem Sie die PHP-Laufzeit gefunden werden kann. Es ist am einfachsten, legen Sie die Treiberdatei in Ihrem PHP-Erweiterung Standardverzeichnis – um das Standardverzeichnis zu finden, führen Sie `php -i | sls extension_dir` auf Windows oder `php -i | grep extension_dir` unter Linux/MacOS. Wenn Sie das Standardverzeichnis für die Erweiterung nicht verwenden, geben Sie ein Verzeichnis, in der PHP-Konfigurationsdatei (php.ini) an, mit der **"extension_dir"** Option. Beispielsweise auf Windows, wenn Sie die Treiberdatei, in abgelegt haben Ihre `c:\php\ext` Verzeichnis, fügen Sie die folgende Zeile in "PHP.ini":
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>Laden des Treibers beim Starten von PHP  
Beim Laden der SQLSRV-Treiber beim Starten von PHP verschieben Sie zunächst eine Treiberdatei in das Erweiterungsverzeichnis. Dann führen Sie folgende Schritte aus:  
  
1.  So aktivieren Sie die **SQLSRV** -Treibers ändern **"PHP.ini"** durch die folgende Zeile dem Abschnitt "Erweiterung" hinzufügen, ändern Sie den Dateinamen entsprechend:  
  
    Unter Windows: 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    Unter Linux, wenn Sie die vorab erstellte Binärdateien für Ihre Distribution heruntergeladen haben: 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    Wenn Sie die binäre SQLSRV aus der Quelle oder PECL kompiliert haben, wird es stattdessen sqlsrv.so benannt werden:
    ```
    extension=sqlsrv.so
    ```
  
2.  So aktivieren Sie die **PDO_SQLSRV** -Treiber verwenden, die Erweiterung für PHP Data Objects (PDO) muss verfügbar sein, entweder als integrierte Erweiterung oder als dynamisch geladene Erweiterung.

    Auf Windows sind im Lieferumfang der vorab erstellte PHP-Binärdateien PDO integriert, daher keine Notwendigkeit zum Ändern der Datei "PHP.ini" besteht, um diese zu laden. Wenn Sie jedoch Sie PHP von der Quelle kompiliert und eine separate PDO-Erweiterung zu erstellenden angegeben, Namen `php_pdo.dll`, und Sie müssen in Ihr Erweiterungsverzeichnis kopieren und fügen Sie die folgende Zeile in "PHP.ini":  
    ```
    extension=php_pdo.dll  
    ```
    Wenn Sie PHP mithilfe Ihres Systems Paket-Managers installiert haben, wird unter Linux wahrscheinlich PDO als dynamisch geladene Erweiterung mit dem Namen pdo.so installiert. Der PDO-Erweiterung geladen werden muss, bevor Sie die PDO_SQLSRV-Erweiterung, oder Laden fehl. Erweiterungen in der Regel mithilfe von einzelnen INI-Dateien geladen werden und diese Dateien werden nach der Datei "PHP.ini" gelesen. Wenn pdo.so über eine eigene INI-Datei geladen wird, ist daher eine separate Datei laden den PDO_SQLSRV-Treiber nach PDO erforderlich. 

    Um herauszufinden, welches Verzeichnis die erweiterungsspezifischen INI-Dateien gespeichert sind, führen Sie `php --ini` und notieren Sie sich unter angegebenen Verzeichnis `Scan for additional .ini files in:`. Suchen Sie die Datei, die pdo.so lädt, denn es wahrscheinlich eine Zahl ist, z. B. 10-pdo.ini vorangestellt ist. Das numerische Präfix gibt die Ladereihenfolge von der INI-Dateien an, während Dateien, die keine numerischen Präfix alphabetisch geladen werden. Erstellen Sie eine Datei laden Sie die PDO_SQLSRV-Treiber-Datei, die aufgerufen wird, entweder 30-pdo_sqlsrv.ini (beliebige Anzahl größer als die pdo.ini funktioniert das Präfix) oder pdo_sqlsrv.ini (sofern keine Reihe pdo.ini vorangestellt ist), und fügen die folgende Zeile hinzu, ändern den Dateinamen als geeignet:  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    Als wird SQLSRV, wenn Sie den PDO_SQLSRV binäre aus der Quelle oder PECL, kompiliert haben es stattdessen pdo_sqlsrv.so genannt werden:
    ```
    extension=pdo_sqlsrv.so
    ```
    Kopieren Sie diese Datei in das Verzeichnis, das die INI-Dateien enthält. 

    Wenn Sie PHP von der Quelle durch integrierte Unterstützung für PDO kompiliert haben, benötigen Sie keine separate INI-Datei, und Sie können über die entsprechende Zeile in "PHP.ini" hinzufügen.
  
3.  Starten Sie den Webserver neu.  
  
> [!NOTE]  
> Führen Sie ein Skript aus, das [phpinfo](https://php.net/manual/en/function.phpinfo.php) aufruft, um zu bestimmen, ob der Treiber erfolgreich geladen wurde.  
  
Weitere Informationen zu **php.ini**-Anweisungen finden Sie unter [Beschreibung der wichtigsten php.ini-Anweisungen](https://php.net/manual/en/ini.core.php).  
  
## <a name="see-also"></a>Weitere Informationen finden Sie unter  
[Erste Schritte mit der Microsoft-Treiber für PHP für SQLServer](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Systemanforderungen für Microsoft-Treiber für PHP für SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)

[Programmierhandbuch für den Microsoft-Treiber für PHP für SQLServer](../../connect/php/programming-guide-for-php-sql-driver.md)

[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)

[API-Referenz für den PDO_SQLSRV-Treiber](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
