---
title: Serialisierbarkeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transaction isolation [ODBC]
- transactions [ODBC], serialization
- serialization [ODBC]
- transactions [ODBC], isolation
ms.assetid: 142e4ac0-2977-4a2b-96ae-c9e5bd2c448a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 49552e7333d8cac2b55a9ae6e8dd7a41ff4c5955
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094332"
---
# <a name="serializability"></a>Serialisierbarkeit
Im Idealfall sollten Transaktionen *serialisierbar*sein. Transaktionen werden als serialisierbar bezeichnet, wenn die Ergebnisse der gleichzeitigen Ausführung von Transaktionen mit den Ergebnissen der seriell Ausführung übereinstimmen, d. h. nacheinander. Es ist nicht wichtig, welche Transaktion zuerst ausgeführt wird, sondern nur, dass das Ergebnis keine Vermischung der Transaktionen widerspiegelt.  
  
 Nehmen Sie beispielsweise an, Transaktion A multipliziert Datenwerte mit 2, und Transaktion B fügt 1 zu Datenwerten hinzu. Nehmen wir nun an, dass zwei Datenwerte vorhanden sind: 0 und 10. Wenn diese Transaktionen nacheinander ausgeführt werden, lauten die neuen Werte 1 und 21, wenn Transaktion A zuerst ausgeführt wird, oder 2 und 22, wenn Transaktion B zuerst ausgeführt wird. Aber was geschieht, wenn die Reihenfolge, in der die beiden Transaktionen ausgeführt werden, für jeden Wert anders ist? Wenn Transaktion A zuerst auf dem ersten Wert ausgeführt wird und Transaktion B zuerst für den zweiten Wert ausgeführt wird, lauten die neuen Werte 1 und 22. Wenn diese Reihenfolge umgekehrt wird, sind die neuen Werte 2 und 21. Die Transaktionen sind serialisierbar, wenn 1, 21 und 2, 22 die einzigen möglichen Ergebnisse sind. Die Transaktionen sind nicht serialisierbar, wenn 1, 22 oder 2, 21 ein mögliches Ergebnis ist.  
  
 Warum ist die Serialisierbarkeit wünschenswert? Anders ausgedrückt: Warum ist es wichtig, dass eine Transaktion abgeschlossen ist, bevor die nächste Transaktion startet? Beachten Sie das folgende Problem. Ein Verkäufer wechselt zum selben Zeitpunkt, an dem ein Clerk Rechnungen sendet. Angenommen, der Verkäufer gibt eine Bestellung von Unternehmen X ein, führt aber keinen Commit für ihn aus. der Verkäufer spricht immer noch mit dem Vertreter des Unternehmens X. Der Clerk fordert eine Liste aller offenen Bestellungen an und ermittelt die Bestellung für das Unternehmen X und sendet Ihnen eine Rechnung. Der Vertreter des Unternehmens X entscheidet nun, dass er seine Bestellung ändern möchte, damit der Verkäufer ihn vor dem Commit der Transaktion ändert. Unternehmen X erhält eine falsche Rechnung.  
  
 Wenn die Transaktionen des Verkäufers und des Clerk serialisierbar waren, wäre dieses Problem nie aufgetreten. Entweder wurde die Transaktion des Verkäufers abgeschlossen, bevor die Transaktion des Clerk gestartet wurde. in diesem Fall hätte der Clerk die richtige Rechnung gesendet, oder die Transaktion des Clerks hätte abgeschlossen, bevor die Transaktion des Verkäufers gestartet wird. in diesem Fall ist der Clerk hätte keine Rechnung an Unternehmen X gesendet.
