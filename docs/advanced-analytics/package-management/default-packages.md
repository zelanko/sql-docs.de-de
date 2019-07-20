---
title: Get R-und python-Paketinformationen
description: Bestimmen Sie die R-und python-Paketversion, überprüfen Sie die Installation, und erhalten Sie eine Liste der installierten Pakete auf SQL Server R Services oder Machine Learning Services.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: dec0fe7147eab6a4b6545decf99e1731d773957c
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68343420"
---
#  <a name="get-r-and-python-package-information"></a>Get R-und python-Paketinformationen
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Manchmal müssen Sie beim Arbeiten mit mehreren Umgebungen oder Installationen von r oder python überprüfen, ob der Code, den Sie ausführen, die erwartete Umgebung für python oder den richtigen Arbeitsbereich für R verwendet. Wenn Sie z. b. [R oder python aktualisiert](../install/upgrade-r-and-python.md)haben, kann sich der Pfad zur R-Bibliothek in einem anderen Ordner als der Standardordner befinden. Wenn Sie r Client oder eine Instanz des eigenständigen Servers installieren, verfügen Sie möglicherweise über mehrere r-Bibliotheken auf dem Computer.

In den Beispielen für R und python-Skripts in diesem Artikel wird gezeigt, wie Sie den Pfad und die Version der von SQL Server verwendeten Pakete erhalten.

## <a name="get-the-r-library-location"></a>Den Speicherort der R-Bibliothek erhalten

Führen Sie für jede Version von SQL Server die folgende Anweisung aus, um die Standard-R-paketbibliothek für die aktuelle Instanz zu überprüfen:

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Optional können Sie [rxsqllibpath](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) in neueren Versionen von revoscaler in SQL Server 2017 Machine Learning Services oder [r Services Upgrade r auf mindestens revoscaler 9.0.1](../install/upgrade-r-and-python.md)verwenden. Diese gespeicherte Prozedur gibt den Pfad der instanzbibliothek und die Version von revoscaler zurück, die von SQL Server verwendet wird:

```sql
EXECUTE sp_execute_external_script
  @language =N'R',
  @script=N'
  sql_r_path <- rxSqlLibPaths("local")
  print(sql_r_path)
  version_info <-packageVersion("RevoScaleR")
  print(version_info)'
```

> [!NOTE]
> Die [rxsqllibpath](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) -Funktion kann nur auf dem lokalen Computer ausgeführt werden. Die Funktion kann keine Bibliothekspfade für Remote Verbindungen zurückgeben.

**Ergebnisse**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.3.0'
```

## <a name="get-the-python-library-location"></a>Speicherort der Python-Bibliothek

Führen Sie für **python** in SQL Server 2017 die folgende Anweisung aus, um die Standardbibliothek für die aktuelle Instanz zu überprüfen. In diesem Beispiel wird die Liste der in der Python `sys.path` -Variablen enthaltenen Ordner zurückgegeben. Die Liste enthält das aktuelle Verzeichnis und den Pfad der Standardbibliothek.

```sql
EXECUTE sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

**Ergebnisse**

```text
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\python35.zip
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\DLLs
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Sphinx-1.5.4-py3.5.egg
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\win32\lib
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\Pythonwin
C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES\lib\site-packages\setuptools-27.2.0-py3.5.egg
```

Weitere Informationen über die Variable `sys.path` und deren Verwendung zum Festlegen des Suchpfads für Module des interpreters finden Sie in der Python- [Dokumentation](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) .

## <a name="list-all-packages"></a>Auflisten aller Pakete

Es gibt mehrere Möglichkeiten, eine komplette Liste der derzeit installierten Pakete zu erhalten. Ein Vorteil beim Ausführen von Paketlisten Befehlen aus sp_execute_external_script besteht darin, dass Sie sicher sind, dass Pakete in der instanzbibliothek installiert werden.

### <a name="r"></a>R

Im folgenden Beispiel wird die R- `installed.packages()` Funktion in [!INCLUDE[tsql](../../includes/tsql-md.md)] einer gespeicherten Prozedur verwendet, um eine Matrix von Paketen zu erhalten, die in der R_SERVICES-Bibliothek für die aktuelle Instanz installiert wurden. Mit diesem Skript werden die Felder "Paketname" und "Version" in der Beschreibungsdatei zurückgegeben.

```sql
EXECUTE sp_execute_external_script
  @language=N'R',
  @script = N'str(OutputDataSet);
  packagematrix <- installed.packages();
  Name <- packagematrix[,1];
  Version <- packagematrix[,3];
  OutputDataSet <- data.frame(Name, Version);',
  @input_data_1 = N''
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Weitere Informationen zu den optionalen Feldern und den Standard Feldern für das Feld "R Package Description [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file)" finden Sie unter.

### <a name="python"></a>Python

Das `pip` Modul wird standardmäßig installiert und unterstützt zahlreiche Vorgänge für die Auflistung installierter Pakete, zusätzlich zu den von python Standard unterstützten Paketen. Sie können natürlich `pip` über eine python-Eingabeaufforderung ausführen. Sie können jedoch auch einige PIP-Funktionen von `sp_execute_external_script`abrufen.

```sql
EXECUTE sp_execute_external_script 
  @language = N'Python', 
  @script = N'
  import pip
  import pandas as pd
  installed_packages = pip.get_installed_distributions()
  installed_packages_list = sorted(["%s==%s" % (i.key, i.version)
     for i in installed_packages])
  df = pd.DataFrame(installed_packages_list)
  OutputDataSet = df'
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

Wenn Sie `pip` von der Befehlszeile aus ausführen, gibt es viele weitere nützliche `pip list` Funktionen: Ruft alle installierten Pakete ab, `pip freeze` listet die von installierten Pakete `pip`auf und listet keine Pakete auf, die PIP selbst sind. hängt von ab. Sie können auch verwenden `pip freeze` , um eine Abhängigkeits Datei zu generieren.

## <a name="find-a-single-package"></a>Suchen eines einzelnen Pakets

Wenn Sie ein Paket installiert haben und sicherstellen möchten, dass es für eine bestimmte SQL Server Instanz verfügbar ist, können Sie den folgenden Befehl für die gespeicherte Prozedur ausführen, um das Paket zu laden und nur Meldungen zurückzugeben.

### <a name="r"></a>R

Dieses Beispiel sucht nach der revoscaler-Bibliothek und lädt diese, falls verfügbar.

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("RevoScaleR")'
GO
```

+ Wenn das Paket gefunden wird, wird eine Meldung zurückgegeben: "Die Befehle wurden erfolgreich abgeschlossen."

+ Wenn das Paket nicht gefunden oder geladen werden kann, wird eine Fehlermeldung mit dem folgenden Text angezeigt: "Es ist kein Paket mit dem Namen ' missingpackagename '" vorhanden.

### <a name="python"></a>Python

Die entsprechende Überprüfung für python kann mithilfe `conda` der Befehle oder `pip` über die Python-Shell durchgeführt werden. Alternativ können Sie diese Anweisung in einer gespeicherten Prozedur ausführen:

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
  import pip
  import pkg_resources
  pckg_name = "revoscalepy"
  pckgs = pandas.DataFrame([(i.key) for i in pip.get_installed_distributions()], columns = ["key"])
  installed_pckg = pckgs.query(''key == @pckg_name'')
  print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")'
```

<a name="get-package-vers"></a>

## <a name="get-package-version"></a>Paketversion erhalten

Informationen zur R-und python-Paketversion finden Sie unter Management Studio.

### <a name="r-package-version"></a>R-Paketversion

Diese Anweisung gibt die revoscaler-Paketversion und die Basis-R-Version zurück.

```sql
EXECUTE sp_execute_external_script
  @language = N'R',
  @script = N'
print(packageDescription("RevoScaleR"))
print(packageDescription("base"))
'
```

### <a name="python-package-version"></a>Python-Paketversion

Diese Anweisung gibt die revoscalepy-Paketversion und die Version von python zurück.

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
import revoscalepy
import sys
print(revoscalepy.__version__)
print(sys.version)
'
```

## <a name="next-steps"></a>Nächste Schritte

+ [Neue R-Pakete installieren](../r/install-additional-r-packages-on-sql-server.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [Tutorials, Beispiele, Lösungen](../tutorials/machine-learning-services-tutorials.md)