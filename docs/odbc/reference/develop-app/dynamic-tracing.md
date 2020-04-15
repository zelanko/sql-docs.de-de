---
title: Dynamische Ablaufverfolgung | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], dynamic
- dynamic tracing [ODBC]
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8cbd2dbae4f4b437f45845ce2791f4a9b0aa8c8b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305766"
---
# <a name="dynamic-tracing"></a>Dynamische Ablaufverfolgung
Die Ablaufverfolgung kann jederzeit in einem Anwendungslauf aktiviert oder deaktiviert werden. Dadurch kann eine Anwendung eine beliebige Anzahl von Funktionsaufrufen verfolgen.  
  
 Die Variable **ODBCSharedTraceFlag** ist so eingestellt, dass die Ablaufverfolgung dynamisch aktiviert wird. Diese Variable wird von allen ausgeführten Kopien des Treiber-Managers gemeinsam genutzt. Wenn eine Anwendung diese Variable festlegt, ist die Ablaufverfolgung für alle derzeit ausgeführten ODBC-Anwendungen aktiviert. Um die Ablaufverfolgung zu deaktivieren, wenn die dynamische Ablaufverfolgung aktiviert ist, ruft eine Anwendung **SQLSetConnectAttr** auf, um SQL_ATTR_TRACE auf SQL_TRACE_OFF festzulegen. Dieser Aufruf deaktiviert die Ablaufverfolgung nur für diese Anwendung. Anwendungen, die mit Odbc32.lib verknüpft sind, können die Verwendung dieser Variablen ändern. Ablaufverfolgungsdaten können in einem Echtzeitfenster anstelle der Ablaufverfolgungsdatei angezeigt werden, die nach der ODBC-Sitzung geöffnet werden muss. Steuerelemente können dem Bildschirm einer Anwendung hinzugefügt werden, um die Ablaufverfolgung nach Belieben ein- oder auszuschalten.  
  
 Die mit ODBC 3 *.x* ausgelieferte Ablaufverfolgungs-DLL ist nicht threadsicher. Es ist nicht garantiert, dass die Protokolldatei korrekt geschrieben wird, wenn die globale Ablaufverfolgung aktiviert ist (die Variable **ODBCSharedTraceFlag** ist festgelegt) und mehr als eine Anwendung gleichzeitig in die Ablaufverfolgungsdatei schreibt. Diese Bedingung gibt keinen Fehler zurück.
