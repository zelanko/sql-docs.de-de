---
title: Desktopdatenbanktreiberarchitektur | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae6fb72bb3ed0a9bca1571eb572bbfbd20fe9995
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288740"
---
# <a name="desktop-database-drivers-architecture"></a>Architektur der Desktop-Datenbanktreiber
Diese Treiber sind für die Verwendung unter Microsoft Windows 95 oder höher oder Windows NT 4.0 und Windows 2000 konzipiert. Unter Windows 95 oder höher werden nur 32-Bit-Anwendungen unterstützt. 16-Bit- und 32-Bit-Anwendungen werden unter Windows NT 4.0 und Windows 2000 unterstützt.  
  
> [!NOTE]  
>  Informationen zur ODBC-Version, die mit diesen Treibern verwendet werden soll, finden Sie in der ODBC-Programmierer-Referenz sowie in den aktuellen und aktuellen Versionshinweisen des *ODBC-Programmierers.* Mit Ausnahme der genannten Bereiche entsprechen diese Treiber der *ODBC-Programmiererreferenz*.  
  
 Die ODBC Desktop-Datenbanktreiber enthalten 32-Bit-Treiber für Microsoft Access, dBASE, Microsoft Excel, Paradox und Text. Keine 16-Bit-Treiber sind enthalten. (Ein Treiber für Microsoft FoxPro ist separat verfügbar.)  
  
 Die Anwendungs-/Treiberarchitektur unter Windows 95 oder höher lautet:  
  
 ![App&#47;Treiberarchitektur: Windows 95 und höher](../../odbc/microsoft/media/odbcjetarch1.gif "ODBCJetArch1")  
  
 Die Verwendung dieser Treiber durch 16-Bit-Anwendungen unter Windows 95 wird nicht unterstützt.  
  
 Die Anwendungs-/Treiberarchitektur unter Windows NT 4.0 und Windows 2000 lautet:  
  
 ![App-treiberarchitektur&#47;: NT 4.0 und Windows 2000](../../odbc/microsoft/media/odbcjetarch2.gif "ODBCJetArch2")  
  
 Die Desktopdatenbanktreiber sind zweistufige Treiber. In einer Konfiguration mit zwei Ebenen führt der Treiber den Prozess des Analysierens, Validierens, Optimierens und Ausführens der Abfrage nicht durch. Stattdessen führt Microsoft Jet diese Aufgaben aus. Es verarbeitet ODBC-API-Aufrufe und fungiert als SQL-Engine. Microsoft Jet ist zu einem integralen, untrennbaren Bestandteil der Treiber geworden: Es wird mit den Treibern ausgeliefert und befindet sich bei den Treibern, auch wenn keine andere Anwendung auf dem Computer es verwendet.  
  
 Die Desktop-Datenbanktreiber bestehen aus sechs verschiedenen Treibern - oder genauer gesagt aus einer Treiberdatei (Odbcjt32.dll), die der ODBC [Driver Manager](../../odbc/reference/the-driver-manager.md) auf sechs verschiedene Arten verwendet. Das DRIVERID-Flag im Registrierungseintrag für eine Datenquelle bestimmt, welchen Treiber in Odbcjt32.dll der Treiber-Manager verwendet. Eine Anwendung übergibt dieses Flag in der Verbindungszeichenfolge, die in einem Aufruf von **SQLDriverConnect**enthalten ist. Standardmäßig ist das Flag die ID des Microsoft Access-Treibers.  
  
 Die Treiber-Setupdatei ändert das DRIVERID-Flag zum Zeitpunkt der Einrichtung. Alle Treiber außer dem Microsoft Access-Treiber verfügen über eine zugeordnete Setup-DLL. Wenn Sie im [Microsoft ODBC-Datenquellenadministrator](../../odbc/admin/odbc-data-source-administrator.md) für eine Datenquelle auf **Setup** klicken, lädt die ODBC-Installations-DLL (Odbcinst.dll) die Setup-DLL. Die Setup-DLL exportiert die ODBC-Installationsfunktion **SQLConfigDataSource**. Wenn ein Fensterhandle an **SQLConfigDataSource**übergeben wird, zeigt diese Funktion ein Setupfenster an und ändert das DRIVERID-Flag entsprechend dem treibern, der von der Benutzeroberfläche ausgewählt wurde.  
  
 Wenn eine Datei programmgesteuert erstellt wird, wird ein NULL-Fensterhandle an **SQLConfigDataSource**übergeben, und die Funktion erstellt dynamisch eine Datenquelle, wodurch das DRIVERID-Flag entsprechend dem *Argument lpszDriver* im Funktionsaufruf geändert wird.  
  
 Odbcjt32.dll implementiert ODBC-Funktionen zusätzlich zur Microsoft Jet-API. Es gibt jedoch keine direkte Zuordnung zwischen ODBC- und Microsoft Jet-Funktionen. Viele Faktoren, wie z. B. die Cursormodelle und die SQL-Zuordnung, verhindern eine direkte Korrelation der Funktionen.  
  
 Der ODBC-Treiber befindet sich zwischen dem Microsoft Jet-Modul und dem ODBC-Treiber-Manager. Einige ODBC-Funktionen, die von einer Anwendung aufgerufen werden, werden vom Treiber-Manager verarbeitet und nicht an den Treiber übergeben. Für diese Funktionen sieht Microsoft Jet den Funktionsaufruf nie, da er keine direkte Verbindung zum Treiber-Manager hat.
