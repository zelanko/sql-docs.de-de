---
description: Programmgesteuertes Festlegen von Optionen für die Paradox-Treiber
title: Programm gesteuertes Festlegen von Optionen für den Paradox-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- Paradox driver [ODBC], setting options programmatically
- desktop database drivers [ODBC], Paradox driver
- Jet-based ODBC drivers [ODBC], Paradox driver
ms.assetid: 7996d3f8-b5f5-4cac-8a66-fc96a42b603e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 85b63df9e18b835c96bc0e59f7c937ece69f3999
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471572"
---
# <a name="setting-options-programmatically-for-the-paradox-driver"></a>Programmgesteuertes Festlegen von Optionen für die Paradox-Treiber

|Option|Beschreibung|Methode|  
|------------|-----------------|------------|  
|Verzeichnis|Legt das Zielverzeichnis fest.|Um diese Option dynamisch festzulegen, verwenden Sie das **DefaultDir** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Sortierreihenfolge|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Die Sequenz kann ASCII (Standard), International, Swedish-Finnish oder Norwegisch (Dänisch) sein.|Um diese Option dynamisch festzulegen, verwenden Sie das **CollatingSequence** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Beschreibung|Eine optionale Beschreibung der Daten in der Datenquelle. Beispiel: "Einstellen von Datum, Gehalts Verlauf und aktueller Review aller Mitarbeiter".|Um diese Option dynamisch festzulegen, verwenden Sie das **Description** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Exklusiv|Wenn das Feld **exklusiv** ausgewählt ist, wird die Datenbank im exklusiven Modus geöffnet, und es kann jeweils nur von einem Benutzer darauf zugegriffen werden. Die Leistung wird verbessert, wenn Sie im exklusiven Modus ausgeführt wird.|Um diese Option dynamisch festzulegen, verwenden Sie das **exklusive** Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|NET-Stil|Der Netzwerk Zugriffs Stil, der für den Zugriff auf Paradox-Daten verwendet werden soll: entweder "3.*x*" für Paradox 3. *x* oder "4. *x*"für Paradox 4. *x* oder 5. *x*. Kann auf "3" festgelegt werden. *x*"oder" 4. *x*", wenn die Version Paradox 4 ist. *x* oder 5. *x*; Wenn die Version Paradox 3 ist. *x*, der Stil muss "3" lauten. *x*".|Um diese Option dynamisch festzulegen, verwenden Sie das " **ParadoxNetStyle** "-Schlüsselwort in einem [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)-aufrufsbefehl.|  
|Seiten Timeout|Gibt den Zeitraum in Sekunden an, in dem eine Seite (falls nicht verwendet) im Puffer verbleibt, bevor Sie entfernt wird. Der Standardwert ist 600 Zehntelsekunden (60 Sekunden). Diese Option gilt für alle Datenquellen, die den ODBC-Treiber verwenden.<br /><br /> Das Seiten Timeout kann aufgrund einer inhärenten Verzögerung nicht 0 sein. Das Seiten Timeout darf nicht kleiner sein als die inhärente Verzögerung, auch wenn die Option Seiten Timeout unter diesem Wert festgelegt ist.|Um diese Option dynamisch festzulegen, verwenden Sie das **PageTimeout** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Nur Leseberechtigung|Legt fest, dass die Datenbank schreibgeschützt ist.|Um diese Option dynamisch festzulegen, verwenden Sie **das Schlüsselwort** "schreibgeschützt" in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Verzeichnis auswählen|Zeigt ein Dialogfeld an, in dem Sie ein Verzeichnis mit den Dateien auswählen können, auf die Sie zugreifen möchten.<br /><br /> Geben Sie beim Definieren eines Datenquellen Verzeichnisses das Verzeichnis an, in dem sich Ihre am häufigsten verwendeten Dateien befinden. Der ODBC-Treiber verwendet dieses Verzeichnis als Standardverzeichnis. Kopieren Sie andere Dateien in dieses Verzeichnis, wenn Sie häufig verwendet werden. Alternativ können Sie Dateinamen in einer SELECT-Anweisung mit dem Verzeichnisnamen qualifizieren:<br /><br /> Select \* from c:\mydir\emp<br /><br /> Oder Sie können ein neues Standardverzeichnis angeben, indem Sie die **SQLSetConnectOption** -Funktion mit der SQL_CURRENT_QUALIFIER-Option verwenden.|Um diese Option dynamisch festzulegen, verwenden Sie das **DefaultDir** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Netzwerk Verzeichnis auswählen|Der vollständige Pfad des Verzeichnisses, das eine Paradox-Sperr Datenbank enthält, da Sie entweder die Datei Pdoxusrs.net (in Paradox 4) enthält.* x*) oder die Paradox.NET-Datei (in Paradox 5).* x*). Wenn das Verzeichnis keine dieser Dateien enthält, erstellt der Paradox-Treiber einen. Weitere Informationen zu diesen Dateien finden Sie in der Paradox-Dokumentation.<br /><br /> Bevor Sie ein Netzwerk Verzeichnis auswählen können, müssen Sie Ihren Paradox-Benutzernamen in das Textfeld **Benutzername** eingeben. Klicken Sie auf **Netzwerk Verzeichnis auswählen** , um ein Netzwerk Verzeichnis auszuwählen.|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort " **ParadoxNetPath** " in einem [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)-aufrufsbefehl.|  
|Benutzername|Der Paradox-Benutzername. Dies ist der Name, der anderen Benutzern von Paradox-Dateien angezeigt wird, wenn eine Sperre auftritt.|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort " **ParadoxUserName** " in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|
