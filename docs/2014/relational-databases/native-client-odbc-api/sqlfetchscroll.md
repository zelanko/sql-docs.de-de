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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 2b4a5094f8bac1e3972b4d0b2daa7a0da9fa3629
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706133"
---
# <a name="sqlfetchscroll"></a>SQLFetchScroll
  **SQLFetchScroll** gibt einen Zeilen Satz von Daten an die Anwendung zurück. Die Größe des Zeilen Satzes wird mithilfe von [SQLSetStmtAttr](sqlsetstmtattr.md)festgelegt. Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client-ODBC-Treiber unterstützt alle definierten Abruf Anweisungen (z. b. SQL_FETCH_RELATIVE) mit den folgenden Einschränkungen:  
  
-   Wenn ein Vorwärtscursor für die Anweisung definiert ist, ist SQL_FETCH_NEXT erforderlich und Versuche, den Abrufvorgang auf eine andere Weise durchzuführen, werden mit einem Fehler quittiert.  
  
-   SQL_FETCH_BOOKMARK wird nur für statische und keysetgesteuerte Cursor unterstützt.  
  
## <a name="sqlfetchscroll-support-for-enhanced-date-and-time-features"></a>SQLFetchScroll-Unterstützung für erweiterte Funktionen für Datum und Uhrzeit  
 Ergebnis Spaltenwerte von Datums-/Uhrzeittypen werden wie in [Konvertierungen von SQL in C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)beschrieben konvertiert.  
  
 Weitere Informationen finden Sie unter [Verbesserungen bei Datum und Uhrzeit &#40;ODBC-&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlfetchscroll-support-for-large-clr-udts"></a>SQLFetchScroll-Unterstützung für große CLR-UDTs  
 **SQLFetchScroll** unterstützt große benutzerdefinierte CLR-Typen (UDTs). Weitere Informationen finden Sie unter [große benutzerdefinierte CLR-Typen &#40;ODBC-&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLFetchScroll-Funktion](https://go.microsoft.com/fwlink/?LinkId=59343)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
