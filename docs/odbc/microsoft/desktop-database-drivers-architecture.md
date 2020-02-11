---
title: Architektur der Desktop-Datenbanktreiber | Microsoft-Dokumentation
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
ms.openlocfilehash: ccd1f14b0cfbcbdbc675a142ebabf11932409832
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68071908"
---
# <a name="desktop-database-drivers-architecture"></a>Architektur der Desktop-Datenbanktreiber
Diese Treiber sind für die Verwendung mit Microsoft Windows 95 oder höher oder Windows NT 4,0 und Windows 2000 konzipiert. Nur 32-Bit-Anwendungen werden unter Windows 95 oder höher unterstützt. 16-Bit-und 32-Bit-Anwendungen werden unter Windows NT 4,0 und Windows 2000 unterstützt.  
  
> [!NOTE]  
>  Informationen zur ODBC-Version, die mit diesen Treibern verwendet werden soll, finden Sie in der *ODBC-Programmier Referenz*und in früheren und aktuellen Versions hinweisen. Mit Ausnahme der genannten Bereiche entsprechen diese Treiber der *ODBC-Programmier Referenz*.  
  
 Die ODBC Desktop-Datenbanktreiber umfassen 32-Bit-Treiber für Microsoft Access, dBASE, Microsoft Excel, Paradox und Text. Es sind keine 16-Bit-Treiber enthalten. (Ein Treiber für Microsoft FoxPro ist separat verfügbar.)  
  
 Die Anwendungs-/Treiberarchitektur unter Windows 95 oder höher ist:  
  
 ![Architektur des App&#47;-Treibers: Windows 95 und höher](../../odbc/microsoft/media/odbcjetarch1.gif "ODBCJetArch1")  
  
 Die Verwendung dieser Treiber mit 16-Bit-Anwendungen unter Windows 95 wird nicht unterstützt.  
  
 Die Anwendungs-/Treiberarchitektur unter Windows NT 4,0 und Windows 2000 lautet:  
  
 ![Architektur des App&#47;-Treibers: NT 4,0 und Windows 2000](../../odbc/microsoft/media/odbcjetarch2.gif "ODBCJetArch2")  
  
 Die Desktop-Datenbanktreiber sind zweistufige Treiber. In einer Konfiguration mit zwei Ebenen führt der Treiber den Prozess der Abfrage, Validierung, Optimierung und Ausführung der Abfrage nicht aus. Stattdessen führt Microsoft Jet diese Aufgaben aus. Er verarbeitet ODBC-API-Aufrufe und fungiert als SQL-Engine. Microsoft Jet wurde zu einem integralen, untrennbaren Teil der Treiber: er wird mit den Treibern ausgeliefert und befindet sich in den Treibern, auch wenn er von keiner anderen Anwendung auf dem Computer verwendet wird.  
  
 Die Desktop-Datenbanktreiber bestehen aus sechs verschiedenen Treibern oder, genauer, einer Treiberdatei (Odbcjt32. dll), die vom ODBC- [Treiber-Manager](../../odbc/reference/the-driver-manager.md) auf sechs verschiedene Arten verwendet wird. Das Flag DriverID im Registrierungs Eintrag für eine Datenquelle bestimmt, welcher Treiber in Odbcjt32. dll vom Treiber-Manager verwendet wird. Eine Anwendung übergibt dieses Flag in der Verbindungs Zeichenfolge, die in einem **SQLDriverConnect**-Befehl enthalten ist. Standardmäßig ist das Flag die ID des Microsoft Access-Treibers.  
  
 Die Treiber Setup Datei ändert das Flag "DriverID" beim Setup. Alle Treiber mit Ausnahme des Microsoft Access-Treibers verfügen über eine zugehörige Setup-DLL. Wenn Sie im [Microsoft ODBC-Datenquellen-Administrator](../../odbc/admin/odbc-data-source-administrator.md) für eine Datenquelle auf **Setup** klicken, lädt die ODBC-Installer-DLL (Odbcinst. dll) die Setup-DLL. Die Setup-DLL exportiert die ODBC-Installationsfunktion **SQLConfigDataSource**. Wenn ein Fenster Handle an **SQLConfigDataSource**übergeben wird, zeigt diese Funktion ein Setup Fenster an und ändert das Flag DriverID entsprechend dem Treiber, der auf der Benutzeroberfläche ausgewählt ist.  
  
 Wenn eine Datei Programm gesteuert erstellt wird, wird ein null-Fenster Handle an **SQLConfigDataSource**übergeben, und die Funktion erstellt dynamisch eine Datenquelle, wobei das DriverID-Flag gemäß dem *lpszDriver* -Argument im Funktions aufgerufene geändert wird.  
  
 Odbcjt32. dll implementiert zusätzlich zur Microsoft Jet-API ODBC-Funktionen. Es gibt jedoch keine direkte Zuordnung zwischen ODBC-und Microsoft Jet-Funktionen. Viele Faktoren (z. b. die Cursor Modelle und die SQL-Zuordnung) verhindern eine direkte Korrelation der Funktionen.  
  
 Der ODBC-Treiber befindet sich zwischen der Microsoft Jet-Engine und dem ODBC-Treiber-Manager. Einige ODBC-Funktionen, die von einer Anwendung aufgerufen werden, werden vom Treiber-Manager verarbeitet und nicht an den Treiber übermittelt. Für diese Funktionen sieht Microsoft Jet den Funktions aufrufnie, weil er keine direkte Verbindung mit dem Treiber-Manager hat.
