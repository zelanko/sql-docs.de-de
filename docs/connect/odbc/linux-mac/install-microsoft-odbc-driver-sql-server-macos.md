---
title: Installation von Microsoft ODBC Driver for SQL Server (macOS)
ms.date: 03/05/2020
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver, installing
author: rothja
ms.author: v-jizho2
manager: jroth
ms.openlocfilehash: 7ad2b810092fae850a667a1611880f4b03b6a9a8
ms.sourcegitcommit: 577e7467821895f530ec2f97a33a965fca808579
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078953"
---
# <a name="install-the-microsoft-odbc-driver-for-sql-server-macos"></a>Installation von Microsoft ODBC Driver for SQL Server (macOS)

In diesem Artikel wird die Installation von Microsoft ODBC Driver for SQL Server unter macOS erläutert. Er enthält außerdem Anweisungen für die optionalen Befehlszeilentools für SQL Server (`bcp` und `sqlcmd`) und die unixODBC-Entwicklungsheader.

In diesem Artikel finden Sie Befehle zum Installieren des ODBC-Treibers über die Bash-Shell. Informationen zum direkten Herunterladen der Pakete finden Sie unter [Herunterladen von ODBC Driver for SQL Server](../download-odbc-driver-for-sql-server.md).

## <a name="microsoft-odbc-17"></a>Microsoft ODBC 17

Führen Sie die folgenden Befehle aus, um Microsoft ODBC Driver 17 for SQL Server unter macOS zu installieren:

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
HOMEBREW_NO_ENV_FILTERING=1 ACCEPT_EULA=Y brew install msodbcsql17 mssql-tools
```

> [!IMPORTANT]
> Wenn Sie das `msodbcsql`-Paket der Version 17 installiert haben, das kurz verfügbar war, sollten Sie es entfernen, bevor Sie das `msodbcsql17`-Paket installieren. Dadurch werden Konflikte vermieden. Das `msodbcsql17`-Paket und das `msodbcsql`-Paket der Version 13 können nebeneinander installiert werden.

## <a name="previous-versions"></a>Vorgängerversionen

In den folgenden Abschnitten finden Sie Anweisungen zum Installieren vorheriger Versionen von Microsoft ODBC Driver unter macOS.

## <a name="odbc-131"></a><a id="13.1"></a> ODBC 13.1

Verwenden Sie die folgenden Befehle, um Microsoft ODBC Driver 13.1 for SQL Server unter OS X 10.11 (El Capitan) und macOS 10.12 (Sierra):

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install msodbcsql@13.1.9.2 mssql-tools@14.0.6.0
```

## <a name="driver-files"></a>Treiberdateien

Der ODBC-Treiber unter macOS besteht aus den folgenden Komponenten:

|Komponente|BESCHREIBUNG|  
|---------------|-----------------|  
|libmsodbcsql.17.dylib oder libmsodbcsql.13.dylib|Die Datei (`dylib`) der dynamischen Bibliothek, die die gesamte Funktionalität des Treibers enthält. Diese Datei wird in `/usr/local/lib/` installiert.|  
|`msodbcsqlr17.rll` oder `msodbcsqlr13.rll`|Die begleitende Ressourcendatei für die Treiberbibliothek. Diese Datei wird in `[driver .dylib directory]../share/msodbcsql17/resources/en_US/` für den Treiber 17 und in `[driver .dylib directory]../share/msodbcsql/resources/en_US/` für den Treiber 13 installiert. | 
|msodbcsql.h|Die Headerdatei, die alle erforderlichen neuen Definitionen für die Verwendung des Treibers enthält.<br /><br /> **Hinweis:**  Sie können im selben Programm nicht auf „msodbcsql.h“ und auf „odbcss.h“ verweisen.<br /><br /> „msodbcsql“ wird in `/usr/local/include/msodbcsql17/` für den Treiber 17 und in `/usr/local/include/msodbcsql/` für den Treiber 13 installiert. |
|LICENSE.txt|Die Textdatei, die die Bestimmungen des Endbenutzer-Lizenzvertrags enthält. Diese Datei wird in `/usr/local/share/doc/msodbcsql17/` für den Treiber 17 und in `/usr/local/share/doc/msodbcsql/` für den Treiber 13 platziert. |
|RELEASE_NOTES|Die Textdatei, die die Versionshinweise enthält. Diese Datei wird in `/usr/local/share/doc/msodbcsql17/` für den Treiber 17 und in `/usr/local/share/doc/msodbcsql/` für den Treiber 13 platziert. |

## <a name="resource-file-loading"></a>Laden der Ressourcendatei

Der Treiber muss die Ressourcendatei laden, um zu funktionieren. Diese Datei heißt `msodbcsqlr17.rll` oder `msodbcsqlr13.rll`, je nach Treiberversion. Wie oben in der Tabelle aufgeführt, ist der Speicherort der `.rll`-Datei relativ zum Speicherort des Treibers selbst (`so` oder `dylib`). Ab Version 17.1 versucht der Treiber auch, die `.rll`-Datei aus dem Standardverzeichnis zu laden, wenn das Laden aus dem relativen Pfad fehlschlägt. Der Standardressourcendatei-Pfad unter macOS lautet `/usr/local/share/msodbcsql17/resources/en_US/`.

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie mit dem ODBC-Treiber keine Verbindung mit SQL Server herstellen können, finden Sie im Artikel zu bekannten Problemen weitere Informationen zur [Problembehandlung bei Verbindungsproblemen](known-issues-in-this-version-of-the-driver.md#connectivity).

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie den Treiber installiert haben, können Sie die [C++-ODBC-Beispielanwendung](../../odbc/cpp-code-example-app-connect-access-sql-db.md) testen. Weitere Informationen zum Entwickeln von ODBC-Anwendungen finden Sie unter [Entwickeln von Anwendungen](../../../odbc/reference/develop-app/developing-applications.md).

Weitere Informationen zum ODBC-Treiber finden Sie in den [Versionshinweisen](release-notes-odbc-sql-server-linux-mac.md) und den [Systemanforderungen](system-requirements.md).
