---
title: Datenlänge, Pufferlänge und Abschneiden | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ed2e5ca1fdaba97dde64329c5e8e1b692f43158
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267748"
---
# <a name="data-length-buffer-length-and-truncation"></a>Datenlänge, Pufferlänge und Abschneiden
Die *Datenlänge* ist die Bytelänge der Daten, die in der Anwendung Datenpuffer gespeichert werden sollen, nicht, wie sie in der Datenquelle gespeichert sind. Diese Unterscheidung ist wichtig, da die Daten häufig in verschiedenen im Datenpuffer als in der Datenquelle gespeichert werden. Für Daten, die an die Datenquelle gesendet werden, ist dies also die Bytelänge der Daten vor der Konvertierung in den Typ der Datenquelle. Für die Daten aus der Datenquelle abgerufen wird ist dies die Bytelänge der Daten nach der Konvertierung in den Datenpuffer-Typ, und bevor jedes Abschneiden erfolgt.  
  
 Für Daten mit fester Länge, z. B. eine ganze Zahl oder einen Datumsstruktur ist die Bytelänge der Daten immer die Größe des Datentyps. Im Allgemeinen reservieren Anwendungen einen Datenpuffer mit der Größe des Datentyps. Wenn die Anwendung einen kleineren Puffer zuordnet, sind die folgen nicht definiert, da der Treiber geht davon aus, der Datenpuffer ist die Größe des Datentyps und die Daten für eine kleinere Puffer nicht abschneidet. Wenn die Anwendung auf einen größeren Puffer zuordnet, wird der zusätzliche Speicherplatz wird nie verwendet.  
  
 Für Daten mit variabler Länge, wie z. B. Zeichen- oder Binärdaten darstellen ist es wichtig zu erkennen, dass die Bytelänge der Daten aus separaten und häufig anders, als die Bytelänge des Puffers ist. Die Beziehung zwischen diesen zwei Längen finden Sie auf die [Puffer](../../../odbc/reference/develop-app/buffers.md) Abschnitt. Wenn die Bytelänge der Daten größer als die Bytelänge des Puffers ist, wird der Treiber schneidet die abgerufenen Daten auf die Bytelänge des Puffers ab und gibt SQL_SUCCESS_WITH_INFO mit SQLSTATE 01004 (Daten wurden abgeschnitten) zurück. Die zurückgegebene Byte-Länge ist jedoch die Länge der Daten den ungekürzten.  
  
 Nehmen wir beispielsweise an, dass eine Anwendung 50 Bytes für einen Binärdaten-Puffer weist. Wenn der Treiber 10 Bytes aus Binärdaten zurückgegeben hat, gibt diese 10 Bytes im Puffer zurück. Die Bytelänge der Daten ist 10, und die Länge in Byte des Puffers ist 50. Wenn der Treiber 60 Bytes aus Binärdaten zurückgegeben hat, schneidet die Daten auf 50 Bytes, gibt die Bytes im Puffer zurück und gibt SQL_SUCCESS_WITH_INFO zurück. Die Bytelänge der Daten ist 60 (die Länge vor der Kürzung), und die Länge des Puffers in Byte ist weiterhin 50.  
  
 Für jede Spalte, die abgeschnitten wird, wird ein Diagnosedatensatz erstellt. Da es Zeit für den Treiber, um diese Datensätze zu erstellen und für die Anwendung für die Verarbeitung dauert, kann Abschneiden Leistung beeinträchtigt werden. In der Regel eine Anwendung dieses Problem vermeiden, Reservierung von Puffern groß genug ist, obwohl dies nicht möglich möglicherweise bei der Arbeit mit langen Daten. Wenn Daten abgeschnitten, kann die Anwendung manchmal einen größeren Puffer reservieren und untergeordnete Daten; Dies gilt nicht in allen Fällen. Wenn eine Kürzung auftritt, beim Abrufen von Daten mit Aufrufen von **SQLGetData**, rufen Sie die Anwendung muss nicht **SQLGetData** für Daten, die bereits zurückgegeben wurde; Weitere Informationen finden Sie unter [erste Long-Daten](../../../odbc/reference/develop-app/getting-long-data.md).
