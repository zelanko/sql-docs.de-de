---
title: Aktivieren der Ablaufverfolgung | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 80bd4023a0260b67d11d7b4ded1bb810b81e0ab2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287350"
---
# <a name="enabling-tracing"></a>Aktivieren der Ablaufverfolgung
Die Ablaufverfolgung kann auf drei Arten aktiviert werden:  
  
-   Legen Sie die Schlüsselwörter **Trace** und **TraceFile** im Registrierungseintrag Odbc.ini fest. Dadurch wird die Ablaufverfolgung aktiviert oder deaktiviert, wenn **SQLAllocHandle** mit einem *HandleType* von SQL_HANDLE_ENV aufgerufen wird. Diese Optionen werden auf der Registerkarte Ablaufverfolgung des Dialogfelds ODBC-Datenquellenadministrator festgelegt, das während der Datenquelleneinrichtung angezeigt wird. Weitere Informationen finden Sie unter [Registrierungseinträge für Datenquellen](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Rufen Sie **SQLSetConnectAttr** auf, um das SQL_ATTR_TRACE Verbindungsattribut auf SQL_OPT_TRACE_ON festzulegen. Dadurch wird die Ablaufverfolgung für die Dauer der Verbindung aktiviert oder deaktiviert. Weitere Informationen finden Sie in der [SQLSetConnectAttr-Funktionsbeschreibung.](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)  
  
-   Verwenden Sie **ODBCSharedTraceFlag,** um die Ablaufverfolgung dynamisch ein- oder auszuschalten. (Weitere Informationen finden Sie im nächsten Thema, [Dynamic Tracing](../../../odbc/reference/develop-app/dynamic-tracing.md).)
