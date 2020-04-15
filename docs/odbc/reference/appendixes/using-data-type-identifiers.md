---
title: Verwenden von Datentyp-Bezeichnern | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8be8eef0441d48ed03ea6ccf8f656627c1dd9b63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301421"
---
# <a name="using-data-type-identifiers"></a>Verwenden von Datentypbezeichnern
Anwendungen verwenden Datentypbezeichner auf zwei Arten: um ihre Puffer für den Treiber zu beschreiben und Metadaten über das Resultset vom Treiber abzurufen, damit sie bestimmen können, welche Art von C-Puffer zum Speichern der Daten verwendet werden sollen. Anwendungen rufen die folgenden Funktionen auf, um diese Aufgaben auszuführen:  
  
-   **SQLBindParameter**, **SQLBindCol**und **SQLGetData** - um den C-Datentyp von Anwendungspuffern zu beschreiben.  
  
-   **SQLBindParameter** - um den SQL-Datentyp dynamischer Parameter zu beschreiben.  
  
-   **SQLColAttribute** und **SQLDescribeCol** - zum Abrufen der SQL-Datentypen von Resultsetspalten.  
  
-   **SQLDescribeParameter** - zum Abrufen der SQL-Datentypen von Parametern.  
  
-   **SQLColumns**, **SQLProcedureColumns**und **SQLSpecialColumns** - zum Abrufen der SQL-Datentypen verschiedener Schemainformationen  
  
-   **SQLGetTypeInfo** - zum Abrufen einer Liste unterstützter Datentypen  
  
 Datentypbezeichner werden im SQL_DESC_CONCISE_TYPE Feld eines Deskriptors gespeichert. Die Deskriptorfunktionen **SQLSetDescField** und **SQLSetDescRec** können mit den entsprechenden Typen verwendet werden, um die in der vorherigen Liste aufgeführten Aufgaben auszuführen. Weitere Informationen finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).
