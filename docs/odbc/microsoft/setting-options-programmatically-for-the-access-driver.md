---
title: Programmgesteuertes Festlegen von Optionen für den Zugriffstreiber | Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300790"
---
# <a name="setting-options-programmatically-for-the-access-driver"></a>Programmgesteuertes Festlegen von Optionen für die Access-Treiber

|Option|Beschreibung|Methode|  
|------------|-----------------|------------|  
|Puffergröße|Die Größe des internen Puffers in Kilobyte, der von Microsoft Access zum Übertragen von Daten auf und von der Festplatte verwendet wird. Die Standardpuffergröße beträgt 2048 KB (angezeigt als 2048). Jeder ganzzahlige Wert, der durch 256 teilbar ist, kann eingegeben werden.|Um diese Option dynamisch festzulegen, verwenden Sie das Schlüsselwort MAXBUFFERSIZE in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Datenquellenname|Ein Name, der die Datenquelle identifiziert, z. B. Lohn- oder Personalabrechnung.|Um diese Option dynamisch festzulegen, verwenden Sie das **DSN-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Datenbank|Eine Microsoft Access-Datenquelle kann eingerichtet werden, ohne eine Datenbank auszuwählen oder zu erstellen. Wenn beim Setup keine Datenbank bereitgestellt wird, wird der Benutzer beim Herstellen einer Verbindung mit der Datenquelle aufgefordert, eine Datenbankdatei auszuwählen.|Um diese Option dynamisch festzulegen, verwenden Sie das **DBQ-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Beschreibung|Eine optionale Beschreibung der Daten in der Datenquelle; z. B. "Mietdatum, Gehaltshistorie und aktuelle Überprüfung aller Mitarbeiter."|Um diese Option dynamisch **DESCRIPTION** festzulegen, verwenden Sie das DESCRIPTION-Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Exklusiv|Wenn das Feld **Exklusiv** ausgewählt ist, wird die Datenbank im Exklusivmodus geöffnet und kann jeweils nur von einem Benutzer aufgerufen werden. Die Leistung wird verbessert, wenn sie im Exklusivmodus ausgeführt wird.|Um diese Option dynamisch festzulegen, verwenden Sie das **SCHLÜSSELwort EXCLUSIVE** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|ImplicitCommitSync|Bestimmt, wie Änderungen, die außerhalb einer Transaktion vorgenommen wurden, in die Datenbank geschrieben werden. Dieser Wert wird zunächst auf "Ja" festgelegt, was bedeutet, dass der Microsoft Access-Treiber auf den Abschluss von Commits in einer internen/impliziten Transaktion wartet.|Diese Option ist im Dialogfeld **Erweiterte Optionen festlegen** für den Microsoft Access-Treiber enthalten.|  
|Seitentimeout|Gibt den Zeitraum in Millisekunden an, in dem eine Seite (falls nicht verwendet) im Puffer verbleibt, bevor sie entfernt wird. Für den Microsoft Access-Treiber ist der Standardwert 500 Millisekunden (0,5 Sekunden). Diese Option gilt für alle Datenquellen, die den ODBC-Treiber verwenden.<br /><br /> Das Seitentimeout kann aufgrund einer inhärenten Verzögerung nicht 0 sein. Das Seitentimeout darf nicht kleiner als die inhärente Verzögerung sein, auch wenn die Option für das Seitentimeout unterhalb dieses Werts festgelegt ist.|Um diese Option dynamisch festzulegen, verwenden Sie das **PAGETIMEOUT-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Nur Leseberechtigung|Legt die Datenbank als schreibgeschützt fest.|Um diese Option dynamisch festzulegen, verwenden Sie das **READONLY-Schlüsselwort** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Systemdatenbank|Der vollständige Pfad der Microsoft Access-Systemdatenbank, die mit der Microsoft Access-Datenbank verwendet werden soll, auf die Sie zugreifen möchten.<br /><br /> Klicken Sie auf die Schaltfläche **Systemdatenbank,** um die zu verwendende Systemdatenbank auszuwählen. Der ODBC Microsoft Access-Treiber fordert den Benutzer zur Eingabe eines Namens und Kennworts auf. Der Standardname ist Admin, und das Standardkennwort in Microsoft Access für den Admin-Benutzer ist eine leere Zeichenfolge.<br /><br /> Um die Sicherheit Ihrer Microsoft Access-Datenbank zu erhöhen, erstellen Sie einen neuen Benutzer, um den Admin-Benutzer zu ersetzen und den Admin-Benutzer zu löschen, oder ändern Sie die Objekte, auf die der Administratorzugriff hat.|Um diese Option dynamisch festzulegen, verwenden Sie das **SCHLÜSSELwort SYSTEMDB** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|Threads|Die Anzahl der Hintergrundthreads, die das Modul verwenden soll. Für den Microsoft Access-Treiber ist dieser Wert standardmäßig 3, kann jedoch geändert werden. Der Benutzer kann die Anzahl der Threads erhöhen, wenn die Datenbank eine große Aktivität aufweist.<br /><br /> Diese Option ist im Dialogfeld **Erweiterte Optionen festlegen** für den Microsoft Access-Treiber enthalten.|Um diese Option dynamisch **THREADS** festzulegen, verwenden Sie das Threads-Schlüsselwort in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|  
|UserCommitSync|Legt fest, ob der Microsoft Access-Treiber eine explizite benutzerdefinierte Transaktion asynchron ausführt. Dieser Wert wird zunächst auf "Ja" festgelegt, was bedeutet, dass der Microsoft Access-Treiber auf den Abschluss von Commits in einer benutzerdefinierten Transaktion wartet.<br /><br /> Das Festlegen dieser Option auf False kann in einer Umgebung mit mehreren Benutzern unvorhersehbare Folgen haben.|Um diese Option dynamisch festzulegen, verwenden Sie das **Schlüsselwort USERCOMMITSYNC** in einem Aufruf von [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).|
