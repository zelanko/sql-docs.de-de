---
title: Abrufen von Ergebnissatzinformationen (ODBC) | Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f1c65841db0fdfd386891cfbd03bdee483ce25f6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300370"
---
# <a name="processing-results---retrieve-result-set-information"></a>Verarbeiten von Ergebnissen: Abrufen von Resultsetinformationen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

    
### <a name="to-get-information-about-a-result-set"></a>So rufen Sie Informationen zu einem Resultset ab  
  
1.  Rufen Sie [SQLNumResultCols auf,](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) um die Anzahl der Spalten im Resultset abzurufen.  
  
2.  Für jede Spalte im Resultset führt die Anwendung nun Folgendes aus:  
  
    -   Rufen Sie [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) auf, um Informationen zur Ergebnisspalte abzurufen.  
  
     oder  
  
    -   Rufen Sie [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) auf, um bestimmte Deskriptorinformationen zur Ergebnisspalte abzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Prozessergebnisse &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[Bestimmen der Eigenschaften eines Result Sets &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
