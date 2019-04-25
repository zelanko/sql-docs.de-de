---
title: Dynamische Ablaufverfolgung | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63dbfda01d96cad53e5830e598b5812ed79d8f04
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62468777"
---
# <a name="dynamic-tracing"></a>Dynamische Ablaufverfolgung
Ablaufverfolgung kann aktiviert oder deaktiviert werden, zu einem beliebigen Zeitpunkt in einer Anwendung ausführen. Dies kann es sich um eine Anwendung, um eine beliebige Anzahl von Funktionsaufrufen zu verfolgen.  
  
 Die Variable **ODBCSharedTraceFlag** zum Aktivieren der Ablaufverfolgung dynamisch festgelegt ist. Diese Variable wird von allen Kopien des Treiber-Managers gemeinsam genutzt. Wenn jede Anwendung diese Variable festgelegt wird, wird die Ablaufverfolgung für alle ODBC-Anwendungen, die derzeit ausgeführt aktiviert. Zum Aktivieren der Ablaufverfolgung aus, wenn dynamische Ablaufverfolgung aktiviert ist, eine Anwendung ruft **SQLSetConnectAttr** SQL_ATTR_TRACE auf SQL_TRACE_OFF festgelegt. Dieser Aufruf wird die Ablaufverfolgung aus, für die Anwendung nur aktivieren. Anwendungen, die mit Odbc32.lib verknüpft sind, können mithilfe dieser Variablen ändern. In einem Fenster in Echtzeit anstelle der Ablaufverfolgungsdatei an, der nach der ODBC-Sitzung geöffnet werden muss, können die Ablaufverfolgung angezeigt werden. Steuerelemente können Bildschirms zum Aktivieren einer Anwendung hinzugefügt werden, Ablaufverfolgung, die auf aktiviert oder deaktiviert wird.  
  
 Die Ablaufverfolgung, die DLL im Lieferumfang ODBC 3.*.x* ist nicht threadsicher. Es ist nicht sichergestellt, dass die Protokolldatei ordnungsgemäß geschrieben werden, wenn globale Ablaufverfolgung aktiviert ist (die Variable **ODBCSharedTraceFlag** festgelegt ist) und mehr als eine Anwendung, die in die Ablaufverfolgungsdatei geschrieben ist, zur gleichen Zeit. Diese Bedingung ist kein Fehler zurückgegeben.
