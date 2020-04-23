---
title: Laden von Microsoft-Treibern für PHP
description: Diese Seite enthält Anweisungen zum Laden der Microsoft-Treiber für PHP für SQL Server in den PHP-Prozessbereich.
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 73899b2ea917c3981b0c696b78de453eacbf894d
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2020
ms.locfileid: "81632772"
---
# <a name="loading-the-microsoft-drivers-for-php-for-sql-server"></a>Laden von Microsoft Drivers for PHP for SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

Dieser Artikel enthält Anweisungen für das Laden der Microsoft-Treiber für PHP für SQL [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]in den PHP-Prozessbereich.  
  
Sie können die vorab erstellten Treiber für Ihre Plattform von der GitHub-Projektseite [Microsoft Drivers for PHP for SQL Server](https://github.com/Microsoft/msphpsql/releases) herunterladen. Jedes Installationspaket enthält SQLSRV- und PDO_SQLSRV-Treiberdateien in Varianten mit und ohne Threads. Unter Windows sind auch 32-Bit- und 64-Bit-Varianten verfügbar. Eine Liste der Treiberdateien, die in den einzelnen Paketen enthalten sind, finden Sie unter [Systemanforderungen für Microsoft-Treiber für PHP für SQL Server](system-requirements-for-the-php-sql-driver.md). Die Treiberdatei muss mit der PHP-Version, der Architektur und dem Threading Ihrer PHP-Umgebung übereinstimmen.

Unter Linux und macOS können die Treiber auch mithilfe von PECL installiert werden, wie im [Tutorial zur Installation](installation-tutorial-linux-mac.md) erläutert.

Sie können die Treiber auch aus der Quelle erstellen, wenn Sie das PHP-Buildsystem oder `phpize` verwenden. Wenn Sie die Treiber aus der Quelle erstellen, haben Sie die Möglichkeit, die Treiber statisch in PHP anstatt als freigegebene Erweiterungen zu erstellen, indem Sie beim Erstellen mit PHP dem `./configure`-Befehl `--enable-sqlsrv=static --with-pdo_sqlsrv=static` (unter Linux und macOS) oder `--enable-sqlsrv=static --with-pdo-sqlsrv=static` (unter Windows) hinzufügen. Weitere Informationen zum PHP-Buildsystem und `phpize` finden Sie in der [PHP-Dokumentation](http://php.net/manual/install.php).
  
## <a name="moving-the-driver-file-into-your-extension-directory"></a>Verschieben Sie die Treiberdatei in Ihr Erweiterungsverzeichnis  
Die Treiberdatei muss sich in einem Verzeichnis befinden, in dem die PHP-Runtime sie finden kann. Es ist am einfachsten, die Treiberdatei im standardmäßigen PHP-Erweiterungsverzeichnis zu platzieren. Sie finden das Standardverzeichnis, indem Sie `php -i | sls extension_dir` unter Windows oder `php -i | grep extension_dir` unter Linux/macOS ausführen. Wenn Sie das standardmäßige Erweiterungsverzeichnis nicht verwenden, geben Sie in der PHP-Konfigurationsdatei (php.ini) mit der Option **extension_dir** ein Verzeichnis an. Wenn Sie die Treiberdatei beispielsweise unter Windows im Verzeichnis `c:\php\ext` abgelegt haben, fügen Sie der php.ini-Datei die folgende Zeile hinzu:
  
```  
extension_dir = "c:\PHP\ext"  
```

## <a name="loading-the-driver-at-php-startup"></a>Laden des Treibers beim Starten von PHP  
Beim Laden der SQLSRV-Treiber beim Starten von PHP verschieben Sie zunächst eine Treiberdatei in das Erweiterungsverzeichnis. Dann führen Sie folgende Schritte aus:  
  
1.  Zum Aktivieren des **SQLSRV**-Treibers ändern Sie **php.ini**, indem Sie im Erweiterungsabschnitt folgende Zeile hinzufügen und dabei den Dateinamen entsprechend ändern:  
  
    Unter Windows: 
    ```  
    extension=php_sqlsrv_72_ts.dll  
    ```  
    Unter Linux, wenn Sie die vorgefertigten Binärdateien für Ihre Distribution heruntergeladen haben: 
    ```  
    extension=php_sqlsrv_72_nts.so  
    ```
    Wenn Sie die SQLSRV-Binärdatei aus der Quelle oder mit PECL kompiliert haben, lautet der Dateiname „sqlsrv.so“:
    ```
    extension=sqlsrv.so
    ```
  
2.  Um den **PDO_SQLSRV**-Treiber zu aktivieren, muss die Erweiterung „PHP Data Objects (PDO) verfügbar sein, entweder als integrierte oder als dynamisch geladene Erweiterung.

    Unter Windows ist PDO in die vorgefertigten PHP-Binärdateien integriert, sodass die Datei „php.ini“ nicht geändert werden muss, um die Erweiterung zu laden. Wenn Sie jedoch PHP aus der Quelle kompiliert und eine separate zu erstellende PDO-Erweiterung angegeben haben, erhält diese den Namen `php_pdo.dll`, und Sie müssen sie in Ihr Erweiterungsverzeichnis kopieren und der Datei „php.ini“ die folgende Zeile hinzufügen:  
    ```
    extension=php_pdo.dll  
    ```
    Wenn Sie PHP unter Linux mit dem Paket-Manager Ihres Systems installiert haben, wird PDO wahrscheinlich als dynamisch geladene Erweiterung namens „pdo.so“ installiert. Die PDO-Erweiterung muss vor der PDO_SQLSRV-Erweiterung geladen werden, da sonst beim Laden ein Fehler auftritt. Erweiterungen werden in der Regel mit individuellen INI-Dateien geladen, und diese Dateien werden nach „php.ini“ gelesen. Wenn „pdo.so“ also über eine eigene INI-Datei geladen wird, ist eine separate Datei erforderlich, die danach den PDO_SQLSRV Treiber lädt. 

    Wenn Sie herausfinden möchten, in welchem Verzeichnis sich die erweiterungsspezifischen INI-Dateien befinden, führen Sie `php --ini` aus, und beachten Sie das unter `Scan for additional .ini files in:` aufgeführte Verzeichnis. Suchen Sie die Datei, die „pdo.so“ lädt. Ihr ist wahrscheinlich ein numerischer Wert vorangestellt, z. B. „10-pdo.ini“. Das numerische Präfix gibt die Ladereihenfolge der INI-Dateien an. Dateien, die kein numerisches Präfix aufweisen, werden alphabetisch geladen. Erstellen Sie eine Datei zum Laden der PDO_SQLSRV-Treiberdatei, die entweder den Namen „30-pdo_sqlsrv.ini“ (eine beliebige Zahl, die größer ist als diejenige, die „pdo.ini“ vorangestellt ist) oder den Namen „pdo_sqlsrv.ini“ (wenn „pdo.ini“ keine Zahl vorangestellt ist) trägt, und fügen Sie der Datei die folgende Zeile hinzu. Ändern Sie ggf. den Dateinamen entsprechend:  
    ```
    extension=php_pdo_sqlsrv_72_nts.so
    ```
    Ebenso wie bei SQLSRV gilt: Wenn Sie die PDO_SQLSRV-Binärdatei aus der Quelle oder mit PECL kompiliert haben, lautet der Dateiname „pdo_sqlsrv.so“:
    ```
    extension=pdo_sqlsrv.so
    ```
    Kopieren Sie diese Datei in das Verzeichnis, das die anderen INI-Dateien enthält. 

    Wenn Sie PHP mit integrierter PDO-Unterstützung aus der Quelle kompiliert haben, benötigen Sie keine separate INI-Datei, und Sie können die entsprechende Zeile oben zur Datei „php.ini“ hinzufügen.
  
3.  Starten Sie den Webserver neu.  
  
> [!NOTE]  
> Führen Sie ein Skript aus, das [phpinfo](https://php.net/manual/en/function.phpinfo.php) aufruft, um zu bestimmen, ob der Treiber erfolgreich geladen wurde.  
  
Weitere Informationen zu **php.ini**-Anweisungen finden Sie unter [Beschreibung der wichtigsten php.ini-Anweisungen](https://php.net/manual/en/ini.core.php).  
  
## <a name="see-also"></a>Weitere Informationen  
[Getting Started with the Microsoft Drivers for PHP for SQL Server (Erste Schritte mit dem Microsoft-Treiber für PHP für SQL Server)](getting-started-with-the-php-sql-driver.md)

[Systemanforderungen für Microsoft-Treiber für PHP für SQL Server](system-requirements-for-the-php-sql-driver.md)

[Programmierhandbuch für die Microsoft-Treiber für PHP für SQL Server](programming-guide-for-php-sql-driver.md)

[API-Referenz für den SQLSRV-Treiber](sqlsrv-driver-api-reference.md)

[API-Referenz für den PDO_SQLSRV-Treiber](pdo-sqlsrv-driver-reference.md)  
  
