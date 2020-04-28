---
title: Attribut Übereinstimmung | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306401"
---
# <a name="attribute-conformance"></a>Attributübereinstimmung
In der folgenden Tabelle ist die Übereinstimmungs Stufe der einzelnen ODBC-Umgebungs Attribute angegeben, in denen diese klar definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|Kernspeicher|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 [1] Dies ist ein optionales Feature, das nicht Teil der Konformitätsstufen ist.  
  
 In der folgenden Tabelle ist die Übereinstimmungs Stufe der einzelnen ODBC-Verbindungs Attribute angegeben, wobei diese klar definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_ATTR_ACCESS_MODE|Kernspeicher|  
|SQL_ATTR_ASYNC_ENABLE|Ebene 1/Ebene 2 [1]|  
|SQL_ATTR_AUTO_IPD|Ebene 2|  
|SQL_ATTR_AUTOCOMMIT|Ebene 1|  
|SQL_ATTR_CONNECTION_DEAD|Ebene 1|  
|SQL_ATTR_CONNECTION_TIMEOUT|Ebene 2|  
|SQL_ATTR_CURRENT_CATALOG|Ebene 2|  
|SQL_ATTR_LOGIN_TIMEOUT|Ebene 2|  
|SQL_ATTR_ODBC_CURSORS|Kernspeicher|  
|SQL_ATTR_PACKET_SIZE|Ebene 2|  
|SQL_ATTR_QUIET_MODE|Kernspeicher|  
|SQL_ATTR_TRACE|Kernspeicher|  
|SQL_ATTR_TRACEFILE|Kernspeicher|  
|SQL_ATTR_TRANSLATE_LIB|Kernspeicher|  
|SQL_ATTR_TRANSLATE_OPTION|Kernspeicher|  
|SQL_ATTR_TXN_ISOLATION|Ebene 1/Ebene 2 [2]|  
  
 [1] Anwendungen, die Asynchronität auf Verbindungs Ebene unterstützen (erforderlich für Ebene 1), müssen das Festlegen dieses Attributs auf SQL_TRUE durch Aufrufen von **SQLSetConnectAttr**unterstützen. das Attribut muss nicht durch **SQLSetStmtAttr**auf einen anderen Wert als seinen Standardwert festgelegt werden können. Anwendungen, die Asynchronität auf Anweisungs Ebene (erforderlich für Ebene 2) unterstützen, müssen das Festlegen dieses Attributs auf SQL_TRUE mithilfe einer der beiden Funktionen unterstützen.  
  
 [2] für die Schnittstellen Konformität der Ebene 1 muss der Treiber zusätzlich zu dem vom Treiber definierten Standardwert einen Wert unterstützen (verfügbar durch Aufrufen von **SQLGetInfo** mit der SQL_DEFAULT_TXN_ISOLATION-Option). Bei der Schnittstellen Konformität der Ebene 2 muss der Treiber auch SQL_TXN_SERIALIZABLE unterstützen.  
  
 In der folgenden Tabelle ist die Übereinstimmungs Stufe der einzelnen ODBC-Anweisungs Attribute angegeben, in denen diese ordnungsgemäß definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_ATTR_APP_PARAM_DESC|Kernspeicher|  
|SQL_ATTR_APP_ROW_DESC|Kernspeicher|  
|SQL_ATTR_ASYNC_ENABLE|Ebene 1/Ebene 2 [1]|  
|SQL_ATTR_CONCURRENCY|Ebene 1/Ebene 2 [2]|  
|SQL_ATTR_CURSOR_SCROLLABLE|Ebene 1|  
|SQL_ATTR_CURSOR_SENSITIVITY|Ebene 2|  
|SQL_ATTR_CURSOR_TYPE|Kern/Ebene 2 [3]|  
|SQL_ATTR_ENABLE_AUTO_IPD|Ebene 2|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|Ebene 2|  
|SQL_ATTR_IMP_PARAM_DESC|Kernspeicher|  
|SQL_ATTR_IMP_ROW_DESC|Kernspeicher|  
|SQL_ATTR_KEYSET_SIZE|Ebene 2|  
|SQL_ATTR_MAX_LENGTH|Ebene 1|  
|SQL_ATTR_MAX_ROWS|Ebene 1|  
|SQL_ATTR_METADATA_ID|Kernspeicher|  
|SQL_ATTR_NOSCAN|Kernspeicher|  
|SQL_ATTR_PARAM_BIND_OFFSET_PTR|Kernspeicher|  
|SQL_ATTR_PARAM_BIND_TYPE|Kernspeicher|  
|SQL_ATTR_PARAM_OPERATION_PTR|Kernspeicher|  
|SQL_ATTR_PARAM_STATUS_PTR|Kernspeicher|  
|SQL_ATTR_PARAMS_PROCESSED_PTR|Kernspeicher|  
|SQL_ATTR_PARAMSET_SIZE|Kernspeicher|  
|SQL_ATTR_QUERY_TIMEOUT|Ebene 2|  
|SQL_ATTR_RETRIEVE_DATA|Ebene 1|  
|SQL_ATTR_ROW_ARRAY_SIZE|Kernspeicher|  
|SQL_ATTR_ROW_BIND_OFFSET_PTR|Kernspeicher|  
|SQL_ATTR_ROW_BIND_TYPE|Kernspeicher|  
|SQL_ATTR_ROW_NUMBER|Ebene 1|  
|SQL_ATTR_ROW_OPERATION_PTR|Ebene 1|  
|SQL_ATTR_ROW_STATUS_PTR|Kernspeicher|  
|SQL_ATTR_ROWS_FETCHED_PTR|Kernspeicher|  
|SQL_ATTR_SIMULATE_CURSOR|Ebene 2|  
|SQL_ATTR_USE_BOOKMARKS|Ebene 2|  
  
 [1] Anwendungen, die Asynchronität auf Verbindungs Ebene unterstützen (erforderlich für Ebene 1), müssen das Festlegen dieses Attributs auf SQL_TRUE durch Aufrufen von **SQLSetConnectAttr**unterstützen. das Attribut muss nicht durch **SQLSetStmtAttr**auf einen anderen Wert als seinen Standardwert festgelegt werden können. Anwendungen, die Asynchronität auf Anweisungs Ebene (erforderlich für Ebene 2) unterstützen, müssen das Festlegen dieses Attributs auf SQL_TRUE mithilfe einer der beiden Funktionen unterstützen.  
  
 [2] für die Schnittstellen Konformität der Ebene 2 muss der Treiber SQL_CONCUR_READ_ONLY und mindestens einen anderen Wert unterstützen.  
  
 [3] für die Schnittstellen Konformität der Ebene 1 muss der Treiber SQL_CURSOR_FORWARD_ONLY und mindestens einen anderen Wert unterstützen. Bei der Schnittstellen Konformität der Ebene 2 muss der Treiber alle Werte unterstützen, die in diesem Dokument definiert sind.
