---
title: 'SQL zu C: GUID | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], GUID
- data conversions from SQL to C types [ODBC], guid
- GUID data type [ODBC]
ms.assetid: cf56c684-c261-4b89-994a-db14ab2241d6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f0f247bc4cb411d535050d7c78e0ea42cc144b0e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296460"
---
# <a name="sql-to-c-guid"></a>SQL zu C: GUID
Der Bezeichner für den GUID ODBC SQL-Datentyp lautet:  
  
 SQL_GUID  
  
 Die folgende Tabelle zeigt die ODBC C-Datentypen, in die GUID-SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typ-Idonid|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > Zeichenbytelänge|Daten|36|–|  
||*BufferLength* < 37|Nicht definiert|Nicht definiert|22003|  
|SQL_C_WCHAR|*BufferLength* > Zeichenlänge|Daten|36|–|  
||*BufferLength* < 37|Nicht definiert|Nicht definiert|22003|  
|SQL_C_BINARY|Bytelänge der \< = Daten *BufferLength*|Daten|Länge der Daten in Bytes|–|  
||Byte-Länge der Daten > *BufferLength*|Nicht definiert|Nicht definiert|22003|  
|SQL_C_GUID|Keine[a]|Daten|16[b]|–|  
  
 [a] Der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **TargetValuePtr* die Größe des C-Datentyps ist.  
  
 [b] Dies ist die Größe des entsprechenden C-Datentyps.
