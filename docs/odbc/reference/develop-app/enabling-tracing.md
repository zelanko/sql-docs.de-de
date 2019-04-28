---
title: Aktivieren der Ablaufverfolgung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], enabling
ms.assetid: 48e318bd-2487-4708-a698-ea01f36a45e9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb6d8eaf4a1f4eaadc4e8e9a7030b81c373d8377
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62943131"
---
# <a name="enabling-tracing"></a>Aktivieren der Ablaufverfolgung
Ablaufverfolgung kann in den folgenden drei Arten aktiviert werden:  
  
-   Legen Sie die **Ablaufverfolgung** und **TraceFile** Schlüsselwörter im Registrierungseintrag Odbc.ini. Dies aktiviert oder deaktiviert die Ablaufverfolgung beim **SQLAllocHandle** mit einem *HandleType* SQL_HANDLE_ENV auf, aufgerufen wird. Diese Optionen werden in der Registerkarte "Ablaufverfolgung" im Dialogfeld ODBC-Datenquellen-Administrator angezeigt wird, während Setup für Data Source festgelegt. Weitere Informationen finden Sie unter [Registrierungseinträge für Datenquellen](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Rufen Sie **SQLSetConnectAttr** das SQL_ATTR_TRACE-Verbindungsattribut auf SQL_OPT_TRACE_ON festgelegt. Dies aktiviert oder deaktiviert die Ablaufverfolgung für die Dauer der Verbindung. Weitere Informationen finden Sie unter den [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) funktionsbeschreibung.  
  
-   Verwendung **ODBCSharedTraceFlag** zu aktivieren oder deaktivieren Sie die Ablaufverfolgung dynamisch. (Weitere Informationen finden Sie im nächste Thema, [dynamische Ablaufverfolgung](../../../odbc/reference/develop-app/dynamic-tracing.md).)
