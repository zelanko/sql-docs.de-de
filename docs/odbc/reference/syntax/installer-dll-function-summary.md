---
title: Zusammenfassung der Installationsdatei-DLL-Funktion | Microsoft Docs
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
ms.openlocfilehash: ddaf20334a84833433961a49e17724d354945c5a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298770"
---
# <a name="installer-dll-function-summary"></a>Installer-DLL – Funktionsübersicht
In der folgenden Tabelle werden die Funktionen in der Installations-DLL beschrieben. Weitere Informationen zur Syntax und Semantik für jede Funktion finden Sie unter [Installer-DLL-API-Referenz](../../../odbc/reference/syntax/installer-dll-api-reference-function.md).  
  
|Aufgabe|Funktionsname|Zweck|  
|----------|-------------------|-------------|  
|Installieren von ODBC|[SQLConfigDriver](../../../odbc/reference/syntax/sqlconfigdriver-function.md)|Lädt die treiberspezifische Setup-DLL.|  
||[SQLGetInstalledDrivers](../../../odbc/reference/syntax/sqlgetinstalleddrivers-function.md)|Gibt eine Liste der installierten Treiber zurück.|  
||[SQLInstallDriverEx](../../../odbc/reference/syntax/sqlinstalldriverex-function.md)|Fügt den Systeminformationen einen Treiber hinzu.|  
||[SQLInstallDriverManager](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|Gibt das Zielverzeichnis für den Treiber-Manager zurück.|  
||[SQLInstallerError](../../../odbc/reference/syntax/sqlinstallererror-function.md)|Gibt Fehler- oder Statusinformationen für die Installationsfunktionen zurück.|  
||[SQLInstallTranslatorEx](../../../odbc/reference/syntax/sqlinstalltranslatorex-function.md)|Fügt den Systeminformationen einen Übersetzer hinzu.|  
||[SQLPostInstallerError](../../../odbc/reference/syntax/sqlpostinstallererror-function.md)|Ermöglicht es einer Treiber- oder Übersetzer-Setupbibliothek, Fehler zu melden.|  
||[SQLRemoveDriver](../../../odbc/reference/syntax/sqlremovedriver-function.md)|Entfernt einen Treiber aus den Systeminformationen.|  
||[SQLRemoveDriverManager](../../../odbc/reference/syntax/sqlremovedrivermanager-function.md)|Entfernt ODBC-Kernkomponenten aus den Systeminformationen.|  
||[SQLRemoveTranslator](../../../odbc/reference/syntax/sqlremovetranslator-function.md)|Entfernt den Übersetzer aus den Systeminformationen.|  
|Konfigurieren von Datenquellen|[SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md)|Ruft die treiberspezifische Setup-DLL auf.|  
||[SQLCreateDataSource](../../../odbc/reference/syntax/sqlcreatedatasource-function.md)|Zeigt ein Dialogfeld an, um eine Datenquelle hinzuzufügen.|  
||[SQLGetConfigMode](../../../odbc/reference/syntax/sqlgetconfigmode-function.md)|Ruft den Konfigurationsmodus ab, der angibt, wo sich die DSN-Werte von Odbc.ini in den Systeminformationen befinden.|  
||[SQLGetPrivateProfileString](../../../odbc/reference/syntax/sqlgetprivateprofilestring-function.md)|Schreibt einen Wert in die Systeminformationen.|  
||[SQLGetTranslator](../../../odbc/reference/syntax/sqlgettranslator-function.md)|Zeigt ein Dialogfeld an, um einen Übersetzer auszuwählen.|  
||[SQLManageDataSources](../../../odbc/reference/syntax/sqlmanagedatasources.md)|Zeigt ein Dialogfeld zum Konfigurieren von Datenquellen und Treibern an.|  
||[SQLReadFileDSN](../../../odbc/reference/syntax/sqlreadfiledsn-function.md)|Liest Informationen aus Datei-DSNs.|  
||[SQLRemoveDefaultDataSource](../../../odbc/reference/syntax/sqlremovedefaultdatasource-function.md)|Entfernt die Standarddatenquelle.|  
||[SQLRemoveDSNFromIni](../../../odbc/reference/syntax/sqlremovedsnfromini-function.md)|Entfernt eine Datenquelle.|  
||[SQLSetConfigMode](../../../odbc/reference/syntax/sqlsetconfigmode-function.md)|Legt den Konfigurationsmodus fest, der angibt, wo sich die DSN-Werte des Odbc.ini-Eintrags in den Systeminformationen befinden.|  
||[SQLValidDSN](../../../odbc/reference/syntax/sqlvaliddsn-function.md)|Überprüft die Länge und Gültigkeit des Datenquellennamens.|  
||[SQLWriteDSNToIni](../../../odbc/reference/syntax/sqlwritedsntoini-function.md)|Fügt eine Datenquelle hinzu.|  
||[SQLWriteFileDSN](../../../odbc/reference/syntax/sqlwritefiledsn-function.md)|Schreibt Informationen in die Datei-DSNs.|  
||[SQLWritePrivateProfileString](../../../odbc/reference/syntax/sqlwriteprivateprofilestring-function.md)|Ruft einen Wert aus den Systeminformationen ab.|
