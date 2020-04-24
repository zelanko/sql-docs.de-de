---
title: SQLConfigDataSource (dBASE-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], dBASE Driver
ms.assetid: 19909902-054c-4e19-9c06-a212aace13fe
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 18c6721b4f34772e8c3cd8e4f515233f80566fb3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283970"
---
# <a name="sqlconfigdatasource-dbase-driver"></a>SQLConfigDataSource (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält dBASE-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource-Funktion,** die zum Hinzufügen, Ändern oder Löschen einer Datenquelle verwendet wird, verwendet dynamisch die folgenden Schlüsselwörter.  
  
|Schlüsselwort|BESCHREIBUNG|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Die Reihenfolge kann sein: ASCII (Standard) oder International.<br /><br /> Dadurch wird die gleiche Option wie **Sequenz sammeln** im Dialogfeld Setup festgelegt.|  
|DEFAULTDIR|Die Pfadspezifikation zum Verzeichnis.|  
|DELETED|Gibt für den dBASE-Treiber an, ob Zeilen, die als gelöscht markiert wurden, abgerufen oder positioniert werden können. Wenn auf 1 gesetzt, werden gelöschte Zeilen nicht angezeigt. Wenn auf 0 gesetzt, werden gelöschte Zeilen wie nicht gelöschte Zeilen behandelt.<br /><br /> Dadurch wird dieselbe Option wie **Gelöschte Zeilen** anzeigen im Dialogfeld Setup festgelegt.|  
|DESCRIPTION|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Dadurch wird die gleiche Option wie **Beschreibung** im Dialogfeld Setup festgelegt.|  
|DRIVER|Die Pfadspezifikation für die Treiber-DLL.|  
|DRIVERID|Eine ganzzahlige ID für den Treiber.<br /><br /> 21 (dBASE III)<br /><br /> 277 (dBASE IV)<br /><br /> 533 (dBASE 5.0)|  
|Fil|Dateityp dBase III, dBase IV oder dBase 5|  
|PAGETIMEOUT|Gibt den Zeitraum in Zehntelsekunden an, in dem eine Seite (falls nicht verwendet) im Puffer verbleibt, bevor sie entfernt wird. Der Standardwert ist 600 Zehntelsekunden (60 Sekunden). Beachten Sie, dass diese Option für alle Datenquellen gilt, die den ODBC-Treiber verwenden.<br /><br /> Dadurch wird dieselbe Option wie **Seitentimeout** im Dialogfeld Setup festgelegt.|  
|READONLY|TRUE, um Datei schreibgeschützt zu machen; FALSE, um die Datei nicht schreibgeschützt zu machen.<br /><br /> Dadurch wird die gleiche Option wie **Nur lesen** im Dialogfeld Setup festgelegt.|  
|STATISTICS|Bestimmt für den dBASE-Treiber, ob Tabellengrößenstatistiken angenähert werden. Beachten Sie, dass diese Option für alle Datenquellen gilt, die den ODBC-Treiber verwenden.<br /><br /> Dadurch wird dieselbe Option wie **Ungefähre Zeilenanzahl** im Setup-Dialogfeld festgelegt.|  
|Threads|Die Anzahl der Hintergrundthreads, die das Modul verwenden soll. Dieser Wert ist 3 und kann nicht geändert werden.<br /><br /> Dadurch wird die gleiche Option wie **Threads** im Dialogfeld Setup festgelegt.|
