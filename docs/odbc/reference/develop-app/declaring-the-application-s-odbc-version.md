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
ms.openlocfilehash: ea97e3cd7a8fee3b3397524bf2c48c428d6a0be0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68076840"
---
# <a name="declaring-the-application39s-odbc-version"></a>Deklarieren die Anwendung&#39;s ODBC-Version
Bevor eine Anwendung eine Verbindung zuordnet, muss er umgebungsattributs SQL_ATTR_ODBC_VERSION festgelegt. Dieses Attribut gibt an, dass die Anwendung die ODBC folgt *2.x* oder ODBC- *3.x* Spezifikation, wenn Sie die folgenden Elemente verwenden:  
  
-   **SQLSTATEs**. SQLSTATE-Werten viele unterscheiden sich in ODBC *2.x* und ODBC *3.x*.  
  
-   **Date, Time und Timestamp-Typ-IDs**. Die folgende Tabelle zeigt die Typ-IDs für Date, Time und Timestamp-Daten in ODBC *2.x* und ODBC *3.x*.  
  
    |ODBC *2.x*|ODBC *3.x*|  
    |----------------|----------------|  
    |**SQL-Typenbezeichner**||  
    |SQL_DATE|SQL_TYPE_DATE|  
    |SQL_TIME|SQL_TYPE_TIME|  
    |SQL_TIMESTAMP|SQL_TYPE_TIMESTAMP|  
    |**C-Typ-IDs**||  
    |SQL_C_DATE|SQL_C_TYPE_DATE|  
    |SQL_C_TIME|SQL_C_TYPE_TIME|  
    |SQL_C_TIMESTAMP|SQL_C_TYPE_TIMESTAMP|  
  
-   _CatalogName_  **-Argument in SQLTables**. In ODBC *2.x*, die Platzhalterzeichen ("%" und "_") in der *CatalogName* Argument buchstäblich behandelt werden. In ODBC *3.x*, werden sie als Platzhalterzeichen behandelt. Daher eine Anwendung, die die ODBC folgt *2.x* Spezifikation kann diese nicht als verwenden Platzhalter Zeichen und nicht mit Escapezeichen versehen werden, wenn diese als Literale zu verwenden. Eine Anwendung, die die ODBC folgt *3.x* Spezifikation kann diese als Platzhalterzeichen verwenden oder mit Escapezeichen versehen und sie als Literale. Weitere Informationen finden Sie unter [Argumente in Katalogfunktionen](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md).  
  
 Die ODBC *3.x* Treiber-Manager und ODBC- *3.x* Treiber prüfen die Version des ODBC-Spezifikation, die eine Anwendung geschrieben, und entsprechend reagieren. Wenn die Anwendung die ODBC folgt z. B. *2.x* -Spezifikation und ruft **SQLExecute** vor dem Aufruf **SQLPrepare**, die ODBC *3.x*-Treiber-Manager gibt SQLSTATE S1010 (Sequenzfehler funktionieren). Wenn die Anwendung die ODBC folgt *3.x* -Spezifikation der Treiber-Manager gibt einen SQLSTATE HY010 (Sequenzfehler funktionieren). Weitere Informationen finden Sie unter [Abwärtskompatibilität und zur Einhaltung von Standards](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).  
  
> [!IMPORTANT]  
>  Anwendungen, die die ODBC folgen *3.x* Spezifikation muss bedingten Code verwenden, um zu vermeiden, mithilfe von Funktionen noch nicht mit ODBC *3.x* beim Arbeiten mit ODBC *2.x* Treiber. ODBC *2.x* Treiber unterstützen keine Funktionen, die noch nicht mit ODBC *3.x* nur, weil die Anwendung wird deklariert, dass dabei die ODBC *3.x* Spezifikation. Darüber hinaus ODBC *3.x* Treiber werden nicht eingestellt, zur Unterstützung von Funktionen, die noch nicht mit ODBC *3.x* nur, weil die Anwendung wird deklariert, dass dabei die ODBC *2.x* Spezifikation.
