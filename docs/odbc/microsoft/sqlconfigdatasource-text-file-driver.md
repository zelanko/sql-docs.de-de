---
title: SQLConfigDataSource (Textdateitreiber) | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2d2809f9b15dd6843e4404c7cf1887c3caa015a3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283920"
---
# <a name="sqlconfigdatasource-text-file-driver"></a>SQLConfigDataSource (Textdateitreiber)
> [!NOTE]  
>  Dieses Thema enthält Textdateitreiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Die **SQLConfigDataSource-Funktion,** die zum Hinzufügen, Ändern oder Löschen einer Datenquelle verwendet wird, verwendet dynamisch die folgenden Schlüsselwörter.  
  
|Schlüsselwort|BESCHREIBUNG|  
|-------------|-----------------|  
|Characterset|Für den Texttreiber, OEM oder ANSI.|  
|COLNAMEHEADER|Gibt für den Texttreiber an, ob der erste Datensatz die Spaltennamen angibt. Entweder TRUE oder FALSE.|  
|DEFAULTDIR|Die Pfadspezifikation zum Verzeichnis.|  
|DESCRIPTION|Eine Beschreibung der Daten in der Datenquelle.<br /><br /> Dadurch wird die gleiche Option wie **Beschreibung** im Dialogfeld Setup festgelegt.|  
|DRIVER|Die Pfadspezifikation für die Treiber-DLL.|  
|DRIVERID|Eine ganzzahlige ID für den Treiber. 27 (Text)|  
|Erweiterungen|Listet die Dateinamenerweiterungen der Textdateien in der Datenquelle auf.<br /><br /> Dadurch wird die gleiche Option wie **Erweiterungsliste** im Dialogfeld Setup festgelegt.|  
|Fil|Dateityp Text|  
|Filetype|Dateityp für den Texttreiber (Text).|  
|FORMAT|Für den Texttreiber können FIXEDLENGTH, TABDELIMITED, CSVDELIMITED (durch ein Komma) oder DELIMITED() (durch das in den Klammern angegebene Sonderzeichen) sein. Das Sonderzeichen ist ein Zeichen lang und kann im Zeichen-, Dezimal- oder Hexadezimalformat vorliegen.|  
|MAXSCANROWS|Die Anzahl der Zu scannenden Zeilen beim Festlegen des Datentyps einer Spalte basierend auf vorhandenen Daten.<br /><br /> Für den Texttreiber können Sie eine Zahl von 1 bis 32767 für die Anzahl der zu scannenden Zeilen eingeben. Der Wert wird jedoch immer standardmäßig auf 25 wertsein. (Eine Zahl außerhalb des Limits gibt einen Fehler zurück.)<br /><br /> Dadurch wird die gleiche Option wie **Zeilen zum Scannen** im Setup-Dialogfeld festgelegt.|  
|READONLY|TRUE, um Datei schreibgeschützt zu machen; FALSE, um die Datei nicht schreibgeschützt zu machen.<br /><br /> Dadurch wird die gleiche Option wie **Nur lesen** im Dialogfeld Setup festgelegt.|
