---
title: Systemanforderungen, Installation und Treiberdateien
ms.custom: ''
ms.date: 02/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d90fa182-1dab-4d6f-bd85-a04dd1479986
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9b48188cbc1eb25774bc127246514d82ca5ef475
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66841082"
---
# <a name="system-requirements-installation-and-driver-files"></a>Systemanforderungen, Installation und Treiberdateien
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

Der ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt Verbindungen mit SQL Server 2014, SQL Server 2012, [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)] und [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
Der ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Windows kann auf einem Computer installiert werden, der auch eine oder mehrere Versionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client besitzt.  
  
Der ODBC Driver 13 und 13.1 für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], zusätzlich zu den oben genannten unterstützt SQL Server 2016. 

Der ODBC Driver 17 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unterstützt alle oben genannten diejenigen sowie SQL Server 2017.

Der ODBC Driver 17 for SQL Server unterstützt SQL Server-2019 Driver, Version 17.3 ab.

Der Treibername, den Sie, in einer Verbindungszeichenfolge angeben lautet `ODBC Driver 11 for SQL Server` oder `ODBC Driver 13 for SQL Server` (für 13 und 13.1) oder `ODBC Driver 17 for SQL Server`.
  
## <a name="supported-operating-systems"></a>Unterstützte Betriebssysteme

Sie können Anwendungen mit dem Treiber auf den folgenden Windows-Betriebssystemen ausführen:  

-   Windows Server 2008 R2 
-   Windows Server 2012
-   Windows Server 2012 R2    
-   Windows Vista SP2 *(nur ODBC-Treiber 11)*  
-   Windows 7  
-   Windows 8
-   Windows 8.1
-   Windows 10
  
## <a name="installing-microsoft-odbc-driver-for-sql-server"></a>Installieren des Microsoft ODBC Driver for SQL Server

Der Treiber installiert ist, beim Ausführen von `msodbcsql.msi` aus einem der folgenden Links:

- [Download: Microsoft ODBC Driver 17 for SQL Server unter Windows](https://www.microsoft.com/download/details.aspx?id=56567)
- [Download: Microsoft ODBC Driver 13.1 for SQL Server unter Windows](https://www.microsoft.com/download/details.aspx?id=53339)
- [Download: Microsoft ODBC Driver 13 for SQL Server on Windows](https://www.microsoft.com/download/details.aspx?id=50420)
- [Download: Microsoft ODBC Driver 11 for SQL Server on Windows](https://www.microsoft.com/download/details.aspx?id=36434) 

> [!NOTE]
> Für diejenigen, die Treiber 17.1.0.1 oder unten installiert haben, wird empfohlen, dass es manuell deinstalliert werden, bevor Sie die neuere Version des Treibers installieren

Er kann parallel mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client installiert werden.  

Wenn Sie `msodbcsql.msi` aufrufen, werden nur die Clientkomponenten standardmäßig installiert. Bei den Clientkomponenten handelt es sich um Dateien, die das Ausführen einer mithilfe des Treibers entwickelten Anwendung unterstützen. Um die SDK-Komponenten zu installieren, geben Sie `ADDLOCAL=ALL` in der Befehlszeile an. Beispiel:  
  
```  
msiexec /i msodbcsql.msi ADDLOCAL=ALL  
```  
  
 Geben Sie `IACCEPTMSODBCSQLLICENSETERMS=YES` an, um den Bedingungen der Endbenutzerlizenz zuzustimmen, falls Sie die Option `/passive`, `/qn`, `/qb` oder `/qr` zum Installieren verwenden. Diese Option muss vollständig in Großbuchstaben angegeben werden. Beispiel:  
  
```  
msiexec /quiet /passive /qn /i msodbcsql.msi IACCEPTMSODBCSQLLICENSETERMS=YES ADDLOCAL=ALL  
```  
  
 So führen Sie eine unbeaufsichtigte Deinstallation aus:  
  
```  
msiexec /quiet /passive /qn /uninstall msodbcsql.msi  
```  
  
Wenn eine Anwendung den Treiber verwendet, sollte die Anwendung angeben, dass sie vom Treiber über die Installationsoption `APPGUID` abhängig ist. Dies ermöglicht dem Treiber-Installer, abhängige Anwendungen vor der Deinstallation zu melden. Um eine Abhängigkeit auf dem Treiber anzugeben, legen Sie den `APPGUID`-Befehlszeilenparameter auf Ihren Produktcode fest, wenn Sie den Treiber unbeaufsichtigt installieren. (Beim Packen des Setupprogramms für die Anwendung mit Microsoft Installer muss ein Produktcode erstellt werden.) Beispiel:  
  
```  
msiexec /i msodbcsql.msi APPGUID={ <Your dependent application's APPGUID> }  
```  

## <a name="command-line-tools-sqlcmdexe-and-bcpexe"></a>Befehlszeilentools: sqlcmd.exe und bcp.exe

Die `bcp.exe` und `sqlcmd.exe` -tools für die Verwendung mit dem Treiber heruntergeladen werden kann, auf [Microsoft Befehlszeilenprogramme 11 für SQL Server](https://www.microsoft.com/download/details.aspx?id=36433), [Microsoft Befehlszeilenprogramme 13 für SQL Server](https://www.microsoft.com/download/details.aspx?id=52680), oder [Microsoft Befehlszeilenprogramme 13.1 für SQLServer](https://www.microsoft.com/download/details.aspx?id=53591). Der Treiber ist eine Voraussetzung für die Installation `sqlcmd.exe` und `bcp.exe`.
  
`bcp.exe` und `sqlcmd.exe` installiert sind, der `110\Tools` Unterordner des `%PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC` für Version 11 und `130\Tools` für 13 und 13.1.

Eine Anwendung, die BCP-Funktionen verwendet, muss den Treiber mit derselben Version angeben, die mit der für die Anwendungskompilierung verwendeten Headerdatei und Bibliothek ausgeliefert wurde.  

Beispielsweise wird beim Kompilieren einer ODBC-Anwendung mit `msodbcsql11.lib` und `msodbcsql.h`, verwenden Sie "DRIVER = {ODBC Driver 11 für SQLServer}" in der Verbindungszeichenfolge.

## <a name="components-of-the-microsoft-odbc-driver-for-includessnoversionincludesssnoversion-mdmd-on-windows"></a>Komponenten von Microsoft ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter Windows 
 Der ODBC-Treiber für Windows enthält die folgenden Komponenten:
 
|Komponente|und Beschreibung|  
|---------------|-----------------|  
|msodbcsql17.dll oder <br> msodbcsql13.dll oder <br> msodbcsql11.dll|Die DLL-Datei (Dynamic-Link Library, DLL), die die gesamte Funktionalität des Treibers enthält Diese Datei wird in % SYSTEMROOT%\System32 installiert.|  
|msodbcdiag17.dll oder <br> msodbcdiag13.dll oder <br> msodbcdiag11.dll|Die Dynamic Link Library (DLL)-Datei, die vom Treiber (Ablaufverfolgung)-Diagnose-Schnittstelle enthält. Diese Datei wird in % SYSTEMROOT%\System32 installiert.|
|msodbcsqlr17.rll oder <br> msodbcsqlr13.rll oder <br> msodbcsqlr11.rll|Die begleitende Ressourcendatei für die Treiberbibliothek. Diese Datei wird in % SYSTEMROOT%\System32\1033 installiert.| 
|s13ch_msodbcsql.chm oder <br> s11ch_msodbcsql.chm |Die Hilfedatei des Datenquellen-Assistenten-, die dokumentiert, wie eine Datenquelle für den Treiber erstellt werden kann. Diese Datei wird in %SYSTEMROOT%\System32\1033 installiert. <br /> <br /> **Hinweis:** keine Chm-Datei für ODBC Driver 17 vorhanden ist. |  
|msodbcsql.h|Die Headerdatei, die alle erforderlichen neuen Definitionen für die Verwendung des Treibers enthält.<br /><br /> **Hinweis:**  Sie können nicht auf „msodbcsql.h“ und „odbcss.h“ im selben Programm verweisen.<br /><br /> „msodbcsql.h“ für ODBC Driver 17 oder 13 wird in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK installiert. <br /> „msodbcsql.h“ für ODBC Driver 11 wird in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK installiert.| 
|msodbcsql17.lib oder <br> msodbcsql13.lib oder <br> msodbcsql11.lib|Die Bibliotheksdatei, die für den Aufruf der **bcp**-Hilfsprogrammfunktionen benötigt wird. Diese Funktionen werden als Teil des Treibers bereitgestellt.<br /><br /> **Hinweis:** Wenn Sie in Ihrem Programm auf diese Bibliotheksdatei verweisen, stellen Sie sicher, dass sie in Ihrem Systempfad sowie im Systempfad der Dateien, die die Anwendungen verwenden, vorhanden ist.<br /><br /> „msodbcsql17.lib“ oder „msodbcsql13.lib“ wird in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\130\SDK installiert.<br /> „msodbcsql11.lib“ wird in %PROGRAMFILES%\Microsoft SQL Server\Client SDK\ODBC\110\SDK installiert.|

  
## <a name="see-also"></a>Weitere Informationen  
 [Microsoft ODBC Driver for SQL Server on Windows](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)  
  
  
