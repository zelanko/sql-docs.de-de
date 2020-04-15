---
title: Attributkonformität | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2880a35f4bdc997cc037cdd0d60720267ff4a58
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306401"
---
# <a name="attribute-conformance"></a>Attributübereinstimmung
Die folgende Tabelle gibt die Konformitätsstufe jedes ODBC-Umgebungsattributs an, wobei dies genau definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|Core|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 [1] Dies ist eine optionale Funktion und als solche nicht Teil der Konformitätsstufen.  
  
 Die folgende Tabelle gibt die Konformitätsstufe jedes ODBC-Verbindungsattributs an, wobei dies genau definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_ATTR_ACCESS_MODE|Core|  
|SQL_ATTR_ASYNC_ENABLE|Stufe 1/Stufe 2[1]|  
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
|SQL_ATTR_TXN_ISOLATION|Stufe 1/Stufe 2[2]|  
  
 [1] Anwendungen, die Asynchronität auf Verbindungsebene unterstützen (erforderlich für Ebene 1), müssen das Festlegen dieses Attributs auf SQL_TRUE durch Aufrufen von **SQLSetConnectAttr**unterstützen. Das Attribut muss nicht über **SQLSetStmtAttr**auf einen anderen Wert als den Standardwert festgelegt werden. Anwendungen, die Asynchronität auf Anweisungsebene unterstützen (erforderlich für Ebene 2), müssen das Festlegen dieses Attributs auf SQL_TRUE mit einer der beiden Funktionen unterstützen.  
  
 [2] Für die Schnittstellenkonformität der Ebene 1 muss der Treiber zusätzlich zum treiberdefinierten Standardwert einen Wert unterstützen (verfügbar durch Aufrufen von **SQLGetInfo** mit der Option SQL_DEFAULT_TXN_ISOLATION). Für die Level 2-Schnittstellenkonformität muss der Treiber auch SQL_TXN_SERIALIZABLE unterstützen.  
  
 Die folgende Tabelle gibt die Konformitätsstufe jedes ODBC-Anweisungsattributs an, wobei dies genau definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_ATTR_APP_PARAM_DESC|Core|  
|SQL_ATTR_APP_ROW_DESC|Core|  
|SQL_ATTR_ASYNC_ENABLE|Stufe 1/Stufe 2[1]|  
|SQL_ATTR_CONCURRENCY|Stufe 1/Stufe 2[2]|  
|SQL_ATTR_CURSOR_SCROLLABLE|Ebene 1|  
|SQL_ATTR_CURSOR_SENSITIVITY|Ebene 2|  
|SQL_ATTR_CURSOR_TYPE|Kern/Stufe 2[3]|  
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
  
 [1] Anwendungen, die Asynchronität auf Verbindungsebene unterstützen (erforderlich für Ebene 1), müssen das Festlegen dieses Attributs auf SQL_TRUE durch Aufrufen von **SQLSetConnectAttr**unterstützen. Das Attribut muss nicht über **SQLSetStmtAttr**auf einen anderen Wert als den Standardwert festgelegt werden. Anwendungen, die Asynchronität auf Anweisungsebene unterstützen (erforderlich für Ebene 2), müssen das Festlegen dieses Attributs auf SQL_TRUE mit einer der beiden Funktionen unterstützen.  
  
 [2] Für die Übereinstimmung der Schnittstelle der Ebene 2 muss der Treiber SQL_CONCUR_READ_ONLY und mindestens einen weiteren Wert unterstützen.  
  
 [3] Für die Übereinstimmung der Schnittstelle der Ebene 1 muss der Treiber SQL_CURSOR_FORWARD_ONLY und mindestens einen weiteren Wert unterstützen. Für die Übereinstimmung der Schnittstelle der Ebene 2 muss der Treiber alle in diesem Dokument definierten Werte unterstützen.
