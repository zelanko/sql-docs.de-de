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
ms.openlocfilehash: 85b515ed4c30d68e62a49e1044c4ddf6f5cc5ab1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67985238"
---
# <a name="sqlconfigdatasource-access-driver"></a>SQLConfigDataSource (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Zugriffs Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource** -Funktion, die verwendet wird, um eine Datenquelle hinzuzufügen, zu ändern oder zu löschen, verwendet dynamisch die folgenden Schlüsselwörter.  
  
|Schlüsselwort|BESCHREIBUNG|  
|-------------|-----------------|  
|CollatingSequence|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Dadurch wird die gleiche Option wie die **Sortierreihenfolge** im Setup Dialogfeld festgelegt.|  
|COMPACT_DB|Führt Datenkomprimierung für eine Datenbankdatei aus. Weist das folgende Format auf: COMPACT_DB =<path_name><optionaL_sort_order \<>optionales Verschlüsselungs Schlüsselwort>.<br /><br /> Wenn das COMPACT_DB-Schlüsselwort in derselben Anweisung mit einem DSN-Schlüsselwort verwendet wird, ignoriert dieser Treiber das DSN-Schlüsselwort. Daher ist die Komprimierung einer Datenbank und die Angabe eines DSN ein zweistufiger Prozess.|  
|CREATE_DB|Erstellt eine Datenbankdatei. Weist das folgende Format auf: CREATE_DB =<path_name \<>optional_sort><optional_ENCRYPT> Schlüsselwort, wobei der Pfadname der vollständige Pfad zu einer Microsoft Access-Datenbank ist. Wenn der Pfadname eine vorhandene Datenbank angibt, wird ein Fehler zurückgegeben. Die Sortierreihenfolge wird im Dialogfeld neue Datenbank angezeigt, das angezeigt wird, wenn im Dialogfeld Microsoft Access-Setup auf die Schaltfläche erstellen geklickt wird. Wenn keine Sortierreihenfolge angegeben wird, wird "Allgemein" verwendet.<br /><br /> Wenn das CREATE_DB-Schlüsselwort in derselben Anweisung mit einem DSN-Schlüsselwort verwendet wird, ignoriert dieser Treiber das DSN-Schlüsselwort. Daher ist das Erstellen einer Datenbank und das Angeben eines DSN ein zweistufiger Prozess. Wenn Sie das CREATE_DB-Schlüsselwort verwenden und der Pfadname der zu erstellenden Microsoft Access-Datenbank ein oder mehrere Leerzeichen enthält, muss der gesamte Pfadname in doppelte Anführungszeichen eingeschlossen werden, wie in den folgenden Beispielen gezeigt:<br /><br /> "C:\Programme\Common Files \ myaccess. mdb"<br /><br /> "C:\programme\access2.mdb"<br /><br /> CREATE_DB = c:\temp\test.mdb (keine Anführungszeichen erforderlich)|  
|CREATE_SYSDB|Erstellt eine Systemdaten Bank Datei. Weist das folgende Format auf: CREATE_SYSDB\<= Pfadname>\<optional-Sortierreihenfolge>, wobei der Pfadname der vollständige Pfad zu einer Microsoft Access-Datenbank ist. Wenn der Pfadname eine vorhandene Datenbank angibt, wird ein Fehler zurückgegeben. Die Sortierreihenfolge wird im Dialogfeld **neue Datenbank** angezeigt, das angezeigt wird, wenn im Dialogfeld **ODBC Microsoft Access Setup** auf die Schaltfläche **Erstellen** geklickt wird. Wenn keine Sortierreihenfolge angegeben wird, wird "Allgemein" verwendet.|  
|CREATE_V2DB|Erstellt eine Datenbankdatei, die mit Microsoft Access 2,0 kompatibel ist. Weist das folgende Format auf: CREATE_V2DB\<= Pfadname>\<optional-Sortierreihenfolge>, wobei der Pfadname der vollständige Pfad zu einer Microsoft Access-Datenbank ist. Wenn der Pfadname eine vorhandene Datenbank angibt, wird ein Fehler zurückgegeben. Die Sortierreihenfolge wird im Dialogfeld neue Datenbank angezeigt, das angezeigt wird, wenn im Dialogfeld Microsoft Access-Setup auf die Schaltfläche erstellen geklickt wird. Wenn keine Sortierreihenfolge angegeben wird, wird "Allgemein" verwendet.<br /><br /> Wenn das CREATE_V2DB-Schlüsselwort in derselben Anweisung mit einem DSN-Schlüsselwort verwendet wird, ignoriert dieser Treiber das DSN-Schlüsselwort. Daher ist das Erstellen einer Datenbank und das Angeben eines DSN ein zweistufiger Prozess.<br /><br /> Wenn Sie das CREATE_V2DB-Schlüsselwort verwenden und der Pfadname der zu erstellenden Microsoft Access-Datenbank ein oder mehrere Leerzeichen enthält, muss der gesamte Pfadname in doppelte Anführungszeichen eingeschlossen werden, wie in den folgenden Beispielen gezeigt:<br /><br /> "C:\Programme\Common Files \ myaccess. mdb"<br /><br /> "C:\programme\access2.mdb"<br /><br /> CREATE_V2DB = c:\temp\test.mdb (keine Anführungszeichen erforderlich)|  
|DBQ|Der Name der Datenbankdatei.<br /><br /> Dadurch wird die gleiche Option wie die **Datenbank** im Setup Dialogfeld festgelegt.|  
|DefaultDir|Die Pfadspezifikation für die Datenbankdatei.|  
|Beschreibung|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Dadurch wird die gleiche Option wie die **Beschreibung** im Setup Dialogfeld festgelegt.|  
|DRIVER|Die Pfadspezifikation für die Treiber-DLL.|  
|DriverID|Eine ganzzahlige ID für den Treiber.  25 (Microsoft Access)|  
|RA|Dateityp MS Access for Microsoft Access|  
|Implizicommitsync|Bestimmt, ob der Microsoft Access-Treiber interne oder implizite Commits asynchron ausführt. Dieser Wert ist anfänglich auf "yes" festgelegt, was bedeutet, dass der Microsoft Access-Treiber auf das Abschließen von Commits in einer internen/impliziten Transaktion wartet.<br /><br /> Der Wert dieser Option sollte nicht geändert werden, ohne dass die Konsequenzen sorgfältig beachtet werden müssen. Weitere Informationen zur Option finden Sie im *Microsoft Jet Datenbank-Engine Programmer es Guide*.<br /><br /> Dadurch wird die gleiche Option wie **ImplicitCommitSync** im Setup Dialogfeld festgelegt.|  
|MAXBUFFERSIZE|Die Größe des internen Puffers in Kilobyte, der von Microsoft Access zum Übertragen von Daten auf den und vom Datenträger verwendet wird. Die Standardpuffergröße beträgt 2048 KB (wird als 2048 angezeigt). Jeder von 256 teilbar ganzzahlige Wert kann verwendet werden. Dadurch wird die gleiche Option wie die **Puffergröße** im Setup Dialogfeld festgelegt.|  
|MaxScanRows|Die Anzahl der Zeilen, die beim Festlegen des Datentyps einer Spalte auf Grundlage vorhandener Daten gescannt werden sollen.<br /><br /> Eine Zahl zwischen 1 und 16 kann für die zu überprüfenden Zeilen eingegeben werden. Der Standardwert ist 8; Wenn der Wert auf 0 festgelegt ist, werden alle Zeilen gescannt. (Eine Zahl außerhalb des Limits gibt einen Fehler zurück.)<br /><br /> Dadurch wird die Option für die **zu über** prüfenden Zeilen im Setup Dialogfeld festgelegt.|  
|PageTimeout|Gibt den Zeitraum in Millisekunden an, den eine Seite (falls nicht verwendet) im Puffer verbleibt, bevor Sie entfernt wird. Der Standardwert ist fünf Zehntelsekunden (0,5 Sekunden). Beachten Sie, dass diese Option für alle Datenquellen gilt, die den ODBC-Treiber verwenden.<br /><br /> Dadurch wird die gleiche Option wie das **Seiten Timeout** im Setup Dialogfeld festgelegt.|  
|PWD|Das Kennwort.|  
|READONLY|TRUE, wenn die Datei schreibgeschützt werden soll. FALSE, wenn die Datei nicht schreibgeschützt sein soll.<br /><br /> Dadurch wird die gleiche **Option wie im** Setup Dialogfeld schreibgeschützt festgelegt.|  
|REPAIR_DB|Repariert eine Datenbank, die durch einen Fehler verursacht wird, der während des Commit-Vorgangs auftritt.<br /><br /> Wenn das REPAIR_DB-Schlüsselwort in derselben Anweisung mit einem DSN-Schlüsselwort verwendet wird, ignoriert dieser Treiber das DSN-Schlüsselwort. Daher ist das Reparieren einer Datenbank und das Angeben eines DSN ein zweistufiger Prozess.|  
|SystemDB|Für den Microsoft Access-Treiber die Pfadspezifikation für die Systemdaten Bank Datei.<br /><br /> Dadurch wird die gleiche Option wie die **System Datenbank** im Setup Dialogfeld festgelegt.|  
|Threads|Die Anzahl der Hintergrundthreads, die von der Engine verwendet werden sollen. Der Standardwert ist 3, kann jedoch geändert werden.<br /><br /> Dadurch wird die gleiche Option wie **Threads** im Setup Dialogfeld festgelegt.|  
|UID|Für den Microsoft Access-Treiber der Benutzer-ID-Name, der für die Anmeldung verwendet wird.|  
|UserCommitSync|Bestimmt, ob der Microsoft Access-Treiber benutzerdefinierte Transaktionen asynchron ausführt. Dieser Wert ist anfänglich auf "yes" festgelegt, was bedeutet, dass der Microsoft Access-Treiber auf das Abschließen von Commits in einer benutzerdefinierten Transaktion wartet.<br /><br /> Der Wert dieser Option sollte nicht geändert werden, ohne dass die Konsequenzen sorgfältig beachtet werden müssen. Weitere Informationen zur Option finden Sie im *Microsoft Jet Datenbank-Engine Programmer es Guide*.<br /><br /> Dadurch wird die gleiche Option wie **UserCommitSync** im Setup Dialogfeld festgelegt.|
