---
title: Erstellen einer SQL Server Native Client ODBC-Treiber Anwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, architecture
- SQL Server Native Client ODBC driver, creating applications
- ODBC function calls
- ODBC, header files
- ODBC applications
- ODBC applications, creating
- SQL Server Native Client ODBC driver, extensions
- applications [SQL Server Native Client]
- SQL Server Native Client ODBC driver, ODBC architecture
- extensions [ODBC]
- ODBC, driver extensions
- function calls [ODBC]
ms.assetid: c83c36e2-734e-4960-bc7e-92235910bc6f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4c5dc6e2452ea538f30e9ac10fa27b051aba13a1
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707104"
---
# <a name="creating-a-sql-server-native-client-odbc-driver-application"></a>Erstellen einer SQL Server Native Client-ODBC-Treiberanwendung
  Die ODBC-Architektur verfügt über vier Komponenten, die die folgenden Funktionen ausführen.  
  
|Komponente|Funktion|  
|---------------|--------------|  
|Application|Ruft ODBC-Funktionen auf, um mit einer ODBC-Datenquelle zu kommunizieren, sendet SQL-Anweisungen und verarbeitet Resultsets.|  
|Treiber-Manager|Verwaltet die Kommunikation zwischen einer Anwendung und allen von der Anwendung verwendeten ODBC-Treibern.|  
|Treiber|Verarbeitet alle ODBC-Funktionsaufrufe von der Anwendung, stellt eine Verbindung zu einer Datenquelle her, übergibt SQL-Anweisungen von der Anwendung an die Datenquelle und gibt Ergebnisse an die Anwendung zurück. Bei Bedarf übersetzt der Treiber ODBC SQL-Code von der Anwendung in den von der Datenquelle verwendeten systemeigenen SQL-Code.|  
|Datenquelle|Enthält alle Informationen, die ein Treiber für den Zugriff auf eine bestimmte Instanz der Daten in einem DBMS benötigt.|  
  
 Eine Anwendung, die den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber für die Kommunikation mit einer Instanz von verwendet, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] führt die folgenden Aufgaben aus:  
  
-   Verbindung mit einer Datenquelle  
  
-   Senden von SQL-Anweisungen an die Datenquelle  
  
-   Verarbeiten der Ergebnisse von Anweisungen von der Datenquelle  
  
-   Verarbeiten von Fehlern und Meldungen  
  
-   Beenden der Verbindung mit der Datenquelle  
  
 Eine komplexere Anwendung, die für den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber geschrieben wurde, kann auch die folgenden Aufgaben ausführen:  
  
-   Verwenden von Cursorn, um die Position in einem Resultset zu bestimmen  
  
-   Anforderung von Commit- oder Rollbackvorgängen zur Steuerung von Transaktionen  
  
-   Ausführen von verteilten Transaktionen, an denen zwei oder mehr Server beteiligt sind  
  
-   Ausführen von gespeicherten Prozeduren auf dem Remoteserver  
  
-   Aufrufen von Katalogfunktionen für die Abfrage der Attribute eines Resultsets  
  
-   Ausführen von Massen Kopier Vorgängen  
  
-   Verwalten von großen Daten Vorgängen (**varchar (max)**, **nvarchar (max)** und **varbinary (max)** -Spalten)  
  
-   Verwenden einer Logik zum Wiederherstellen einer Verbindung, um bei der Konfiguration der Datenbankspiegelung ein Failover zu ermöglichen  
  
-   Protokollieren von Leistungsdaten und Abfragen mit langer Ausführungszeit  
  
 Um ODBC-Funktionen aufrufen können, muss eine C- oder C++-Anwendung die Headerdateien sql.h, sqlext.h und sqltypes.h enthalten. Um API-Funktionen des ODBC-Installationsprogramms aufrufen zu können, muss eine Anwendung die Headerdatei odbcinst.h enthalten. Eine ODBC-Unicode-Anwendung muss die Headerdatei sqlucode.h enthalten. ODBC-Anwendungen müssen mit der Datei odbc32.lib verknüpft werden. ODBC-Anwendungen, die API-Funktionen des ODBC-Installationsprogramms aufrufen, müssen mit der Datei odbccp32.lib verknüpft werden. Diese Dateien sind im Windows Platform SDK enthalten.  
  
 Viele ODBC-Treiber, einschließlich des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-Treibers, bieten Treiber spezifische ODBC-Erweiterungen. Um die Vorteile von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client-ODBC-treiberspezifischen Erweiterungen zu nutzen, sollte eine Anwendung die Header Datei sqlncli. h enthalten. Diese Headerdatei enthält Folgendes:  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client-ODBC-Treiber spezifische Verbindungs Attribute.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client-ODBC-Treiber spezifische Anweisungs Attribute.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client-ODBC-Treiber spezifische Spalten Attribute.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifische Datentypen  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifische, benutzerdefinierte Datentypen  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client-ODBC-Treiber spezifische [SQLGetInfo](../../native-client-odbc-api/sqlgetinfo.md) -Typen.  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Diagnose Felder für Native Client-ODBC-Treiber.  
  
-   Für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] spezifische, dynamische Diagnosefunktionscodes  
  
-   C/C++-Definitionen für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-spezifische, systemeigene C-Datentypen (die zurückgegeben werden, wenn Spalten an den C-Datentyp SQL_C_BINARY gebunden werden).  
  
-   Typdefinition für die SQLPERF-Datenstruktur  
  
-   Massenkopiermakros und Prototypen zur Unterstützung von APIs für das Massenkopieren über eine ODBC-Verbindung  
  
-   Aufrufen der API-Funktionen für verteilte Abfragemetadaten für Listen mit verknüpften Servern und den zugehörigen Katalogen  
  
 Jede C-oder C++-ODBC-Anwendung, die die Massen Kopierfunktion des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC-Treibers verwendet, muss mit der Datei sqlncli11. lib verknüpft werden. Anwendungen, die die API-Funktionen für verteilte Abfragemetadaten aufrufen, müssen ebenfalls mit der Datei sqlncli11.lib verknüpft werden. Die Dateien sqlncli. h und sqlncli11. lib werden als Teil der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Entwicklertools verteilt. Die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Verzeichnisse Include und Lib müssen sich wie im folgenden Beispiel in den Verzeichnissen INCLUDE und LIB des Compilers befinden:  
  
```  
LIB=c:\Program Files\Microsoft Data Access SDK 2.8\Libs\x86\lib;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Lib;  
INCLUDE=c:\Program Files\Microsoft Data Access SDK 2.8\inc;C:\Program Files\Microsoft SQL Server\100\Tools\SDK\Include;  
```  
  
 Ob es erforderlich ist, dass bei der Anwendung mehrere ODBC-Aufrufe gleichzeitig ausstehen können, ist eine Entwurfsentscheidung, die früh im Prozess der Erstellung einer Anwendung getroffen werden muss. Es gibt zwei Methoden zur Unterstützung mehrerer gleichzeitiger ODBC-Aufrufe, die in den verbleibenden Themen dieses Abschnitts beschrieben werden. Weitere Informationen finden Sie in der [ODBC Programmer es Reference](https://go.microsoft.com/fwlink/?LinkId=45250).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
-   [Asynchroner Modus und SQLCancel](../../native-client-odbc-api/sqlcancel.md)  
  
-   [Multithreadanwendungen](creating-a-driver-application-multithreaded-applications.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md)  
  
  
