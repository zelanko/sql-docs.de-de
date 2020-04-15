---
title: Programmgesteuertes Festlegen von Optionen für den Paradox-Treiber | Microsoft Docs
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
ms.openlocfilehash: d04de1f0de4baca5b3f474ef9fbcf3f886e6906f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300760"
---
# <a name="setting-options-programmatically-for-the-paradox-driver"></a>Programmgesteuertes Festlegen von Optionen für die Paradox-Treiber

|Option|Beschreibung|Methode|  
|------------|-----------------|------------|  
|Verzeichnis|Legt das Zielverzeichnis fest.|Um diese Option dynamisch festzulegen, verwenden Sie das **DEFAULTDIR-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Sortierungssequenz|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Die Sequenz kann ASCII (Standard), International, Schwedisch-Finnisch oder Norwegisch-Dänisch sein.|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort **COLLATINGSEQUENCE** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Beschreibung|Eine optionale Beschreibung der Daten in der Datenquelle; z. B. "Mietdatum, Gehaltshistorie und aktuelle Überprüfung aller Mitarbeiter."|Um diese Option dynamisch **DESCRIPTION** festzulegen, verwenden Sie das DESCRIPTION-Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Exklusiv|Wenn das Feld **Exklusiv** ausgewählt ist, wird die Datenbank im Exklusivmodus geöffnet und kann jeweils nur von einem Benutzer aufgerufen werden. Die Leistung wird verbessert, wenn sie im Exklusivmodus ausgeführt wird.|Um diese Option dynamisch festzulegen, verwenden Sie das **SCHLÜSSELwort EXCLUSIVE** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Net Style|Der Netzwerkzugriffsstil, der beim Zugriff auf Paradox-Daten verwendet werden soll: entweder "3.*x*" für Paradox 3. *x* oder "4. *x*" für Paradox 4. *x* oder 5. *x*. Kann auf "3" gesetzt werden. *x*" oder "4. *x*" wenn die Version Paradox 4 ist. *x* oder 5. *x*; wenn die Version Paradox 3 ist. *x*muss der Stil "3" sein. *x*".|Um diese Option dynamisch festzulegen, verwenden Sie das **Schlüsselwort PARADOXNETSTYLE** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Seitentimeout|Gibt den Zeitraum in Zehntelsekunden an, in dem eine Seite (falls nicht verwendet) im Puffer verbleibt, bevor sie entfernt wird. Der Standardwert ist 600 Zehntelsekunden (60 Sekunden). Diese Option gilt für alle Datenquellen, die den ODBC-Treiber verwenden.<br /><br /> Das Seitentimeout kann aufgrund einer inhärenten Verzögerung nicht 0 sein. Das Seitentimeout darf nicht kleiner als die inhärente Verzögerung sein, auch wenn die Option für das Seitentimeout unterhalb dieses Werts festgelegt ist.|Um diese Option dynamisch festzulegen, verwenden Sie das **PAGETIMEOUT-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Nur Leseberechtigung|Legt die Datenbank als schreibgeschützt fest.|Um diese Option dynamisch festzulegen, verwenden Sie das **READONLY-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Verzeichnis auswählen|Zeigt ein Dialogfeld an, in dem Sie ein Verzeichnis auswählen können, das die Dateien enthält, auf die Sie zugreifen möchten.<br /><br /> Geben Sie beim Definieren eines Datenquellenverzeichnisses das Verzeichnis an, in dem sich die am häufigsten verwendeten Dateien befinden. Der ODBC-Treiber verwendet dieses Verzeichnis als Standardverzeichnis. Kopieren Sie andere Dateien in dieses Verzeichnis, wenn sie häufig verwendet werden. Alternativ können Sie Dateinamen in einer SELECT-Anweisung mit dem Verzeichnisnamen qualifizieren:<br /><br /> SELECT \* VON C:'MYDIR'EMP<br /><br /> Sie können auch ein neues Standardverzeichnis angeben, indem Sie die **SQLSetConnectOption-Funktion** mit der Option SQL_CURRENT_QUALIFIER verwenden.|Um diese Option dynamisch festzulegen, verwenden Sie das **DEFAULTDIR-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Netzwerkverzeichnis auswählen|Der vollständige Pfad des Verzeichnisses, das eine Paradox-Sperrdatenbank enthält, da es entweder die Pdoxusrs.net-Datei enthält (in Paradox 4.* x*) oder die Paradox.net Datei (in Paradox 5.* x*). Wenn das Verzeichnis keine dieser Dateien enthält, erstellt der Paradox-Treiber eine. Informationen zu diesen Dateien finden Sie in der Paradox-Dokumentation.<br /><br /> Bevor Sie ein Netzwerkverzeichnis auswählen können, müssen Sie Ihren Paradox-Benutzernamen in das Textfeld **Benutzername** eingeben. Klicken Sie auf **Netzwerkverzeichnis auswählen,** um ein Netzwerkverzeichnis auszuwählen.|Um diese Option dynamisch festzulegen, verwenden Sie das **Schlüsselwort PARADOXNETPATH** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|  
|Benutzername|Der Paradox-Benutzername. Dies ist der Name, der anderen Benutzern von Paradox-Dateien angezeigt wird, wenn eine Sperre auftritt.|Um diese Option dynamisch festzulegen, verwenden Sie das **Schlüsselwort PARADOXUSERNAME** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).|
