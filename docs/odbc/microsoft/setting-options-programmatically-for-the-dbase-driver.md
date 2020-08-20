---
description: Programmgesteuertes Festlegen von Optionen für die dBASE-Treiber
title: Programm gesteuertes Festlegen von Optionen für den dBase-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: 336d0fd4-5448-4d8c-b7d9-49e857228e36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c4b86b8284ca9a47e3ad40b1680a362035a3f13
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471582"
---
# <a name="setting-options-programmatically-for-the-dbase-driver"></a>Programmgesteuertes Festlegen von Optionen für die dBASE-Treiber

|Option|Beschreibung|Methode|  
|------------|-----------------|------------|  
|Ungefähre Zeilen Anzahl|Bestimmt, ob Statistiken der Tabellengröße angeglichen werden. Diese Option gilt für alle Datenquellen, die den ODBC-Treiber verwenden.|Um diese Option dynamisch festzulegen, verwenden Sie das **Statistics** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Sortierreihenfolge|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Die Sequenz kann wie folgt lauten: ASCII (Standard) oder International.|Um diese Option dynamisch festzulegen, verwenden Sie das **CollatingSequence** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Datenquellenname|Ein Name, der die Datenquelle identifiziert, z. b. Gehaltsabrechnung oder Personal.|Um diese Option dynamisch festzulegen, verwenden Sie das **DSN** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Datenbank|Eine Microsoft Access-Datenquelle kann eingerichtet werden, ohne dass eine Datenbank ausgewählt oder erstellt wird. Wenn beim Setup keine Datenbank bereitgestellt wird, werden die Benutzer beim Herstellen einer Verbindung mit der Datenquelle aufgefordert, eine Datenbankdatei auszuwählen.|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort **DBQ** in einem [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)-aufrufsbefehl.|  
|Beschreibung|Eine optionale Beschreibung der Daten in der Datenquelle. Beispiel: "Einstellen von Datum, Gehalts Verlauf und aktueller Review aller Mitarbeiter".|Um diese Option dynamisch festzulegen, verwenden Sie das **Description** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Exklusiv|Wenn das Feld **exklusiv** ausgewählt ist, wird die Datenbank im exklusiven Modus geöffnet, und es kann jeweils nur von einem Benutzer darauf zugegriffen werden. Die Leistung wird verbessert, wenn Sie im exklusiven Modus ausgeführt wird.|Um diese Option dynamisch festzulegen, verwenden Sie das **exklusive** Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Seiten Timeout|Gibt den Zeitraum in Sekunden an, in dem eine Seite (falls nicht verwendet) im Puffer verbleibt, bevor Sie entfernt wird. Der Standardwert ist 600 Zehntelsekunden (60 Sekunden). Diese Option gilt für alle Datenquellen, die den ODBC-Treiber verwenden.<br /><br /> Das Seiten Timeout kann aufgrund einer inhärenten Verzögerung nicht 0 sein. Das Seiten Timeout darf nicht kleiner sein als die inhärente Verzögerung, auch wenn die Option Seiten Timeout unter diesem Wert festgelegt ist.|Um diese Option dynamisch festzulegen, verwenden Sie das **PageTimeout** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Nur Leseberechtigung|Legt fest, dass die Datenbank schreibgeschützt ist.|Um diese Option dynamisch festzulegen, verwenden Sie **das Schlüsselwort** "schreibgeschützt" in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Verzeichnis auswählen|Zeigt ein Dialogfeld an, in dem Sie ein Verzeichnis auswählen können, das die Dateien enthält, auf die Sie zugreifen möchten.<br /><br /> Wenn Sie ein Datenquellen Verzeichnis definieren, geben Sie das Verzeichnis an, in dem sich die am häufigsten verwendeten Dateien befinden. Der ODBC-Treiber verwendet dieses Verzeichnis als Standardverzeichnis. Kopieren Sie andere Dateien in dieses Verzeichnis, wenn Sie häufig verwendet werden. Alternativ können Sie Dateinamen in einer SELECT-Anweisung mit dem Verzeichnisnamen qualifizieren:<br /><br /> Select \* from c:\mydir\emp<br /><br /> Oder Sie können ein neues Standardverzeichnis angeben, indem Sie die **SQLSetConnectOption** -Funktion mit der SQL_CURRENT_QUALIFIER-Option verwenden.|Um diese Option dynamisch festzulegen, verwenden Sie das **DefaultDir** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Gelöschte Zeilen anzeigen|Gibt an, ob Zeilen, die als gelöscht markiert wurden, abgerufen oder positioniert werden können. Wenn diese Option deaktiviert ist, werden gelöschte Zeilen nicht angezeigt. Wenn diese Option aktiviert ist, werden gelöschte Zeilen wie nicht gelöschte Zeilen behandelt. Standardmäßig ist das Kontrollkästchen deaktiviert.|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort **deleted** in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|
