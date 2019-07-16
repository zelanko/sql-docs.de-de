---
title: SQLConfigDataSource (dBASE-Treiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 569a83110d7d5a3cd25eed8f68753d13793f8b10
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054101"
---
# <a name="sqlconfigdatasource-dbase-driver"></a>SQLConfigDataSource (dBASE-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die dBASE-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource** -Funktion, die verwendet wird, zum Hinzufügen, ändern oder Löschen einer Datenquelle verwendet die folgenden Schlüsselwörter.  
  
|Schlüsselwort|Beschreibung|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Die Sequenz sind möglich: ASCII (Standard) und internationale.<br /><br /> Hiermit wird die gleiche Option als **Sortierreihenfolge Sequenz** im Dialogfeld "Setup".|  
|WERT|Die Pfadangabe in das Verzeichnis.|  
|DELETED|DBASE-Treiber gibt an, ob Zeilen, die als gelöscht markiert wurden abgerufen oder auf positioniert werden können. Wenn es sich bei Festlegung auf 1, gelöschte Zeilen nicht angezeigt werden; Wenn es sich bei Festlegung auf 0, gelöschte Zeilen werden als nicht gelöschter Zeilen behandelt.<br /><br /> Hiermit wird die gleiche Option als **anzeigen gelöschter Zeilen** im Dialogfeld "Setup".|  
|DESCRIPTION|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Hiermit wird die gleiche Option als **Beschreibung** im Dialogfeld "Setup".|  
|DRIVER|Die Pfadangabe für den Treiber-DLL.|  
|DRIVERID|Eine ganzzahlige ID für den Treiber.<br /><br /> 21 (dBASE III)<br /><br /> 277 (dBASE IV)<br /><br /> 533 (dBASE 5.0)|  
|FIL|Datei geben dBase III, dBase IV oder dBase 5|  
|' PAGETIMEOUT '|Gibt den Zeitraum, in Zehntelsekunden, die eine Seite (sofern nicht verwendet wird) im Puffer bleibt, bevor Sie entfernt werden. Der Standardwert ist 600 Zehntelsekunden (60 Sekunden). Beachten Sie, dass diese Option auf alle Datenquellen gilt, die den ODBC-Treiber verwenden.<br /><br /> Hiermit wird die gleiche Option als **Page Timeout** im Dialogfeld "Setup".|  
|READONLY|True, um die Datei schreibgeschützt zu machen. "False", um die Datei nicht schreibgeschützt machen.<br /><br /> Hiermit wird die gleiche Option als **Read Only** im Dialogfeld "Setup".|  
|STATISTICS|DBASE-Treiber bestimmt, ob die Größe von Tabellenstatistiken angeglichen werden. Beachten Sie, dass diese Option auf alle Datenquellen gilt, die den ODBC-Treiber verwenden.<br /><br /> Hiermit wird die gleiche Option als **Ungefähre Zeilenanzahl** im Dialogfeld "Setup".|  
|THREADS|Die Anzahl von Hintergrundthreads für das Modul zu verwenden. Dieser Wert ist 3 und kann nicht geändert werden.<br /><br /> Hiermit wird die gleiche Option als **Threads** im Dialogfeld "Setup".|
