---
title: Systemanforderungen, Installation und Treiberdateien
ms.custom: ''
ms.date: 09/24/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6365b86a4efe8d29273035d62f76c7bb02b15335
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "74908849"
---
# <a name="system-requirements-installation-and-driver-files"></a>Systemanforderungen, Installation und Treiberdateien

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

In diesem Artikel werden die ODBC-Treiber erläutert, die eine Verbindung mit SQL Server herstellen.

## <a name="driver-versions"></a>Treiberversionen

| Treiberversion | Beschreibung der Unterstützung |
| :------------- | :--------------------- |
| ODBC-Treiber 11 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] | Unterstützt Verbindungen mit SQL Server 2014, SQL Server 2012, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)] und [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. |
| ODBC-Treiber 11 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Windows | Kann auf einem Computer installiert werden, auf dem auch eine oder mehrere Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client vorhanden sind. |
| ODBC-Treiber 13 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] | Unterstützt Verbindungen mit SQL Server 2016, SQL Server 2014, SQL Server 2012, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] und [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)]. |
| ODBC-Treiber 13.1 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] | Unterstützt zusätzlich zu den für Version 13 genannten Komponenten auch SQL Server 2017. |
| ODBC-Treiber 17 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] | Unterstützt die gleichen Datenbankversionen wie Version 13.1. |
| ODBC Driver 17 for SQL Server | Bietet ab Treiberversion 17.3 Unterstützung für SQL Server 2019. |
| &nbsp; | &nbsp; |

### <a name="connection-string-details"></a>Details zu Verbindungszeichenfolgen

Der in einer Verbindungszeichenfolge angegebene Treibername lautet `ODBC Driver 11 for SQL Server` oder `ODBC Driver 13 for SQL Server` (sowohl für 13 als auch für 13.1) oder `ODBC Driver 17 for SQL Server`.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

Sie können Anwendungen mit dem Treiber auf den folgenden Windows-Betriebssystemen ausführen:  

- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2
- Windows Server 2016
- Windows Vista SP2 &nbsp; _(nur ODBC-Treiber 11)_
- Windows 7
- Windows 8
- Windows 8.1
- Windows 10

## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>Installieren des Microsoft ODBC Driver for SQL Server

Der Treiber wird installiert, wenn Sie `msodbcsql.msi` über einen der folgenden Links ausführen:

- [Download: Microsoft ODBC Driver 17 for SQL Server unter Windows](https://www.microsoft.com/download/details.aspx?id=56567)
- [Download: Microsoft ODBC Driver 13.1 for SQL Server unter Windows](https://www.microsoft.com/download/details.aspx?id=53339)
- [Download: Microsoft ODBC Driver 13 for SQL Server on Windows](https://www.microsoft.com/download/details.aspx?id=50420)
- [Download: Microsoft ODBC Driver 11 for SQL Server unter Windows](https://www.microsoft.com/download/details.aspx?id=36434)

> [!NOTE]
> Wenn Sie die Treiberversion 17.1.0.1 oder niedriger installiert haben, wird empfohlen, diese manuell zu deinstallieren, bevor Sie eine neuere Version installieren.

### <a name="side-by-side-with-native-client"></a>Parallele Installation mit Native Client

Der Treiber kann parallel mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client installiert werden.

Wenn Sie `msodbcsql.msi` aufrufen, werden nur die Clientkomponenten standardmäßig installiert. Bei den Clientkomponenten handelt es sich um Dateien, die das Ausführen einer mithilfe des Treibers entwickelten Anwendung unterstützen. Um die SDK-Komponenten zu installieren, geben Sie `ADDLOCAL=ALL` in der Befehlszeile an. Beispiel:
  
```console
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  

### <a name="end-user-license"></a>Endbenutzerlizenz

Geben Sie `IACCEPTMSODBCSQLLICENSETERMS=YES` an, um den Bedingungen der Endbenutzerlizenz zuzustimmen, falls Sie die Option `/passive`, `/qn`, `/qb` oder `/qr` zum Installieren verwenden. Diese Option muss vollständig in Großbuchstaben angegeben werden. Beispiel:
  
```console
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  

### <a name="silent-uninstall"></a>Unbeaufsichtigte Deinstallation

Das folgende Beispiel veranschaulicht, wie Sie eine unbeaufsichtigte Deinstallation durchführen.
  
```console
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  

### <a name="indicate-dependency"></a>Angeben von Abhängigkeiten

Wenn eine Anwendung den Treiber verwendet, sollte die Anwendung angeben, dass sie vom Treiber über die Installationsoption `APPGUID` abhängig ist. Dies ermöglicht dem Treiber-Installer, abhängige Anwendungen vor der Deinstallation zu melden. Um eine Abhängigkeit auf dem Treiber anzugeben, legen Sie den `APPGUID`-Befehlszeilenparameter auf Ihren Produktcode fest, wenn Sie den Treiber unbeaufsichtigt installieren. Der Produktcode muss beim Packen des Setupprogramms für die Anwendung mit Microsoft Installer erstellt werden. Beispiel:
  
```console
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>Befehlszeilentools: sqlcmd.exe und bcp.exe

Die Tools `bcp.exe` und `sqlcmd.exe` zur Verwendung mit dem Treiber können hier heruntergeladen werden: [Microsoft Command Line Utilities 11 for SQL Server](https://www.microsoft.com/download/details.aspx?id=36433) (Microsoft-Befehlszeilen-Hilfsprogramme 11 für SQL Server), [Microsoft Command Line Utilities 13 for SQL Server](https://www.microsoft.com/download/details.aspx?id=52680) (Microsoft-Befehlszeilen-Hilfsprogramme 13 für SQL Server) oder [Microsoft Command Line Utilities 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53591) (Microsoft-Befehlszeilen-Hilfsprogramme 13.1 für SQL Server). Der Treiber ist eine Voraussetzung für die Installation von `sqlcmd.exe` und `bcp.exe`.
  
`bcp.exe` und `sqlcmd.exe` werden für Version 11 in den Unterordner `110\Tools` und für die Versionen 13 und 13.1 in den Unterordner `130\Tools` von `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC` installiert.

Eine Anwendung, die BCP-Funktionen verwendet, muss den Treiber mit derselben Version angeben, die mit der für die Anwendungskompilierung verwendeten Headerdatei und Bibliothek ausgeliefert wurde.  

Wenn Sie beispielweise eine ODBC-Anwendung mit `msodbcsql11.lib` und `msodbcsql.h` kompilieren, verwenden Sie „DRIVER={ODBC Driver 11 for SQL Server}“ in der Verbindungszeichenfolge.

## <a name="components-of-the-microsoft-odbc-driver-for-ssnoversion-on-windows"></a>Komponenten von Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Windows

Der ODBC-Treiber für Windows enthält die folgenden Komponenten:

| Komponente | Beschreibung |
| :-------- | :---------- |
|msodbcsql17.dll oder <br/> msodbcsql13.dll oder <br/> msodbcsql11.dll|Die DLL-Datei (Dynamic-Link Library, DLL), die die gesamte Funktionalität des Treibers enthält Diese Datei wird in „%SYSTEMROOT%\System32“ installiert.|  
|msodbcdiag17.dll oder <br/> msodbcdiag13.dll oder <br/> msodbcdiag11.dll|Die DLL-Datei (Dynamic-Link Library), die die Diagnoseschnittstelle (Ablaufverfolgung) des Treibers enthält. Diese Datei wird in „%SYSTEMROOT%\System32“ installiert.|
|msodbcsqlr17.rll oder <br/> msodbcsqlr13.rll oder <br/> msodbcsqlr11.rll|Die begleitende Ressourcendatei für die Treiberbibliothek. Diese Datei wird in „%SYSTEMROOT%\System32\1033“ installiert.| 
|s13ch_msodbcsql.chm oder <br/> s11ch_msodbcsql.chm |Die Hilfedatei des Datenquellen-Assistenten-, die dokumentiert, wie eine Datenquelle für den Treiber erstellt werden kann. Diese Datei wird in „%SYSTEMROOT%\System32\1033“ installiert. <br /> <br /> **HINWEIS:** Für die ODBC-Treiberversion 17 ist keine CHM-Datei vorhanden. |  
|msodbcsql.h|Die Headerdatei, die alle erforderlichen neuen Definitionen für die Verwendung des Treibers enthält.<br /><br /> **Hinweis:**  Sie können im selben Programm nicht auf „msodbcsql.h“ und „odbcss.h“ verweisen.<br /><br /> „msodbcsql.h“ für ODBC Driver 17 oder 13 wird in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK installiert. <br /> „msodbcsql.h“ für ODBC Driver 11 wird in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK installiert.| 
|msodbcsql17.lib oder <br/> msodbcsql13.lib oder <br/> msodbcsql11.lib|Die Bibliotheksdatei, die für den Aufruf der **bcp**-Hilfsprogrammfunktionen benötigt wird. Diese Funktionen werden als Teil des Treibers bereitgestellt.<br /><br /> **Hinweis:**  Wenn Sie in Ihrem Programm auf diese Bibliotheksdatei verweisen, stellen Sie sicher, dass sie in Ihrem Systempfad sowie im Systempfad der Dateien, die die Anwendung verwenden, vorhanden ist.<br /><br /> „msodbcsql17.lib“ oder „msodbcsql13.lib“ wird in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK installiert.<br /> „msodbcsql11.lib“ wird in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK installiert.|
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Weitere Informationen

[Microsoft ODBC Driver for SQL Server unter Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
