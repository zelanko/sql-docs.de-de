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
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48142180"
---
# <a name="retrieve-result-set-information-odbc"></a>Abrufen von Resultsetinformationen (ODBC)
    
### <a name="to-get-information-about-a-result-set"></a>So rufen Sie Informationen zu einem Resultset ab  
  
1.  Rufen Sie [SQLNumResultCols](../native-client-odbc-api/sqlnumresultcols.md) um die Anzahl der Spalten im Resultset zu erhalten.  
  
2.  Für jede Spalte im Resultset führt die Anwendung nun Folgendes aus:  
  
    -   Rufen Sie [SQLDescribeCol](../native-client-odbc-api/sqldescribecol.md) zum Abrufen von Informationen über die Ergebnisspalte.  
  
     oder  
  
    -   Rufen Sie [SQLColAttribute](../native-client-odbc-api/sqlcolattribute.md) um spezifische Deskriptorinformationen über die Ergebnisspalte abzurufen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verarbeiten von Ergebnissen: Themen zur Vorgehensweise &#40;ODBC&#41;](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)   
 [Bestimmen der Eigenschaften eines Resultsets &#40;ODBC&#41;](../native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
