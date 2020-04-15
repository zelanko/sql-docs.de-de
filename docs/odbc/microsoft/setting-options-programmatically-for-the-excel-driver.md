---
title: Programmgesteuertes Festlegen von Optionen für den Excel-Treiber | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300770"
---
# <a name="setting-options-programmatically-for-the-excel-driver"></a>Programmgesteuertes Festlegen von Optionen für die Excel-Treiber

|Option|Beschreibung|Methode|  
|------------|-----------------|------------|  
|Datenquellenname|Ein Name, der die Datenquelle identifiziert, z. B. Lohn- oder Personalabrechnung.|Um diese Option dynamisch festzulegen, verwenden Sie das **DSN-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Datenbank|Eine Microsoft Access-Datenquelle kann eingerichtet werden, ohne eine Datenbank auszuwählen oder zu erstellen. Wenn beim Setup keine Datenbank bereitgestellt wird, wird der Benutzer beim Herstellen einer Verbindung mit der Datenquelle aufgefordert, eine Datenbankdatei auszuwählen.|Um diese Option dynamisch festzulegen, verwenden Sie das **DBQ-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Beschreibung|Eine optionale Beschreibung der Daten in der Datenquelle; z. B. "Mietdatum, Gehaltshistorie und aktuelle Überprüfung aller Mitarbeiter."|Um diese Option dynamisch **DESCRIPTION** festzulegen, verwenden Sie das DESCRIPTION-Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Verzeichnis|Zeigt das aktuell ausgewählte Verzeichnis an.<br /><br /> Bei Microsoft Excel 3.0/4.0-Dateien wird die Pfadanzeige mit "Verzeichnis" beschriftet, während für Microsoft Excel 5.0-, 7.0- oder 97-Dateien die Pfadanzeige mit "Arbeitsmappe" beschriftet ist.|Um diese Option dynamisch festzulegen, verwenden Sie das **DEFAULTDIR-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Nur Leseberechtigung|Legt die Datenbank als schreibgeschützt fest.|Um diese Option dynamisch festzulegen, verwenden Sie das **READONLY-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Zeilen zum Scannen|Die Anzahl der zu scannenden Zeilen, um den Datentyp jeder Spalte zu bestimmen. Der Datentyp wird anhand der maximalen Anzahl der gefundenen Datentypen bestimmt. Wenn Daten gefunden werden, die nicht mit dem für die Spalte erratenen Datentyp übereinstimmen, wird der Datentyp als NULL-Wert zurückgegeben.<br /><br /> Für den Microsoft Excel-Treiber können Sie eine Zahl von 1 bis 16 für die zu scannenden Zeilen eingeben. Der Wert ist standardmäßig 8; Wenn sie auf 0 gesetzt ist, werden alle Zeilen gescannt. (Eine Zahl außerhalb des Limits gibt einen Fehler zurück.)|Um diese Option dynamisch festzulegen, verwenden Sie das **Schlüsselwort MAXSCANROWS** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|  
|Verzeichnis auswählen|Zeigt ein Dialogfeld an, in dem Sie ein Verzeichnis auswählen können, das die Dateien enthält, auf die Sie zugreifen möchten.<br /><br /> Geben Sie beim Definieren eines Datenquellenverzeichnisses (für alle Treiber außer Microsoft Access) das Verzeichnis an, in dem sich die am häufigsten verwendeten Dateien befinden. Der ODBC-Treiber verwendet dieses Verzeichnis als Standardverzeichnis. Kopieren Sie andere Dateien in dieses Verzeichnis, wenn sie häufig verwendet werden. Alternativ können Sie Dateinamen in einer SELECT-Anweisung mit dem Verzeichnisnamen qualifizieren:<br /><br /> SELECT \* VON C:'MYDIR'EMP<br /><br /> Sie können auch ein neues Standardverzeichnis angeben, indem Sie die **SQLSetConnectOption-Funktion** mit der Option SQL_CURRENT_QUALIFIER verwenden.<br /><br /> Bei Microsoft Excel 3.0- oder 4.0-Dateien wird die Pfadanzeige mit "Verzeichnis" und die Pfadauswahlschaltfläche mit "Verzeichnis auswählen" beschriftet. Bei Microsoft Excel 5.0-, 7.0- oder 97-Dateien wird die Pfadanzeige mit "Arbeitsmappe" und die Schaltfläche "Arbeitsmappe auswählen" mit der Pfadauswahl beschriftet. Geben Sie beim Definieren eines Datenquellenverzeichnisses das Verzeichnis an, in dem sich die am häufigsten verwendeten Microsoft Excel-Dateien für Microsoft Excel 3.0/4.0 befinden, oder das Verzeichnis, in dem sich die Arbeitsmappendatei für Microsoft Excel 5.0, 7.0 oder 97 befindet. **Aktuelles Verzeichnis verwenden** ist für Microsoft Excel 5.0, 7.0 und 97 deaktiviert.|Um diese Option dynamisch festzulegen, verwenden Sie das **DEFAULTDIR-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).|
