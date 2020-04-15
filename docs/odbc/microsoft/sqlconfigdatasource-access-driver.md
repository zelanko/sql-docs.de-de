---
title: SQLConfigDataSource (Zugriffstreiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 48668525b578845fc330881d7c7de503d69d0928
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284050"
---
# <a name="sqlconfigdatasource-access-driver"></a>SQLConfigDataSource (Access-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Access Driver-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource-Funktion,** die zum Hinzufügen, Ändern oder Löschen einer Datenquelle verwendet wird, verwendet dynamisch die folgenden Schlüsselwörter.  
  
|Schlüsselwort|BESCHREIBUNG|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Dadurch wird die gleiche Option wie **Sequenz sammeln** im Dialogfeld Setup festgelegt.|  
|COMPACT_DB|Führt die Datenkomprimierung für eine Datenbankdatei aus. Hat das folgende Format: COMPACT_DB= \<<path_name><optionaL_sort_order>optionaL_sort_order optionale ENCRYPT-Schlüsselwort> path_name.<br /><br /> Wenn Sie das Schlüsselwort COMPACT_DB in derselben Anweisung mit einem DSN-Schlüsselwort verwenden, ignoriert dieser Treiber das DSN-Schlüsselwort. Daher ist das Komprimieren einer Datenbank und das Angeben eines DSN ein zweistufiger Prozess.|  
|CREATE_DB|Erstellt eine Datenbankdatei. Hat das folgende Format: CREATE_DB=<path_name>\<><optional_ENCRYPT Schlüsselwort> optional_sort Reihenfolge, wobei der Pfadname der vollständige Pfad zu einer Microsoft Access-Datenbank ist. Ein Fehler wird zurückgegeben, wenn der Pfadname eine vorhandene Datenbank angibt. Die Sortierreihenfolge wird wie im Dialogfeld Neue Datenbank eingerichtet, wenn die Schaltfläche Erstellen im Dialogfeld Microsoft Access Setup gedrückt wird. Wenn keine Sortierreihenfolge angegeben ist, wird General verwendet.<br /><br /> Wenn Sie das CREATE_DB-Schlüsselwort in derselben Anweisung mit einem DSN-Schlüsselwort verwenden, ignoriert dieser Treiber das DSN-Schlüsselwort. Daher ist das Erstellen einer Datenbank und das Angeben eines DSN ein zweistufiger Prozess. Wenn der Pfadname der zu erstellenden Microsoft Access-Datenbank ein oder mehrere Leerzeichen enthält, muss bei Verwendung des Schlüsselworts CREATE_DB ein oder mehrere Leerzeichen enthalten, der gesamte Pfadname muss durch doppelte Anführungszeichen eingeschlossen werden, wie in den folgenden Beispielen gezeigt:<br /><br /> "C:-PROGRAM FILES-COMMON FILES- MyAccess.mdb"<br /><br /> "C:-PROGRAMM-DATEIEN-Access2.mdb"<br /><br /> CREATE_DB=C:'TEMP'test.mdb (keine Anführungszeichen erforderlich)|  
|CREATE_SYSDB|Erstellt eine Systemdatenbankdatei. Hat das folgende Format:\<CREATE_SYSDB= \<Pfadname>optional-sort-order>, wobei der Pfadname der vollständige Pfad zu einer Microsoft Access-Datenbank ist. Ein Fehler wird zurückgegeben, wenn der Pfadname eine vorhandene Datenbank angibt. Die Sortierreihenfolge wird wie im Dialogfeld **Neue Datenbank** eingerichtet, wenn im Dialogfeld **ODBC Microsoft Access Setup** auf die Schaltfläche **Erstellen** geklickt wird. Wenn keine Sortierreihenfolge angegeben ist, wird General verwendet.|  
|CREATE_V2DB|Erstellt eine Datenbankdatei, die mit Microsoft Access 2.0 kompatibel ist. Hat das folgende Format:\<CREATE_V2DB= \<pfad-name>optional-sort-order>, wobei der Pfadname der vollständige Pfad zu einer Microsoft Access-Datenbank ist. Ein Fehler wird zurückgegeben, wenn der Pfadname eine vorhandene Datenbank angibt. Die Sortierreihenfolge wird wie im Dialogfeld Neue Datenbank eingerichtet, wenn die Schaltfläche Erstellen im Dialogfeld Microsoft Access Setup gedrückt wird. Wenn keine Sortierreihenfolge angegeben ist, wird General verwendet.<br /><br /> Wenn Sie das Schlüsselwort CREATE_V2DB in derselben Anweisung mit einem DSN-Schlüsselwort verwenden, ignoriert dieser Treiber das DSN-Schlüsselwort. Daher ist das Erstellen einer Datenbank und das Angeben eines DSN ein zweistufiger Prozess.<br /><br /> Wenn der Pfadname der zu erstellenden Microsoft Access-Datenbank ein oder mehrere Leerzeichen enthält, muss bei Verwendung des Schlüsselworts CREATE_V2DB ein oder mehrere Leerzeichen enthalten, der gesamte Pfadname muss durch doppelte Anführungszeichen eingeschlossen werden, wie in den folgenden Beispielen gezeigt:<br /><br /> "C:-PROGRAM FILES-COMMON FILES- MyAccess.mdb"<br /><br /> "C:-PROGRAMM-DATEIEN-Access2.mdb"<br /><br /> CREATE_V2DB=C:-TEMP-Test.mdb (keine Anführungszeichen erforderlich)|  
|Dbq|Der Name der Datenbankdatei.<br /><br /> Dadurch wird die gleiche Option wie **Datenbank** im Dialogfeld Setup festgelegt.|  
|DEFAULTDIR|Die Pfadspezifikation zur Datenbankdatei.|  
|DESCRIPTION|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Dadurch wird die gleiche Option wie **Beschreibung** im Dialogfeld Setup festgelegt.|  
|DRIVER|Die Pfadspezifikation für die Treiber-DLL.|  
|DRIVERID|Eine ganzzahlige ID für den Treiber.  25 (Microsoft Access)|  
|Fil|Dateityp MS Access für Microsoft Access|  
|IMPLIZITES COMMITSYNC|Legt fest, ob der Microsoft Access-Treiber interne oder implizite Commits asynchron ausführt. Dieser Wert wird zunächst auf "Ja" festgelegt, was bedeutet, dass der Microsoft Access-Treiber auf den Abschluss von Commits in einer internen/impliziten Transaktion wartet.<br /><br /> Der Wert dieser Option sollte nicht ohne sorgfältige Berücksichtigung der Folgen geändert werden. Weitere Informationen zu dieser Option finden Sie im *Microsoft Jet Database Engine Programmer es Guide*.<br /><br /> Dadurch wird die gleiche Option wie **ImplicitCommitSync** im Setup-Dialogfeld festgelegt.|  
|Maxbuffersize|Die Größe des internen Puffers in Kilobyte, der von Microsoft Access zum Übertragen von Daten auf und von der Festplatte verwendet wird. Die Standardpuffergröße beträgt 2048 KB (angezeigt als 2048). Jeder ganzzahlige Wert, der durch 256 teilbar ist, kann verwendet werden. Dadurch wird dieselbe Option wie **Puffergröße** im Dialogfeld Setup festgelegt.|  
|MAXSCANROWS|Die Anzahl der Zu scannenden Zeilen beim Festlegen des Datentyps einer Spalte basierend auf vorhandenen Daten.<br /><br /> Für die zu scannenden Zeilen kann eine Zahl von 1 bis 16 eingegeben werden. Der Wert ist standardmäßig 8; Wenn sie auf 0 gesetzt ist, werden alle Zeilen gescannt. (Eine Zahl außerhalb des Limits gibt einen Fehler zurück.)<br /><br /> Dadurch wird die gleiche Option wie **Zeilen zum Scannen** im Setup-Dialogfeld festgelegt.|  
|PAGETIMEOUT|Gibt den Zeitraum in Millisekunden an, in dem eine Seite (falls nicht verwendet) im Puffer verbleibt, bevor sie entfernt wird. Der Standardwert ist fünf Zehntelsekunden (0,5 Sekunden). Beachten Sie, dass diese Option für alle Datenquellen gilt, die den ODBC-Treiber verwenden.<br /><br /> Dadurch wird dieselbe Option wie **Seitentimeout** im Dialogfeld Setup festgelegt.|  
|PWD|Das Kennwort.|  
|READONLY|TRUE, um Datei schreibgeschützt zu machen; FALSE, um die Datei nicht schreibgeschützt zu machen.<br /><br /> Dadurch wird die gleiche Option wie **Nur lesen** im Dialogfeld Setup festgelegt.|  
|REPAIR_DB|Repariert eine Datenbank, die durch einen Fehler beschädigt wurde, der während des Commitvorgangs auftritt.<br /><br /> Wenn Sie das Schlüsselwort REPAIR_DB in derselben Anweisung mit einem DSN-Schlüsselwort verwenden, ignoriert dieser Treiber das DSN-Schlüsselwort. Daher ist das Reparieren einer Datenbank und das Angeben eines DSN ein zweistufiger Prozess.|  
|SYSTEMDB|Für den Microsoft Access-Treiber die Pfadspezifikation zur Systemdatenbankdatei.<br /><br /> Dadurch wird die gleiche Option wie **die Systemdatenbank** im Dialogfeld Setup festgelegt.|  
|Threads|Die Anzahl der Hintergrundthreads, die das Modul verwenden soll. Dieser Wert ist standardmäßig 3, kann jedoch geändert werden.<br /><br /> Dadurch wird die gleiche Option wie **Threads** im Dialogfeld Setup festgelegt.|  
|UID|Für den Microsoft Access-Treiber den Benutzernamen, der für die Anmeldung verwendet wird.|  
|USERCOMMITSYNC|Bestimmt, ob der Microsoft Access-Treiber benutzerdefinierte Transaktionen asynchron ausführt. Dieser Wert wird zunächst auf "Ja" festgelegt, was bedeutet, dass der Microsoft Access-Treiber auf den Abschluss von Commits in einer benutzerdefinierten Transaktion wartet.<br /><br /> Der Wert dieser Option sollte nicht ohne sorgfältige Berücksichtigung der Folgen geändert werden. Weitere Informationen zu dieser Option finden Sie im *Microsoft Jet Database Engine Programmer es Guide*.<br /><br /> Dadurch wird die gleiche Option wie **UserCommitSync** im Dialogfeld Setup festgelegt.|
