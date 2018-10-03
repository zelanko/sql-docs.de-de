---
title: Festlegen von Optionen für die Access-Treiber programmgesteuert | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], setting options programmatically
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
ms.assetid: 1690eb71-0cd3-4c00-9e15-f6a3ac5316dd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5227985c56d5e2fd4730c86fe9182c8b16b2cb02
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47804458"
---
# <a name="setting-options-programmatically-for-the-access-driver"></a>Programmgesteuertes Festlegen von Optionen für die Access-Treiber
|Option|Description|Methode|  
|------------|-----------------|------------|  
|Puffergröße|Die Größe des internen Puffers, in Kilobyte, die von Microsoft Access verwendet wird, um Daten zu und vom Datenträger übertragen werden soll. Die Standardpuffergröße beträgt 2048 KB, die (angezeigt als 2048). Jeder ganzzahlige Wert von 256 geteilt werden kann, kann eingegeben werden.|Um diese Option dynamisch festzulegen, verwenden Sie das MAXBUFFERSIZE-Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Datenquellenname|Ein Name, der die Datenquelle, z. B. Gehaltsabrechnungen oder Mitarbeiter identifiziert.|Um diese Option dynamisch festzulegen, verwenden die **DSN** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Datenbank|Eine Microsoft Access-Datenquelle kann ohne auswählen oder Erstellen einer Datenbank eingerichtet werden. Wenn beim Setup keine Datenbank angegeben ist, wird der Benutzer aufgefordert werden, um eine Datei auszuwählen, Herstellen der Verbindung mit der Datenquelle.|Um diese Option dynamisch festzulegen, verwenden die **DBQ** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Description|Eine optionale Beschreibung der Daten in der Datenquelle; z. B. "Hire Date, Gehaltsverlauf und aktuelle Überprüfung aller Mitarbeiter."|Um diese Option dynamisch festzulegen, verwenden die **Beschreibung** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Exclusive|Wenn die **exklusive** aktiviert ist, wird die Datenbank wird im exklusiven Modus geöffnet und kann jeweils nur ein einziger Benutzer zugegriffen werden. Leistung wird verbessert, wenn im exklusiven Modus ausgeführt wird.|Um diese Option dynamisch festzulegen, verwenden die **exklusive** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|ImplicitCommitSync|Bestimmt, wie die Änderungen, die außerhalb einer Transaktion an die Datenbank geschrieben werden. Dieser Wert wird anfangs festgelegt, auf "Ja", was bedeutet, dass die Microsoft Access-Treiber für Commits in einer internen/implizite Transaktion abgeschlossen werden gewartet wird.|Diese Option befindet sich auf die **erweiterte Optionen festlegen** im Dialogfeld für die Microsoft Access-Treiber.|  
|Timeout der Seite|Gibt die Zeitspanne in Millisekunden, die eine Seite (sofern nicht verwendet wird) im Puffer bleibt, bevor Sie entfernt werden. Microsoft Access-Treiber ist der Standardwert 500 Millisekunden (0,5 Sekunden). Diese Option gilt für alle Datenquellen, die den ODBC-Treiber verwenden.<br /><br /> Das Timeout der Seite darf nicht 0 aufgrund einer inhärenten Verzögerung sein. Das Timeout der Seite darf nicht kleiner als die inhärenten Verzögerung sein, auch wenn die Seite Timeoutoption unter diesen Wert festgelegt ist.|Um diese Option dynamisch festzulegen, verwenden die **des Werts PAGETIMEOUT** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Schreibgeschützt|Legt die Datenbank als schreibgeschützt fest.|Um diese Option dynamisch festzulegen, verwenden die **READONLY** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Systemdatenbank|Der vollständige Pfad der Microsoft Access-Systemdatenbank, die mit Microsoft Access-Datenbank verwendet werden, die Sie zugreifen möchten.<br /><br /> Klicken Sie auf die **Systemdatenbank** klicken, um das zu verwendende Systemdatenbank auszuwählen. Der ODBC-Microsoft Access-Treiber wird der Benutzer für Name und Kennwort aufgefordert. Der Standardname ist Administrator aus, und das Standardkennwort in Microsoft Access für den Administratorbenutzer ist eine leere Zeichenfolge.<br /><br /> Um die Sicherheit Ihrer Microsoft Access-Datenbank zu erhöhen, Erstellen eines neuen Benutzers als Ersatz für den Administratorbenutzer den Administratorbenutzer zu löschen oder ändern Sie die Objekte, die auf die Admin-Benutzer Zugriff hat.|Um diese Option dynamisch festzulegen, verwenden die **SYSTEMDB** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Threads|Die Anzahl von Hintergrundthreads für das Modul zu verwenden. Microsoft Access-Treiber wird dieser Wert standardmäßig auf 3 jedoch geändert werden kann. Der Benutzer möchte die Anzahl der Threads erhöht, wenn eine große Menge an Aktivität in der Datenbank vorhanden ist.<br /><br /> Diese Option befindet sich auf die **erweiterte Optionen festlegen** im Dialogfeld für die Microsoft Access-Treiber.|Um diese Option dynamisch festzulegen, verwenden die **THREADS** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|UserCommitSync|Bestimmt, ob die Microsoft Access-Treiber eine explizite Transaktionen für eine benutzerdefinierte asynchron ausführt. Dieser Wert wird anfangs festgelegt, auf "Ja", was bedeutet, dass die Wartezeit des Treibers Microsoft Access für Commits in einer benutzerdefinierten Transaktion ausgeführt werden.<br /><br /> Wenn diese Option auf "false" kann zu unvorhersehbaren folgen in einer mehrbenutzerumgebung haben.|Um diese Option dynamisch festzulegen, verwenden die **USERCOMMITSYNC** Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|
