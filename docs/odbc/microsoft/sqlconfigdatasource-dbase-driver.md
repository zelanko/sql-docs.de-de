---
description: SQLConfigDataSource (dBASE-Treiber)
title: SQLConfigDataSource (dBase-Treiber) | Microsoft-Dokumentation
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
ms.openlocfilehash: 23e734c5aafc903e210eea18f002f4c5e8d7a456
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88411956"
---
# <a name="sqlconfigdatasource-dbase-driver"></a>SQLConfigDataSource (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu dBASE-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource** -Funktion, die verwendet wird, um eine Datenquelle hinzuzufügen, zu ändern oder zu löschen, verwendet dynamisch die folgenden Schlüsselwörter.  
  
|Schlüsselwort|Beschreibung|  
|-------------|-----------------|  
|CollatingSequence|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Die Sequenz kann wie folgt lauten: ASCII (Standard) oder International.<br /><br /> Dadurch wird die gleiche Option wie die **Sortierreihenfolge** im Setup Dialogfeld festgelegt.|  
|DefaultDir|Die Pfadspezifikation für das Verzeichnis.|  
|DELETED|Gibt für den dBase-Treiber an, ob Zeilen, die als gelöscht markiert wurden, abgerufen oder positioniert werden können. Wenn der Wert auf 1 festgelegt ist, werden gelöschte Zeilen nicht angezeigt. Wenn der Wert auf 0 festgelegt ist, werden gelöschte Zeilen wie nicht gelöschte Zeilen behandelt.<br /><br /> Dadurch wird die gleiche Option wie das **Anzeigen gelöschter Zeilen** im Setup Dialogfeld festgelegt.|  
|DESCRIPTION|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Dadurch wird die gleiche Option wie die **Beschreibung** im Setup Dialogfeld festgelegt.|  
|DRIVER|Die Pfadspezifikation für die Treiber-DLL.|  
|DriverID|Eine ganzzahlige ID für den Treiber.<br /><br /> 21 (dBASE III)<br /><br /> 277 (dBASE IV)<br /><br /> 533 (dBASE 5,0)|  
|RA|Dateityp dBASE III, dBASE IV oder dBASE 5|  
|PageTimeout|Gibt den Zeitraum in Sekunden an, in dem eine Seite (falls nicht verwendet) im Puffer verbleibt, bevor Sie entfernt wird. Der Standardwert ist 600 Zehntelsekunden (60 Sekunden). Beachten Sie, dass diese Option für alle Datenquellen gilt, die den ODBC-Treiber verwenden.<br /><br /> Dadurch wird die gleiche Option wie das **Seiten Timeout** im Setup Dialogfeld festgelegt.|  
|READONLY|TRUE, wenn die Datei schreibgeschützt werden soll. FALSE, wenn die Datei nicht schreibgeschützt sein soll.<br /><br /> Dadurch wird die gleiche **Option wie im** Setup Dialogfeld schreibgeschützt festgelegt.|  
|STATISTICS|Bestimmt für den dBase-Treiber, ob die Statistiken der Tabellengröße angleichen. Beachten Sie, dass diese Option für alle Datenquellen gilt, die den ODBC-Treiber verwenden.<br /><br /> Dadurch wird die gleiche Option wie die **ungefähre Zeilen Anzahl** im Setup Dialogfeld festgelegt.|  
|Threads|Die Anzahl der Hintergrundthreads, die von der Engine verwendet werden sollen. Dieser Wert ist 3 und kann nicht geändert werden.<br /><br /> Dadurch wird die gleiche Option wie **Threads** im Setup Dialogfeld festgelegt.|
