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
ms.openlocfilehash: 6ab9a4035e3a714e6725f28f7e4e370bf3fd0119
ms.sourcegitcommit: 82b70c39550402a2b0b327db32bf5ecf88b50d3c
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73032990"
---
# <a name="system-requirements-installation-and-driver-files"></a>Systemanforderungen, Installation und Treiberdateien

[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

In diesem Artikel werden die ODBC-Treiber erläutert, die eine Verbindung mit SQL Server herstellen.

## <a name="driver-versions"></a>Treiberversionen

| Treiberversion | Beschreibung der Unterstützung |
| :------------- | :--------------------- |
| ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] | Unterstützt Verbindungen mit SQL Server 2014, SQL Server 2012, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)]und [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. |
| ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on Windows | Kann auf einem Computer installiert werden, auf dem auch eine oder mehrere Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client installiert sind. |
| ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] | Unterstützt Verbindungen mit SQL Server 2016, SQL Server 2014, SQL Server 2012, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]und [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)]. |
| ODBC-Treiber 13,1 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <br/> Zusätzlich zu den oben aufgeführten für 13 | Unterstützt SQL Server 2017. |
| ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] | Unterstützt die gleichen Daten Bank Versionen wie 13,1. |
| ODBC Driver 17 for SQL Server | Unterstützt SQL Server 2019 ab Treiber Version 17,3. |
| &nbsp; | &nbsp; |

### <a name="connection-string-details"></a>Verbindungs Zeichen folgen Details

Der Treiber Name, den Sie in einer Verbindungs Zeichenfolge angeben, ist `ODBC Driver 11 for SQL Server` oder `ODBC Driver 13 for SQL Server` (sowohl für 13 als auch 13,1) oder `ODBC Driver 17 for SQL Server`.

## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

Sie können Anwendungen mit dem Treiber auf den folgenden Windows-Betriebssystemen ausführen:  

- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2
- Windows Server 2016
- Windows Vista SP2 &nbsp; _(nur ODBC Driver 11)_
- Windows 7
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
> Für Benutzer, die über Treiber 17.1.0.1 oder eine der folgenden Versionen verfügen, wird empfohlen, dass Sie manuell deinstalliert werden, bevor Sie die neuere Version des Treibers installieren.

### <a name="side-by-side-with-native-client"></a>Parallele Verwendung von Native Client

Der Treiber kann parallel mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client installiert werden.

Wenn Sie `msodbcsql.msi` aufrufen, werden nur die Clientkomponenten standardmäßig installiert. Bei den Clientkomponenten handelt es sich um Dateien, die das Ausführen einer mithilfe des Treibers entwickelten Anwendung unterstützen. Um die SDK-Komponenten zu installieren, geben Sie `ADDLOCAL=ALL` in der Befehlszeile an. Beispiel:
  
```console
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  

### <a name="end-user-license"></a>Endbenutzer Lizenz

Geben Sie `IACCEPTMSODBCSQLLICENSETERMS=YES` an, um den Bedingungen der Endbenutzerlizenz zuzustimmen, falls Sie die Option `/passive`, `/qn`, `/qb` oder `/qr` zum Installieren verwenden. Diese Option muss vollständig in Großbuchstaben angegeben werden. Beispiel:
  
```console
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  

### <a name="silent-uninstall"></a>Automatische Deinstallation

Das folgende Beispiel zeigt, wie eine unbeaufsichtigte Deinstallation durchgeführt wird.
  
```console
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  

### <a name="indicate-dependency"></a>Abhängigkeit angeben

Wenn eine Anwendung den Treiber verwendet, sollte die Anwendung angeben, dass sie vom Treiber über die Installationsoption `APPGUID` abhängig ist. Dies ermöglicht dem Treiber-Installer, abhängige Anwendungen vor der Deinstallation zu melden. Um eine Abhängigkeit auf dem Treiber anzugeben, legen Sie den `APPGUID`-Befehlszeilenparameter auf Ihren Produktcode fest, wenn Sie den Treiber unbeaufsichtigt installieren. Der Produktcode muss beim Packen des Setupprogramms für die Anwendung mit Microsoft Installer erstellt werden. Beispiel:
  
```console
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>Befehlszeilentools: sqlcmd.exe und bcp.exe

Die `bcp.exe`-und `sqlcmd.exe` Tools für die Verwendung mit dem Treiber können bei [Microsoft Befehlszeilen-Hilfsprogramme 11 für SQL Server](https://www.microsoft.com/download/details.aspx?id=36433), [Microsoft Befehlszeilen-Hilfsprogramme 13 für SQL Server](https://www.microsoft.com/download/details.aspx?id=52680)oder [Microsoft Befehlszeilen-Hilfsprogramme 13,1 für SQL Server heruntergeladen werden. ](https://www.microsoft.com/download/details.aspx?id=53591). Der Treiber ist eine Voraussetzung für die Installation von `sqlcmd.exe` und `bcp.exe`.
  
`bcp.exe` und `sqlcmd.exe` werden im Unterordner `110\Tools` von `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC` für Version 11 installiert und `130\Tools` für 13 und 13,1.

Eine Anwendung, die BCP-Funktionen verwendet, muss den Treiber mit derselben Version angeben, die mit der für die Anwendungskompilierung verwendeten Headerdatei und Bibliothek ausgeliefert wurde.  

Wenn Sie z. b. eine ODBC-Anwendung mit `msodbcsql11.lib` und `msodbcsql.h`kompilieren, verwenden Sie "Driver = {ODBC Driver 11 for SQL Server}" in der Verbindungs Zeichenfolge.

## <a name="components-of-the-microsoft-odbc-driver-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Komponenten von Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Windows

Der ODBC-Treiber für Windows enthält die folgenden Komponenten:

| Komponente | und Beschreibung |
| :-------- | :---------- |
|msodbcsql17. dll oder <br/> msodbcsql13.dll oder <br/> msodbcsql11.dll|Die DLL-Datei (Dynamic-Link Library, DLL), die die gesamte Funktionalität des Treibers enthält Diese Datei wird unter%SystemRoot%\System32. installiert.|  
|msodbcdiag17. dll oder <br/> msodbcdiag13. dll oder <br/> msodbcdiag11.dll|Die DLL-Datei (Dynamic-Link Library), die die Diagnoseschnittstelle (Ablauf Verfolgung) des Treibers enthält. Diese Datei wird unter%SystemRoot%\System32. installiert.|
|msodbcsqlr17.rll oder <br/> msodbcsqlr13.rll oder <br/> msodbcsqlr11.rll|Die begleitende Ressourcendatei für die Treiberbibliothek. Diese Datei wird unter%systemroot%\system32\1033. installiert.| 
|s13ch_msodbcsql.chm oder <br/> s11ch_msodbcsql.chm |Die Hilfedatei des Datenquellen-Assistenten-, die dokumentiert, wie eine Datenquelle für den Treiber erstellt werden kann. Diese Datei wird unter%systemroot%\system32\1033 installiert. <br /> <br /> **Hinweis:** Es ist keine CHM-Datei für den ODBC-Treiber 17 vorhanden. |  
|msodbcsql.h|Die Headerdatei, die alle erforderlichen neuen Definitionen für die Verwendung des Treibers enthält.<br /><br /> **Hinweis:**  Sie können nicht auf „msodbcsql.h“ und „odbcss.h“ im selben Programm verweisen.<br /><br /> „msodbcsql.h“ für ODBC Driver 17 oder 13 wird in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK installiert. <br /> „msodbcsql.h“ für ODBC Driver 11 wird in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK installiert.| 
|msodbcsql17.lib oder <br/> msodbcsql13.lib oder <br/> msodbcsql11.lib|Die Bibliotheksdatei, die für den Aufruf der **bcp**-Hilfsprogrammfunktionen benötigt wird. Diese Funktionen werden als Teil des Treibers bereitgestellt.<br /><br /> **Hinweis:** Wenn Sie in Ihrem Programm auf diese Bibliotheksdatei verweisen, stellen Sie sicher, dass sie in Ihrem Systempfad sowie im Systempfad der Dateien, die die Anwendungen verwenden, vorhanden ist.<br /><br /> „msodbcsql17.lib“ oder „msodbcsql13.lib“ wird in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK installiert.<br /> „msodbcsql11.lib“ wird in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK installiert.|
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Siehe auch

[Microsoft ODBC Driver for SQL Server unter Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
