---
title: Programm gesteuertes Festlegen von Optionen für den Zugriffs Treiber | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9a90f0a20569a2a0a5bb93dec7aa4b95b50093dc
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300790"
---
# <a name="setting-options-programmatically-for-the-access-driver"></a>Programmgesteuertes Festlegen von Optionen für die Access-Treiber

|Option|BESCHREIBUNG|Methode|  
|------------|-----------------|------------|  
|Puffergröße|Die Größe des internen Puffers in Kilobyte, der von Microsoft Access zum Übertragen von Daten auf den und vom Datenträger verwendet wird. Die Standardpuffergröße beträgt 2048 KB (wird als 2048 angezeigt). Jeder von 256 teilbar ganzzahlige Wert kann eingegeben werden.|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort "MaxBufferSize" in einem [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)-aufrufsbefehl.|  
|Datenquellenname|Ein Name, der die Datenquelle identifiziert, z. b. Gehaltsabrechnung oder Personal.|Um diese Option dynamisch festzulegen, verwenden Sie das **DSN** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Datenbank|Eine Microsoft Access-Datenquelle kann eingerichtet werden, ohne dass eine Datenbank ausgewählt oder erstellt wird. Wenn beim Setup keine Datenbank bereitgestellt wird, wird der Benutzer beim Herstellen einer Verbindung mit der Datenquelle aufgefordert, eine Datenbankdatei auszuwählen.|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort **DBQ** in einem [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)-aufrufsbefehl.|  
|BESCHREIBUNG|Eine optionale Beschreibung der Daten in der Datenquelle. Beispiel: "Einstellen von Datum, Gehalts Verlauf und aktueller Review aller Mitarbeiter".|Um diese Option dynamisch festzulegen, verwenden Sie das **Description** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Exklusiv|Wenn das Feld **exklusiv** ausgewählt ist, wird die Datenbank im exklusiven Modus geöffnet, und es kann jeweils nur von einem Benutzer darauf zugegriffen werden. Die Leistung wird verbessert, wenn Sie im exklusiven Modus ausgeführt wird.|Um diese Option dynamisch festzulegen, verwenden Sie das **exklusive** Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Implizicommitsync|Bestimmt, wie Änderungen, die außerhalb einer Transaktion vorgenommen werden, in die Datenbank geschrieben werden. Dieser Wert ist anfänglich auf "yes" festgelegt, was bedeutet, dass der Microsoft Access-Treiber auf das Abschließen von Commits in einer internen/impliziten Transaktion wartet.|Diese Option ist im Dialogfeld **Erweiterte Optionen festlegen** für den Microsoft Access-Treiber enthalten.|  
|Seiten Timeout|Gibt den Zeitraum in Millisekunden an, den eine Seite (falls nicht verwendet) im Puffer verbleibt, bevor Sie entfernt wird. Für den Microsoft Access-Treiber beträgt der Standardwert 500 Millisekunden (0,5 Sekunden). Diese Option gilt für alle Datenquellen, die den ODBC-Treiber verwenden.<br /><br /> Das Seiten Timeout kann aufgrund einer inhärenten Verzögerung nicht 0 sein. Das Seiten Timeout darf nicht kleiner sein als die inhärente Verzögerung, auch wenn die Option Seiten Timeout unter diesem Wert festgelegt ist.|Um diese Option dynamisch festzulegen, verwenden Sie das **PageTimeout** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Nur Leseberechtigung|Legt fest, dass die Datenbank schreibgeschützt ist.|Um diese Option dynamisch festzulegen, verwenden Sie **das Schlüsselwort** "schreibgeschützt" in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|System Datenbank|Der vollständige Pfad der Microsoft Access-Systemdatenbank, die mit der Microsoft Access-Datenbank verwendet werden soll, auf die Sie zugreifen möchten.<br /><br /> Klicken Sie auf die Schaltfläche **Systemdatenbank** , um die zu verwendende Systemdatenbank auszuwählen. Der ODBC-Microsoft Access-Treiber fordert den Benutzer auf, einen Namen und ein Kennwort einzugeben. Der Standardname ist admin, und das Standard Kennwort in Microsoft Access für den Administrator Benutzer ist eine leere Zeichenfolge.<br /><br /> Um die Sicherheit Ihrer Microsoft Access-Datenbank zu erhöhen, erstellen Sie einen neuen Benutzer, um den Administrator Benutzer zu ersetzen und den Administrator Benutzer zu löschen, oder ändern Sie die Objekte, auf die der Administrator Benutzer Zugriff hat.|Um diese Option dynamisch festzulegen, verwenden Sie das **SystemDB** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Threads|Die Anzahl der Hintergrundthreads, die von der Engine verwendet werden sollen. Für den Microsoft Access-Treiber ist dieser Wert standardmäßig auf 3 eingestellt, kann jedoch geändert werden. Der Benutzer möchte möglicherweise die Anzahl der Threads erhöhen, wenn eine große Menge an Aktivität in der Datenbank vorhanden ist.<br /><br /> Diese Option ist im Dialogfeld **Erweiterte Optionen festlegen** für den Microsoft Access-Treiber enthalten.|Um diese Option dynamisch festzulegen, verwenden Sie das **Threads** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|UserCommitSync|Bestimmt, ob der Microsoft Access-Treiber eine explizite benutzerdefinierte Transaktion asynchron ausführt. Dieser Wert ist anfänglich auf "yes" festgelegt, was bedeutet, dass der Microsoft Access-Treiber auf das Abschließen von Commits in einer benutzerdefinierten Transaktion wartet.<br /><br /> Wenn diese Option auf "false" festgelegt wird, kann dies in einer mehr Benutzerumgebung unvorhersehbare Konsequenzen haben.|Um diese Option dynamisch festzulegen, verwenden Sie das **UserCommitSync** -Schlüsselwort in einem-Befehl von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|
