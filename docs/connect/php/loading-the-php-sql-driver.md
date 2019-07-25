---
title: Laden der Microsoft-Treiber für PHP für SQL Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/11/2019
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
ms.openlocfilehash: e3c6614425cf8796bd7ec462a62f9410b9ca5857
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67936381"
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>Laden von Microsoft Drivers for PHP for SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Dieser Artikel enthält Anweisungen für das Laden der Microsoft-Treiber für PHP für SQL [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]in den PHP-Prozessbereich.  
  
Sie können die vordefinierten Treiber für Ihre Plattform von der Seite [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) GitHub Project herunterladen. Jedes Installationspaket enthält sqlsrv-und PDO_SQLSRV-Treiberdateien in Thread-und nicht-Thread-Varianten. Unter Windows sind Sie auch in 32-Bit-und 64-Bit-Varianten verfügbar. Eine Liste der in den einzelnen Paketen enthaltenen Treiberdateien finden Sie [unter System Anforderungen für die Microsoft-Treiber für SQL Server PHP](../../connect/php/system-requirements-for-the-php-sql-driver.md) . Die Treiberdatei muss mit der PHP-Version, der Architektur und der dreversitheit Ihrer PHP-Umgebung identisch sein.

Unter Linux und macOS können die Treiber alternativ mithilfe von PECL installiert werden, wie im Installations- [Tutorial](../../connect/php/installation-tutorial-linux-mac.md)zu finden.

Sie können die Treiber auch aus dem Quellcode erstellen, wenn Sie PHP oder mithilfe `phpize`von erstellen. Wenn Sie die Treiber aus der Quelle erstellen, haben Sie die Möglichkeit, Sie statisch in PHP zu erstellen, anstatt Sie als freigegebene Erweiterungen zu erstellen, `--enable-sqlsrv=static --with-pdo_sqlsrv=static` indem Sie (unter Linux und macOS `--enable-sqlsrv=static --with-pdo-sqlsrv=static` ) oder (unter Windows) `./configure` dem Befehl hinzufügen, wenn PHP wird aufgebaut. Weitere Informationen zum PHP-Buildsystem und `phpize`finden Sie in der [PHP-Dokumentation](http://php.net/manual/install.php).
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Verschieben Sie die Treiberdatei in Ihr Erweiterungsverzeichnis  
Die Treiberdatei muss sich in einem Verzeichnis befinden, in dem die PHP-Laufzeit Sie finden kann. Es ist am einfachsten, die Treiberdatei in Ihr PHP-Standard Erweiterungs Verzeichnis zu versetzen, um das Standardverzeichnis `php -i | sls extension_dir` zu finden, `php -i | grep extension_dir` das unter Windows oder unter Linux/macOS ausgeführt wird. Wenn Sie das standardmäßige Erweiterungs Verzeichnis nicht verwenden, geben Sie ein Verzeichnis in der PHP-Konfigurationsdatei (PHP. ini) mithilfe der **extension_dir** -Option an. Wenn Sie z. b. unter Windows die Treiberdatei in Ihrem `c:\php\ext` Verzeichnis abgelegt haben, fügen Sie die folgende Zeile zu "php. ini" hinzu:
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>Laden des Treibers beim Starten von PHP  
Beim Laden der SQLSRV-Treiber beim Starten von PHP verschieben Sie zunächst eine Treiberdatei in das Erweiterungsverzeichnis. Dann führen Sie folgende Schritte aus:  
  
1.  Um den **sqlsrv** -Treiber zu aktivieren, ändern Sie **php. ini** , indem Sie die folgende Zeile dem Erweiterungs Abschnitt hinzufügen und den Dateinamen entsprechend ändern:  
  
    Unter Windows: 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    Unter Linux: Wenn Sie die vorgefertigten Binärdateien für Ihre Distribution heruntergeladen haben: 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    Wenn Sie die sqlsrv-Binärdatei aus Quelle oder mit PECL kompiliert haben, wird Sie stattdessen mit dem Namen sqlsrv.so:
    ```
    extension=sqlsrv.so
    ```
  
2.  Um den **PDO_SQLSRV** -Treiber zu aktivieren, muss die PHP-Erweiterung (Data Objects, PDO) als integrierte Erweiterung oder als dynamisch geladene Erweiterung verfügbar sein.

    Unter Windows sind die vorgefertigten php-Binärdateien mit PDO integriert, sodass es nicht erforderlich ist, die Datei "php. ini" zu ändern, um Sie zu laden. Wenn Sie jedoch PHP von der Quelle kompiliert und eine separate PDO-Erweiterung für die Erstellung angegeben haben, wird Sie benannt `php_pdo.dll`, und Sie müssen Sie in das Erweiterungs Verzeichnis kopieren und der Datei "php. ini" die folgende Zeile hinzufügen:  
    ```
    extension=php_pdo.dll  
    ```
    Wenn Sie unter Linux PHP mit dem Paket-Manager Ihres Systems installiert haben, wird PDO wahrscheinlich als dynamisch geladene Erweiterung namens PDO.so installiert. Die PDO-Erweiterung muss vor der PDO_SQLSRV-Erweiterung geladen werden, oder das Laden schlägt fehl. Erweiterungen werden in der Regel mit einzelnen ini-Dateien geladen, und diese Dateien werden nach PHP. ini gelesen. Wenn PDO.so über die eigene INI-Datei geladen wird, wird daher eine separate Datei geladen, die den PDO_SQLSRV-Treiber nach der Verwendung von PDO lädt. 

    Um herauszufinden, welches Verzeichnis die Erweiterungs spezifischen ini-Dateien finden, führen `php --ini` Sie aus, und notieren Sie sich das Verzeichnis, das unter `Scan for additional .ini files in:`aufgeführt ist. Suchen Sie die Datei, die PDO.so lädt. wahrscheinlich wird ihr ein Wert vorangestellt, z. b. "10-PDO. ini". Das numerische Präfix gibt die Lade Reihenfolge der INI-Dateien an, während Dateien, die nicht über ein numerisches Präfix verfügen, alphabetisch geladen werden. Erstellen Sie eine Datei zum Laden der PDO_SQLSRV-Treiberdatei namens "30-pdo_sqlsrv. ini" (eine beliebige Zahl, die größer ist als die, die "PDO. ini" verwendet) oder "PDO_SQLSRV. ini" (wenn "PDO. ini" keine Zahl vorangestellt ist), und fügen Sie der Datei die folgende Zeile hinzu, und ändern Sie den Dateinamen als. gegebenenfalls  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    Wie bei sqlsrv heißt dies, wenn Sie die PDO_SQLSRV-Binärdatei von der Quelle oder mit der PECL kompiliert haben, stattdessen heißt Sie PDO_SQLSRV.
    ```
    extension=pdo_sqlsrv.so
    ```
    Kopieren Sie diese Datei in das Verzeichnis, das die anderen ini-Dateien enthält. 

    Wenn Sie PHP von der Quelle mit integrierter PDO-Unterstützung kompiliert haben, benötigen Sie keine separate ini-Datei, und Sie können die entsprechende Zeile oben der Datei "php. ini" hinzufügen.
  
3.  Starten Sie den Webserver neu.  
  
> [!NOTE]  
> Führen Sie ein Skript aus, das [phpinfo](https://php.net/manual/en/function.phpinfo.php) aufruft, um zu bestimmen, ob der Treiber erfolgreich geladen wurde.  
  
Weitere Informationen zu **php.ini**-Anweisungen finden Sie unter [Beschreibung der wichtigsten php.ini-Anweisungen](https://php.net/manual/en/ini.core.php).  
  
## <a name="see-also"></a>Weitere Informationen  
[Getting Started with the Microsoft Drivers for PHP for SQL Server (Erste Schritte mit dem Microsoft-Treiber für PHP für SQL Server)](../../connect/php/getting-started-with-the-php-sql-driver.md)

[Systemanforderungen für Microsoft-Treiber für PHP für SQL Server](../../connect/php/system-requirements-for-the-php-sql-driver.md)

[Programmierhandbuch für die Microsoft-Treiber für PHP für SQL Server](../../connect/php/programming-guide-for-php-sql-driver.md)

[API-Referenz für den SQLSRV-Treiber](../../connect/php/sqlsrv-driver-api-reference.md)

[API-Referenz für den PDO_SQLSRV-Treiber](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
