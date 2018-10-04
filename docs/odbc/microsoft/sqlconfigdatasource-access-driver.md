---
title: SQLConfigDataSource (Access-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], Access Driver
- Access driver [ODBC], SQLConfigDataSource
ms.assetid: 1b152fb7-fa12-46b9-b168-006bb1355e77
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dd626d476bf1c4ac8b4f83f397584c367299904f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47637938"
---
# <a name="sqlconfigdatasource-access-driver"></a>SQLConfigDataSource (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Access-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource** -Funktion, die verwendet wird, zum Hinzufügen, ändern oder Löschen einer Datenquelle verwendet die folgenden Schlüsselwörter.  
  
|Schlüsselwort|Description|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Hiermit wird die gleiche Option als **Sortierreihenfolge Sequenz** im Dialogfeld "Setup".|  
|COMPACT_DB|Führt Komprimierung der Daten in einer Datenbankdatei an. Weist das folgende Format: COMPACT_DB = < Lokales_Laufwerk >< OptionaL_sort_order >\<optional VERSCHLÜSSELN Schlüsselwort >.<br /><br /> Wenn Sie das Schlüsselwort COMPACT_DB in derselben Anweisung mit einem DSN-Schlüsselwort verwenden, ignoriert dieser Treiber das DSN-Schlüsselwort. Aus diesem Grund ist die Komprimierung einer Datenbank, und geben Sie einen DSN ein zweistufiger Prozess.|  
|CREATE_DB|Erstellt eine Datei an. Weist das folgende Format: CREATE_DB = < Lokales_Laufwerk >\<Optional_sort-Reihenfolge >< Optional_ENCRYPT Schlüsselwort >, wobei der Name des Pfads den vollständigen Pfad zu einer Microsoft Access-Datenbank ist. Wenn der Pfadname eine vorhandene Datenbank angegeben, wird ein Fehler zurückgegeben werden. Die Sortierreihenfolge ist als Gruppe aktiv, im Dialogfeld neue Datenbank angezeigt, wenn die Schaltfläche "erstellen" im Dialogfeld Setup für Microsoft Access gedrückt wird. Wenn keine Sortierreihenfolge angegeben ist, wird allgemein verwendet.<br /><br /> Wenn Sie das Schlüsselwort CREATE_DB in derselben Anweisung mit einem DSN-Schlüsselwort verwenden, ignoriert dieser Treiber das DSN-Schlüsselwort. Aus diesem Grund ist eine Datenbank erstellen, und geben einen DSN ein zweistufiger Prozess. Bei Verwendung der CREATE_DB-Schlüsselwort, wenn der Pfadname der Microsoft Access-Datenbank erstellt werden ein oder mehrere Leerzeichen enthält muss klicken Sie dann der gesamte Pfadnamen von doppelten Anführungszeichen eingeschlossen werden, wie in den folgenden Beispielen gezeigt:<br /><br /> "C:\PROGRAM FILES\COMMON < MyAccess.mdb"<br /><br /> "C:\Programme\Microsoft FILES\Access2.mdb"<br /><br /> CREATE_DB=C:\TEMP\test.mdb (es werden keine Anführungszeichen erforderlich)|  
|CREATE_SYSDB|Erstellt eine System-Datenbankdatei an. Weist das folgende Format: CREATE_SYSDB =\<-Pfadname >\<optional Sortierreihenfolge >, wobei der Name des Pfads für den vollständigen Pfad zu einer Microsoft Access-Datenbank ist. Wenn der Pfadname eine vorhandene Datenbank angegeben, wird ein Fehler zurückgegeben werden. Die Sortierreihenfolge ist als Gruppe eingerichtet, der **neue Datenbank** Dialogfeld angezeigt wird, wenn die **erstellen** Schaltfläche geklickt wird, der **ODBC-Setup für Microsoft Access** im Dialogfeld. Wenn keine Sortierreihenfolge angegeben ist, wird allgemein verwendet.|  
|CREATE_V2DB|Erstellt eine Datei, die in Microsoft Access 2.0 kompatibel ist. Weist das folgende Format: CREATE_V2DB =\<-Pfadname >\<optional Sortierreihenfolge >, wobei der Name des Pfads für den vollständigen Pfad zu einer Microsoft Access-Datenbank ist. Wenn der Pfadname eine vorhandene Datenbank angegeben, wird ein Fehler zurückgegeben werden. Die Sortierreihenfolge ist als Gruppe aktiv, im Dialogfeld neue Datenbank angezeigt, wenn die Schaltfläche "erstellen" im Dialogfeld Setup für Microsoft Access gedrückt wird. Wenn keine Sortierreihenfolge angegeben ist, wird allgemein verwendet.<br /><br /> Wenn Sie das Schlüsselwort CREATE_V2DB in derselben Anweisung mit einem DSN-Schlüsselwort verwenden, ignoriert dieser Treiber das DSN-Schlüsselwort. Aus diesem Grund ist eine Datenbank erstellen, und geben einen DSN ein zweistufiger Prozess.<br /><br /> Bei Verwendung der CREATE_V2DB-Schlüsselwort, wenn der Pfadname der Microsoft Access-Datenbank erstellt werden ein oder mehrere Leerzeichen enthält muss klicken Sie dann der gesamte Pfadnamen von doppelten Anführungszeichen eingeschlossen werden, wie in den folgenden Beispielen gezeigt:<br /><br /> "C:\PROGRAM FILES\COMMON < MyAccess.mdb"<br /><br /> "C:\Programme\Microsoft FILES\Access2.mdb"<br /><br /> CREATE_V2DB=C:\TEMP\test.mdb (es werden keine Anführungszeichen erforderlich)|  
|DBQ|Der Name der Datenbankdatei.<br /><br /> Hiermit wird die gleiche Option als **Datenbank** im Dialogfeld "Setup".|  
|WERT|Die Pfadangabe für die Datenbankdatei.|  
|DESCRIPTION|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Hiermit wird die gleiche Option als **Beschreibung** im Dialogfeld "Setup".|  
|DRIVER|Die Pfadangabe für den Treiber-DLL.|  
|DRIVERID|Eine ganzzahlige ID für den Treiber.  25 (Microsoft Access)|  
|FIL|Dateityp MS Access für Microsoft Access|  
|IMPLICITCOMMITSYNC|Bestimmt, ob die Microsoft Access-Treiber intern oder implizite Commits asynchron ausführt. Dieser Wert wird anfangs festgelegt, auf "Ja", was bedeutet, dass die Microsoft Access-Treiber für Commits in einer internen/implizite Transaktion abgeschlossen werden gewartet wird.<br /><br /> Der Wert dieser Option sollte nicht ohne sorgfältig die Konsequenzen geändert werden. Weitere Informationen zu dieser Option finden Sie unter den *Microsoft Jet-Datenbank-Engine Handbuch für Programmierer*.<br /><br /> Hiermit wird die gleiche Option als **ImplicitCommitSync** im Dialogfeld "Setup".|  
|MAXBUFFERSIZE|Die Größe des internen Puffers, in Kilobyte, die von Microsoft Access verwendet wird, um Daten zu und vom Datenträger übertragen werden soll. Die Standardpuffergröße beträgt 2048 KB, die (angezeigt als 2048). Jeder ganzzahlige Wert von 256 geteilt werden kann, kann verwendet werden. Hiermit wird die gleiche Option als **Puffergröße** im Dialogfeld "Setup".|  
|MAXSCANROWS|Die Anzahl von Zeilen gescannt werden müssen, wenn Sie einen Spaltendatentyp basierend auf den vorhandenen Daten festlegen.<br /><br /> Eine Zahl zwischen 1 und 16 kann für die Zeilen zu scannen eingegeben werden. Der Standardwert ist 8; Wenn es auf 0 festgelegt ist, werden alle Zeilen überprüft. (Eine Zahl außerhalb der Grenzwert wird einen Fehler zurückgegeben.)<br /><br /> Hiermit wird die gleiche Option als **zu scannende Zeilen** im Dialogfeld "Setup".|  
|' PAGETIMEOUT '|Gibt die Zeitspanne in Millisekunden, die eine Seite (sofern nicht verwendet wird) im Puffer bleibt, bevor Sie entfernt werden. Der Standardwert ist 5-Zehntelsekunden (0,5 Sekunden). Beachten Sie, dass diese Option auf alle Datenquellen gilt, die den ODBC-Treiber verwenden.<br /><br /> Hiermit wird die gleiche Option als **Page Timeout** im Dialogfeld "Setup".|  
|PWD|Das Kennwort.|  
|READONLY|True, um die Datei schreibgeschützt zu machen. "False", um die Datei nicht schreibgeschützt machen.<br /><br /> Hiermit wird die gleiche Option als **Read Only** im Dialogfeld "Setup".|  
|REPAIR_DB|Repariert eine Datenbank beschädigt, die durch einen Fehler, der während des Commitprozesses auftritt.<br /><br /> Wenn Sie das Schlüsselwort REPAIR_DB in derselben Anweisung mit einem DSN-Schlüsselwort verwenden, ignoriert dieser Treiber das DSN-Schlüsselwort. Aus diesem Grund ist eine Datenbank zu reparieren, und geben einen DSN ein zweistufiger Prozess.|  
|SYSTEMDB|Microsoft Access-Treiber die Pfadangabe zur System-Datei.<br /><br /> Hiermit wird die gleiche Option als **Systemdatenbank** im Dialogfeld "Setup".|  
|THREADS|Die Anzahl von Hintergrundthreads für das Modul zu verwenden. Dieser Wert standardmäßig auf 3, aber Sie kann geändert werden.<br /><br /> Hiermit wird die gleiche Option als **Threads** im Dialogfeld "Setup".|  
|UID|Microsoft Access-Treiber verwendet, der Namen der Benutzer-ID für die Anmeldung.|  
|USERCOMMITSYNC|Bestimmt, ob die Microsoft Access-Treiber für benutzerdefinierte Transaktionen asynchron ausgeführt werden wird. Dieser Wert wird anfangs festgelegt, auf "Ja", was bedeutet, dass die Wartezeit des Treibers Microsoft Access für Commits in einer benutzerdefinierten Transaktion ausgeführt werden.<br /><br /> Der Wert dieser Option sollte nicht ohne sorgfältig die Konsequenzen geändert werden. Weitere Informationen zu dieser Option finden Sie unter den *Microsoft Jet-Datenbank-Engine Handbuch für Programmierer*.<br /><br /> Hiermit wird die gleiche Option als **UserCommitSync** im Dialogfeld "Setup".|
