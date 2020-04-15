---
title: SQLTables (Excel-Treiber) | Microsoft Docs
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
ms.openlocfilehash: c436a1f52a862cda753d8c043515f5584607d98c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299300"
---
# <a name="sqltables-excel-driver"></a>SQLTables (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält Excel-Treiberspezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie im entsprechenden Thema unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Kommentare|  
|--------------|--------------|  
|*szTableOwner*|Das einzige gültige Argument für *szTableOwner* ist NULL, da keine der Treiber Besitzernamen unterstützt. Wenn *szTableOwner* auf NULL gesetzt ist, werden alle Tabellen zurückgegeben. NULL wird in der Spalte TABLE_OWNER zurückgegeben.|  
|*szTableQualifier*|Wenn der Treiber Microsoft Excel 3.0 oder 4.0 verwendet wird und Sie **SQLTables** mit einem Wert für *szTableQualifier* aufrufen, der nicht der Name einer vorhandenen Tabelle ist, erstellt der Treiber eine Tabelle mit diesem Namen.<br /><br /> In der Spalte TABLE_QUALIFIER gibt **SQLTables** den Pfad in ein Verzeichnis zurück.|  
|*SzTableType*|Für Microsoft Excel 3.0 oder 4.0 ist "TABLE" der einzige unterstützte Tabellentyp.<br /><br /> Für spätere Versionen von Microsoft Excel-Dateien wird "SYSTEM TABLE" für Blattnamen zurückgegeben (Tabellen mit einem "-" am Ende), und "TABLE" wird für Tabellen in Arbeitsblättern zurückgegeben.|
