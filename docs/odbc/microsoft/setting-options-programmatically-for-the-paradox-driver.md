---
title: Festlegen von Optionen für die Paradox-Treiber programmgesteuert | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 658d03469e2733b0c25513a4d4a89c6ab88b9852
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063514"
---
# <a name="setting-options-programmatically-for-the-paradox-driver"></a>Programmgesteuertes Festlegen von Optionen für die Paradox-Treiber

|Option|Beschreibung|Methode|  
|------------|-----------------|------------|  
|Verzeichnis|Legt die entsprechenden Verzeichnis fest.|Um diese Option dynamisch festzulegen, verwenden die **Wert** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Sortierreihenfolge|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Die Sequenz kann ASCII (Standard) sein, internationale, Finnish-Swedish oder Danish-Norwegian.|Um diese Option dynamisch festzulegen, verwenden die **COLLATINGSEQUENCE** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Beschreibung|Eine optionale Beschreibung der Daten in der Datenquelle; z. B. "Hire Date, Gehaltsverlauf und aktuelle Überprüfung aller Mitarbeiter."|Um diese Option dynamisch festzulegen, verwenden die **Beschreibung** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Exclusive|Wenn die **exklusive** aktiviert ist, wird die Datenbank wird im exklusiven Modus geöffnet und kann jeweils nur ein einziger Benutzer zugegriffen werden. Leistung wird verbessert, wenn im exklusiven Modus ausgeführt wird.|Um diese Option dynamisch festzulegen, verwenden die **exklusive** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|NET-Stil|Das Netzwerk den Zugriff zu verwendende Format beim Paradox-Daten: entweder "3.*x*" für Paradox-3. *X* oder "4. *X*"für Paradox 4. *X* oder 5. *X*. Kann auf "3. festgelegt werden *x*"oder" 4. *X*"ist die Version 4-Paradox. *X* oder 5. *X*; Wenn die Version 3 für Paradox. *X*, das Format muss "3. *X*".|Um diese Option dynamisch festzulegen, verwenden die **PARADOXNETSTYLE** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Timeout der Seite|Gibt den Zeitraum, in Zehntelsekunden, die eine Seite (sofern nicht verwendet wird) im Puffer bleibt, bevor Sie entfernt werden. Der Standardwert ist 600 Zehntelsekunden (60 Sekunden). Diese Option gilt für alle Datenquellen, die den ODBC-Treiber verwenden.<br /><br /> Das Timeout der Seite darf nicht 0 aufgrund einer inhärenten Verzögerung sein. Das Timeout der Seite darf nicht kleiner als die inhärenten Verzögerung sein, auch wenn die Seite Timeoutoption unter diesen Wert festgelegt ist.|Um diese Option dynamisch festzulegen, verwenden die **des Werts PAGETIMEOUT** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Schreibgeschützt|Legt die Datenbank als schreibgeschützt fest.|Um diese Option dynamisch festzulegen, verwenden die **READONLY** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Wählen Sie Verzeichnis|Zeigt ein Dialogfeld, in dem Sie ein Verzeichnis mit den Dateien, die Sie zugreifen möchten auswählen können.<br /><br /> Beim Definieren eines Quellverzeichnisses Daten geben Sie das Verzeichnis, in dem Ihre am häufigsten Dateien verwendeten, befinden. Der ODBC-Treiber wird dieses Verzeichnis als Standardverzeichnis verwendet. Kopieren Sie andere Dateien in dieses Verzeichnis, wenn sie häufig verwendet werden. Alternativ können Sie den Dateinamen in einer SELECT-Anweisung mit den Namen des Verzeichnisses qualifizieren:<br /><br /> WÄHLEN SIE \* AUS C:\MYDIR\EMP<br /><br /> Sie können ein neues Standardverzeichnis angeben, mit der **SQLSetConnectOption** -Funktion mit der Option SQL_CURRENT_QUALIFIER.|Um diese Option dynamisch festzulegen, verwenden die **Wert** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Wählen Sie Netzwerkverzeichnis|Der vollständige Pfad des Verzeichnisses mit der eine Sperre Paradox-Datenbank, weil sie entweder die Pdoxusrs.net-Datei enthält (Paradox-4. *X*) oder die Datei Paradox.net (Paradox-5. *X*). Wenn das Verzeichnis nicht mit einer dieser Dateien enthält, die Paradox-Treiber wird erstellt. Informationen zu diesen Dateien finden Sie unter der Dokumentation für die Paradox.<br /><br /> Bevor Sie ein Netzwerkverzeichnis auswählen können, müssen Sie in Ihren Paradox-Benutzernamen eingeben der **Benutzernamen** Textfeld. Klicken Sie auf **Netzwerkverzeichnis wählen** ein Netzwerkverzeichnis auswählen.|Um diese Option dynamisch festzulegen, verwenden die **x** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Benutzername|Der Benutzername für die Paradox. Dies ist der Name, anderen Benutzern von Paradox-Dateien angezeigt werden, wenn eine Sperre auftritt.|Um diese Option dynamisch festzulegen, verwenden die **PARADOXUSERNAME** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|
