---
title: Datenlänge, Pufferlänge und Abschneiden | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data buffers [ODBC], length
- data length [ODBC]
- truncating data [ODBC]
- length of data buffers [ODBC]
- buffers [ODBC], length
ms.assetid: 2825c6e7-b9ff-42fe-84fc-7fb39728ac5d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2e7b8d1e60cd83594509c2ab5cbc24e04546eca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305229"
---
# <a name="data-length-buffer-length-and-truncation"></a>Datenlänge, Pufferlänge und Abschneiden
Die *Datenlänge* ist die Bytelänge der Daten, die im Datenpuffer der Anwendung gespeichert werden würde, nicht wie sie in der Datenquelle gespeichert werden. Diese Unterscheidung ist wichtig, da die Daten häufig in verschiedenen Typen im Datenpuffer als in der Datenquelle gespeichert werden. Für Daten, die an die Datenquelle gesendet werden, ist dies die Bytelänge der Daten vor der Konvertierung in den Typ der Datenquelle. Bei Daten, die aus der Datenquelle abgerufen werden, ist dies die Bytelänge der Daten nach der Konvertierung in den Datenpuffertyp und bevor eine Kürzung durchgeführt wird.  
  
 Bei Daten fester Länge, z. B. einer ganzzahligen oder einer Datumsstruktur, ist die Bytelänge der Daten immer die Größe des Datentyps. Im Allgemeinen weisen Anwendungen einen Datenpuffer zu, der die Größe des Datentyps hat. Wenn die Anwendung einen kleineren Puffer zuweist, sind die Folgen nicht definiert, da der Treiber davon ausgeht, dass der Datenpuffer die Größe des Datentyps hat, und die Daten nicht abgeschnitten werden, um in einen kleineren Puffer zu passen. Wenn die Anwendung einen größeren Puffer zuweist, wird der zusätzliche Speicherplatz nie verwendet.  
  
 Bei Daten variabler Länge, z. B. Zeichen- oder Binärdaten, ist es wichtig zu erkennen, dass die Bytelänge der Daten von der Bytelänge des Puffers getrennt und oft von der Bytelänge abweicht. Die Beziehung dieser beiden Längen wird im Abschnitt [Puffer](../../../odbc/reference/develop-app/buffers.md) beschrieben. Wenn die Bytelänge der Daten größer als die Bytelänge des Puffers ist, kürt der Treiber abgerufene Daten auf die Bytelänge des Puffers und gibt SQL_SUCCESS_WITH_INFO mit SQLSTATE 01004 zurück (Daten abgeschnitten). Die zurückgegebene Bytelänge ist jedoch die Länge der nicht abgeschnittenen Daten.  
  
 Angenommen, eine Anwendung weist 50 Bytes für einen binären Datenpuffer zu. Wenn der Treiber 10 Byte binärer Daten zurückgeben muss, gibt er diese 10 Bytes im Puffer zurück. Die Bytelänge der Daten ist 10, und die Bytelänge des Puffers ist 50. Wenn der Treiber 60 Byte binärer Daten zurückgeben muss, werden die Daten auf 50 Byte abgeschnitten, diese Bytes im Puffer zurückgegeben und SQL_SUCCESS_WITH_INFO zurückgegeben. Die Bytelänge der Daten beträgt 60 (die Länge vor dem Abschneideen), und die Bytelänge des Puffers ist immer noch 50.  
  
 Für jede Spalte, die abgeschnitten wird, wird ein Diagnosedatensatz erstellt. Da es einige Zeit dauert, bis der Treiber diese Datensätze erstellt und die Anwendung sie verarbeitet, kann das Abschneiden die Leistung beeinträchtigen. Normalerweise kann eine Anwendung dieses Problem vermeiden, indem sie ausreichend große Puffer zuweist, obwohl dies bei der Arbeit mit langen Daten möglicherweise nicht möglich ist. Wenn Daten abgeschnitten werden, kann die Anwendung manchmal einen größeren Puffer zuweisen und die Daten erneut abrufen. dies gilt nicht in allen Fällen. Wenn beim Abrufen von Daten mit Aufrufen von **SQLGetData**eine Herabsschneidung auftritt, muss die Anwendung **SQLGetData** nicht für Daten aufrufen, die bereits zurückgegeben wurden. Weitere Informationen finden Sie unter [Abrufen langer Daten](../../../odbc/reference/develop-app/getting-long-data.md).
