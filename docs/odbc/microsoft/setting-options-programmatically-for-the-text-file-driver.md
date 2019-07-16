---
title: Festlegen von Optionen für die Textdateitreiber programmgesteuert | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: cbde2ca1-5d4e-4444-a371-a72f3ac4d92a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e1a28e5c7ccf3c701e5f97440cd97ed843ab53dd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063504"
---
# <a name="setting-options-programmatically-for-the-text-file-driver"></a>Programmgesteuertes Festlegen von Optionen für die Textdateitreiber

|Option|Beschreibung|Methode|  
|------------|-----------------|------------|  
|Datenquellenname|Ein Name, der die Datenquelle, z. B. Gehaltsabrechnungen oder Mitarbeiter identifiziert.|Um diese Option dynamisch festzulegen, verwenden die **DSN** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Definieren von Format|Zeigt die **-Text-Format definieren** Dialogfeld und ermöglicht Ihnen die Angabe des Schemas für einzelne Tabellen im Data Source-Verzeichnis.|Diese Option kann nicht dynamisch festgelegt werden, durch einen Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Beschreibung|Eine optionale Beschreibung der Daten in der Datenquelle; z. B. "Hire Date, Gehaltsverlauf und aktuelle Überprüfung aller Mitarbeiter."|Um diese Option dynamisch festzulegen, verwenden die **Beschreibung** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Verzeichnis|Wählt die entsprechenden Verzeichnis.|Um diese Option dynamisch festzulegen, verwenden die **Wert** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Liste der Erweiterungen|Listet die Dateinamenerweiterungen der Text-Dateien für die Datenquelle an. Wenn der Text-Treiber verwendet wird, wird eine Datei ohne Erweiterung erstellt, wenn die CREATE TABLE-Anweisung mit einem Namen ausgeführt wird, die keine Erweiterung besitzt. Andere Treiber erstellen Sie eine Datei mit einer standarderweiterung, wenn keine Erweiterung angegeben wird. Zum Erstellen einer Datei mit der Erweiterung TXT, muss die Erweiterung im Namen enthalten sein. Zum Anzeigen von Dateien ohne Erweiterungen in der **-Text-Format definieren** im Dialogfeld "*." die Liste der Erweiterungen hinzugefügt werden muss.|Um diese Option dynamisch festzulegen, verwenden die **ERWEITERUNGEN** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Schreibgeschützt|Legt die Datenbank als schreibgeschützt fest.|Um diese Option dynamisch festzulegen, verwenden die **READONLY** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Zu scannende Zeilen|Die Anzahl der Zeilen zu scannen, um den Datentyp jeder Spalte zu ermitteln. Der Datentyp wird bestimmt, erhält die maximale Anzahl der Arten von Daten, die gefunden. Wenn Daten, die den Datentyp für die Spalte ermittelten nicht übereinstimmen gefunden werden, wird der Datentyp als ein NULL-Wert zurückgegeben.<br /><br /> Für den Text-Treiber können Sie eine Zahl zwischen 1 und 32767 für die Anzahl der zu durchsuchenden Zeilen eingeben; Allerdings wird standardmäßig der Wert immer auf 25. (Eine Zahl außerhalb der Grenzwert wird einen Fehler zurückgegeben.)|Um diese Option dynamisch festzulegen, verwenden die **MAXSCANROWS** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Wählen Sie Verzeichnis|Zeigt ein Dialogfeld, in dem Sie ein Verzeichnis mit den Dateien, die Sie zugreifen möchten auswählen können.<br /><br /> Beim Definieren eines Quellverzeichnisses Daten geben Sie das Verzeichnis, in dem Ihre am häufigsten Dateien verwendeten, befinden. Der ODBC-Treiber wird dieses Verzeichnis als Standardverzeichnis verwendet. Kopieren Sie andere Dateien in dieses Verzeichnis, wenn sie häufig verwendet werden. Alternativ können Sie den Dateinamen in einer SELECT-Anweisung mit den Namen des Verzeichnisses qualifizieren: `SELECT * FROM C:\MYDIR\EMP`<br /><br /> Sie können ein neues Standardverzeichnis angeben, mit der **SQLSetConnectOption** -Funktion mit der Option SQL_CURRENT_QUALIFIER.|Um diese Option dynamisch festzulegen, verwenden die **Wert** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|
