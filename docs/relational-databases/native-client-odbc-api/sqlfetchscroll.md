---
title: SQLFetchScroll | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4418a1ce37958c704e30692ab1cfed57aca471f5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2018
ms.locfileid: "37410249"
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SQLFetchScroll** ein Rowset von Daten an die Anwendung zurück. Die Größe des Rowsets wird mit festgelegt [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md). Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt alle definierten abrufanweisungen (beispielsweise SQL_FETCH_RELATIVE) mit folgenden Einschränkungen:  
  
-   Wenn ein Vorwärtscursor für die Anweisung definiert ist, ist SQL_FETCH_NEXT erforderlich und Versuche, den Abrufvorgang auf eine andere Weise durchzuführen, werden mit einem Fehler quittiert.  
  
-   SQL_FETCH_BOOKMARK wird nur für statische und keysetgesteuerte Cursor unterstützt.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>SQLFetchScroll-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Ergebnisspaltenwerte von Datum-/Uhrzeit-Typen werden konvertiert, wie in beschrieben [Konvertierungen von SQL-in C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>SQLFetchScroll-Unterstützung für große CLR-UDTs  
 **SQLFetchScroll** unterstützt große CLR-benutzerdefinierte Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLFetchScroll-Funktion](http://go.microsoft.com/fwlink/?LinkId=59343)   
 [ODBC-API-Implementierungsdetails](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
