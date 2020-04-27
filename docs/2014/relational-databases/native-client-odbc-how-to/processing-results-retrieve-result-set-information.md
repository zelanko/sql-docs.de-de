---
title: Abrufen von Resultsetinformationen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a39a6715a9ba8ab08d846aabb96e5b0665a2aa43
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63200294"
---
# <a name="retrieve-result-set-information-odbc"></a>Abrufen von Resultsetinformationen (ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>So rufen Sie Informationen zu einem Resultset ab  
  
1.  Führen Sie [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) aus, um die Anzahl der Spalten im Resultset abzurufen.  
  
2.  Für jede Spalte im Resultset führt die Anwendung nun Folgendes aus:  
  
    -   Führen Sie [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) aus, um Informationen über die Ergebnisspalte abzurufen.  
  
     Oder  
  
    -   Führen Sie [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) aus, um bestimmte Deskriptorinformationen über die Ergebnisspalte abzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Themen zur Vorgehensweise bei der Verarbeitung von Ergebnissen &#40;ODBC-&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [Bestimmen der Eigenschaften eines Resultsets &#40;ODBC-&#41;](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
