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
ms.openlocfilehash: 2b99d0b97179899b804a31b48a1334172e214f9f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68133446"
---
# <a name="processing-results---retrieve-result-set-information"></a>Verarbeiten von Ergebnissen: Abrufen von Resultsetinformationen
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

    
### <a name="to-get-information-about-a-result-set"></a>So rufen Sie Informationen zu einem Resultset ab  
  
1.  Rufen Sie [SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) um die Anzahl der Spalten im Resultset zu erhalten.  
  
2.  Für jede Spalte im Resultset führt die Anwendung nun Folgendes aus:  
  
    -   Rufen Sie [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) zum Abrufen von Informationen über die Ergebnisspalte.  
  
     oder  
  
    -   Rufen Sie [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) um spezifische Deskriptorinformationen über die Ergebnisspalte abzurufen.  
  
## <a name="see-also"></a>Siehe auch  
[Verarbeiten von Ergebnissen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[Bestimmen der Eigenschaften eines Resultsets &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
