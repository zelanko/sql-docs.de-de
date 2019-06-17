---
title: SQLConfigDataSource (Textdateitreiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], SQLConfigDataSource
- SQLConfigDataSource function [ODBC], Text File Driver
ms.assetid: c505d36e-1e72-47b2-a9e5-e4926b408468
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1635538f69b313a73a24ab1531f8793c7d98741e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62665256"
---
# <a name="sqlconfigdatasource-text-file-driver"></a>SQLConfigDataSource (Textdateitreiber)
> [!NOTE]  
>  Dieses Thema enthält die Textdatei-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource** -Funktion, die verwendet wird, zum Hinzufügen, ändern oder Löschen einer Datenquelle verwendet die folgenden Schlüsselwörter.  
  
|Schlüsselwort|Beschreibung|  
|-------------|-----------------|  
|CHARACTERSET|Für den Text-Treiber, OEM oder ANSI.|  
|COLNAMEHEADER|Gibt an, ob der erste Datensatz der Daten die Spaltennamen angeben, für den Text-Treiber. Entweder "true" oder "false".|  
|WERT|Die Pfadangabe in das Verzeichnis.|  
|DESCRIPTION|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Hiermit wird die gleiche Option als **Beschreibung** im Dialogfeld "Setup".|  
|DRIVER|Die Pfadangabe für den Treiber-DLL.|  
|DRIVERID|Eine ganzzahlige ID für den Treiber. 27 (Text)|  
|ERWEITERUNGEN|Listet die Dateinamenerweiterungen der Text-Dateien für die Datenquelle an.<br /><br /> Hiermit wird die gleiche Option als **Erweiterungenliste** im Dialogfeld "Setup".|  
|FIL|Geben Sie Text-Datei|  
|DATEITYP|Der Dateityp für den Text-Treiber (Text).|  
|FORMAT|Für den Text-Treiber können FIXEDLENGTH TABDELIMITED, CSVDELIMITED (durch ein Komma) oder DELIMITED() (durch das Sonderzeichen, das in Klammern angegeben) sein. Das Sonderzeichen, das kann ist ein Zeichen lang und in Zeichen, Dezimal oder hexadezimal-Format.|  
|MAXSCANROWS|Die Anzahl von Zeilen gescannt werden müssen, wenn Sie einen Spaltendatentyp basierend auf den vorhandenen Daten festlegen.<br /><br /> Für den Text-Treiber können Sie eine Zahl zwischen 1 und 32767 für die Anzahl der zu durchsuchenden Zeilen eingeben; Allerdings wird standardmäßig der Wert immer auf 25. (Eine Zahl außerhalb der Grenzwert wird einen Fehler zurückgegeben.)<br /><br /> Hiermit wird die gleiche Option als **zu scannende Zeilen** im Dialogfeld "Setup".|  
|READONLY|True, um die Datei schreibgeschützt zu machen. "False", um die Datei nicht schreibgeschützt machen.<br /><br /> Hiermit wird die gleiche Option als **Read Only** im Dialogfeld "Setup".|
