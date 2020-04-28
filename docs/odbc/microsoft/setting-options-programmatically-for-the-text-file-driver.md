---
title: Programm gesteuertes Festlegen von Optionen für den Text Datei Treiber | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300750"
---
# <a name="setting-options-programmatically-for-the-text-file-driver"></a>Programmgesteuertes Festlegen von Optionen für die Textdateitreiber

|Option|BESCHREIBUNG|Methode|  
|------------|-----------------|------------|  
|Datenquellenname|Ein Name, der die Datenquelle identifiziert, z. b. Gehaltsabrechnung oder Personal.|Um diese Option dynamisch festzulegen, verwenden Sie das **DSN** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Format definieren|Zeigt das Dialogfeld **Text Format definieren** an und ermöglicht es Ihnen, das Schema für einzelne Tabellen im Datenquellen Verzeichnis anzugeben.|Diese Option kann nicht dynamisch durch einen-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)festgelegt werden.|  
|BESCHREIBUNG|Eine optionale Beschreibung der Daten in der Datenquelle. Beispiel: "Einstellen von Datum, Gehalts Verlauf und aktueller Review aller Mitarbeiter".|Um diese Option dynamisch festzulegen, verwenden Sie das **Description** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Verzeichnis|Wählt das Zielverzeichnis aus.|Um diese Option dynamisch festzulegen, verwenden Sie das **DefaultDir** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Liste der Erweiterungen|Listet die Dateinamen Erweiterungen der Textdateien in der Datenquelle auf. Wenn der Text Treiber verwendet wird, wird eine Datei ohne Erweiterung erstellt, wenn die CREATE TABLE-Anweisung mit einem Namen ohne Erweiterung ausgeführt wird. Andere Treiber erstellen eine Datei mit einer Standard Erweiterung, wenn keine Erweiterung angegeben wird. Zum Erstellen einer Datei mit der Erweiterung. txt muss die Erweiterung im Namen enthalten sein. Um Dateien ohne Erweiterungen im Dialogfeld **Text Format definieren** anzuzeigen, "*." muss der Erweiterungs Liste hinzugefügt werden.|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort **Extensions** in einem [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)-Befehl.|  
|Nur Leseberechtigung|Legt fest, dass die Datenbank schreibgeschützt ist.|Um diese Option dynamisch festzulegen, verwenden Sie **das Schlüsselwort** "schreibgeschützt" in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|  
|Zu überprüfenden Zeilen|Die Anzahl der zu überprüfenden Zeilen, um den Datentyp jeder Spalte zu bestimmen. Der-Datentyp wird anhand der maximalen Anzahl von gefundenen Daten bestimmt. Wenn Daten gefunden werden, die nicht mit dem für die Spalte erraten Datentyp identisch sind, wird der Datentyp als NULL-Wert zurückgegeben.<br /><br /> Für den Text Treiber können Sie eine Zahl zwischen 1 und 32767 für die Anzahl der zu überprüfenden Zeilen eingeben. Allerdings ist der Wert immer standardmäßig 25. (Eine Zahl außerhalb des Limits gibt einen Fehler zurück.)|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort **MaxScanRows** in einem [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)-aufrufsbefehl.|  
|Verzeichnis auswählen|Zeigt ein Dialogfeld an, in dem Sie ein Verzeichnis mit den Dateien auswählen können, auf die Sie zugreifen möchten.<br /><br /> Geben Sie beim Definieren eines Datenquellen Verzeichnisses das Verzeichnis an, in dem sich Ihre am häufigsten verwendeten Dateien befinden. Der ODBC-Treiber verwendet dieses Verzeichnis als Standardverzeichnis. Kopieren Sie andere Dateien in dieses Verzeichnis, wenn Sie häufig verwendet werden. Alternativ können Sie Dateinamen in einer SELECT-Anweisung mit dem Verzeichnisnamen qualifizieren:`SELECT * FROM C:\MYDIR\EMP`<br /><br /> Oder Sie können ein neues Standardverzeichnis angeben, indem Sie die **SQLSetConnectOption** -Funktion mit der SQL_CURRENT_QUALIFIER-Option verwenden.|Um diese Option dynamisch festzulegen, verwenden Sie das **DefaultDir** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).|
