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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 33cc778d921b90a460dab6bda352fd7627d2cf7b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054074"
---
# <a name="sqlconfigdatasource-paradox-driver"></a>SQLConfigDataSource (Paradox-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Paradox-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource** -Funktion, die verwendet wird, zum Hinzufügen, ändern oder Löschen einer Datenquelle verwendet die folgenden Schlüsselwörter.  
  
|Schlüsselwort|Beschreibung|  
|-------------|-----------------|  
|COLLATINGSEQUENCE|Die Reihenfolge, in der die Felder sortiert werden.<br /><br /> Wenn die Paradox-Treiber verwendet wird, kann die Sequenz ASCII (Standard) sein, internationale, Finnish-Swedish oder Danish-Norwegian.<br /><br /> Hiermit wird die gleiche Option als **Sortierreihenfolge Sequenz** im Dialogfeld "Setup".|  
|DBQ|Der Name der Datenbankdatei.<br /><br /> Hiermit wird die gleiche Option als **Datenbank** im Dialogfeld "Setup".|  
|WERT|Die Pfadangabe in das Verzeichnis.|  
|DESCRIPTION|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Hiermit wird die gleiche Option als **Beschreibung** im Dialogfeld "Setup".|  
|DRIVER|Die Pfadangabe für den Treiber-DLL.|  
|DRIVERID|Eine ganzzahlige ID für den Treiber.<br /><br /> 26 (Paradox 3.x)<br /><br /> 282 (Paradox 4.x)<br /><br /> 538 (Paradox 5.x)|  
|EXKLUSIVE|Bestimmt, ob die Datenbank im exklusiven Modus (Zugriff durch mehrere Benutzer gleichzeitig) geöffnet oder shared-Modus wird (Zugriff durch mehrere Benutzer gleichzeitig). Kann "true" (im exklusiven Modus) oder "false" (shared-Modus).<br /><br /> Hiermit wird die gleiche Option als **exklusive** im Dialogfeld "Setup".|  
|FIL|Dateityp Paradox 3.x, Paradox 4.x oder Paradox 5.x|  
|DATEITYP|Der Dateityp für den Text-Treiber (Text).|  
|' PAGETIMEOUT '|Gibt den Zeitraum, in Zehntelsekunden, die eine Seite (sofern nicht verwendet wird) im Puffer bleibt, bevor Sie entfernt werden. Der Standardwert ist 600 Zehntelsekunden (60 Sekunden). Beachten Sie, dass diese Option auf alle Datenquellen gilt, die den ODBC-Treiber verwenden.<br /><br /> Hiermit wird die gleiche Option als **Page Timeout** im Dialogfeld "Setup".|  
|X|Der vollständige Pfad des Verzeichnisses mit der eine Sperre Paradox-Datenbank, weil sie entweder die PDOXUSRS.net-Datei enthält (Paradox-4. *X*) oder die Datei PARADOX.net (Paradox-5. *X*). Wenn das Verzeichnis nicht mit einer dieser Dateien enthält, die Paradox-Treiber wird erstellt. Informationen zu diesen Dateien finden Sie unter der Dokumentation für die Paradox.<br /><br /> Bevor ein Netzwerkverzeichnis ausgewählt werden kann, muss ein Benutzernamen für die Paradox eingegeben werden.<br /><br /> Hiermit wird die gleiche Option als **Netzwerkverzeichnis wählen** im Dialogfeld "Setup".|  
|PARADOXNETSTYLE|Für die Paradox-Treiber, Zugriff auf das Netzwerk zu verwendende Format beim Paradox-Daten: entweder "3.x" für Paradox-3. *x* oder "4.x" für Paradox 4. *X* oder 5. *X*. Kann festgelegt werden, "3.x" oder "4.x" ist die Version 4 von Paradox. *x* oder 5. *X*; Wenn die Version 3 für Paradox. *X*, das Format muss "3.x" sein.<br /><br /> Hiermit wird die gleiche Option als **Net Stil** im Dialogfeld "Setup".|  
|PARADOXUSERNAME|Für die Paradox-Treiber, den Benutzernamen für die Paradox.<br /><br /> Hiermit wird die gleiche Option als **Benutzernamen** im Dialogfeld "Setup".|  
|PWD|Das Kennwort.<br /><br /> Dies ist ein optionales Schlüsselwort, und wird vom Treiber nicht in die Datei geschrieben werden. Hiermit wird in einem Aufruf von **SQLDriverConnect** für Kennwort-gesicherte Paradox-Dateien. Das verwendete Kennwort ist gültig, wenn eine Tabelle geöffnet wird. Wenn kein Kennwort in der Verbindungszeichenfolge übergeben wird, wird kein Kennwort für diese Tabelle eingerichtet. Wenn Tabellen verschiedene Kennwörter verwendet werden, mehr als eine kann nicht geöffnet werden, in der gleichen Sitzung, noch können in den Tabellen verknüpft werden.|  
|READONLY|True, um die Datei schreibgeschützt zu machen. "False", um die Datei nicht schreibgeschützt machen.<br /><br /> Hiermit wird die gleiche Option als **Read Only** im Dialogfeld "Setup".|  
|THREADS|Die Anzahl von Hintergrundthreads für das Modul zu verwenden. Dieser Wert ist 3, und kann nicht geändert werden.<br /><br /> Hiermit wird die gleiche Option als **Threads** im Dialogfeld "Setup".|
