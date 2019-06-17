---
title: Ebene-2-Schnittstellenübereinstimmung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- level 2 interface conformance levels [ODBC]
- conformance levels [ODBC], interface
ms.assetid: 2dc87840-f2fe-43dd-9d7b-bd95523081d9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bff3de6a9b9ec57f1ea96d6db17b9b30c5a22996
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63179820"
---
# <a name="level-2-interface-conformance"></a>Schnittstellenübereinstimmung auf Ebene 2
Der Konformitätsgrad des Level 2-Schnittstelle enthält die Ebene-1-Schnittstelle Konformitätsgrad Funktionalität sowie die folgenden Features:  
  
|||  
|-|-|  
|201|Verwenden Sie die dreiteilige Namen von Tabellen und Sichten. (Weitere Informationen finden Sie in der zweiteiligen Benennungskonvention Unterstützungsfunktion 101 in [Ebene-1-Schnittstellenübereinstimmung](../../../odbc/reference/develop-app/level-1-interface-conformance.md).)|  
|202|Dynamische Parameter zu beschreiben, durch den Aufruf **SQLDescribeParam**.|  
|203|Verwenden Sie nicht nur Eingabeparameter, aber auch Ausgabe und Eingabe/Ausgabe-Parameter und Ergebniswerte von gespeicherten Prozeduren.|  
|204|Verwenden von Lesezeichen, einschließlich Abrufen von Lesezeichen, durch den Aufruf **SQLDescribeCol** und **SQLColAttribute** für die Spalte die Zahl 0, Abrufen von auf ein Lesezeichen, durch den Aufruf **SQLFetchScroll** mit der *FetchOrientation* -Argument auf SQL_FETCH_BOOKMARK; und aktualisieren, löschen und Abrufen von Lesezeichen-Vorgängen, durch den Aufruf **SQLBulkOperations** mit der *Vorgang* -Argument auf SQL_UPDATE_BY_BOOKMARK SQL_DELETE_BY_BOOKMARK oder SQL_FETCH_BY_BOOKMARK festgelegt.|  
|205|Abrufen, die auf Weitere Informationen zum Wörterbuch mit Daten, durch den Aufruf **SQLColumnPrivileges**, **SQLForeignKeys**, und **SQLTablePrivileges**.|  
|206|Verwenden Sie ODBC-Funktionen anstelle von SQL-Anweisungen, um die zusätzliche, durch Aufrufen von Vorgängen **SQLBulkOperations** mit SQL_ADD, oder **SQLSetPos** SQL_DELETE oder SQL_UPDATE auf. (Unterstützung für Aufrufe von **SQLSetPos** mit der *LockType* -Argument auf SQL_LOCK_EXCLUSIVE oder SQL_LOCK_UNLOCK ist nicht Teil der Ebenen der schnittstellenübereinstimmung, jedoch ist ein optionales Feature.)|  
|207|Aktivieren Sie die asynchrone Ausführung der ODBC-Funktionen für die angegebene einzelne Anweisungen.|  
|208|Abrufen der SQL_ROWVER Zeile identifizieren-Spalte mit Tabellen, durch den Aufruf **SQLSpecialColumns**. (Weitere Informationen finden Sie auf die Unterstützung für **SQLSpecialColumns** mit der *IdentifierType* Argument festgelegt wird, um SQL_BEST_ROWID als 20 im feature [Kernschnittstellenübereinstimmung](../../../odbc/reference/develop-app/core-interface-conformance.md) .)|  
|209|Legen Sie das SQL_ATTR_CONCURRENCY-Anweisungsattribut auf mindestens einen anderen Wert als SQL_CONCUR_READ_ONLY.|  
|210|Die Fähigkeit, Timeout-anmeldeanforderung und SQL-Abfragen (SQL_ATTR_LOGIN_TIMEOUT und SQL_ATTR_QUERY_TIMEOUT).|  
|211|Die Möglichkeit, um die Standardisolationsstufe zu ändern; die Fähigkeit zum Ausführen von Transaktionen mit der "serialisierbar" Maß an Isolation.|
