---
title: SQL Server Express localdb-Header und Versionsinformationen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_location:
- sqluserinstance.dll
ms.assetid: 506b5161-b902-4894-b87b-9192d7b1664a
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 6e390430115daf394c5e94267dad30a87851375d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63128696"
---
# <a name="sql-server-express-localdb-header-and-version-information"></a>SQL Server Express LocalDB-Header und Versionsinformationen
  Es gibt keine separate Headerdatei für die SQL Server Express LocalDB-Instanz-API. Die Signaturen und Fehlercodes der LocalDB-Funktion sind in der SQL Server Native Client-Headerdatei (sqlncli.h) definiert. Zur Verwendung der LocalDB-Instanz-API müssen Sie die Headerdatei sqlncli.h in das Projekt einfügen.  
  
## <a name="localdb-versioning"></a>LocalDB-Versionsverwaltung  
 Die LocalDB-Installation verwendet pro Haupt-SQL Server-Version einen einzelnen Satz Binärdateien. Diese LocalDB-Versionen werden gewartet und unabhängig gepatcht. Das bedeutet, dass der Benutzer angeben muss, welche LocalDB-Baselineversion (also Haupt-SQL Server-Version) er verwendet. Die Version wird im Standard Versions Format angegeben, das von der .NET Framework **System. Version** -Klasse definiert wird:  
  
 *Hauptversion. neben Version [. Build [. Revision]]*  
  
 Die ersten beiden Zahlen in der Versions Zeichenfolge (*Haupt* -und *neben*Version) sind obligatorisch. Die letzten zwei Zahlen in der Versions Zeichenfolge (*Build* und *Revision*) sind optional und werden standardmäßig auf 0 (null) gesetzt, wenn der Benutzer Sie verlässt. Dies bedeutet Folgendes: Wenn der Benutzer nur "12,2" als localdb-Versionsnummer angibt, wird er so behandelt, als ob der Benutzer "12.2.0.0" angegeben hätte.  
  
 Die Version für die LocalDB-Installation ist im Registrierungsschlüssel MSSQLServer\CurrentVersion unter dem SQL Server-Instanz-Registrierungsschlüssel definiert. Beispiel:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL12E.LOCALDB\ MSSQLServer\CurrentVersion: "CurrentVersion"="12.0.2531.0"  
```  
  
 Mehrere LocalDB-Versionen auf derselben Arbeitsstation werden gleichzeitig unterstützt. Benutzercode verwendet jedoch immer die neueste verfügbare **sqluserinstance** -dll auf dem lokalen Computer, um eine Verbindung mit localdb-Instanzen herzustellen.  
  
## <a name="locating-the-sqluserinstance-dll"></a>Suchen der SQLUserInstance-DLL  
 Zum Auffinden der **sqluserinstance** -dll verwendet der Client Anbieter den folgenden Registrierungsschlüssel:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions]  
```  
  
 Unter diesem Schlüssel befindet sich eine Liste Schlüssel, einer für jede Version der auf dem Computer installierten LocalDB. Jeder dieser Schlüssel wird mit der localdb-Versionsnummer im Format * \<Haupt Versions>* benannt. Neben Versions>(z. b. lautet der Schlüssel [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] für den Namen 12,0). * \<* Unter jedem Versionsschlüssel dort ist ein `InstanceAPIPath`-Name-Wert-Paar, das den vollständigen Pfad zur mit dieser Version installierten SQLUserInstance.dll-Datei definiert. Im folgenden Beispiel werden die Registrierungseinträge für einen Computer gezeigt, auf dem die LocalDB-Versionen 11.0 und 12.0 installiert sind:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"]  
```  
  
 Der Client Anbieter muss die neueste Version unter allen installierten Versionen suchen und die DLL-Datei **sqluserinstance** aus dem zugeordneten `InstanceAPIPath` Wert laden.  
  
### <a name="wow64-mode-on-64-bit-windows"></a>WOW64-Modus unter 64-Bit-Windows  
 64-Bit-Installationen von LocalDB weisen einen zusätzlichen Satz Registrierungsschlüssel auf, der 32-Bit-Anwendungen, die im WOW64 (Windows-32-on-Windows-64)-Modus ausgeführt werden, die Verwendung von LocalDB ermöglicht. Insbesondere unter 64-Bit-Windows erstellt LocalDB-MSI die folgenden Registrierungsschlüssel:  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"]  
  
```  
  
 64-Bit-Programme, `Installed Versions` die den Schlüssel lesen, sehen Werte, die auf 64-Bit-Versionen der **sqluserinstance** -dll verweisen, während 32-Bit-Programme (die auf 64-Bit-Fenstern im WOW64 `Installed Versions` -Modus ausgeführt werden `Wow6432Node` ) automatisch an einen Schlüssel in der Hive umgeleitet werden. Dieser Schlüssel enthält Werte, die auf 32-Bit-Versionen der **sqluserinstance** -dll verweisen.  
  
## <a name="using-localdb_define_proxy_functions"></a>Verwenden von LOCALDB_DEFINE_PROXY_FUNCTIONS  
 Die API der localdb-Instanz definiert eine Konstante mit dem Namen LOCALDB_DEFINE_PROXY_FUNCTIONS, die das erkennen und Laden der **sqluserinstance** -dll automatisiert.  
  
 Der durch diese Konstante aktivierte Abschnitt des Codes stellt eine Implementierung der Proxys für jede der LocalDB-APIs bereit. In den Proxy Implementierungen wird eine gemeinsame Funktion verwendet, um eine Bindung an Einstiegspunkte in der zuletzt installierten **sqluserinstance** -DLL herzustellen, und dann die Anforderungen weiterzuleiten.  
  
 Die Proxyfunktionen werden nur aktiviert, wenn die Konstante LOCALDB_DEFINE_PROXY_FUNCTIONS vor dem Einfügen der Datei sqlncli.h im Benutzercode definiert wurde. Die Konstante darf in nur einem Quellenmodul (CPP-Datei) definiert werden, da sie externe Funktionsnamen für alle API-Einstiegspunkte definiert. Sie stellt eine Implementierung der Proxys für alle LocalDB-APIs bereit.  
  
 Im folgenden Codebeispiel wird gezeigt, wie das Makro vom systemeigenen C++-Code verwendet wird:  
  
```  
// Define the LOCALDB_DEFINE_PROXY_FUNCTIONS constant to enable the LocalDB proxy functions   
// The #define has to take place BEFORE the API header file (sqlncli.h) is included  
#define LOCALDB_DEFINE_PROXY_FUNCTIONS  
#include <sqlncli.h>  
...  
HRESULT hr = S_OK;  
  
// Create LocalDB instance by calling the create API proxy function included by macro  
if (FAILED(hr = LocalDBCreateInstance( L"12.0", L"name", 0)))  
{  
...  
}  
...  
  
```  
  
  
