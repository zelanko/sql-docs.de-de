---
title: Deklarieren der Anwendungs&#39;s ODBC-Version | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285230"
---
# <a name="declaring-the-application39s-odbc-version"></a>Deklarieren der Anwendungs&#39;s ODBC-Version
Bevor eine Anwendung eine Verbindung zuordnet, muss Sie das SQL_ATTR_ODBC_VERSION Environment-Attribut festlegen. Dieses Attribut gibt an, dass die Anwendung der ODBC *2. x* -oder ODBC *3. x* -Spezifikation folgt, wenn die folgenden Elemente verwendet werden:  
  
-   **Sqlstates**. Viele SQLSTATE-Werte unterscheiden sich in ODBC *2. x* und ODBC *3. x*.  
  
-   **Datums-, Uhrzeit-und Timestamp-Typbezeichner**. In der folgenden Tabelle werden die Typbezeichner für Datums-, Uhrzeit-und Zeitstempel Daten in ODBC *2. x* und ODBC *3. x*angezeigt.  
  
    |ODBC *2. x*|ODBC *3. x*|  
    |----------------|----------------|  
    |**SQL-Typenbezeichner**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**C-Typbezeichner**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   _CatalogName_-**Argument in SQLTables**.   In ODBC *2. x*werden die Platzhalter Zeichen ("%" und "_") im *CatalogName* -Argument wörtlich behandelt. In ODBC *3. x*werden Sie als Platzhalter Zeichen behandelt. Daher kann eine Anwendung, die auf die ODBC *2. x* -Spezifikation folgt, diese nicht als Platzhalter Zeichen verwenden und nicht mit Escapezeichen versehen, wenn Sie als Literale verwendet werden. Eine Anwendung, die der ODBC *3. x* -Spezifikation folgt, kann diese als Platzhalter Zeichen verwenden oder Sie mit Escapezeichen versehen und als Literale verwenden. Weitere Informationen finden Sie unter [Argumente in Katalog Funktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 Die Treiber ODBC *3. x* Driver Manager und ODBC *3. x* überprüfen die Version der ODBC-Spezifikation, auf die eine Anwendung geschrieben wird, und reagieren entsprechend. Wenn die Anwendung z. b. der ODBC *2. x* -Spezifikation folgt und **SQLExecute** aufruft, bevor **SQLPrepare**aufgerufen wird, gibt der ODBC *3. x* -Treiber-Manager SQLSTATE S1010 (Funktions Sequenz Fehler) zurück. Wenn die Anwendung der ODBC *3. x* -Spezifikation folgt, gibt der Treiber-Manager SQLSTATE HY010 (Funktions Sequenz Fehler) zurück. Weitere Informationen finden Sie unter abwärts [Kompatibilität und Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Anwendungen, die der ODBC *3. x* -Spezifikation folgen, müssen bedingten Code verwenden, um die Verwendung von Funktionen in ODBC *3. x* beim Arbeiten mit ODBC *2. x* -Treibern zu vermeiden. ODBC *2. x* -Treiber unterstützen keine neuen Funktionen in ODBC *3. x* , nur weil die Anwendung deklariert, dass Sie auf die ODBC *3. x* -Spezifikation folgt. Darüber hinaus unterstützen ODBC *3. x* -Treiber keine Funktionen, die neu in ODBC *3. x* sind, sondern nur, weil die Anwendung deklariert, dass Sie auf die ODBC *2. x* -Spezifikation folgt.
