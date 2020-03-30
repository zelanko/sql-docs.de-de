---
title: Abrufen von Paketinformationen für R
description: Erfahren Sie, wie Sie Informationen zum Installieren von R-Paketen in SQL Server Machine Learning Services und SQL Server R Services abrufen.
ms.custom: ''
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/15/2019
ms.topic: conceptual
author: garyericson
ms.author: garye
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 41e5f384878dfb284c31d6ba2886c9e223d03ca3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "74479425"
---
# <a name="get-r-package-information"></a>Abrufen von Paketinformationen für R

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

In diesem Artikel erfahren Sie, wie Sie Informationen zum Installieren von R-Paketen in SQL Server Machine Learning Services und SQL Server R Services abrufen. Dabei wird anhand von R-Beispielskripts veranschaulicht, wie Sie Paketinformationen, z. B. Installationspfad und Version, auflisten können.

## <a name="default-r-library-location"></a>Standardspeicherort der R-Bibliothek

Wenn Sie Machine Learning-Funktionen mit SQL Server installieren, wird eine einzelne Paketbibliothek auf Instanzebene für jede von Ihnen installierte Sprache erstellt. Unter Windows ist die Instanzbibliothek ein gesicherter Ordner, der bei SQL Server registriert ist.

Alle Skripts oder Codes, die datenbankintern in SQL Server ausgeführt werden, müssen Funktionen aus der Instanzbibliothek laden. SQL Server kann nicht auf Pakete zugreifen, die in anderen Bibliotheken installiert sind. Dies gilt auch für Remoteclients: Jedes R-Skript, das im Servercomputekontext ausgeführt wird, kann nur Pakete verwenden, die in der Instanzbibliothek installiert sind.
Zum Schutz der Serverressourcen kann die Standardinstanzbibliothek nur von einem Computeradministrator geändert werden.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Der Standardpfad der Binärdateien für R lautet:

`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Der Standardpfad der Binärdateien für R lautet:

`C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
Der Standardpfad der Binärdateien für R lautet:

`C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\R_SERVICES\library`
::: moniker-end

Dabei wird von der standardmäßigen SQL-Instanz, MSSQLSERVER, ausgegangen. Wenn SQL Server als benutzerdefinierte benannte Instanz installiert wird, wird stattdessen der angegebene Name verwendet.

<!-- I don't think this note is necessary. If you have these other products installed, you'd already know about them.
> [!NOTE]
> If you find other folders having similar subfolder names and files, you probably have a standalone installation of  Microsoft R Server or Machine Learning Server. These server products have different installers and paths: C:\Program Files\Microsoft\R Server\R_SERVER or C:\Program Files\Microsoft\ML SERVER\R_SERVER. For more information, see [Install R Server 9.1 for Windows](https://docs.microsoft.com/machine-learning-server/install/r-server-install-windows) or [Install Machine Learning Server for Windows](https://docs.microsoft.com/machine-learning-server/install/machine-learning-server-windows-install).
-->

Sie können die folgende Anweisung ausführen, um die Standardbibliothek des R-Pakets für die aktuelle Instanz zu überprüfen:

```sql
EXECUTE sp_execute_external_script  
  @language = N'R',
  @script = N'OutputDataSet <- data.frame(.libPaths());'
WITH RESULT SETS (([DefaultLibraryName] VARCHAR(MAX) NOT NULL));
GO
```

In der folgenden Anweisung wird [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths) verwendet, um den Pfad der Instanzbibliothek und die von SQL Server verwendete Version von RevoScaleR zurückzugeben:

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
> Die [rxSqlLibPaths](https://docs.microsoft.com/machine-learning-server/r-reference/revoscaler/rxsqllibpaths)-Funktion kann nur auf dem lokalen Computer ausgeführt werden. Die Funktion kann keine Bibliothekspfade für Remoteverbindungen zurückgeben.

## <a name="default-r-packages"></a>R-Standardpakete

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

Die folgenden R-Pakete werden mit SQL Server R Services installiert.

|Pakete | Version | BESCHREIBUNG |
|---------|---------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 8.0.3 | Wird für Remotecomputekontexte, Streaming, parallele Ausführung von RX-Funktionen für Datenimport und Transformation, Modellierung, Visualisierung und Analyse verwendet. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 1.0.0 | Wird zum Einschließen von R-Skripts in gespeicherte Prozeduren verwendet. |

::: moniker-end

::: moniker range=">=sql-server-2017||=sqlallproducts-allversions"

Wenn Sie bei der Installation die R-Funktion auswählen, werden die folgenden R-Pakete mit SQL Server Machine Learning Services installiert.

|Pakete | Version | BESCHREIBUNG |
|---------|---------|-------------|
| [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)  | 9.2 | Wird für Remotecomputekontexte, Streaming, parallele Ausführung von RX-Funktionen für Datenimport und Transformation, Modellierung, Visualisierung und Analyse verwendet. |
| [sqlrutils](https://docs.microsoft.com/machine-learning-server/r-reference/sqlrutils/sqlrutils) | 1.0.0 | Wird zum Einschließen von R-Skripts in gespeicherte Prozeduren verwendet. |
| [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)| 1.4.0 | Fügt Machine Learning-Algorithmen in R hinzu. | 
| [olapR](https://docs.microsoft.com/machine-learning-server/r-reference/olapr/olapr) | 1.0.0 | Wird zum Schreiben von MDX-Anweisungen in R verwendet. |

::: moniker-end

### <a name="component-upgrades"></a>Komponentenupgrades

R-Pakete werden standardmäßig durch Service Packs und kumulative Updates aktualisiert. Zusätzliche Pakete und vollständige Versionsupgrades von R-Kernkomponenten sind nur durch Produktupgrades oder durch Binden des R-Supports an Microsoft Machine Learning Server möglich.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Außerdem können Sie MicrosoftML- und olapR-Pakete über ein Komponentenupgrade zu einer SQL Server-Instanz hinzufügen.
::: moniker-end

Weitere Informationen finden Sie unter [Upgrade R and Python components in SQL Server (Upgrade von R- und Python-Komponenten in SQL Server)](../install/upgrade-r-and-python.md).

## <a name="default-open-source-r-packages"></a>Open-Source-Standardpakete für R

Die R-Unterstützung umfasst Open-Source-Funktionen, sodass Sie grundlegende R-Funktionen aufrufen und zusätzliche Open-Source- und Drittanbieterpakete installieren können. Die Unterstützung der Programmiersprache R schließt Kernfunktionen **base**, **stats**, **utils** und andere ein. Eine Basisinstallation von R umfasst auch zahlreiche Beispieldatasets und standardmäßige R-Tools wie **RGui** (ein einfacher interaktiver Editor) und **RTerm** (eine R-Eingabeaufforderung).

Als Open-Source-Distribution von R ist [Microsoft R Open (MRO)](https://mran.microsoft.com/open) in der Installation enthalten. MRO ergänzt die R-Basisinstallation, indem dadurch zusätzliche Open-Source-Pakete wie die [Intel Math Kernel Library](https://en.wikipedia.org/wiki/Math_Kernel_Library) eingebunden werden.

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"
Beim SQL Server R Services-Setup wird zusammen mit MRO die R-Version 3.2.2 bereitgestellt.
::: moniker-end

::: moniker range="=sql-server-2017||=sqlallproducts-allversions"
Beim SQL Server Machine Learning Services-Setup wird zusammen mit MRO die R-Version 3.3.3 bereitgestellt.
::: moniker-end

> [!IMPORTANT]
> Überschreiben Sie die vom SQL Server-Setup installierte Version von R niemals manuell mit neueren, online verfügbaren Versionen. R-Pakete von Microsoft basieren auf bestimmten Versionen von R. Die Änderung Ihrer Installation könnte diese instabil machen.

## <a name="list-all-installed-r-packages"></a>Auflisten aller installierten R-Pakete

Im folgenden Beispiel wird die R-Funktion `installed.packages()` in einer gespeicherten Prozedur [!INCLUDE[tsql](../../includes/tsql-md.md)] verwendet, um eine Liste von R-Paketen anzuzeigen, die in der Bibliothek „R_SERVICES“ für die aktuelle SQL-Instanz installiert wurden. Dieses Skript gibt die Felder mit dem Paketnamen und der Version in der Datei „DESCRIPTION“ zurück.

```sql
EXECUTE sp_execute_external_script
  @language=N'R',
@script = N'str(OutputDataSet);
packagematrix <- installed.packages();
Name <- packagematrix[,1];
Version <- packagematrix[,3];
OutputDataSet <- data.frame(Name, Version);',
@input_data_1 = N'
  '
WITH RESULT SETS ((PackageName nvarchar(250), PackageVersion nvarchar(max) ))
```

Weitere Informationen zu den optionalen und Standardfeldern für das R-Paket im Feld „DESCRIPTION“ finden Sie unter [https://cran.r-project.org](https://cran.r-project.org/doc/manuals/R-exts.html#The-DESCRIPTION-file).

## <a name="find-a-single-r-package"></a>Suchen eines einzelnen R-Pakets

Wenn Sie ein R-Paket installiert haben und sicherstellen möchten, dass es für eine bestimmte SQL Server-Instanz verfügbar ist, können Sie eine gespeicherte Prozedur ausführen, um das Paket zu laden und Meldungen zurückzugeben.

Mit der folgenden Anweisung wird zum Beispiel das Paket [glue](https://cran.r-project.org/web/packages/glue/) gesucht und, falls verfügbar, geladen.
Wenn das Paket nicht gefunden oder geladen werden kann, erhalten Sie eine Fehlermeldung mit dem Text „Es ist kein Paket mit dem Namen ‚gule‘ vorhanden.“

```sql
EXECUTE sp_execute_external_script  
  @language =N'R',
  @script=N'require("glue")'
GO
```

Weitere Informationen über das Paket finden Sie in der `packageDescription`.
Die folgende Anweisung gibt Informationen zum Paket **glue** zurück.

```sql
EXECUTE sp_execute_external_script
  @language = N'R',
  @script = N'
print(packageDescription("glue"))
  '
```

## <a name="next-steps"></a>Nächste Schritte

::: moniker range="<=sql-server-2017||=sqlallproducts-allversions"
+ [Installieren von Paketen mit R-Tools](install-r-packages-standard-tools.md)
::: moniker-end
::: moniker range=">sql-server-2017||=sqlallproducts-allversions"
+ [Installieren von neuen R-Paketen mit sqlmlutils](install-additional-r-packages-on-sql-server.md)
::: moniker-end
+ [Abrufen von Paketinformationen für Python](python-package-information.md)
+ [Neue Python-Pakete installieren](../python/install-additional-python-packages-on-sql-server.md)
+ [R- und Python-Tutorials](../tutorials/machine-learning-services-tutorials.md)
