---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 89157178aa9c134bdb1b9518343007adb1e1e05f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68132424"
---
# <a name="sqltables-excel-driver"></a>SQLTables (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Excel-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Kommentare|  
|--------------|--------------|  
|*szTableOwner*|Das einzige gültige Argument für *SzTableOwner* ist NULL, weil keine Treiber Besitzernamens unterstützt. Mit *SzTableOwner* auf NULL festgelegt, werden alle Tabellen zurückgegeben. In der Spalte TABLE_OWNER wird NULL zurückgegeben.|  
|*szTableQualifier*|Wenn der Microsoft Excel-Version 3.0 oder 4.0-Treiber verwendet wird, wenn Sie aufrufen **SQLTables** mit einem Wert für *SzTableQualifier* , die nicht den Namen einer vorhandenen Tabelle, der Treiber erstellt eine Tabelle mit diesem Namen.<br /><br /> In der Spalte TABLE_QUALIFIER **SQLTables** gibt den Pfad zu einem Verzeichnis zurück.|  
|*SzTableType*|Für Microsoft Excel, 3.0 oder 4.0 ist "TABLE" der einzige unterstützte Tabellentyp.<br /><br /> Informationen zu höheren Versionen von Microsoft Excel-Dateien ist "-SYSTEMTABELLE" wird für Tabellennamen (Tabellen mit einem "$" am Ende) zurückgegeben, und "TABLE" für Tabellen in Arbeitsblättern.|
