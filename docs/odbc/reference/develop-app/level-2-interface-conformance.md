---
description: Schnittstellenübereinstimmung auf Ebene 2
title: Schnittstellen Konformität der Ebene 2 | Microsoft-Dokumentation
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 31b7148b05d3870a7f23a51167fffeb1860c26d8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476562"
---
# <a name="level-2-interface-conformance"></a>Schnittstellenübereinstimmung auf Ebene 2
Die Schnittstelle für die Schnittstellen Konformität der Ebene 2 umfasst die Funktionen der Schnittstellen Konformität auf Ebene 1 sowie die folgenden Features:  
  
|Funktions Nummer|Beschreibung|  
|-|-|  
|201|Verwenden Sie dreiteilige Namen von Datenbanktabellen und-Sichten. (Weitere Informationen finden Sie unter die zweiteilige namens Unterstützung 101 in der [Schnittstellen Konformität der Ebene 1](../../../odbc/reference/develop-app/level-1-interface-conformance.md).)|  
|202|Beschreiben Sie die dynamischen Parameter durch Aufrufen von **SQLDescribeParam**.|  
|203|Verwenden Sie nicht nur Eingabeparameter, sondern auch Ausgabe-und Eingabe-/Ausgabeparameter sowie Ergebnis Werte gespeicherter Prozeduren.|  
|204|Verwenden von Lesezeichen, einschließlich Abrufen von Lesezeichen, durch Aufrufen von **SQLDescribeCol** und **SQLColAttribute** für die Spaltennummer 0; Abrufen auf der Grundlage eines Lesezeichens, durch Aufrufen von **SQLFetchScroll** , wobei das *FetchOrientation* -Argument auf SQL_FETCH_BOOKMARK festgelegt ist. und zum Aktualisieren, löschen und Abrufen von Lesezeichen Vorgängen durch Aufrufen von **SQLBulkOperations** mit dem *Operations* -Argument, das auf SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK oder SQL_FETCH_BY_BOOKMARK festgelegt ist.|  
|205|Rufen Sie erweiterte Informationen über das Datenwörterbuch ab, indem Sie **SQLColumnPrivileges**, **sqlfremdnkeys**und **SQLTablePrivileges**aufrufen.|  
|206|Verwenden Sie ODBC-Funktionen anstelle von SQL-Anweisungen, um zusätzliche Daten Bank Vorgänge auszuführen, indem Sie **SQLBulkOperations** mit SQL_ADD oder **SQLSetPos** mit SQL_DELETE oder SQL_UPDATE aufrufen. (Die Unterstützung von Aufrufen von **SQLSetPos** mit dem *Lock Type* -Argument, das auf SQL_LOCK_EXCLUSIVE oder SQL_LOCK_UNLOCK festgelegt ist, ist nicht Teil der Übereinstimmungs Ebenen, aber ist ein optionales Feature.)|  
|207|Aktivieren Sie die asynchrone Ausführung von ODBC-Funktionen für bestimmte einzelne Anweisungen.|  
|208|Rufen Sie die SQL_ROWVER Zeilen identifizierende Spalte der Tabellen ab, indem Sie **SQLSpecialColumns**aufrufen. (Weitere Informationen finden Sie unter Unterstützung für **SQLSpecialColumns** , wobei das *bezeichnertype* -Argument auf SQL_BEST_ROWID als Funktion 20 in der [Kern Schnittstellen Konformität](../../../odbc/reference/develop-app/core-interface-conformance.md)festgelegt ist.)|  
|209|Legen Sie das SQL_ATTR_CONCURRENCY-Anweisungs Attribut auf mindestens einen anderen Wert als SQL_CONCUR_READ_ONLY fest.|  
|210|Die Möglichkeit zum Timeout der Anmelde Anforderung und der SQL-Abfragen (SQL_ATTR_LOGIN_TIMEOUT und SQL_ATTR_QUERY_TIMEOUT).|  
|211|Die Möglichkeit, die Standard Isolationsstufe zu ändern; die Möglichkeit, Transaktionen mit der Isolationsstufe "serialisierbar" auszuführen.|
