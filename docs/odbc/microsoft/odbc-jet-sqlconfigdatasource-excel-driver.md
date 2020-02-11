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
ms.openlocfilehash: ab33bfdef2b633cd5a7a3e215a3f6522d8d664ca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915703"
---
# <a name="odbc-jet-sqlconfigdatasource-excel-driver"></a>ODBC Jet SQLConfigDataSource (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Excel-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource** -Funktion, die verwendet wird, um eine Datenquelle hinzuzufügen, zu ändern oder zu löschen, verwendet dynamisch die folgenden Schlüsselwörter.  
  
|Schlüsselwort|BESCHREIBUNG|  
|-------------|-----------------|  
|DBQ|Der Name der Arbeitsmappendatei für den Microsoft Excel-Treiber beim Zugriff auf Microsoft Excel 5,0-Dateien oder spätere Dateien.<br /><br /> Dadurch wird die gleiche Option wie die **Datenbank** im Setup Dialogfeld festgelegt.|  
|DefaultDir|Die Pfadspezifikation für das Verzeichnis.<br /><br /> Dadurch wird die gleiche Option wie **Select Directory** oder **Select Workbook** im Setup Dialogfeld festgelegt.|  
|Beschreibung|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Dadurch wird die gleiche Option wie die **Beschreibung** im Setup Dialogfeld festgelegt.|  
|DRIVER|Die Pfadspezifikation für die Treiber-DLL.|  
|DriverID|Eine ganzzahlige ID für den Treiber.<br /><br /> 534 (Microsoft Excel 3,0)<br /><br /> 278 (Microsoft Excel 4,0)<br /><br /> 22 (Microsoft Excel 5.0/7.0)<br /><br /> 790 (Microsoft Excel 97-2003)|  
|RA|Dateityp, z. b. Excel 3,0, Excel 4,0, Excel 5,0, Excel 7,0, Excel 97, Excel 2000 oder Excel 2003.|  
|Firstrowhasnames|Gibt an, ob die Zellen der ersten Zeile des Bereichs die Spaltennamen für die Tabelle (1) oder nicht (0) enthalten.|  
|MaxScanRows|Die Anzahl der Zeilen, die beim Festlegen des Datentyps einer Spalte auf Grundlage vorhandener Daten gescannt werden sollen.<br /><br /> Eine Zahl zwischen 1 und 16 kann für die zu überprüfenden Zeilen eingegeben werden. Der Standardwert ist 8; Wenn der Wert auf 0 festgelegt ist, werden alle Zeilen gescannt. (Eine Zahl außerhalb des Limits gibt einen Fehler zurück.)<br /><br /> Dadurch wird die Option für die **zu über** prüfenden Zeilen im Setup Dialogfeld festgelegt.|  
|READONLY|TRUE, wenn die Datei schreibgeschützt werden soll. FALSE, wenn die Datei nicht schreibgeschützt sein soll.<br /><br /> Dadurch wird die gleiche **Option wie im** Setup Dialogfeld schreibgeschützt festgelegt.|  
|Threads|Die Anzahl der Hintergrundthreads, die von der Engine verwendet werden sollen. Für den Microsoft Access-Treiber ist dieser Wert standardmäßig auf 3 eingestellt, kann jedoch geändert werden. Für den dBASE-Wert ist "mikrosoftexceldriver" der Wert "3" und kann nicht geändert werden.<br /><br /> Dadurch wird die gleiche Option wie **Threads** im Setup Dialogfeld festgelegt.|
