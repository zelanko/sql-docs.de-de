---
title: Abrufen von Paketinformationen für Python
description: Erfahren Sie, wie Sie Informationen zu installierten Python-Paketen, einschließlich Versionen und Installations Speicherorte, auf SQL Server Machine Learning Services erhalten.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/22/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1aa12da4a138ea8f292fa8b64db00456d3c35fe3
ms.sourcegitcommit: 01c8df19cdf0670c02c645ac7d8cc9720c5db084
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2019
ms.locfileid: "70000446"
---
# <a name="get-python-package-information"></a>Abrufen von Paketinformationen für Python

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel wird beschrieben, wie Sie Informationen zu installierten Python-Paketen, einschließlich Versionen und Installations Speicherorten, auf SQL Server Machine Learning Services erhalten. Python-Beispiel Skripts veranschaulichen, wie Sie Paketinformationen wie den Installationspfad und die Version auflisten.

## <a name="default-python-library-location"></a>Standard Speicherort der Python-Bibliothek

Wenn Sie Machine Learning mit SQL Server installieren, wird eine einzelne paketbibliothek auf Instanzebene für jede von Ihnen installierte Sprache erstellt. Unter Windows ist die instanzbibliothek ein sicherer Ordner, der bei SQL Server registriert ist.

Alle Skripts oder Code, die in-Database auf SQL Server ausgeführt werden, müssen Funktionen aus der instanzbibliothek laden. SQL Server kann nicht auf Pakete zugreifen, die in anderen Bibliotheken installiert sind. Dies gilt auch für Remote Clients: bei Python-Code, der im computekontext des Servers ausgeführt wird, können nur Pakete verwendet werden, die in der instanzbibliothek installiert sind.
Die standardinstanzbibliothek kann nur von einem Computer Administrator geändert werden, um Server Objekte zu schützen.

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Der Standardpfad der Binärdateien für python lautet:

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\PYTHON_SERVICES`
::: moniker-end

::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
Der Standardpfad der Binärdateien für python lautet:

`C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\PYTHON_SERVICES`
::: moniker-end

Dabei wird die standardmäßige SQL-Instanz, MSSQLSERVER, vorausgesetzt. Wenn SQL Server als benutzerdefinierte benannte Instanz installiert wird, wird stattdessen der angegebene Name verwendet.

Führen Sie die folgende Anweisung aus, um die Standardbibliothek für die aktuelle Instanz zu überprüfen. In diesem Beispiel wird die Liste der in der Python `sys.path` -Variablen enthaltenen Ordner zurückgegeben. Die Liste enthält das aktuelle Verzeichnis und den Pfad der Standardbibliothek.

```sql
EXECUTE sp_execute_external_script
  @language =N'Python',
  @script=N'import sys; print("\n".join(sys.path))'
```

Weitere Informationen über die Variable `sys.path` und deren Verwendung zum Festlegen des Suchpfads für Module des interpreters finden Sie [Untermodul Suchpfad](https://docs.python.org/2/tutorial/modules.html#the-module-search-path).

## <a name="default-python-packages"></a>Standard-Python-Pakete

Die folgenden Python-Pakete werden mit SQL Server Machine Learning Services installiert, wenn Sie die python-Funktion während des Setups auswählen.

| Pakete | Version |  Beschreibung |
| ---------|---------|--------------|
| [revoscalepy](https://docs.microsoft.com/machine-learning-server/python-reference/revoscalepy/revoscalepy-package) | 9,2 | Wird für remotecomputekontexte, Streaming, parallele Ausführung von RX-Funktionen für Datenimport und-Transformation, Modellierung, Visualisierung und Analyse verwendet. |
| [microsoftml](https://docs.microsoft.com/machine-learning-server/python-reference/microsoftml/microsoftml-package) | 9,2 | Fügt Machine Learning-Algorithmen in python hinzu. |

### <a name="component-upgrades"></a>Komponenten Upgrades

Standardmäßig werden Python-Pakete durch Service Packs und kumulative Updates aktualisiert. Zusätzliche Pakete und vollständige Versions Upgrades von python-Kernkomponenten sind nur durch Produkt Upgrades oder durch Binden der Python-Unterstützung an Microsoft Machine Learning Server möglich.

Weitere Informationen finden Sie unter [Aktualisieren von R-und python-Komponenten in SQL Server](../install/upgrade-r-and-python.md).

## <a name="default-open-source-python-packages"></a>Standardmäßige Open-Source-Python-Pakete

Wenn Sie die Option "Python-Sprache" während des Setups auswählen, wird Anaconda 4,2 Distribution (über python 3,5) installiert. Zusätzlich zu den python-Codebibliotheken umfasst die Standardinstallation Beispiel Daten, Komponententests und Beispiel Skripts.

> [!IMPORTANT]
> Sie sollten die von installierte Python-Version niemals manuell überschreiben, indem Sie SQL Server-Setup mit neueren Versionen im Web installieren. Microsoft Python-Pakete basieren auf bestimmten Versionen von Anaconda. Wenn Sie Ihre Installation ändern, könnte dies destabilisiert werden.

## <a name="list-all-installed-python-packages"></a>Auflisten aller installierten Python-Pakete

Das folgende Beispielskript zeigt eine Liste installierter Pakete und ihrer Versionen an.

```sql
EXECUTE sp_execute_external_script 
  @language = N'Python', 
  @script = N'
import pkg_resources
import pandas as pd
installed_packages = pkg_resources.working_set
installed_packages_list = sorted(["%s==%s" % (i.key, i.version) for i in installed_packages])
df = pd.DataFrame(installed_packages_list)
OutputDataSet = df
  '
WITH RESULT SETS (( PackageVersion nvarchar (150) ))
```

## <a name="find-a-single-python-package"></a>Suchen eines einzelnen python-Pakets

Wenn Sie ein Python-Paket installiert haben und sicherstellen möchten, dass es für eine bestimmte SQL Server Instanz verfügbar ist, können Sie eine gespeicherte Prozedur ausführen, um das Paket zu laden und Nachrichten zurückzugeben.

Der folgende Code sucht z. b. nach `scikit-learn` dem Paket.
Wenn das Paket gefunden wird, gibt der Code die Meldung "Package scikit-Learn ist installiert" zurück.

```sql
EXECUTE sp_execute_external_script
  @language = N'Python',
  @script = N'
import pkg_resources
pckg_name = "scikit-learn"
pckgs = pandas.DataFrame([(i.key) for i in pkg_resources.working_set], columns = ["key"])
installed_pckg = pckgs.query(''key == @pckg_name'')
print("Package", pckg_name, "is", "not" if installed_pckg.empty else "", "installed")
  '
```

<a name="get-package-vers"></a>

Im folgenden Beispiel werden die Versionen des revoscalepy-Pakets und von python zurückgegeben.

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

+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [R-Paketinformationen erhalten](r-package-information.md)
+ [Neue R-Pakete installieren](../r/install-additional-r-packages-on-sql-server.md)
+ [Tutorials zu R und python](../tutorials/machine-learning-services-tutorials.md)
