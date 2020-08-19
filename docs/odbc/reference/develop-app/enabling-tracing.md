---
description: Aktivieren der Ablaufverfolgung
title: Aktivieren der Ablauf Verfolgung | Microsoft-Dokumentation
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
ms.openlocfilehash: af9a78989a80124fb9a7f475edf17022e7942bde
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482983"
---
# <a name="enabling-tracing"></a>Aktivieren der Ablaufverfolgung
Die Ablauf Verfolgung kann auf die folgenden drei Arten aktiviert werden:  
  
-   Legen Sie die Schlüsselwörter **Trace** und **Tracefile** im Registrierungs Eintrag Odbc.ini fest. Dadurch wird die Ablauf Verfolgung aktiviert oder deaktiviert, wenn **sqlprovichandle** mit dem *Typ* "SQL_HANDLE_ENV" aufgerufen wird. Diese Optionen werden im Dialogfeld ODBC-Datenquellen-Administrator auf der Registerkarte Ablauf Verfolgung festgelegt, das beim Einrichten der Datenquelle angezeigt wird. Weitere Informationen finden Sie unter [Registrierungseinträge für Datenquellen](../../../odbc/reference/install/registry-entries-for-data-sources.md).  
  
-   Aufrufen von **SQLSetConnectAttr** , um das SQL_ATTR_TRACE-Verbindungs Attribut auf SQL_OPT_TRACE_ON festzulegen. Dadurch wird die Ablauf Verfolgung für die Dauer der Verbindung aktiviert oder deaktiviert. Weitere Informationen finden Sie in der Beschreibung der [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md) -Funktion.  
  
-   Verwenden Sie **odbcsharedtraceflag** , um die Ablauf Verfolgung dynamisch zu aktivieren bzw. zu deaktivieren. (Weitere Informationen finden Sie im nächsten Thema [Dynamic Tracing](../../../odbc/reference/develop-app/dynamic-tracing.md).)
