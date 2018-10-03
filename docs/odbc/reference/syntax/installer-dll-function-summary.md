---
title: Installationsprogramm-DLL – Funktionszusammenfassung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], installer DLL functions
- installer DLL [ODBC]
ms.assetid: 666c09d3-1e10-4d89-9b42-eda2957a87f0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ecb486f51caa97c715d54885c34575a60bfdfb83
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47723328"
---
# <a name="installer-dll-function-summary"></a>Installer-DLL – Funktionsübersicht
Die folgende Tabelle beschreibt die Funktionen in die Installationsprogramm-DLL. Weitere Informationen zur Syntax und Semantik für die einzelnen Funktionen finden Sie unter [Installationsprogramm-DLL-API-Referenz](../../../odbc/reference/syntax/installer-dll-api-reference-function.md).  
  
|Task|Funktionsname|Zweck|  
|----------|-------------------|-------------|  
|Installieren von ODBC|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|Lädt die Setup-DLL für Treiber-spezifische.|  
||[SQLGetInstalledDrivers](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|Gibt eine Liste der installierten Treiber.|  
||[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|Fügt einen Treiber in der Systeminformationen.|  
||[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|Gibt das Zielverzeichnis für den Treiber-Manager zurück.|  
||[SQLInstallerError](../../../odbc/reference/syntax/sqlinstallererror-function.md)|Gibt Informationen über Fehler oder Status die Installer-Funktionen zurück.|  
||[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|Fügt einen Übersetzer die Systeminformationen hinzu.|  
||[SQLPostInstallerError](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|Ermöglicht eine Treiber oder Übersetzer-Setup-Bibliothek, um Fehler zu melden.|  
||[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|Entfernt einen Treiber aus den Systeminformationen.|  
||[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|Entfernt ODBC-Komponenten, aus der Systeminformationen.|  
||[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|Entfernt das Konvertierungsprogramm aus der Systeminformationen.|  
|Konfigurieren von Datenquellen|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|Ruft den Setup-DLL für Treiber-spezifische.|  
||[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|Zeigt ein Dialogfeld zum Hinzufügen einer Datenquelle.|  
||[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|Ruft den Konfigurationsmodus zu wechseln, der angibt, in dem der Odbc.ini Eintrag Auflisten von DSN-Werte in den Systeminformationen ab.|  
||[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|Schreibt einen Wert in der Systeminformationen.|  
||[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|Zeigt ein Dialogfeld zum Auswählen von eines Übersetzers.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|Zeigt ein Dialogfeld zum Konfigurieren von Datenquellen und Treiber.|  
||[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Liest Informationen aus der Datei-DSNs.|  
||[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|Die Standarddatenquelle wird entfernt.|  
||[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|Entfernt eine Datenquelle an.|  
||[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|Legt den Konfigurationsmodus zu wechseln, der angibt, in dem der Odbc.ini Eintrag Auflisten von DSN-Werte in den Systeminformationen fest.|  
||[SQLValidDSN](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|Überprüft die Länge und die Gültigkeit der Namen der Datenquelle.|  
||[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|Fügt eine Datenquelle an.|  
||[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|Schreibt Informationen in dem Datei-DSNs.|  
||[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|Ruft einen Wert aus der Systeminformationen.|
