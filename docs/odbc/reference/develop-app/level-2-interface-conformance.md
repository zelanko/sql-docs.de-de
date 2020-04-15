---
title: Level 2-Schnittstellenkonformität | Microsoft Docs
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
ms.openlocfilehash: 3ee57d716cbb93f855e1fd78d41bff62a681eb6c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306162"
---
# <a name="level-2-interface-conformance"></a>Schnittstellenübereinstimmung auf Ebene 2
Die Level 2-Schnittstellenkonformitätsstufe umfasst die Funktionalität der Level 1-Schnittstelle und die folgenden Funktionen:  
  
|||  
|-|-|  
|201|Verwenden Sie dreiteilige Namen von Datenbanktabellen und -ansichten. (Weitere Informationen finden Sie in der zweiteiligen Benennungsunterstützungsfunktion 101 in [Level 1 Interface Conformance](../../../odbc/reference/develop-app/level-1-interface-conformance.md).)|  
|202|Beschreiben Sie dynamische Parameter, indem Sie **SQLDescribeParam**aufrufen.|  
|203|Verwenden Sie nicht nur Eingabeparameter, sondern auch Ausgabe- und Eingabe-/Ausgabeparameter sowie Ergebniswerte gespeicherter Prozeduren.|  
|204|Verwenden Sie Lesezeichen, einschließlich des Abrufens von Lesezeichen, indem Sie **SQLDescribeCol** und **SQLColAttribute** unter Spaltennummer 0 aufrufen. Abrufen basierend auf einer Textmarke, indem **SQLFetchScroll** mit dem *FetchOrientation-Argument* aufgerufen wird, das auf SQL_FETCH_BOOKMARK festgelegt ist. und aktualisieren, löschen und abrufen nach Lesezeichenvorgängen, indem **SQLBulkOperations** aufgerufen wird, wobei das *Argument Operation* auf SQL_UPDATE_BY_BOOKMARK, SQL_DELETE_BY_BOOKMARK oder SQL_FETCH_BY_BOOKMARK festgelegt ist.|  
|205|Rufen Sie erweiterte Informationen zum Datenwörterbuch ab, indem Sie **SQLColumnPrivileges**, **SQLForeignKeys**und **SQLTablePrivileges**aufrufen.|  
|206|Verwenden Sie ODBC-Funktionen anstelle von SQL-Anweisungen, um zusätzliche Datenbankvorgänge auszuführen, indem Sie **SQLBulkOperations** mit SQL_ADD oder **SQLSetPos** mit SQL_DELETE oder SQL_UPDATE aufrufen. (Unterstützung für Aufrufe von **SQLSetPos** mit dem *LockType-Argument,* das auf SQL_LOCK_EXCLUSIVE oder SQL_LOCK_UNLOCK festgelegt ist, ist kein Teil der Konformitätsebenen, sondern ein optionales Feature.)|  
|207|Aktivieren Sie die asynchrone Ausführung von ODBC-Funktionen für bestimmte Einzelanweisungen.|  
|208|Rufen Sie die SQL_ROWVER Zeilenidentifizierende Spalte von Tabellen ab, indem Sie **SQLSpecialColumns**aufrufen. (Weitere Informationen finden Sie in der Unterstützung für **SQLSpecialColumns** mit dem *Argument IdentifierType,* das auf SQL_BEST_ROWID als Feature 20 in [Core Interface Conformance](../../../odbc/reference/develop-app/core-interface-conformance.md)festgelegt ist.)|  
|209|Legen Sie das SQL_ATTR_CONCURRENCY Anweisungsattribut auf mindestens einen anderen Wert als SQL_CONCUR_READ_ONLY fest.|  
|210|Die Möglichkeit, Anmeldeanforderungen und SQL-Abfragen (SQL_ATTR_LOGIN_TIMEOUT und SQL_ATTR_QUERY_TIMEOUT) zu zeitende Zeit zu erfolgende.|  
|211|Die Möglichkeit, die Standardisolationsstufe zu ändern; die Möglichkeit, Transaktionen mit der "serialisierbaren" Isolationsstufe auszuführen.|
