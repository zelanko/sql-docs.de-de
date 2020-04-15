---
title: Schnittstellenkonformität der Stufe 1 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interface conformance levels [ODBC]
- conformance levels [ODBC], interface
- level 1 interface conformance levels [ODBC]
ms.assetid: ee3f5c08-0583-4f3b-8354-ef71b6086a7e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d31d5fe8aea1df4e7937104580efb820ba6f031
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306181"
---
# <a name="level-1-interface-conformance"></a>Schnittstellenübereinstimmung auf Ebene 1
Die Level 1-Schnittstellenkonformitätsstufe umfasst die Core-Schnittstellenkonformitätsfunktionalität sowie zusätzliche Funktionen, z. B. Transaktionen, die normalerweise in einem relationalen OLTP-DBMS verfügbar sind. Ein Schnittstellenkonformer Treiber der Ebene 1 ermöglicht der Anwendung neben den Funktionen in der Core-Schnittstellenkonformitätsebene Folgendes:  
  
|||  
|-|-|  
|101|Geben Sie das Schema von Datenbanktabellen und Ansichten (mit zweiteiliger Benennung) an. (Weitere Informationen finden Sie in der dreiteiligen Benennungsfunktion 201 in [Level 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|102|Ruft die echte asynchrone Ausführung von ODBC-Funktionen auf, wobei die entsprechenden ODBC-Funktionen alle synchron oder alle asynchron enden für eine bestimmte Verbindung sind.|  
|103|Verwenden Sie scrollbare Cursor, und erzielen Sie dadurch Zugriff auf ein Resultset in anderen Methoden als nur Vorwärtsmethoden, indem Sie **SQLFetchScroll** mit dem anderen *Argument FetchOrientation* als SQL_FETCH_NEXT aufrufen. (Die SQL_FETCH_BOOKMARK *FetchOrientation* befindet sich in Feature 204 in [Level 2 Interface Conformance](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|104|Abrufen von Primärschlüsseln von Tabellen durch Aufrufen von **SQLPrimaryKeys**.|  
|105|Verwenden Sie gespeicherte Prozeduren über die ODBC-Escapesequenz für Prozeduraufrufe, und fragen Sie das Datenwörterbuch zu gespeicherten Prozeduren ab, indem Sie **SQLProcedureColumns** und **SQLProcedures**aufrufen. (Der Prozess, mit dem Prozeduren erstellt und in der Datenquelle gespeichert werden, liegt außerhalb des Rahmens dieses Dokuments.)|  
|106|Stellen Sie eine Verbindung zu einer Datenquelle her, indem Sie die verfügbaren Server interaktiv durchsuchen, indem Sie **SQLBrowseConnect**aufrufen.|  
|107|Verwenden Sie ODBC-Funktionen anstelle von SQL-Anweisungen, um bestimmte Datenbankvorgänge auszuführen: **SQLSetPos** mit SQL_POSITION und SQL_REFRESH.|  
|108|Erhalten Sie Zugriff auf den Inhalt mehrerer Resultsets, die von Batches und gespeicherten Prozeduren generiert werden, indem Sie **SQLMoreResults**aufrufen.|  
|109|Begrenzen Sie Transaktionen, die mehrere ODBC-Funktionen umfassen, mit echter Atomität und der Möglichkeit, SQL_ROLLBACK in **SQLEndTran**anzugeben.|
