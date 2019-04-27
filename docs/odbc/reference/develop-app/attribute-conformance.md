---
title: Attribut-Konformität | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
- conformance levels [ODBC], attribute
- attribute conformance levels [ODBC]
ms.assetid: 34fea100-10f9-46d5-bc50-3aa867b70f24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 44f1311d98f37412454ad2352366492a8d5a1768
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62672531"
---
# <a name="attribute-conformance"></a>Attributübereinstimmung
Die folgende Tabelle zeigt dem Konformitätsgrad des jedes Attribut für den ODBC-Umgebung, in denen dies gut definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|Core|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 [1] Dies ist ein optionales Feature und als solches ist nicht Teil der Ebenen der schnittstellenübereinstimmung.  
  
 Die folgende Tabelle gibt an, dem Konformitätsgrad des jede ODBC-Verbindungsattributs, in denen dies gut definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_ATTR_ACCESS_MODE|Core|  
|SQL_ATTR_ASYNC_ENABLE|Ebene 1/Ebene 2 [1]|  
|SQL_ATTR_AUTO_IPD|Ebene 2|  
|SQL_ATTR_AUTOCOMMIT|Ebene 1|  
|SQL_ATTR_CONNECTION_DEAD|Ebene 1|  
|SQL_ATTR_CONNECTION_TIMEOUT|Ebene 2|  
|SQL_ATTR_CURRENT_CATALOG|Ebene 2|  
|SQL_ATTR_LOGIN_TIMEOUT|Ebene 2|  
|SQL_ATTR_ODBC_CURSORS|Core|  
|SQL_ATTR_PACKET_SIZE|Ebene 2|  
|SQL_ATTR_QUIET_MODE|Core|  
|SQL_ATTR_TRACE|Core|  
|SQL_ATTR_TRACEFILE|Core|  
|SQL_ATTR_TRANSLATE_LIB|Core|  
|SQL_ATTR_TRANSLATE_OPTION|Core|  
|SQL_ATTR_TXN_ISOLATION|Ebene 1/Ebene 2 [2]|  
  
 [1]-Anwendungen, die auf Serverebene Asynchronie (erforderlich für Ebene 1) unterstützen müssen durch Festlegen dieses Attributs auf SQL_TRUE durch Aufrufen von unterstützen **SQLSetConnectAttr**; das Attribut muss nicht auf einen anderen Wert als den Standardwert festgelegt werden. Wert über **SQLSetStmtAttr**. Anwendungen, die auf Anweisungsebene Asynchronie (erforderlich für Ebene 2) unterstützen müssen durch Festlegen dieses Attributs auf SQL_TRUE, die mit beiden-Funktion unterstützen.  
  
 [2] für Ebene-1-schnittstellenübereinstimmung der Treiber muss einen Wert neben den treiberdefinierten Standardwert unterstützen (durch Aufrufen von verfügbaren **SQLGetInfo** mit der Option SQL_DEFAULT_TXN_ISOLATION). Für Ebene-2-schnittstellenübereinstimmung muss der Treiber auch sql_txn_serializable festgelegt sind unterstützen.  
  
 Die folgende Tabelle gibt an, dem Konformitätsgrad des einzelnen ODBC-Anweisungsattribut, zu dem, in denen dies gut definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_ATTR_APP_PARAM_DESC|Core|  
|SQL_ATTR_APP_ROW_DESC|Core|  
|SQL_ATTR_ASYNC_ENABLE|Ebene 1/Ebene 2 [1]|  
|SQL_ATTR_CONCURRENCY|Ebene 1/Ebene 2 [2]|  
|SQL_ATTR_CURSOR_SCROLLABLE|Ebene 1|  
|SQL_ATTR_CURSOR_SENSITIVITY|Ebene 2|  
|SQL_ATTR_CURSOR_TYPE|Core-Ebene-2 [3]|  
|SQL_ATTR_ENABLE_AUTO_IPD|Ebene 2|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Ebene 2|  
|SQL_ATTR_IMP_PARAM_DESC|Core|  
|SQL_ATTR_IMP_ROW_DESC|Core|  
|SQL_ATTR_KEYSET_SIZE|Ebene 2|  
|SQL_ATTR_MAX_LENGTH|Ebene 1|  
|SQL_ATTR_MAX_ROWS|Ebene 1|  
|SQL_ATTR_METADATA_ID|Core|  
|SQL_ATTR_NOSCAN|Core|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|Core|  
|SQL_ATTR_PARAM_BIND_TYPE|Core|  
|SQL_ATTR_PARAM_OPERATION_PTR|Core|  
|SQL_ATTR_PARAM_STATUS_PTR|Core|  
|SQL_ATTR_PARAMS_PROCESSED_PTR|Core|  
|SQL_ATTR_PARAMSET_SIZE|Core|  
|SQL_ATTR_QUERY_TIMEOUT|Ebene 2|  
|SQL_ATTR_RETRIEVE_DATA|Ebene 1|  
|SQL_ATTR_ROW_ARRAY_SIZE|Core|  
|SQL_ATTR_ROW_BIND_OFFSET_PTR|Core|  
|SQL_ATTR_ROW_BIND_TYPE|Core|  
|SQL_ATTR_ROW_NUMBER|Ebene 1|  
|SQL_ATTR_ROW_OPERATION_PTR|Ebene 1|  
|SQL_ATTR_ROW_STATUS_PTR|Core|  
|SQL_ATTR_ROWS_FETCHED_PTR|Core|  
|SQL_ATTR_SIMULATE_CURSOR|Ebene 2|  
|SQL_ATTR_USE_BOOKMARKS|Ebene 2|  
  
 [1]-Anwendungen, die auf Serverebene Asynchronie (erforderlich für Ebene 1) unterstützen müssen durch Festlegen dieses Attributs auf SQL_TRUE durch Aufrufen von unterstützen **SQLSetConnectAttr**; das Attribut muss nicht auf einen anderen Wert als den Standardwert festgelegt werden. Wert über **SQLSetStmtAttr**. Anwendungen, die auf Anweisungsebene Asynchronie (erforderlich für Ebene 2) unterstützen müssen durch Festlegen dieses Attributs auf SQL_TRUE, die mit beiden-Funktion unterstützen.  
  
 [2] ' für Ebene-2-schnittstellenübereinstimmung muss der Treiber SQL_CONCUR_READ_ONLY und mindestens einen anderen Wert unterstützen.  
  
 [3] für Ebene-1-schnittstellenübereinstimmung muss der Treiber SQL_CURSOR_FORWARD_ONLY und mindestens einen anderen Wert unterstützen. Für Ebene-2-schnittstellenübereinstimmung muss der Treiber alle Werte, die in diesem Dokument definierte unterstützen.
