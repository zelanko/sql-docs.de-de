---
title: 'SQL in C: GUID | Microsoft-Dokumentation'
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1a2ed3cffcb196cb09841df3b54fbfab53e22477
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68056876"
---
# <a name="sql-to-c-guid"></a>SQL in C: GUID
Der Bezeichner für den GUID-ODBC-SQL-Datentyp ist:  
  
 SQL_GUID  
  
 Die folgende Tabelle zeigt die ODBC-C-Datentypen, die in denen GUID-SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Ausdrücke in der Tabelle, finden Sie unter [Konvertieren von Daten aus SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typ-ID|Test|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > Zeichen Länge in Byte|Daten|36|n/v|  
||*BufferLength* < 37|Nicht definiert|Nicht definiert|22003|  
|SQL_C_WCHAR|*BufferLength* > Zeichenlänge|Daten|36|n/v|  
||*BufferLength* < 37|Nicht definiert|Nicht definiert|22003|  
|SQL_C_BINARY|Die Bytelänge der Daten \< =  *Pufferlänge*|Daten|Länge der Daten in bytes|n/v|  
||Die Bytelänge der Daten > *Pufferlänge*|Nicht definiert|Nicht definiert|22003|  
|SQL_C_GUID|Keine [a]|Daten|16 [b]|n/v|  
  
 [a] den Wert der *Pufferlänge* für diese Konvertierung ignoriert wird. Der Treiber setzt voraus, dass die Größe des **TargetValuePtr* ist die Größe der C-Datentyp.  
  
 [b] Dies ist die Größe des entsprechenden C-Datentyp.
