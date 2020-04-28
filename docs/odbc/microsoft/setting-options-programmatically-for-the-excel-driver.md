---
title: Programm gesteuertes Festlegen von Optionen für den Excel-Treiber | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1fcd5542e4beee1f7c7a30d5e0ee9f2815a3f0b6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300770"
---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Programmgesteuertes Festlegen von Optionen für die Excel-Treiber

|Option|BESCHREIBUNG|Methode|  
|------------|-----------------|------------|  
|Datenquellenname|Ein Name, der die Datenquelle identifiziert, z. b. Gehaltsabrechnung oder Personal.|Um diese Option dynamisch festzulegen, verwenden Sie das **DSN** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Datenbank|Eine Microsoft Access-Datenquelle kann eingerichtet werden, ohne dass eine Datenbank ausgewählt oder erstellt wird. Wenn beim Setup keine Datenbank bereitgestellt wird, wird der Benutzer beim Herstellen einer Verbindung mit der Datenquelle aufgefordert, eine Datenbankdatei auszuwählen.|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort **DBQ** in einem [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)-aufrufsbefehl.|  
|BESCHREIBUNG|Eine optionale Beschreibung der Daten in der Datenquelle. Beispiel: "Einstellen von Datum, Gehalts Verlauf und aktueller Review aller Mitarbeiter".|Um diese Option dynamisch festzulegen, verwenden Sie das **Description** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Verzeichnis|Zeigt das aktuell ausgewählte Verzeichnis an.<br /><br /> Bei Microsoft Excel 3.0/4.0-Dateien lautet die Pfad Anzeige "Directory", während für Microsoft Excel 5,0-, 7,0-oder 97-Dateien die Pfad Anzeige mit der Bezeichnung "Arbeitsmappe" gekennzeichnet ist.|Um diese Option dynamisch festzulegen, verwenden Sie das **DefaultDir** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Nur Leseberechtigung|Legt fest, dass die Datenbank schreibgeschützt ist.|Um diese Option dynamisch festzulegen, verwenden Sie **das Schlüsselwort** "schreibgeschützt" in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Zu überprüfenden Zeilen|Die Anzahl der zu überprüfenden Zeilen, um den Datentyp jeder Spalte zu bestimmen. Der-Datentyp wird anhand der maximalen Anzahl von gefundenen Daten bestimmt. Wenn Daten gefunden werden, die nicht mit dem für die Spalte erraten Datentyp identisch sind, wird der Datentyp als NULL-Wert zurückgegeben.<br /><br /> Für den Microsoft Excel-Treiber können Sie eine Zahl zwischen 1 und 16 für die zu überprüfenden Zeilen eingeben. Der Standardwert ist 8; Wenn der Wert auf 0 festgelegt ist, werden alle Zeilen gescannt. (Eine Zahl außerhalb des Limits gibt einen Fehler zurück.)|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort **MaxScanRows** in einem [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)-aufrufsbefehl.|  
|Verzeichnis auswählen|Zeigt ein Dialogfeld an, in dem Sie ein Verzeichnis mit den Dateien auswählen können, auf die Sie zugreifen möchten.<br /><br /> Wenn Sie ein Datenquellen Verzeichnis definieren (für alle Treiber außer Microsoft Access), geben Sie das Verzeichnis an, in dem sich die am häufigsten verwendeten Dateien befinden. Der ODBC-Treiber verwendet dieses Verzeichnis als Standardverzeichnis. Kopieren Sie andere Dateien in dieses Verzeichnis, wenn Sie häufig verwendet werden. Alternativ können Sie Dateinamen in einer SELECT-Anweisung mit dem Verzeichnisnamen qualifizieren:<br /><br /> Select \* from c:\mydir\emp<br /><br /> Oder Sie können ein neues Standardverzeichnis angeben, indem Sie die **SQLSetConnectOption** -Funktion mit der SQL_CURRENT_QUALIFIER-Option verwenden.<br /><br /> Für Microsoft Excel 3,0-oder 4,0-Dateien wird die Pfad Anzeige mit der Bezeichnung "Verzeichnis" und die Schaltfläche für die Pfad Auswahl als "Verzeichnis auswählen" bezeichnet. Bei Microsoft Excel 5,0-, 7,0-oder 97-Dateien hat die Pfad Anzeige die Bezeichnung "Arbeitsmappe", und die Schaltfläche "Pfad Auswahl" hat die Bezeichnung "Arbeitsmappe auswählen". Wenn Sie ein Datenquellen Verzeichnis definieren, geben Sie das Verzeichnis an, in dem sich Ihre am häufigsten verwendeten Microsoft Excel-Dateien für Microsoft Excel 3.0/4.0 befinden, oder das Verzeichnis, in dem sich die Arbeitsmappendatei für Microsoft Excel 5,0, 7,0 oder 97 befindet. **Aktuelles Verzeichnis verwenden** ist für Microsoft Excel 5,0, 7,0 und 97 deaktiviert.|Um diese Option dynamisch festzulegen, verwenden Sie das **DefaultDir** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|
