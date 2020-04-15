---
title: Deklarieren der Anwendung&#39;s ODBC-Version | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- declaring ODBC version [ODBC]
- data sources [ODBC], declaring ODBC version
- ODBC drivers [ODBC], declaring ODBC version
- connecting to driver [ODBC], declaring ODBC version
- connecting to data source [ODBC], declaring ODBC version
- version declaration [ODBC]
ms.assetid: 083a1ef5-580a-4979-9cf3-50f4549a080a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ba346ed7f7a261446110c5513026d20a86fd3a19
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285230"
---
# <a name="declaring-the-application39s-odbc-version"></a>Deklarieren der Anwendung&#39;s ODBC-Version
Bevor eine Anwendung eine Verbindung zuweist, muss sie das SQL_ATTR_ODBC_VERSION Umgebungsattribut festlegen. Dieses Attribut besagt, dass die Anwendung die ODBC *2.x-* oder ODBC *3.x-Spezifikation* folgt, wenn die folgenden Elemente verwendet werden:  
  
-   **SQLSTATEs**. Viele SQLSTATE-Werte unterscheiden sich in ODBC *2.x* und ODBC *3.x*.  
  
-   **Datums-, Uhrzeit- und Zeitstempeltypbezeichner**. Die folgende Tabelle zeigt die Typbezeichner für Datums-, Uhrzeit- und Zeitstempeldaten in ODBC *2.x* und ODBC *3.x*.  
  
    |ODBC *2.x*|ODBC *3.x*|  
    |----------------|----------------|  
    |**SQL-Typenbezeichner**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**C-Typ-Bezeichner**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   _CatalogName-Argument_  **in SQLTables**. In ODBC *2.x*werden die Platzhalterzeichen ("%" und "_") im *CatalogName-Argument* wörtlich behandelt. In ODBC *3.x*werden sie als Platzhalterzeichen behandelt. Daher kann eine Anwendung, die der ODBC *2.x-Spezifikation* folgt, diese nicht als Platzhalterzeichen verwenden und sie nicht entkommen, wenn sie als Literale verwendet werden. Eine Anwendung, die der ODBC *3.x-Spezifikation* folgt, kann diese als Platzhalterzeichen verwenden oder sie umgehen und als Literale verwenden. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 Die Treiber ODBC *3.x* Driver Manager und ODBC *3.x* überprüfen die Version der ODBC-Spezifikation, auf die eine Anwendung geschrieben ist, und reagieren entsprechend. Wenn die Anwendung beispielsweise der ODBC *2.x-Spezifikation* folgt und **SQLExecute** aufruft, bevor **SIE SQLPrepare**aufruft, gibt der ODBC *3.x-Treiber-Manager* SQLSTATE S1010 (Funktionssequenzfehler) zurück. Wenn die Anwendung der ODBC *3.x-Spezifikation* folgt, gibt der Treiber-Manager SQLSTATE HY010 (Funktionssequenzfehler) zurück. Weitere Informationen finden Sie unter [Abwärtskompatibilität und Konformität von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Anwendungen, die der ODBC *3.x-Spezifikation* folgen, müssen bedingten Code verwenden, um zu vermeiden, dass odBC *3.x* bei der Arbeit mit ODBC *2.x-Treibern* eine neue Funktionalität verwendet. ODBC *2.x-Treiber* unterstützen keine Funktionalität, die für ODBC *3.x* neu ist, nur weil die Anwendung deklariert, dass sie der ODBC *3.x-Spezifikation* folgt. Darüber hinaus unterstützen ODBC *3.x-Treiber* nicht die Funktionalität, die für ODBC *3.x* neu ist, nur weil die Anwendung deklariert, dass sie der ODBC *2.x-Spezifikation* folgt.
