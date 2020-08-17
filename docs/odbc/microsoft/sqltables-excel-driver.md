---
description: SQLTables (Excel-Treiber)
title: SQLTables (Excel-Treiber) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLTables
- SQLTables function [ODBC], Excel Driver
ms.assetid: 9410b686-4b5b-4b51-b5ef-f9d2e7a48faa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: acedd48fb48e8f8db844feb1911f044c472006a4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339646"
---
# <a name="sqltables-excel-driver"></a>SQLTables (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Informationen zu Excel-Treibern. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Kommentare|  
|--------------|--------------|  
|*sztableowner*|Das einzige gültige Argument für *sztableowner* ist NULL, da keiner der Treiber Besitzer Namen unterstützt. Wenn *sztableowner* auf NULL festgelegt ist, werden alle Tabellen zurückgegeben. NULL wird in der TABLE_OWNER Spalte zurückgegeben.|  
|*sztablequalifizierer*|Wenn der Microsoft Excel 3,0-oder 4,0-Treiber verwendet wird, erstellt der Treiber eine Tabelle mit diesem Namen, wenn **SQLTables** mit einem Wert für *sztablequalifier* aufgerufen wird, der nicht der Name einer vorhandenen Tabelle ist.<br /><br /> In der Spalte TABLE_QUALIFIER gibt **SQLTables** den Pfad zu einem Verzeichnis zurück.|  
|*Sztabletype*|Für Microsoft Excel 3,0 oder 4,0 ist "Table" der einzige unterstützte Tabellentyp.<br /><br /> Für spätere Versionen von Microsoft Excel-Dateien wird "System Tabelle" für Blattnamen (Tabellen mit "$" am Ende) und "Table" für Tabellen in Arbeitsblättern zurückgegeben.|
