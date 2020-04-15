---
title: Anweisungsattribute | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement attributes
- statement attributes [ODBC]
ms.assetid: 4c59cd8e-a713-4095-9065-20d5bdeafe43
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec24cc43e8c57e47ddda9f20fac1807f42453e84
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299643"
---
# <a name="statement-attributes"></a>Anweisungsattribute
Anweisungsattribute sind Merkmale der Anweisung. Beispielsweise, ob Lesezeichen verwendet werden sollen und welche Art von Cursor mit dem Ergebnissatz der Anweisung verwendet werden soll, sind Anweisungsattribute.  
  
 Anweisungsattribute werden mit **SQLSetStmtAttr** und ihren aktuellen Einstellungen festgelegt, die mit **SQLGetStmtAttr**abgerufen werden. Es ist nicht erforderlich, dass eine Anwendung Anweisungsattribute festgelegt hat. Alle Anweisungsattribute weisen Standardwerte auf, von denen einige treiberspezifisch sind.  
  
 Wann ein Anweisungsattribut festgelegt werden kann, hängt vom Attribut selbst ab. Die Attribute SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR und SQL_ATTR_USE_BOOKMARKS -Anweisung müssen festgelegt werden, bevor die Anweisung ausgeführt wird. Die SQL_ATTR_ASYNC_ENABLE- und SQL_ATTR_NOSCAN Anweisungsattribute können jederzeit festgelegt, aber erst angewendet werden, wenn die Anweisung erneut verwendet wird. SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS und SQL_ATTR_QUERY_TIMEOUT Anweisungsattribute können jederzeit festgelegt werden, aber es ist treiberspezifisch, ob sie angewendet werden, bevor die Anweisung erneut verwendet wird. Die verbleibenden Anweisungsattribute können jederzeit festgelegt werden.  
  
> [!NOTE]  
>  Die Möglichkeit, Anweisungsattribute auf Verbindungsebene durch Aufrufen von **SQLSetConnectAttr** festzulegen, ist in ODBC 3 veraltet. *x*. ODBC 3. *x-Anwendungen* sollten niemals Anweisungsattribute auf Verbindungsebene festlegen. ODBC 3. *x-Treiber* müssen diese Funktionalität nur unterstützen, wenn sie mit ODBC 2 arbeiten sollten. *x-Anwendungen.* Weitere Informationen finden Sie unter [SQLSetConnectOption Mapping](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) in Anhang G: Treiberrichtlinien für Abwärtskompatibilität.  
>   
>  Eine Ausnahme bilden die SQL_ATTR_METADATA_ID- und SQL_ATTR_ASYNC_ENABLE-Attribute, die sowohl Verbindungsattribute als auch Anweisungsattribute sind und entweder auf Verbindungsebene oder auf Anweisungsebene festgelegt werden können.  
>   
>  Keines der in ODBC 3 eingeführten Anweisungsattribute. *x* (mit Ausnahme von SQL_ATTR_METADATA_ID) kann auf Verbindungsebene eingestellt werden.  
  
 Weitere Informationen finden Sie in der [SQLSetStmtAttr-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)
