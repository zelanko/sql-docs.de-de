---
title: Serialisierbarkeit | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0557e011578d313765614c05a2a9cf1b975bbc08
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304161"
---
# <a name="serializability"></a>Serialisierbarkeit
Im Idealfall sollten Transaktionen *serialisierbar*sein. Transaktionen werden als serialisierbar bezeichnet, wenn die Ergebnisse der gleichzeitig endenden Transaktionen mit den Ergebnissen ihrer serialen Ausführung identisch sind - d. h. einer nach dem anderen. Es ist nicht wichtig, welche Transaktion zuerst ausgeführt wird, nur dass das Ergebnis keine Vermischung der Transaktionen widerspiegelt.  
  
 Angenommen, Transaktion A multipliziert Datenwerte mit 2, und Transaktion B fügt 1 zu Datenwerten hinzu. Angenommen, es gibt zwei Datenwerte: 0 und 10. Wenn diese Transaktionen nacheinander ausgeführt werden, sind die neuen Werte 1 und 21, wenn Transaktion A zuerst ausgeführt wird, oder 2 und 22, wenn Transaktion B zuerst ausgeführt wird. Was ist jedoch, wenn die Reihenfolge, in der die beiden Transaktionen ausgeführt werden, für jeden Wert unterschiedlich ist? Wenn Transaktion A zuerst auf dem ersten Wert ausgeführt wird und Transaktion B zuerst auf dem zweiten Wert ausgeführt wird, sind die neuen Werte 1 und 22. Wenn diese Reihenfolge umgekehrt wird, sind die neuen Werte 2 und 21. Die Transaktionen sind serialisierbar, wenn 1, 21 und 2, 22 die einzig möglichen Ergebnisse sind. Die Transaktionen sind nicht serialisierbar, wenn 1, 22 oder 2, 21 ein mögliches Ergebnis ist.  
  
 Warum ist Serialisierbarkeit wünschenswert? Mit anderen Worten, warum ist es wichtig, dass es scheint, dass eine Transaktion beendet wird, bevor die nächste Transaktion beginnt? Berücksichtigen Sie das folgende Problem. Ein Verkäufer gibt Aufträge ein, während ein Sachbearbeiter Rechnungen aussendet. Angenommen, der Verkäufer gibt einen Auftrag von Unternehmen X ein, übernimmt ihn jedoch nicht. der Verkäufer spricht noch mit dem Vertreter von Unternehmen X. Der Sachbearbeiter fordert eine Liste aller offenen Aufträge an und entdeckt die Bestellung für Unternehmen X und sendet ihnen eine Rechnung. Nun entscheidet der Vertreter von Unternehmen X, dass er seine Bestellung ändern möchte, sodass der Verkäufer ihn ändert, bevor er die Transaktion übergibt. Unternehmen X erhält eine falsche Rechnung.  
  
 Wären die Transaktionen des Verkäufers und des Sachbearbeiters serialisierbar gewesen, wäre dieses Problem nie aufgetreten. Entweder wäre die Transaktion des Verkäufers vor Dem Start der Transaktion des Sachbearbeiters abgeschlossen worden, in diesem Fall hätte der Sachbearbeiter die korrekte Rechnung gesendet, oder die Transaktion des Sachbearbeiters wäre vor Dem Start der Transaktion des Verkäufers abgeschlossen worden, in diesem Fall hätte der Sachbearbeiter überhaupt keine Rechnung an Unternehmen X geschickt.
