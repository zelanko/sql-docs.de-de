---
title: SQLConfigDataSource (Paradox-Treiber) | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283930"
---
# <a name="sqlconfigdatasource-paradox-driver"></a>SQLConfigDataSource (Paradox-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Paradox-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource** -Funktion, die verwendet wird, um eine Datenquelle hinzuzufügen, zu ändern oder zu löschen, verwendet dynamisch die folgenden Schlüsselwörter.  
  
|Stichwort|BESCHREIBUNG|  
|-------------|-----------------|  
|CollatingSequence|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Wenn der Paradox-Treiber verwendet wird, kann die Sequenz "ASCII (Standard)", "International", "Swedish-Finnish" oder "Norwegian-Danish" sein.<br /><br /> Dadurch wird die gleiche Option wie die **Sortierreihenfolge** im Setup Dialogfeld festgelegt.|  
|DBQ|Der Name der Datenbankdatei.<br /><br /> Dadurch wird die gleiche Option wie die **Datenbank** im Setup Dialogfeld festgelegt.|  
|DefaultDir|Die Pfadspezifikation für das Verzeichnis.|  
|DESCRIPTION|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Dadurch wird die gleiche Option wie die **Beschreibung** im Setup Dialogfeld festgelegt.|  
|DRIVER|Die Pfadspezifikation für die Treiber-DLL.|  
|DriverID|Eine ganzzahlige ID für den Treiber.<br /><br /> 26 (Paradox 3. x)<br /><br /> 282 (Paradox 4. x)<br /><br /> 538 (Paradox 5. x)|  
|Ausschließliche|Bestimmt, ob die Datenbank im exklusiven Modus geöffnet wird (nur von einem Benutzer gleichzeitig aufgerufen) oder im freigegebenen Modus (Zugriff durch mehrere Benutzer gleichzeitig). Kann true (exklusiver Modus) oder false (Shared-Modus) sein.<br /><br /> Dadurch wird im Setup Dialogfeld dieselbe Option wie **exklusiv** festgelegt.|  
|RA|Dateityp Paradox 3. x, Paradox 4. x oder Paradox 5. x|  
|FILETYPE|Dateityp für den Text Treiber (Text).|  
|PageTimeout|Gibt den Zeitraum in Sekunden an, in dem eine Seite (falls nicht verwendet) im Puffer verbleibt, bevor Sie entfernt wird. Der Standardwert ist 600 Zehntelsekunden (60 Sekunden). Beachten Sie, dass diese Option für alle Datenquellen gilt, die den ODBC-Treiber verwenden.<br /><br /> Dadurch wird die gleiche Option wie das **Seiten Timeout** im Setup Dialogfeld festgelegt.|  
|Paradoxinetpath|Der vollständige Pfad des Verzeichnisses, das eine Paradox-Sperr Datenbank enthält, da Sie entweder die Datei Pdoxusrs.net (in Paradox 4) enthält.* x*) oder die Paradox.NET-Datei (in Paradox 5).* x*). Wenn das Verzeichnis keine dieser Dateien enthält, erstellt der Paradox-Treiber einen. Weitere Informationen zu diesen Dateien finden Sie in der Paradox-Dokumentation.<br /><br /> Bevor ein Netzwerk Verzeichnis ausgewählt werden kann, muss ein Paradox-Benutzername eingegeben werden.<br /><br /> Dadurch wird die gleiche Option wie **Select Network Directory** im Setup Dialogfeld festgelegt.|  
|Paradoxinetstyle|Für den Paradox-Treiber der Netzwerk Zugriffs Stil, der für den Zugriff auf Paradox-Daten verwendet werden soll: entweder "3. x" für Paradox 3. *x* oder "4. x" für Paradox 4. *x* oder 5. *x*. Kann auf "3. x" oder "4. x" festgelegt werden, wenn die Version Paradox 4 ist. *x* oder 5. *x*; Wenn die Version Paradox 3 ist. *x*, der Stil muss "3. x" lauten.<br /><br /> Dadurch wird die gleiche Option wie **net Style** im Setup Dialogfeld festgelegt.|  
|"Paradoxiname"|Für den Paradox-Treiber der Paradox-Benutzername.<br /><br /> Dadurch wird die gleiche Option wie der **Benutzer Name** im Setup Dialogfeld festgelegt.|  
|PWD|Das Kennwort.<br /><br /> Hierbei handelt es sich um ein optionales Schlüsselwort, das vom Treiber niemals in die Datei geschrieben wird. Sie wird in einem-Befehl für **SQLDriverConnect** mit Kenn Wort geschützten Paradox-Dateien verwendet. Das verwendete Kennwort ist gültig, wenn eine Tabelle geöffnet wird. Wenn kein Kennwort in der Verbindungs Zeichenfolge angegeben wird, wird kein Kennwort für diese Tabelle festgelegt. Wenn Tabellen über unterschiedliche Kenn Wörter verfügen, kann mehr als eine Sitzung nicht in derselben Sitzung geöffnet werden, und die Tabellen können auch nicht verknüpft werden.|  
|READONLY|TRUE, wenn die Datei schreibgeschützt werden soll. FALSE, wenn die Datei nicht schreibgeschützt sein soll.<br /><br /> Dadurch wird die gleiche **Option wie im** Setup Dialogfeld schreibgeschützt festgelegt.|  
|Threads|Die Anzahl der Hintergrundthreads, die von der Engine verwendet werden sollen. Dieser Wert ist 3 und kann nicht geändert werden.<br /><br /> Dadurch wird die gleiche Option wie **Threads** im Setup Dialogfeld festgelegt.|
