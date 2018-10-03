---
title: Statusdatensätze | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 986cd3c48104bfe822934eb415b854b8e976f242
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47813768"
---
# <a name="status-records"></a>Statusdatensätze
Die Felder in den statusdatensätzen enthalten Informationen über bestimmte Fehler oder Warnungen, die von der Quelle-Treiber-Manager, Treiber oder Daten, einschließlich der SQLSTATE, systemeigener Fehlernummer, diagnosemeldung, Spaltennummer und Zeilennummer zurückgegeben. Statusdatensätze können erstellt werden, nur verwendet werden, wenn die Funktion SQL_ERROR, SQL_SUCCESS_WITH_INFO, SQL_NO_DATA, SQL_NEED_DATA oder SQL_STILL_EXECUTING zurückgibt. Eine vollständige Liste der Felder in den statusdatensätzen, finden Sie unter den [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) funktionsbeschreibung.  
  
 Dieser Abschnitt enthält die folgenden Themen.  
  
-   [Sequenz der Statusdatensätze](../../../odbc/reference/develop-app/sequence-of-status-records.md)  
  
-   [SQLSTATEs](../../../odbc/reference/develop-app/sqlstates.md)  
  
-   [Diagnosemeldungen](../../../odbc/reference/develop-app/diagnostic-messages.md)
