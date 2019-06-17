---
title: Erhalten Sie Informationen zu R und Python-Paket – SQL Server Machine Learning Services
description: R und Python-Paket-Version zu ermitteln, Überprüfen der Installation und Abrufen einer Liste der installierten Pakete auf SQL Server R Services oder Machine Learning-Dienste.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: c2cf95e2d86836cd22aaa9dc67942f9d83c97e8c
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141409"
---
#  <a name="get-r-and-python-package-information"></a>Abrufen von Informationen von R und Python-Paket
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In einigen Fällen müssen wenn Sie mit mehreren Umgebungen oder Installationen von R oder Python arbeiten, Sie sicherstellen, dass der Code, den Sie ausführen, die erwartete Umgebung für Python oder dem richtigen Arbeitsbereich für r verwendet wird Wenn man beispielsweise [aktualisiert, R oder Python](../install/upgrade-r-and-python.md), der Pfad zu der R-Bibliothek möglicherweise einen anderen Ordner als den Standardwert. Auch wenn Sie R-Client oder eine Instanz von dem eigenständigen Server installieren, müssen Sie mehrere R-Bibliotheken auf Ihrem Computer möglicherweise.

R und Python-Skript-Beispiele in diesem Artikel veranschaulichen um den Pfad und die Version von SQL Server verwendete Pakete zu erhalten.

## <a name="get-the-r-library-location"></a>Erhalten Sie den Speicherort der R-Bibliothek

Führen Sie für alle Versionen von SQL Server die folgende Anweisung aus, um die Standard-R-paketbibliothek für die aktuelle Instanz zu überprüfen:

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

Optional können Sie [RxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) in neueren Versionen von RevoScaleR in SQL Server 2017-Machine Learning Services oder [R Services aktualisiert R, um mindestens RevoScaleR 9.0.1](../install/upgrade-r-and-python.md). Diese gespeicherte Prozedur gibt den Pfad der Instanz-Bibliothek und die Version von RevoScaleR, die von SQL Server verwendet:

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
> Die [RxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) Funktion kann nur auf dem lokalen Computer ausgeführt werden. Die Funktion kann nicht für Remoteverbindungen Library-Pfade zurück.

**Ergebnisse**

```text
STDOUT message(s) from external script: 
[1] "C:/Program Files/Microsoft SQL Server/MSSQL14.MSSQLSERVER1000/R_SERVICES/library"
[1] '9.3.0'
```

## <a name="get-the-python-library-location"></a>Abrufen des Standorts der Python-Bibliothek

Für **Python** in SQL Server 2017, führen Sie die folgende Anweisung aus, um zu überprüfen, ob die Standardbibliothek für die aktuelle Instanz. In diesem Beispiel gibt die Liste der Ordner für die Python `sys.path` Variable. Die Liste enthält das aktuelle Verzeichnis und den Pfad für die standard-Bibliothek.

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

Weitere Informationen zur Variablen `sys.path` und wie es zum Festlegen des Interpreters Suchpfad für Module verwendet wird, finden Sie unter den [Python-Dokumentation](https://docs.python.org/2/tutorial/modules.html#the-module-search-path)

## <a name="list-all-packages"></a>Liste aller Pakete

Es gibt mehrere Möglichkeiten, die Sie eine vollständige Liste der derzeit installierten Pakete abrufen können. Ein Vorteil der Liste der Paketbefehle sp_execute_external_script ausgeführt wird, dass Sie garantiert in der Bibliothek der Instanz installierten Pakete abzurufen.

### <a name="r"></a>R

Im folgenden Beispiel wird die R-Funktion `installed.packages()` in einem [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozedur, um eine Matrix aus Paketen abzurufen, die in der Bibliothek R_SERVICES für die aktuelle Instanz installiert wurden. Dieses Skript paketfelder aus Name und Version in der DESCRIPTION-Datei zurückgibt, wird nur der Name zurückgegeben werden.

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

Weitere Informationen zu den optionalen und Standardfelder für das Beschreibungsfeld der R-Pakets, finden Sie unter [ https://cran.r-project.org ](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

### <a name="python"></a>Python

Die `pip` Modul wird standardmäßig installiert, und unterstützt viele Vorgänge zum Auflisten der installierten Pakete, zusätzlich zu den von der Standardversion von Python unterstützt. Sie können ausführen `pip` aus einem Python-Eingabeaufforderung, natürlich, aber Sie können auch einige Pip-Funktionen aufrufen aus `sp_execute_external_script`.

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

Bei der Ausführung `pip` über die Befehlszeile, es gibt viele weitere Funktionen: `pip list` ruft Sie alle Pakete, die installiert werden, während `pip freeze` Listet die Pakete installiert, indem Sie `pip`, und nicht-Pakete, die selbst pip auflisten hängt ab. Sie können auch `pip freeze` zum Generieren einer Abhängigkeitsdatei.

## <a name="find-a-single-package"></a>Suchen eines einzelnen Pakets

Wenn Sie ein Paket installiert haben und möchten sicherstellen, dass er für eine bestimmte SQL Server-Instanz verfügbar ist, können Sie durch Ausführen der folgenden Aufruf der gespeicherten Prozedur zum Laden Sie das Paket, und nur diejenigen Nachrichten zurück.

### <a name="r"></a>R

In diesem Beispiel sucht und lädt die RevoScaleR-Bibliothek, falls verfügbar.

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("RevoScaleR")'
GO
```

+ Wenn das Paket gefunden wird, wird eine Meldung zurückgegeben: "Die Befehle erfolgreich abgeschlossen."

+ Wenn das Paket gespeichert oder geladen werden kann nicht, erhalten Sie eine Fehlermeldung, die mit dem Text: "ist kein Paket namens"MissingPackageName""

### <a name="python"></a>Python

Das entsprechende Kontrollkästchen für Python kann ausgeführt werden, aus der Python-shell, mit `conda` oder `pip` Befehle. Alternativ führen Sie diese Anweisung in einer gespeicherten Prozedur:

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

## <a name="get-package-version"></a>Erste Version des Pakets

Sie können R und Python-Paket Versionsinformationen, die mithilfe von Management Studio.

### <a name="r-package-version"></a>Die Version der R-Pakets

Diese Anweisung gibt die RevoScaleR-Paket-Version und die Basis-R-Version zurück.

```sql
EXECUTE sp_execute_external_script
  @language = N'R',
  @script = N'
print(packageDescription("RevoScaleR"))
print(packageDescription("base"))
'
```

### <a name="python-package-version"></a>Die Version der Python-Pakets

Diese Anweisung gibt die Revoscalepy-Paketversion und den Python-Version zurück.

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