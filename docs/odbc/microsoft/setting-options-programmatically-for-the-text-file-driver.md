---
title: Programmgesteuertes Festlegen von Optionen für den Textdateitreiber | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e19c3b49479047bc92a7b6f72359d4951d8df16e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300750"
---
# <a name="setting-options-programmatically-for-the-text-file-driver"></a>Programmgesteuertes Festlegen von Optionen für die Textdateitreiber

|Option|Beschreibung|Methode|  
|------------|-----------------|------------|  
|Datenquellenname|Ein Name, der die Datenquelle identifiziert, z. B. Lohn- oder Personalabrechnung.|Um diese Option dynamisch festzulegen, verwenden Sie das **DSN-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Format definieren|Zeigt das Dialogfeld **Textformat definieren** an und ermöglicht es Ihnen, das Schema für einzelne Tabellen im Datenquellenverzeichnis anzugeben.|Diese Option kann nicht dynamisch durch einen Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)festgelegt werden.|  
|Beschreibung|Eine optionale Beschreibung der Daten in der Datenquelle; z. B. "Mietdatum, Gehaltshistorie und aktuelle Überprüfung aller Mitarbeiter."|Um diese Option dynamisch **DESCRIPTION** festzulegen, verwenden Sie das DESCRIPTION-Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Verzeichnis|Wählt das Zielverzeichnis aus.|Um diese Option dynamisch festzulegen, verwenden Sie das **DEFAULTDIR-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Erweiterungsliste|Listet die Dateinamenerweiterungen der Textdateien in der Datenquelle auf. Wenn der Texttreiber verwendet wird, wird eine Datei ohne Erweiterung erstellt, wenn die CREATE TABLE-Anweisung mit einem Namen ausgeführt wird, der keine Erweiterung hat. Andere Treiber erstellen eine Datei mit einer Standarderweiterung, wenn keine Erweiterung bereitgestellt wird. Um eine Datei mit der Erweiterung .txt zu erstellen, muss die Erweiterung im Namen enthalten sein. So zeigen Sie Dateien ohne Erweiterungen im Dialogfeld **Textformat definieren** ,*" an. der Erweiterungsliste hinzugefügt werden.|Um diese Option dynamisch festzulegen, verwenden Sie das **Schlüsselwort EXTENSIONS** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Nur Leseberechtigung|Legt die Datenbank als schreibgeschützt fest.|Um diese Option dynamisch festzulegen, verwenden Sie das **READONLY-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Zeilen zum Scannen|Die Anzahl der zu scannenden Zeilen, um den Datentyp jeder Spalte zu bestimmen. Der Datentyp wird anhand der maximalen Anzahl der gefundenen Datentypen bestimmt. Wenn Daten gefunden werden, die nicht mit dem für die Spalte erratenen Datentyp übereinstimmen, wird der Datentyp als NULL-Wert zurückgegeben.<br /><br /> Für den Texttreiber können Sie eine Zahl von 1 bis 32767 für die Anzahl der zu scannenden Zeilen eingeben. Der Wert wird jedoch immer standardmäßig auf 25 wertsein. (Eine Zahl außerhalb des Limits gibt einen Fehler zurück.)|Um diese Option dynamisch festzulegen, verwenden Sie das **Schlüsselwort MAXSCANROWS** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Verzeichnis auswählen|Zeigt ein Dialogfeld an, in dem Sie ein Verzeichnis auswählen können, das die Dateien enthält, auf die Sie zugreifen möchten.<br /><br /> Geben Sie beim Definieren eines Datenquellenverzeichnisses das Verzeichnis an, in dem sich die am häufigsten verwendeten Dateien befinden. Der ODBC-Treiber verwendet dieses Verzeichnis als Standardverzeichnis. Kopieren Sie andere Dateien in dieses Verzeichnis, wenn sie häufig verwendet werden. Alternativ können Sie Dateinamen in einer SELECT-Anweisung mit dem Verzeichnisnamen qualifizieren:`SELECT * FROM C:\MYDIR\EMP`<br /><br /> Sie können auch ein neues Standardverzeichnis angeben, indem Sie die **SQLSetConnectOption-Funktion** mit der Option SQL_CURRENT_QUALIFIER verwenden.|Um diese Option dynamisch festzulegen, verwenden Sie das **DEFAULTDIR-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|
