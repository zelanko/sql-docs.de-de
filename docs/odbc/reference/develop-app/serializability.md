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
manager: craigg
ms.openlocfilehash: 7e7972fb72607edca8c1599c2d028b073c184642
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63251470"
---
# <a name="serializability"></a>Serialisierbarkeit
Idealerweise sollten Transaktionen sein *serialisierbar*. Transaktionen werden als serialisierbar, wenn die Ergebnisse der Transaktionen gleichzeitig ausgeführt werden wie die Ergebnisse der Ausführung dieser seriell - identisch sind, also eine nach der anderen. Es ist nicht wichtig, welcher Transaktion zuerst ausgeführt wird, die das Ergebnis Mischung der Transaktionen nicht widerspiegelt.  
  
 Nehmen wir beispielsweise an die Transaktion A Datenwerte multipliziert diesen mit 2 und Transaktion B 1 auf Datenwerte hinzugefügt. Nehmen wir nun an, dass zwei Datenwerte vorhanden sind: 0 und 10. Wenn diese Transaktionen nacheinander ausgeführt werden, werden die neuen Werte 1 und 21, wenn die Transaktion A zuerst ausgeführt wird, oder 2 und 22 sein, wenn die Transaktion B zuerst ausgeführt wird. Aber was geschieht, wenn die Reihenfolge, in der die beiden Transaktionen ausgeführt werden, für jeden Wert unterscheidet? Wenn die Transaktion, die eine erste auf dem ersten Wert ausgeführt wird und die Transaktion B zuerst auf dem zweiten Wert ausgeführt werden, werden die neuen Werte 1 und 22. Wenn Sie diese Reihenfolge umgekehrt ist, werden die neuen Werte 2 und 21. Die Transaktionen serialisierbar sind, wenn 1, 21 und 2 sind 22 die einzig mögliche Ergebnisse. Die Transaktionen sind, ist nicht serialisierbar, wenn 1, 22 oder 2, 21 ein mögliches Ergebnis.  
  
 Was ist also Serialisierbarkeit sinnvoll? Das heißt, warum es wichtig ist, dass sie eine Transaktion angezeigt abgeschlossen ist, bevor die nächste Transaktion gestartet wird? Nehmen Sie das folgende Problem. Ein Vertriebsmitarbeiter wird Aufträge zur gleichen Zeit eingeben, die eine sachbearbeiterin, Rechnungen gesendet werden. Nehmen Sie an den Verkäufer gibt eine Bestellung von Company-X, aber keinen commit; der Verkäufer ist immer noch kommuniziert mit der Vertreter von Company-X. Die clerkgröße fordert eine Liste aller offenen Bestellungen und ermittelt die Reihenfolge für Company-X und sendet sie eine Rechnung. Nachdem die Vertreter des Unternehmens X entscheidet sich, dass die Reihenfolge geändert, damit die Vertriebsmitarbeiter vor dem Commit der Transaktion geändert werden soll. Unternehmens X Ruft eine falsche Rechnung ab.  
  
 Wenn die des Verkäufers und des Sachbearbeiters Transaktionen serialisierbar sind, würde dieses Problem nie aufgetreten. Des Verkäufers Transaktion würde abgeschlossen haben, bevor die Clerks in der Transaktion wird gestartet, in diesem Fall der Clerk haben, die richtige Abrechnung gesendet würde, oder den Clerk die Transaktion wird abgeschlossen haben, bevor des Verkäufers Transaktion gestartet werden, in diesem Fall die Clerk würde keine Rechnung an Unternehmen X überhaupt gesendet haben.
