---
description: Installer-DLL – Funktionsübersicht
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3666808659abb29a1f5a1eb1e8be62e8cf0507f6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88461232"
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
||[Sqlgetconfigmode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|Ruft den Konfigurations Modus ab, der angibt, wo sich der Odbc.ini Eintrag mit den DSN-Werten in den Systeminformationen befindet.|  
||[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|Schreibt einen Wert in die Systeminformationen.|  
||[Sqlgettranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|Zeigt ein Dialogfeld an, in dem ein Translator ausgewählt werden soll.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|Zeigt ein Dialogfeld zum Konfigurieren von Datenquellen und Treibern an.|  
||[Sqllesfiledsn](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Liest Informationen aus Datei-DSNs.|  
||[Sqlremovedefaultdatasource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|Entfernt die Standarddaten Quelle.|  
||[Sqlremovedsnfromini](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|Entfernt eine Datenquelle.|  
||[Sqlsetconfigmode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|Legt den Konfigurations Modus fest, der angibt, wo der Odbc.ini Eintrag mit DSN-Werten in den Systeminformationen steht.|  
||[Sqlvaliddsn](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|Überprüft die Länge und die Gültigkeit des Datenquellen namens.|  
||[Sqlschreitedsnder ini](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|Fügt eine Datenquelle hinzu.|  
||[Sqlschreitefiledsn](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|Schreibt Informationen in Datei-DSNs.|  
||[Sqlschreiteprivateprofilestring](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|Ruft einen Wert aus den Systeminformationen ab.|
