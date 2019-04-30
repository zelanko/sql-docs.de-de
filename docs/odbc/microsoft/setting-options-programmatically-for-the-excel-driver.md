---
title: Festlegen von Optionen für Excel-Treibers programmgesteuert | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], setting options programmatically
ms.assetid: b5ee3636-4591-427a-a65a-a2d5926fcc1a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 271f61247b6083abd31657fe319bce234bc16f50
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63285018"
---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Programmgesteuertes Festlegen von Optionen für die Excel-Treiber

|Option|Description|Methode|  
|------------|-----------------|------------|  
|Datenquellenname|Ein Name, der die Datenquelle, z. B. Gehaltsabrechnungen oder Mitarbeiter identifiziert.|Um diese Option dynamisch festzulegen, verwenden die **DSN** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Datenbank|Eine Microsoft Access-Datenquelle kann ohne auswählen oder Erstellen einer Datenbank eingerichtet werden. Wenn beim Setup keine Datenbank angegeben ist, wird der Benutzer aufgefordert werden, um eine Datei auszuwählen, Herstellen der Verbindung mit der Datenquelle.|Um diese Option dynamisch festzulegen, verwenden die **DBQ** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Description|Eine optionale Beschreibung der Daten in der Datenquelle; z. B. "Hire Date, Gehaltsverlauf und aktuelle Überprüfung aller Mitarbeiter."|Um diese Option dynamisch festzulegen, verwenden die **Beschreibung** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Verzeichnis|Zeigt das aktuell ausgewählte Verzeichnis.<br /><br /> Für Microsoft Excel 3.0/4.0-Dateien, die Pfad-Anzeige wird mit der Bezeichnung "Directory", während Sie sich für Microsoft Excel 5.0, 7.0 oder 97-Dateien, die Pfad-Anzeige wird mit der Bezeichnung "Workbook".|Um diese Option dynamisch festzulegen, verwenden die **Wert** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Schreibgeschützt|Legt die Datenbank als schreibgeschützt fest.|Um diese Option dynamisch festzulegen, verwenden die **READONLY** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Zu scannende Zeilen|Die Anzahl der Zeilen zu scannen, um den Datentyp jeder Spalte zu ermitteln. Der Datentyp wird bestimmt, erhält die maximale Anzahl der Arten von Daten, die gefunden. Wenn Daten, die den Datentyp für die Spalte ermittelten nicht übereinstimmen gefunden werden, wird der Datentyp als ein NULL-Wert zurückgegeben.<br /><br /> Microsoft Excel-Treiber können Sie eine Zahl von 1 bis 16 für die Zeilen zu scannen eingeben. Der Standardwert ist 8; Wenn es auf 0 festgelegt ist, werden alle Zeilen überprüft. (Eine Zahl außerhalb der Grenzwert wird einen Fehler zurückgegeben.)|Um diese Option dynamisch festzulegen, verwenden die **MAXSCANROWS** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Wählen Sie Verzeichnis|Zeigt ein Dialogfeld, in dem Sie ein Verzeichnis mit den Dateien, die Sie zugreifen möchten auswählen können.<br /><br /> Wenn Sie ein Datenverzeichnis für die Quelle (für alle mit Ausnahme von Microsoft Access-Treiber) zu definieren, geben Sie das Verzeichnis, in denen die am häufigsten verwendeten Dateien gespeichert sind. Der ODBC-Treiber wird dieses Verzeichnis als Standardverzeichnis verwendet. Kopieren Sie andere Dateien in dieses Verzeichnis, wenn sie häufig verwendet werden. Alternativ können Sie den Dateinamen in einer SELECT-Anweisung mit den Namen des Verzeichnisses qualifizieren:<br /><br /> SELECT \* FROM C:\MYDIR\EMP<br /><br /> Sie können ein neues Standardverzeichnis angeben, mit der **SQLSetConnectOption** -Funktion mit der Option SQL_CURRENT_QUALIFIER.<br /><br /> Für Microsoft Excel, 3.0 oder 4.0-Dateien die Pfad-Anzeige wird mit der Bezeichnung "Directory", und die Schaltfläche "Auswahl Pfad" wird mit der Bezeichnung "Verzeichnis auswählen". Für Microsoft Excel 5.0, 7.0 oder 97-Dateien die Pfad-Anzeige wird mit der Bezeichnung "Arbeitsmappe", und die Schaltfläche "Auswahl Pfad" wird mit der Bezeichnung "Arbeitsmappe auswählen". Wenn Sie ein Datenverzeichnis für die Datenquelle zu definieren, geben Sie dem Verzeichnis, in dem Ihre am häufigsten verwendeten Microsoft Excel-Dateien für Microsoft Excel 3.0/4.0 befinden, oder das Verzeichnis, in dem die Datei für Microsoft Excel 5.0, 7.0 oder 97 befindet. **Verwenden Sie die aktuellen Verzeichnis** für Microsoft Excel 5.0, 7.0 und 97 deaktiviert ist.|Um diese Option dynamisch festzulegen, verwenden die **Wert** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|
