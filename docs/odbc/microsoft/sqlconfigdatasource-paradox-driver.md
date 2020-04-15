---
title: SQLConfigDataSource (Paradox-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLConfigDataSource
ms.assetid: 59e84c4e-debe-49d7-b97b-84c736b0c793
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68e60d7ca9c37865c1b265297d24591638a44965
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283930"
---
# <a name="sqlconfigdatasource-paradox-driver"></a>SQLConfigDataSource (Paradox-Treiber)
> [!NOTE]  
>  Dieses Thema enthält paradox driverspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource-Funktion,** die zum Hinzufügen, Ändern oder Löschen einer Datenquelle verwendet wird, verwendet dynamisch die folgenden Schlüsselwörter.  
  
|Schlüsselwort|BESCHREIBUNG|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Wenn der Paradox-Treiber verwendet wird, kann die Sequenz ASCII (Standard), International, Schwedisch-Finnisch oder Norwegisch-Dänisch sein.<br /><br /> Dadurch wird die gleiche Option wie **Sequenz sammeln** im Dialogfeld Setup festgelegt.|  
|Dbq|Der Name der Datenbankdatei.<br /><br /> Dadurch wird die gleiche Option wie **Datenbank** im Dialogfeld Setup festgelegt.|  
|DEFAULTDIR|Die Pfadspezifikation zum Verzeichnis.|  
|DESCRIPTION|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Dadurch wird die gleiche Option wie **Beschreibung** im Dialogfeld Setup festgelegt.|  
|DRIVER|Die Pfadspezifikation für die Treiber-DLL.|  
|DRIVERID|Eine ganzzahlige ID für den Treiber.<br /><br /> 26 (Paradox 3.x)<br /><br /> 282 (Paradox 4.x)<br /><br /> 538 (Paradox 5.x)|  
|Exklusive|Legt fest, ob die Datenbank im exklusiven Modus (auf den jeweils nur ein Benutzer zugreifen) oder im freigegebenen Modus (auf den jeweils mehr als ein Benutzer zugreifen) geöffnet wird. Kann true (exklusiver Modus) oder false (shared mode) sein.<br /><br /> Dadurch wird die gleiche Option wie **Exklusiv** im Dialogfeld Setup festgelegt.|  
|Fil|Dateityp Paradox 3.x, Paradox 4.x oder Paradox 5.x|  
|Filetype|Dateityp für den Texttreiber (Text).|  
|PAGETIMEOUT|Gibt den Zeitraum in Zehntelsekunden an, in dem eine Seite (falls nicht verwendet) im Puffer verbleibt, bevor sie entfernt wird. Der Standardwert ist 600 Zehntelsekunden (60 Sekunden). Beachten Sie, dass diese Option für alle Datenquellen gilt, die den ODBC-Treiber verwenden.<br /><br /> Dadurch wird dieselbe Option wie **Seitentimeout** im Dialogfeld Setup festgelegt.|  
|PARADOXNETPATH|Der vollständige Pfad des Verzeichnisses, das eine Paradox-Sperrdatenbank enthält, da es entweder die PDOXUSRS.net-Datei enthält (in Paradox 4.* x*) oder die PARADOX.net Datei (in Paradox 5.* x*). Wenn das Verzeichnis keine dieser Dateien enthält, erstellt der Paradox-Treiber eine. Informationen zu diesen Dateien finden Sie in der Paradox-Dokumentation.<br /><br /> Bevor ein Netzwerkverzeichnis ausgewählt werden kann, muss ein Paradox-Benutzername eingegeben werden.<br /><br /> Dadurch wird dieselbe Option wie **Netzwerkverzeichnis** auswählen im Dialogfeld Setup festgelegt.|  
|PARADOXNETSTYLE|Für den Paradox-Treiber ist der Netzwerkzugriffsstil für den Zugriff auf Paradox-Daten zu verwenden: entweder "3.x" für Paradox 3. *x* oder "4.x" für Paradox 4. *x* oder 5. *x*. Kann auf "3.x" oder "4.x" gesetzt werden, wenn die Version Paradox 4 ist. *x* oder 5. *x*; wenn die Version Paradox 3 ist. *x*muss der Stil "3.x" sein.<br /><br /> Dadurch wird die gleiche Option wie **Net Style** im Dialogfeld Setup festgelegt.|  
|PARADOXUSERNAME|Für den Paradox-Treiber den Paradox-Benutzernamen.<br /><br /> Dadurch wird dieselbe Option wie **Benutzername** im Dialogfeld Setup festgelegt.|  
|PWD|Das Kennwort.<br /><br /> Dies ist ein optionales Schlüsselwort und wird nie vom Treiber in die Datei geschrieben. Es wird in einem Aufruf von **SQLDriverConnect** gegen kennwortgesicherte Paradox-Dateien verwendet. Das verwendete Kennwort ist gültig, wenn eine Tabelle geöffnet wird. Wenn in der Verbindungszeichenfolge kein Kennwort übergeben wird, wird kein Kennwort für diese Tabelle eingerichtet. Wenn Tabellen unterschiedliche Kennwörter haben, können nicht mehr als eine in derselben Sitzung geöffnet werden, und die Tabellen können auch nicht verknüpft werden.|  
|READONLY|TRUE, um Datei schreibgeschützt zu machen; FALSE, um die Datei nicht schreibgeschützt zu machen.<br /><br /> Dadurch wird die gleiche Option wie **Nur lesen** im Dialogfeld Setup festgelegt.|  
|Threads|Die Anzahl der Hintergrundthreads, die das Modul verwenden soll. Dieser Wert ist 3 und kann nicht geändert werden.<br /><br /> Dadurch wird die gleiche Option wie **Threads** im Dialogfeld Setup festgelegt.|
