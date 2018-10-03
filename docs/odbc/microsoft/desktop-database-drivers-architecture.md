---
title: Desktop-Treiber eine Datenbankarchitektur mit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], architecture
- ODBC desktop database drivers [ODBC], architecture
- desktop database drivers [ODBC], architecture
ms.assetid: 8b4d13f7-ab37-40b4-a9c6-145e7385352f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 01de6a3707ea2ed96399c678625f3e94c13fc5db
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649568"
---
# <a name="desktop-database-drivers-architecture"></a>Architektur der Desktop-Datenbanktreiber
Diese Treiber sind für die Verwendung unter Microsoft Windows 95 oder höher oder Windows NT 4.0 und Windows 2000 vorgesehen. Nur 32-Bit-Anwendungen werden unter Windows 95 oder höher unterstützt. 16-Bit- und 32-Bit-Anwendungen werden unter Windows NT 4.0 und Windows 2000 unterstützt.  
  
> [!NOTE]  
>  Informationen zur Version von ODBC mit diesen Treibern verwendet werden, finden Sie in der *ODBC Programmer's Reference*, und die Anmerkungen zu dieser vergangenen und aktuellen Version. Mit Ausnahme der aufgeführten Bereiche, diese Treiber entsprechen den *ODBC Programmer's Reference*.  
  
 Der ODBC-Desktop-Datenbanktreiber enthalten 32-Bit-Treiber für Microsoft Access, dBASE, Microsoft Excel, Paradox und Text. Es sind keine 16 - Bit-Treiber enthalten. (Ein Treiber für Microsoft FoxPro steht getrennt.)  
  
 Die Anwendung/Treiberarchitektur unter Windows 95 oder höher ausgeführt wird:  
  
 ![App&#47;Treiberarchitektur: Windows 95 und höher](../../odbc/microsoft/media/odbcjetarch1.gif "ODBCJetArch1")  
  
 Die Verwendung dieser Treiber von 16-Bit-Anwendungen unter Windows 95 wird nicht unterstützt.  
  
 Die Anwendung/Driver-Architektur in Windows NT 4.0 und Windows 2000 ist:  
  
 ![App&#47;Treiberarchitektur: NT 4.0 und Windows 2000](../../odbc/microsoft/media/odbcjetarch2.gif "ODBCJetArch2")  
  
 Die Desktop-Datenbanktreiber sind zwei-Ebenen-Treiber. In einer Konfiguration mit zwei Ebenen führt der Treiber nicht den Prozess der Analyse, Überprüfung, optimieren und Ausführen der Abfrage aus. Microsoft Jet stattdessen führt folgende Aufgaben aus. Er verarbeitet die ODBC-API-Aufrufe und fungiert als eine SQL-Engine. Microsoft Jet ist ein integraler, untrennbar Teil der Treiber geworden: Es ist im Lieferumfang der Treiber und mit den Treibern befindet, auch wenn keine andere Anwendung auf dem Computer verwendet.  
  
 Die Desktop-Datenbanktreiber bestehen aus sechs verschiedenen-Treiber – oder, genauer gesagt, einen Treiber (Odbcjt32.dll) Datei, die die ODBC [-Treiber-Manager](../../odbc/reference/the-driver-manager.md) auf sechs verschiedene Arten verwendet. Das DRIVERID-Flag in der Registrierung für eine Datenquelle bestimmt, welche Treiber in Odbcjt32.dll des Treiber-Managers verwendet. Eine Anwendung übergibt dieses Flag in der Verbindungszeichenfolge enthalten, die in einem Aufruf von **SQLDriverConnect**. Standardmäßig ist das Flag für die ID der dem Microsoft Access-Treiber.  
  
 Die Setup-Treiberdatei ändert das DRIVERID-Flag beim Setup. Alle Treiber, mit Ausnahme von der Microsoft Access-Treiber müssen ein Setup-DLL verknüpft. Beim Klicken auf **Setup** in die [Microsoft ODBC-Datenquellenadministrator](../../odbc/admin/odbc-data-source-administrator.md) für eine Datenquelle, lädt der ODBC-Installationsprogramm-DLL (die Datei Odbcinst.dll) der Setup-DLL. Der Setup-DLL exportiert, die ODBC-Installer-Funktion **SQLConfigDataSource**. Wenn ein Fensterhandle, um übergeben wird **SQLConfigDataSource**, diese Funktion zeigt ein Setup-Fenster und ändert das DRIVERID-Flag entsprechend der Treiber, die von der Benutzeroberfläche ausgewählt.  
  
 Wenn Sie eine Datei programmgesteuert erstellt wird, an ein Fensterhandle von NULL übergeben **SQLConfigDataSource**, und die Funktion erstellt eine Datenquelle dynamisch und ändern das Flag DRIVERID gemäß der *LpszDriver*Argument im Funktionsaufruf.  
  
 Odbcjt32.dll implementiert ODBC-Funktionen auf der Microsoft Jet-API. Es ist jedoch keine direkte Zuordnung zwischen der ODBC- und Microsoft Jet-Funktionen. Viele Faktoren, z. B. die Cursormodelle und SQL-Zuordnung zu verhindern, dass eine direkte Korrelation der Funktionen.  
  
 Der ODBC-Treiber befindet sich zwischen der Microsoft Jet-Engine und der ODBC-Treiber-Manager. Einige ODBC-Funktionen, die von einer Anwendung aufgerufen werden, werden vom Treiber-Manager behandelt und nicht an den Treiber übergeben. Für diese Funktionen erkennt Microsoft Jet nie die Funktion aufrufen, da er nicht über eine direkte Verbindung zu der Treiber-Manager verfügt.
