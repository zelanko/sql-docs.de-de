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
manager: craigg
ms.openlocfilehash: 23ce67350b7fa7d0a88f3d51e618ce9bb9f9ebcf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63287290"
---
# <a name="sqltables-excel-driver"></a>SQLTables (Excel-Treiber)
> [!NOTE]  
>  Dieses Thema enthält die Excel-Treiber-spezifische Informationen. Allgemeine Informationen zu dieser Funktion finden Sie unter den entsprechenden Themen unter [ODBC-API-Referenz](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Kommentare|  
|--------------|--------------|  
|*szTableOwner*|Das einzige gültige Argument für *SzTableOwner* ist NULL, weil keine Treiber Besitzernamens unterstützt. Mit *SzTableOwner* auf NULL festgelegt, werden alle Tabellen zurückgegeben. In der Spalte TABLE_OWNER wird NULL zurückgegeben.|  
|*szTableQualifier*|Wenn der Microsoft Excel-Version 3.0 oder 4.0-Treiber verwendet wird, wenn Sie aufrufen **SQLTables** mit einem Wert für *SzTableQualifier* , die nicht den Namen einer vorhandenen Tabelle, der Treiber erstellt eine Tabelle mit diesem Namen.<br /><br /> In der Spalte TABLE_QUALIFIER **SQLTables** gibt den Pfad zu einem Verzeichnis zurück.|  
|*SzTableType*|Für Microsoft Excel, 3.0 oder 4.0 ist "TABLE" der einzige unterstützte Tabellentyp.<br /><br /> Informationen zu höheren Versionen von Microsoft Excel-Dateien ist "-SYSTEMTABELLE" wird für Tabellennamen (Tabellen mit einem "$" am Ende) zurückgegeben, und "TABLE" für Tabellen in Arbeitsblättern.|
