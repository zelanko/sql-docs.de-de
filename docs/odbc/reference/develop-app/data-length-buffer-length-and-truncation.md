---
title: Daten Länge, Pufferlänge und Abschneiden | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305229"
---
# <a name="data-length-buffer-length-and-truncation"></a>Datenlänge, Pufferlänge und Abschneiden
Die *Daten Länge* entspricht der Byte Länge der Daten, die im Datenpuffer der Anwendung gespeichert werden, und nicht so, wie Sie in der Datenquelle gespeichert werden. Dieser Unterschied ist wichtig, da die Daten häufig in verschiedenen Typen im Datenpuffer gespeichert werden als in der Datenquelle. Bei Daten, die an die Datenquelle gesendet werden, handelt es sich hierbei um die Byte Länge der Daten vor der Konvertierung in den Typ der Datenquelle. Bei Daten, die aus der Datenquelle abgerufen werden, entspricht dies der Byte Länge der Daten nach der Konvertierung in den Typ des Daten Puffers und vor dem Abschneiden.  
  
 Für Daten mit fester Länge, z. b. eine ganze Zahl oder eine Datums Struktur, entspricht die Byte Länge der Daten immer der Größe des Datentyps. Im allgemeinen weisen Anwendungen einen Datenpuffer mit der Größe des Datentyps zu. Wenn die Anwendung einen kleineren Puffer bereitstellt, sind die Folgen nicht definiert, da der Treiber annimmt, dass der Datenpuffer die Größe des Datentyps ist, und die Daten nicht abschneiden, damit Sie in einen kleineren Puffer passen. Wenn die Anwendung einen größeren Puffer zuordnet, wird der zusätzliche Speicherplatz nie verwendet.  
  
 Bei Daten mit variabler Länge, wie z. b. Zeichen-oder Binärdaten, ist es wichtig zu erkennen, dass die Byte Länge der Daten getrennt von und häufig von der Byte Länge des Puffers abweicht. Die Beziehung zwischen diesen beiden Längen wird im Abschnitt " [Puffer](../../../odbc/reference/develop-app/buffers.md) " beschrieben. Wenn die Byte Länge der Daten größer als die Byte Länge des Puffers ist, verkürzt der Treiber die abgerufenen Daten auf die Byte Länge des Puffers und gibt SQL_SUCCESS_WITH_INFO mit SQLSTATE 01004 (abgeschnittene Daten) zurück. Die zurückgegebene Byte Länge entspricht jedoch der Länge der nicht abgeschnittene Daten.  
  
 Nehmen Sie z. b. an, eine Anwendung ordnet 50 Bytes für einen binären Datenpuffer zu. Wenn der Treiber 10 Bytes an Binärdaten zurückgibt, die zurückgegeben werden sollen, werden diese 10 Bytes im Puffer zurückgegeben. Die Byte Länge der Daten ist 10, und die Byte Länge des Puffers beträgt 50. Wenn der Treiber über 60 Bytes an Binärdaten verfügt, die zurückgegeben werden, werden die Daten auf 50 Bytes gekürzt, die Bytes im Puffer zurückgegeben und SQL_SUCCESS_WITH_INFO zurückgegeben. Die Byte Länge der Daten beträgt 60 (die Länge vor dem Abschneiden), und die Byte Länge des Puffers beträgt weiterhin 50.  
  
 Für jede Spalte, die abgeschnitten wird, wird ein Diagnosedaten Satz erstellt. Da es Zeit dauert, bis der Treiber diese Datensätze erstellt und diese von der Anwendung verarbeitet werden kann, kann die Leistung durch Abschneiden beeinträchtigt werden. In der Regel kann eine Anwendung dieses Problem vermeiden, indem Sie ausreichend große Puffer zuordnet, obwohl dies bei der Arbeit mit langen Daten möglicherweise nicht möglich ist. Wenn Daten abgeschnitten werden, kann die Anwendung mitunter einen größeren Puffer zuordnen und die Daten erneut abrufen. Dies gilt nicht für alle Fälle. Wenn beim Abrufen von Daten mit Aufrufen von **SQLGetData**abgeschnitten wird, muss die Anwendung **SQLGetData** nicht für bereits zurückgegebene Daten aufrufen. Weitere Informationen finden Sie unter [erhalten von langen Daten](../../../odbc/reference/develop-app/getting-long-data.md).
