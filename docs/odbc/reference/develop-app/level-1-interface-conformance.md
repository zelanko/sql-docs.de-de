---
title: Schnittstellen Konformität der Ebene 1 | Microsoft-Dokumentation
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
ms.openlocfilehash: 29f59cf06eac1ce0f6589ad9c7cba8491e8383b5
ms.sourcegitcommit: 99f61724de5edf6640efd99916d464172eb23f92
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87363424"
---
# <a name="level-1-interface-conformance"></a>Schnittstellenübereinstimmung auf Ebene 1
Die Schnittstelle für die Schnittstellen Konformität der Ebene 1 umfasst die grundlegende Funktionalität der Schnittstellen Konformität sowie zusätzliche Funktionen, wie z. b. Transaktionen, die normalerweise in einem relationalen OLTP-DBMS verfügbar sind. Mithilfe eines Schnittstellen kompatiblen Treibers der Ebene 1 kann die Anwendung zusätzlich zu den Features im Übereinstimmungs Grad der Kernschnittstelle folgende Aktionen ausführen:  
  
|Funktions Nummer|BESCHREIBUNG|  
|-|-|  
|101|Geben Sie das Schema von Datenbanktabellen und-Sichten an (mit zweit Eider Benennung). (Weitere Informationen finden Sie unter die dreiteilige Benennungs Funktion 201 in der [Schnittstellen Konformität der Ebene 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|102|Rufen Sie die tatsächliche asynchrone Ausführung von ODBC-Funktionen auf, bei denen anwendbare ODBC-Funktionen alle synchron oder alle asynchron für eine bestimmte Verbindung sind.|  
|103|Verwenden Sie Bild lauffähigen Cursor, und erreichen Sie somit den Zugriff auf ein Resultset in anderen Methoden als vorwärts, indem Sie **SQLFetchScroll** mit dem *FetchOrientation* -Argument außer SQL_FETCH_NEXT aufrufen. (Der SQL_FETCH_BOOKMARK *FetchOrientation* ist in der Funktion 204 in der [Schnittstellen Konformität der Ebene 2](../../../odbc/reference/develop-app/level-2-interface-conformance.md).)|  
|104|Abrufen von primär Schlüsseln von Tabellen durch Aufrufen von **SQLPrimaryKeys**.|  
|105|Verwenden Sie gespeicherte Prozeduren über die ODBC-Escapesequenz für Prozedur Aufrufe, und Fragen Sie das Datenwörterbuch nach gespeicherten Prozeduren ab, indem Sie **sqlprocedurecolumschlag** und **SQLProcedures**aufrufen. (Der Prozess, mit dem Prozeduren erstellt und in der Datenquelle gespeichert werden, liegt außerhalb des Umfangs dieses Dokuments.)|  
|106|Stellen Sie eine Verbindung mit einer Datenquelle her, indem Sie die verfügbaren Server durch Aufrufen von **sqlbrowseconnetct**interaktiv durchsuchen.|  
|107|Verwenden Sie ODBC-Funktionen anstelle von SQL-Anweisungen, um bestimmte Daten Bank Vorgänge auszuführen: **SQLSetPos** mit SQL_POSITION und SQL_REFRESH.|  
|108|Durch Aufrufen von **SQLMoreResults**erhalten Sie Zugriff auf den Inhalt mehrerer Resultsets, die durch Batches und gespeicherte Prozeduren generiert werden.|  
|109|Begrenzen von Transaktionen, die mehrere ODBC-Funktionen umfassen, mit echter Atomizität und der Möglichkeit, SQL_ROLLBACK in **SQLEndTran**anzugeben.|
