---
title: 'SQL zu C: GUID | Microsoft-Dokumentation'
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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056876"
---
# <a name="sql-to-c-guid"></a>SQL zu C: GUID
Der Bezeichner für den GUID ODBC-SQL-Datentyp lautet:  
  
 SQL_GUID  
  
 In der folgenden Tabelle werden die ODBC-C-Datentypen angezeigt, in die GUID-SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typbezeichner|Test|**Targetvalueptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|Länge des *pufflength* -> Zeichens|Data|36|–|  
||*BufferLength* < 37|Undefined|Undefined|22003|  
|SQL_C_WCHAR|Länge der *BufferLength* -> Zeichen|Data|36|–|  
||*BufferLength* < 37|Undefined|Undefined|22003|  
|SQL_C_BINARY|Byte Länge der Daten \< =  *Pufferlänge*|Data|Länge der Daten in Bytes|–|  
||Byte Länge der Daten > *BufferLength*|Undefined|Undefined|22003|  
|SQL_C_GUID|Keine [a]|Data|16 [b]|–|  
  
 [a] der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **targetvalueptr* die Größe des C-Datentyps ist.  
  
 [b] Dies ist die Größe des entsprechenden C-Datentyps.
