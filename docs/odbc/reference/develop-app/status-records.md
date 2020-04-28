---
title: Status Datensätze | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- status records [ODBC]
- diagnostic records [ODBC]
ms.assetid: 4a987f69-158f-4cc4-a31b-2b7dd8dcbb87
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4afef16137404fcdfd3e1d328642f1d314829538
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81301371"
---
# <a name="status-records"></a>Statusdatensätze
Die Felder in den Statusdaten Sätzen enthalten Informationen zu bestimmten Fehlern oder Warnungen, die vom Treiber-Manager, Treiber oder der Datenquelle zurückgegeben werden, einschließlich SQLSTATE, System eigener Fehlernummer, Diagnose Meldung, Spaltennummer und Zeilennummer. Status Datensätze können nur erstellt werden, wenn die Funktion SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA oder SQL_STILL_EXECUTING zurückgibt. Eine umfassende Liste der Felder in den Statusdaten Sätzen finden Sie in der Beschreibung der [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) -Funktion.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Sequenz der Statusdatensätze](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [SQLSTATEs](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Diagnosemeldungen](../../../odbc/reference/develop-app/diagnostic-messages.md)
