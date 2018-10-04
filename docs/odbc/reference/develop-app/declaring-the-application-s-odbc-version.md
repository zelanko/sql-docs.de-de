---
title: Deklarieren die Anwendung&#39;s ODBC-Version | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd212f45e02ddce4c64a8b4a7d664ddaedf8090a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47666828"
---
# <a name="declaring-the-application39s-odbc-version"></a>Deklarieren die Anwendung&#39;s ODBC-Version
Bevor eine Anwendung eine Verbindung zuordnet, muss er umgebungsattributs SQL_ATTR_ODBC_VERSION festgelegt. Dieses Attribut gibt an, dass die Anwendung die ODBC 2. folgt. *x* oder ODBC-3. *X* Spezifikation, wenn Sie die folgenden Elemente verwenden:  
  
-   **SQLSTATEs**. SQLSTATE-Werten viele unterscheiden sich in ODBC 2. *x* und ODBC 3. *X*.  
  
-   **Date, Time und Timestamp-Typ-IDs**. Die folgende Tabelle zeigt die Typ-IDs für Date, Time und Timestampdaten in ODBC 2. *x* und ODBC 3. *X*.  
  
    |ODBC-2. *x*|ODBC 3. *x*|  
    |----------------|----------------|  
    |**SQL-Typenbezeichner**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**C-Typ-IDs**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   *CatalogName***-Argument in SQLTables**.   In ODBC 2. *x*, die Platzhalterzeichen ("%" und "_") in der *CatalogName* Argument buchstäblich behandelt werden. In ODBC 3. *x*, werden sie als Platzhalterzeichen behandelt. Daher eine Anwendung, die die ODBC 2. folgt. *x* Spezifikation kann diese nicht als verwenden Platzhalter Zeichen und nicht mit Escapezeichen versehen werden, wenn diese als Literale zu verwenden. Eine Anwendung, die die ODBC 3. folgt. *x* Spezifikation kann diese als Platzhalterzeichen verwenden oder mit Escapezeichen versehen und sie als Literale. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 Die ODBC 3.*.x* Treiber-Manager und ODBC 3.*.x* Treiber prüfen die Version des ODBC-Spezifikation, die eine Anwendung geschrieben, und entsprechend reagieren. Beispielsweise, wenn die Anwendung die ODBC 2. folgt. *x* -Spezifikation und ruft **SQLExecute** vor dem Aufruf **SQLPrepare**, die ODBC 3.*.x* -Treiber-Manager gibt SQLSTATE S1010 (zurück. Fehler bei Funktionssequenz). Wenn die Anwendung die ODBC 3. folgt *.x* -Spezifikation der Treiber-Manager gibt einen SQLSTATE HY010 (Sequenzfehler funktionieren). Weitere Informationen finden Sie unter [Abwärtskompatibilität und zur Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Anwendungen, die die ODBC 3. folgen. *x* Spezifikation muss bedingten Code verwenden, um zu vermeiden, mithilfe von Funktionen noch nicht mit ODBC 3. *X* beim Arbeiten mit ODBC 2. *X* Treiber. ODBC-2. *x* Treiber unterstützen keine Funktionen, die noch nicht mit ODBC 3. *X* nur, weil die Anwendung wird deklariert, dass die ODBC 3. folgt. *X* Spezifikation. Darüber hinaus ODBC 3. *x* Treiber sind nicht zur Unterstützung von Funktionen, die noch nicht mit ODBC 3. eingestellt. *X* nur, weil die Anwendung gibt an, dass sie die ODBC 2. folgt. *X* Spezifikation.
