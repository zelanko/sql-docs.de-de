---
title: SQLFetchScroll | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFetchScroll function
ms.assetid: 524a3985-a08d-4445-99e0-bb551a666615
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3c9614a71c0015d17178a57d33c5fd0d9b62433c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63154691"
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
  **SQLFetchScroll** ein Rowset von Daten an die Anwendung zurück. Die Größe des Rowsets wird mit festgelegt [SQLSetStmtAttr](sqlsetstmtattr.md). Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC-Treiber unterstützt alle definierten abrufanweisungen (beispielsweise SQL_FETCH_RELATIVE) mit folgenden Einschränkungen:  
  
-   Wenn ein Vorwärtscursor für die Anweisung definiert ist, ist SQL_FETCH_NEXT erforderlich und Versuche, den Abrufvorgang auf eine andere Weise durchzuführen, werden mit einem Fehler quittiert.  
  
-   SQL_FETCH_BOOKMARK wird nur für statische und keysetgesteuerte Cursor unterstützt.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>SQLFetchScroll-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Ergebnisspaltenwerte von Datum-/Uhrzeit-Typen werden konvertiert, wie in beschrieben [Konvertierungen von SQL-in C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md).  
  
 Weitere Informationen finden Sie unter [Datums- / Uhrzeitverbesserungen &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>SQLFetchScroll-Unterstützung für große CLR-UDTs  
 **SQLFetchScroll** unterstützt große CLR-benutzerdefinierte Typen (UDTs). Weitere Informationen finden Sie unter [Large CLR User-Defined Typen &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Siehe auch  
 [SQLFetchScroll-Funktion](https://go.microsoft.com/fwlink/?LinkId=59343)   
 [ODBC-API-Implementierungsdetails](odbc-api-implementation-details.md)  
  
  
