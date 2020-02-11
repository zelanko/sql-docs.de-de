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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6ed360c39b87efe851bcbbb5c60762288ea1719
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68114282"
---
# <a name="status-records"></a>Statusdatensätze
Die Felder in den Statusdaten Sätzen enthalten Informationen zu bestimmten Fehlern oder Warnungen, die vom Treiber-Manager, Treiber oder der Datenquelle zurückgegeben werden, einschließlich SQLSTATE, System eigener Fehlernummer, Diagnose Meldung, Spaltennummer und Zeilennummer. Status Datensätze können nur erstellt werden, wenn die Funktion SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA oder SQL_STILL_EXECUTING zurückgibt. Eine umfassende Liste der Felder in den Statusdaten Sätzen finden Sie in der Beschreibung der [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) -Funktion.  
  
 Dieser Abschnitt enthält die folgenden Themen:  
  
-   [Sequenz der Statusdatensätze](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [SQLSTATEs](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Diagnosemeldungen](../../../odbc/reference/develop-app/diagnostic-messages.md)
