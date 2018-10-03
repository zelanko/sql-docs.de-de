---
title: ODBC Jet SQLConfigDataSource (Excel-Treiber) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dbad3b1e6dda82a9f9fc584683e53f8e2a109cca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47715388"
---
# <a name="odbc-jet-sqlconfigdatasource-excel-driver"></a>ODBC Jet SQLConfigDataSource (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Excel-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource** -Funktion, die verwendet wird, zum Hinzufügen, ändern oder Löschen einer Datenquelle verwendet die folgenden Schlüsselwörter.  
  
|Schlüsselwort|Description|  
|-------------|-----------------|  
|DBQ|Für den Microsoft Excel-Treiber beim Zugriff auf Microsoft Excel 5.0 oder höher Dateien, den Namen der Arbeitsmappendatei.<br /><br /> Hiermit wird die gleiche Option als **Datenbank** im Dialogfeld "Setup".|  
|WERT|Die Pfadangabe in das Verzeichnis.<br /><br /> Hiermit wird die gleiche Option als **Verzeichnis auswählen** oder **Arbeitsmappe auswählen** im Dialogfeld "Setup".|  
|DESCRIPTION|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Hiermit wird die gleiche Option als **Beschreibung** im Dialogfeld "Setup".|  
|DRIVER|Die Pfadangabe für den Treiber-DLL.|  
|DRIVERID|Eine ganzzahlige ID für den Treiber.<br /><br /> 534 (Microsoft Excel 3.0)<br /><br /> 278 (Microsoft Excel 4.0)<br /><br /> 22 (Microsoft Excel 5.0/7.0)<br /><br /> 790 (Microsoft Excel 97-2003)|  
|FIL|Dateityp, z. B. Excel 3.0, Excel 4.0, 5.0 für Excel, Excel 7.0, Excel 97, Excel 2000 oder Excel 2003.|  
|FIRSTROWHASNAMES|Gibt an, ob die Zellen der ersten Zeile des Bereichs die Spaltennamen für die Tabelle (1) oder nicht enthalten (0).|  
|MAXSCANROWS|Die Anzahl von Zeilen gescannt werden müssen, wenn Sie einen Spaltendatentyp basierend auf den vorhandenen Daten festlegen.<br /><br /> Eine Zahl zwischen 1 und 16 kann für die Zeilen zu scannen eingegeben werden. Der Standardwert ist 8; Wenn es auf 0 festgelegt ist, werden alle Zeilen überprüft. (Eine Zahl außerhalb der Grenzwert wird einen Fehler zurückgegeben.)<br /><br /> Hiermit wird die gleiche Option als **zu scannende Zeilen** im Dialogfeld "Setup".|  
|READONLY|True, um die Datei schreibgeschützt zu machen. "False", um die Datei nicht schreibgeschützt machen.<br /><br /> Hiermit wird die gleiche Option als **Read Only** im Dialogfeld "Setup".|  
|THREADS|Die Anzahl von Hintergrundthreads für das Modul zu verwenden. Microsoft Access-Treiber wird dieser Wert standardmäßig auf 3 jedoch geändert werden kann. Für die dBASE MicrosoftExceldriver dieser Wert ist 3, und kann nicht geändert werden.<br /><br /> Hiermit wird die gleiche Option als **Threads** im Dialogfeld "Setup".|
