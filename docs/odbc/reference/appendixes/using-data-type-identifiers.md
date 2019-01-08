---
title: -Datentypbezeichner mit | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f14294b76fc7977de256697c730f7dca31e7a469
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2018
ms.locfileid: "52516606"
---
# <a name="using-data-type-identifiers"></a>Verwenden von Datentypbezeichnern
Anwendungen verwenden-Datentypbezeichner gibt es zwei Möglichkeiten: um ihre Puffer an den Treiber zu beschreiben, und klicken Sie zum Abrufen von Metadaten über das Resultset aus dem Treiber, damit sie feststellen können, welche Art von C puffert, um zum Speichern der Daten zu verwenden. Anwendungen rufen Sie die folgenden Funktionen zum Ausführen dieser Aufgaben:  
  
-   **SQLBindParameter**, **SQLBindCol**, und **SQLGetData** – zur Beschreibung des C-Datentyp, der Anwendungspuffer.  
  
-   **SQLBindParameter** – um den SQL-Datentyp, der dynamische Parameter zu beschreiben.  
  
-   **SQLColAttribute** und **SQLDescribeCol** – um die SQL-Datentypen der Spalten im Resultset abzurufen.  
  
-   **SQLDescribeParameter** – die SQL-Datentypen von Parametern abgerufen.  
  
-   **SQLColumns**, **SQLProcedureColumns**, und **SQLSpecialColumns** – die SQL-Datentypen von verschiedenen Schemainformationen abrufen  
  
-   **SQLGetTypeInfo** – zum Abrufen einer Liste der unterstützten Datentypen  
  
 -Datentypbezeichner werden in das Feld SQL_DESC_CONCISE_TYPE einen Deskriptor gespeichert. Die Funktionen der Deskriptor **SQLSetDescField** und **SQLSetDescRec** kann mit den entsprechenden Typen verwendet werden, die in der vorherigen Liste aufgeführten Aufgaben ausführen. Weitere Informationen finden Sie unter [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).
