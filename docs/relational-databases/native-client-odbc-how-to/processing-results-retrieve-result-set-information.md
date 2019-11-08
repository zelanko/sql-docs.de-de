---
title: Abrufen von Resultsetinformationen (ODBC) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC]
- result sets [ODBC], fetching
ms.assetid: 34f235e4-f80b-4123-8764-9deb18506f14
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f2d998dd8b4444298ff67abc8369993d17e26f55
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2019
ms.locfileid: "73780326"
---
# <a name="processing-results---retrieve-result-set-information"></a>Verarbeiten von Ergebnissen: Abrufen von Resultsetinformationen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-get-information-about-a-result-set"></a>So rufen Sie Informationen zu einem Resultset ab  
  
1.  Führen Sie [SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) aus, um die Anzahl der Spalten im Resultset abzurufen.  
  
2.  Für jede Spalte im Resultset führt die Anwendung nun Folgendes aus:  
  
    -   Führen Sie [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) aus, um Informationen über die Ergebnisspalte abzurufen.  
  
     oder  
  
    -   Führen Sie [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) aus, um bestimmte Deskriptorinformationen über die Ergebnisspalte abzurufen.  
  
## <a name="see-also"></a>Siehe auch  
[Prozessergebnisse &#40;(ODBC)&#41;](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[Bestimmen der Eigenschaften eines Resultsets &#40;(ODBC)&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
