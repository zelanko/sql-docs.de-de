---
title: Zusammenfassung der Installer DLL-Funktion | Microsoft-Dokumentation
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
ms.openlocfilehash: e6d2a865764a3d802a7e5a5341226d7d1aa855f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68095686"
---
# <a name="installer-dll-function-summary"></a>Installer-DLL – Funktionsübersicht
In der folgenden Tabelle werden die Funktionen in der Installationsprogramm-dll beschrieben. Weitere Informationen zur Syntax und Semantik für die einzelnen Funktionen finden Sie unter [Installations](../../../odbc/reference/syntax/installer-dll-api-reference-function.md)Programm-dll-API-Referenz.  
  
|Aufgabe|Funktionsname|Zweck|  
|----------|-------------------|-------------|  
|Installieren von ODBC|[Sqlconfigdriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|Lädt die Treiber spezifische Setup-DLL.|  
||[Sqlgetinstalleddrivers](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|Gibt eine Liste der installierten Treiber zurück.|  
||[Sqlinstalldriverex](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|Fügt den Systeminformationen einen Treiber hinzu.|  
||[Sqlinstalldrivermanager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|Gibt das Zielverzeichnis für den Treiber-Manager zurück.|  
||[Sqlinstallererror](../../../odbc/reference/syntax/sqlinstallererror-function.md)|Gibt Fehler-oder Statusinformationen für die Installer-Funktionen zurück.|  
||[Sqlinstalltranslatorex](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|Fügt den Systeminformationen einen Konvertierer hinzu.|  
||[Sqlpostinstallererror](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|Ermöglicht es einer Treiber-oder Konvertierungs-Setup Bibliothek, Fehler zu melden.|  
||[Sqlremovedriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|Entfernt einen Treiber aus den Systeminformationen.|  
||[Sqlremovedrivermanager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|Entfernt ODBC-Kernkomponenten aus den Systeminformationen.|  
||[Sqlremovetranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|Entfernt den Übersetzer aus den Systeminformationen.|  
|Konfigurieren von Datenquellen|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|Ruft die Treiber spezifische Setup-DLL auf.|  
||[Sqlkreatedatasource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|Zeigt ein Dialogfeld zum Hinzufügen einer Datenquelle an.|  
||[Sqlgetconfigmode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|Ruft den Konfigurations Modus ab, der angibt, wo der ODBC. ini-Eintrag DSN-Werte in den Systeminformationen aufgeführt werden.|  
||[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|Schreibt einen Wert in die Systeminformationen.|  
||[Sqlgettranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|Zeigt ein Dialogfeld an, in dem ein Translator ausgewählt werden soll.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|Zeigt ein Dialogfeld zum Konfigurieren von Datenquellen und Treibern an.|  
||[Sqllesfiledsn](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Liest Informationen aus Datei-DSNs.|  
||[Sqlremovedefaultdatasource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|Entfernt die Standarddaten Quelle.|  
||[Sqlremovedsnfromini](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|Entfernt eine Datenquelle.|  
||[Sqlsetconfigmode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|Legt den Konfigurations Modus fest, der angibt, wo der ODBC. ini-Eintrag DSN-Werte in den Systeminformationen aufgeführt werden.|  
||[Sqlvaliddsn](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|Überprüft die Länge und die Gültigkeit des Datenquellen namens.|  
||[Sqlschreitedsnder ini](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|Fügt eine Datenquelle hinzu.|  
||[Sqlschreitefiledsn](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|Schreibt Informationen in Datei-DSNs.|  
||[Sqlschreiteprivateprofilestring](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|Ruft einen Wert aus den Systeminformationen ab.|
