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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f00fe6310c339d7ec24736c5f659d3b7b7d84ce8
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006577"
---
# <a name="processing-results---retrieve-result-set-information"></a>Verarbeiten von Ergebnissen: Abrufen von Resultsetinformationen
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

    
### <a name="to-get-information-about-a-result-set"></a>So rufen Sie Informationen zu einem Resultset ab  
  
1.  Führen Sie [SQLNumResultCols](../../relational-databases/native-client-odbc-api/sqlnumresultcols.md) aus, um die Anzahl der Spalten im Resultset abzurufen.  
  
2.  Für jede Spalte im Resultset führt die Anwendung nun Folgendes aus:  
  
    -   Führen Sie [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) aus, um Informationen über die Ergebnisspalte abzurufen.  
  
     oder  
  
    -   Führen Sie [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md) aus, um bestimmte Deskriptorinformationen über die Ergebnisspalte abzurufen.  
  
## <a name="see-also"></a>Weitere Informationen  
[Verarbeiten von Ergebnissen &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-how-to/processing-results-process-results.md)

[Bestimmen der Eigenschaften eines Resultsets &#40;ODBC-&#41;](../../relational-databases/native-client-odbc-results/determining-the-characteristics-of-a-result-set-odbc.md)  
  
  
