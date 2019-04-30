---
title: Programmgesteuertes Festlegen von Optionen für die dBASE-Treiber | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a268e72262f9f8252ea89774876f3d04008fe4c4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63284942"
---
# <a name="setting-options-programmatically-for-the-dbase-driver"></a>Programmgesteuertes Festlegen von Optionen für die dBASE-Treiber

|Option|Description|Methode|  
|------------|-----------------|------------|  
|Ungefähre Zeilenzählung|Bestimmt, ob die Größe von Tabellenstatistiken angeglichen werden. Diese Option gilt für alle Datenquellen, die den ODBC-Treiber verwenden.|Um diese Option dynamisch festzulegen, verwenden die **Statistiken** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Sortierreihenfolge|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Die Sequenz sind möglich: ASCII (Standard) und internationale.|Um diese Option dynamisch festzulegen, verwenden die **COLLATINGSEQUENCE** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Datenquellenname|Ein Name, der die Datenquelle, z. B. Gehaltsabrechnungen oder Mitarbeiter identifiziert.|Um diese Option dynamisch festzulegen, verwenden die **DSN** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Datenbank|Eine Microsoft Access-Datenquelle kann ohne auswählen oder Erstellen einer Datenbank eingerichtet werden. Wenn beim Setup keine Datenbank angegeben wird, werden Benutzer aufgefordert werden, eine Datei auswählen, wenn sie eine Verbindung mit der Datenquelle herstellen.|Um diese Option dynamisch festzulegen, verwenden die **DBQ** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Description|Eine optionale Beschreibung der Daten in der Datenquelle; z. B. "Hire Date, Gehaltsverlauf und aktuelle Überprüfung aller Mitarbeiter."|Um diese Option dynamisch festzulegen, verwenden die **Beschreibung** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Exclusive|Wenn die **exklusive** aktiviert ist, wird die Datenbank wird im exklusiven Modus geöffnet und kann jeweils nur ein einziger Benutzer zugegriffen werden. Leistung wird verbessert, wenn sie im exklusiven Modus ausgeführt wird.|Um diese Option dynamisch festzulegen, verwenden die **exklusive** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Timeout der Seite|Gibt den Zeitraum, in Zehntelsekunden, die eine Seite (sofern nicht verwendet wird) im Puffer bleibt, bevor sie entfernt wird. Der Standardwert ist 600 Zehntelsekunden (60 Sekunden). Diese Option gilt für alle Datenquellen, die den ODBC-Treiber verwenden.<br /><br /> Das Timeout der Seite darf nicht 0 aufgrund einer inhärenten Verzögerung sein. Das Timeout der Seite darf nicht kleiner als die inhärenten Verzögerung sein, auch wenn die Seite Timeoutoption unter diesen Wert festgelegt ist.|Um diese Option dynamisch festzulegen, verwenden die **des Werts PAGETIMEOUT** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Schreibgeschützt|Legt die Datenbank als schreibgeschützt fest.|Um diese Option dynamisch festzulegen, verwenden die **READONLY** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Wählen Sie Verzeichnis|Zeigt ein Dialogfeld, in dem Sie ein Verzeichnis auswählen können, das Dateien enthält, die Sie zugreifen möchten.<br /><br /> Wenn Sie ein Datenverzeichnis für die Datenquelle definieren, geben Sie das Verzeichnis, in denen die am häufigsten verwendeten Dateien gespeichert sind. Der ODBC-Treiber wird dieses Verzeichnis als Standardverzeichnis verwendet. Kopieren Sie andere Dateien in dieses Verzeichnis, wenn sie häufig verwendet werden. Alternativ können Sie den Dateinamen in einer SELECT-Anweisung mit den Namen des Verzeichnisses qualifizieren:<br /><br /> SELECT \* FROM C:\MYDIR\EMP<br /><br /> Sie können ein neues Standardverzeichnis angeben, mit der **SQLSetConnectOption** -Funktion mit der Option SQL_CURRENT_QUALIFIER.|Um diese Option dynamisch festzulegen, verwenden die **Wert** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|  
|Gelöschte Zeilen anzeigen|Gibt an, ob Zeilen, die als gelöscht markiert wurden abgerufen oder auf positioniert werden können. Wenn deaktiviert, werden gelöschte Zeilen nicht angezeigt wird; Wenn ausgewählt, werden gelöschte Zeilen behandelt nicht vorläufig gelöschte Zeilen identisch. Standardmäßig ist das Kontrollkästchen deaktiviert.|Um diese Option dynamisch festzulegen, verwenden die **gelöschte** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).|
