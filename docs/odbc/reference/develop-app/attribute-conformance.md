---
description: Attributübereinstimmung
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
ms.openlocfilehash: 19c58dfe7f8c4219d134cd1662ce8d57b9c76de6
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476902"
---
# <a name="attribute-conformance"></a>Attributübereinstimmung
In der folgenden Tabelle ist die Übereinstimmungs Stufe der einzelnen ODBC-Umgebungs Attribute angegeben, in denen diese klar definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_ATTR_CONNECTION_POOLING|--[1]|  
|SQL_ATTR_CP_MATCH|--[1]|  
|SQL_ATTR_ODBC_VER|Core|  
|SQL_ATTR_OUTPUT_NTS|--[1]|  
  
 [1] Dies ist ein optionales Feature, das nicht Teil der Konformitätsstufen ist.  
  
 In der folgenden Tabelle ist die Übereinstimmungs Stufe der einzelnen ODBC-Verbindungs Attribute angegeben, wobei diese klar definiert ist.  
  
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
  
 [1] Anwendungen, die Asynchronität auf Verbindungs Ebene unterstützen (erforderlich für Ebene 1), müssen das Festlegen dieses Attributs auf SQL_TRUE durch Aufrufen von **SQLSetConnectAttr**unterstützen. das Attribut muss nicht durch **SQLSetStmtAttr**auf einen anderen Wert als seinen Standardwert festgelegt werden können. Anwendungen, die Asynchronität auf Anweisungs Ebene (erforderlich für Ebene 2) unterstützen, müssen das Festlegen dieses Attributs auf SQL_TRUE mithilfe einer der beiden Funktionen unterstützen.  
  
 [2] für die Schnittstellen Konformität der Ebene 1 muss der Treiber zusätzlich zu dem vom Treiber definierten Standardwert einen Wert unterstützen (verfügbar durch Aufrufen von **SQLGetInfo** mit der SQL_DEFAULT_TXN_ISOLATION-Option). Bei der Schnittstellen Konformität der Ebene 2 muss der Treiber auch SQL_TXN_SERIALIZABLE unterstützen.  
  
 In der folgenden Tabelle ist die Übereinstimmungs Stufe der einzelnen ODBC-Anweisungs Attribute angegeben, in denen diese ordnungsgemäß definiert ist.  
  
|Funktion|Übereinstimmungsebene|  
|--------------|-----------------------|  
|SQL_ATTR_APP_PARAM_DESC|Core|  
|SQL_ATTR_APP_ROW_DESC|Core|  
|SQL_ATTR_ASYNC_ENABLE|Ebene 1/Ebene 2 [1]|  
|SQL_ATTR_CONCURRENCY|Ebene 1/Ebene 2 [2]|  
|SQL_ATTR_CURSOR_SCROLLABLE|Ebene 1|  
|SQL_ATTR_CURSOR_SENSITIVITY|Ebene 2|  
|SQL_ATTR_CURSOR_TYPE|Kern/Ebene 2 [3]|  
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
  
 [1] Anwendungen, die Asynchronität auf Verbindungs Ebene unterstützen (erforderlich für Ebene 1), müssen das Festlegen dieses Attributs auf SQL_TRUE durch Aufrufen von **SQLSetConnectAttr**unterstützen. das Attribut muss nicht durch **SQLSetStmtAttr**auf einen anderen Wert als seinen Standardwert festgelegt werden können. Anwendungen, die Asynchronität auf Anweisungs Ebene (erforderlich für Ebene 2) unterstützen, müssen das Festlegen dieses Attributs auf SQL_TRUE mithilfe einer der beiden Funktionen unterstützen.  
  
 [2] für die Schnittstellen Konformität der Ebene 2 muss der Treiber SQL_CONCUR_READ_ONLY und mindestens einen anderen Wert unterstützen.  
  
 [3] für die Schnittstellen Konformität der Ebene 1 muss der Treiber SQL_CURSOR_FORWARD_ONLY und mindestens einen anderen Wert unterstützen. Bei der Schnittstellen Konformität der Ebene 2 muss der Treiber alle Werte unterstützen, die in diesem Dokument definiert sind.
