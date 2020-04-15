---
title: ODBC Jet SQLConfigDataSource (Excel-Treiber) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLConfigDataSource function [ODBC], Excel Driver
- Excel driver [ODBC], SqlConfigDataSource
ms.assetid: 885b3bea-f4b6-4902-b994-f78a912b612f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a76482acd1182d900336d7ac9826b16968e00caa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293010"
---
# <a name="odbc-jet-sqlconfigdatasource-excel-driver"></a>ODBC Jet SQLConfigDataSource (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Excel-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource-Funktion,** die zum Hinzufügen, Ändern oder Löschen einer Datenquelle verwendet wird, verwendet dynamisch die folgenden Schlüsselwörter.  
  
|Schlüsselwort|BESCHREIBUNG|  
|-------------|-----------------|  
|Dbq|Für den Microsoft Excel-Treiber beim Zugriff auf Microsoft Excel 5.0 oder höher Dateien der Name der Arbeitsmappendatei.<br /><br /> Dadurch wird die gleiche Option wie **Datenbank** im Dialogfeld Setup festgelegt.|  
|DEFAULTDIR|Die Pfadspezifikation zum Verzeichnis.<br /><br /> Dadurch wird dieselbe Option wie **Verzeichnis auswählen** oder **Arbeitsmappe** auswählen im Dialogfeld Setup festgelegt.|  
|DESCRIPTION|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Dadurch wird die gleiche Option wie **Beschreibung** im Dialogfeld Setup festgelegt.|  
|DRIVER|Die Pfadspezifikation für die Treiber-DLL.|  
|DRIVERID|Eine ganzzahlige ID für den Treiber.<br /><br /> 534 (Microsoft Excel 3.0)<br /><br /> 278 (Microsoft Excel 4.0)<br /><br /> 22 (Microsoft Excel 5.0/7.0)<br /><br /> 790 (Microsoft Excel 97-2003)|  
|Fil|Dateityp, z. B. Excel 3.0, Excel 4.0, Excel 5.0, Excel 7.0, Excel 97, Excel 2000 oder Excel 2003.|  
|FIRSTROWHASNAMES|Gibt an, ob die Zellen der ersten Zeile des Bereichs die Spaltennamen für die Tabelle (1) enthalten oder nicht (0).|  
|MAXSCANROWS|Die Anzahl der Zu scannenden Zeilen beim Festlegen des Datentyps einer Spalte basierend auf vorhandenen Daten.<br /><br /> Für die zu scannenden Zeilen kann eine Zahl von 1 bis 16 eingegeben werden. Der Wert ist standardmäßig 8; Wenn sie auf 0 gesetzt ist, werden alle Zeilen gescannt. (Eine Zahl außerhalb des Limits gibt einen Fehler zurück.)<br /><br /> Dadurch wird die gleiche Option wie **Zeilen zum Scannen** im Setup-Dialogfeld festgelegt.|  
|READONLY|TRUE, um Datei schreibgeschützt zu machen; FALSE, um die Datei nicht schreibgeschützt zu machen.<br /><br /> Dadurch wird die gleiche Option wie **Nur lesen** im Dialogfeld Setup festgelegt.|  
|Threads|Die Anzahl der Hintergrundthreads, die das Modul verwenden soll. Für den Microsoft Access-Treiber ist dieser Wert standardmäßig 3, kann jedoch geändert werden. Für dBASE, MicrosoftExceldriver, ist dieser Wert 3 und kann nicht geändert werden.<br /><br /> Dadurch wird die gleiche Option wie **Threads** im Dialogfeld Setup festgelegt.|
