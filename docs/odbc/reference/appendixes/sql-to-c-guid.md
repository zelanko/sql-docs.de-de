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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f0f247bc4cb411d535050d7c78e0ea42cc144b0e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296460"
---
# <a name="sql-to-c-guid"></a>SQL zu C: GUID
Der Bezeichner für den GUID ODBC-SQL-Datentyp lautet:  
  
 SQL_GUID  
  
 In der folgenden Tabelle werden die ODBC-C-Datentypen angezeigt, in die GUID-SQL-Daten konvertiert werden können. Eine Erläuterung der Spalten und Begriffe in der Tabelle finden [Sie unter Datentypen von SQL in C-Datentypen](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md).  
  
|C-Typbezeichner|Test|**Targetvalueptr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|Länge des *pufflength* -> Zeichens|Daten|36|Nicht zutreffend|  
||*BufferLength* < 37|Nicht definiert|Nicht definiert|22003|  
|SQL_C_WCHAR|Länge der *BufferLength* -> Zeichen|Daten|36|Nicht zutreffend|  
||*BufferLength* < 37|Nicht definiert|Nicht definiert|22003|  
|SQL_C_BINARY|Byte Länge der Daten \< =  *Pufferlänge*|Daten|Länge der Daten in Bytes|Nicht zutreffend|  
||Byte Länge der Daten > *BufferLength*|Nicht definiert|Nicht definiert|22003|  
|SQL_C_GUID|Keine [a]|Daten|16 [b]|Nicht zutreffend|  
  
 [a] der Wert von *BufferLength* wird für diese Konvertierung ignoriert. Der Treiber geht davon aus, dass die Größe von **targetvalueptr* die Größe des C-Datentyps ist.  
  
 [b] Dies ist die Größe des entsprechenden C-Datentyps.
