---
title: Programmgesteuertes Festlegen von Optionen für den dBASE-Treiber | Microsoft Docs
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
ms.openlocfilehash: 75889d9ff3ccfe01f9b8d5141df7774205522815
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300780"
---
# <a name="setting-options-programmatically-for-the-dbase-driver"></a>Programmgesteuertes Festlegen von Optionen für die dBASE-Treiber

|Option|Beschreibung|Methode|  
|------------|-----------------|------------|  
|Ungefähre Zeilenanzahl|Bestimmt, ob Tabellengrößenstatistiken angenähert werden. Diese Option gilt für alle Datenquellen, die den ODBC-Treiber verwenden.|Um diese Option dynamisch festzulegen, verwenden Sie das **Schlüsselwort STATISTICS** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Sortierungssequenz|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Die Reihenfolge kann sein: ASCII (Standard) oder International.|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort **COLLATINGSEQUENCE** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Datenquellenname|Ein Name, der die Datenquelle identifiziert, z. B. Lohn- oder Personalabrechnung.|Um diese Option dynamisch festzulegen, verwenden Sie das **DSN-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Datenbank|Eine Microsoft Access-Datenquelle kann eingerichtet werden, ohne eine Datenbank auszuwählen oder zu erstellen. Wenn beim Setup keine Datenbank bereitgestellt wird, werden Benutzer aufgefordert, eine Datenbankdatei auszuwählen, wenn sie eine Verbindung mit der Datenquelle herstellen.|Um diese Option dynamisch festzulegen, verwenden Sie das **DBQ-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Beschreibung|Eine optionale Beschreibung der Daten in der Datenquelle; z. B. "Mietdatum, Gehaltshistorie und aktuelle Überprüfung aller Mitarbeiter."|Um diese Option dynamisch **DESCRIPTION** festzulegen, verwenden Sie das DESCRIPTION-Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Exklusiv|Wenn das Feld **Exklusiv** ausgewählt ist, wird die Datenbank im Exklusivmodus geöffnet und kann jeweils nur von einem Benutzer aufgerufen werden. Die Leistung wird verbessert, wenn sie im Exklusivmodus ausgeführt wird.|Um diese Option dynamisch festzulegen, verwenden Sie das **SCHLÜSSELwort EXCLUSIVE** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Seitentimeout|Gibt den Zeitraum in Zehntelsekunden an, in dem eine Seite (falls nicht verwendet) im Puffer verbleibt, bevor sie entfernt wird. Der Standardwert ist 600 Zehntelsekunden (60 Sekunden). Diese Option gilt für alle Datenquellen, die den ODBC-Treiber verwenden.<br /><br /> Das Seitentimeout kann aufgrund einer inhärenten Verzögerung nicht 0 sein. Das Seitentimeout darf nicht kleiner als die inhärente Verzögerung sein, auch wenn die Option für das Seitentimeout unterhalb dieses Werts festgelegt ist.|Um diese Option dynamisch festzulegen, verwenden Sie das **PAGETIMEOUT-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Nur Leseberechtigung|Legt die Datenbank als schreibgeschützt fest.|Um diese Option dynamisch festzulegen, verwenden Sie das **READONLY-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Verzeichnis auswählen|Zeigt ein Dialogfeld an, in dem Sie ein Verzeichnis auswählen können, das die Dateien enthält, auf die Sie zugreifen möchten.<br /><br /> Wenn Sie ein Datenquellenverzeichnis definieren, geben Sie das Verzeichnis an, in dem sich die am häufigsten verwendeten Dateien befinden. Der ODBC-Treiber verwendet dieses Verzeichnis als Standardverzeichnis. Kopieren Sie andere Dateien in dieses Verzeichnis, wenn sie häufig verwendet werden. Alternativ können Sie Dateinamen in einer SELECT-Anweisung mit dem Verzeichnisnamen qualifizieren:<br /><br /> SELECT \* VON C:'MYDIR'EMP<br /><br /> Sie können auch ein neues Standardverzeichnis angeben, indem Sie die **SQLSetConnectOption-Funktion** mit der Option SQL_CURRENT_QUALIFIER verwenden.|Um diese Option dynamisch festzulegen, verwenden Sie das **DEFAULTDIR-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Gelöschte Zeilen anzeigen|Gibt an, ob Zeilen, die als gelöscht markiert wurden, abgerufen oder positioniert werden können. Wenn diese Option deaktiviert ist, werden gelöschte Zeilen nicht angezeigt. Wenn diese Option ausgewählt ist, werden gelöschte Zeilen wie nicht gelöschte Zeilen behandelt. Standardmäßig ist das Kontrollkästchen deaktiviert.|Um diese Option dynamisch **DELETED** festzulegen, verwenden Sie das DELETED-Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|
