---
title: Gleichzeitigkeitssteuerung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], concurrency control
- concurrency control [ODBC]
ms.assetid: 75e4adb3-3d43-49c5-8c5e-8df96310d912
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8afba3b3b8c8fee1307473c790186d509b37d982
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81294850"
---
# <a name="concurrency-control"></a>Gleichzeitigkeitssteuerung
*Parallelität* ist die Fähigkeit von zwei Transaktionen, dieselben Daten gleichzeitig zu verwenden, und mit erhöhter Transaktionsisolation kommt in der Regel reduzierte Parallelität. Dies liegt daran, dass die Transaktionsisolation in der Regel durch Sperren von Zeilen implementiert wird und wenn mehr Zeilen gesperrt sind, können weniger Transaktionen abgeschlossen werden, ohne dass sie zumindest vorübergehend von einer gesperrten Zeile blockiert werden. Reduzierte Parallelität wird im Allgemeinen als Kompromiss für die höheren Transaktionsisolationsstufen akzeptiert, die zur Aufrechterhaltung der Datenbankintegrität erforderlich sind, aber sie kann zu einem Problem in interaktiven Anwendungen mit hoher Lese-/Schreibaktivität werden, die Cursor verwenden.  
  
 Angenommen, eine Anwendung führt die SQL-Anweisung **SELECT \* FROM Orders**aus. Es ruft **SQLFetchScroll** auf, um das Resultset zu scrollen, und ermöglicht es dem Benutzer, Aufträge zu aktualisieren, zu löschen oder einzufügen. Nachdem der Benutzer die Transaktion aktualisiert, gelöscht oder eingefügt hat, überträgt die Anwendung die Transaktion.  
  
 Wenn die Isolationsstufe wiederholbar gelesen werden kann, kann die Transaktion - je nachdem, wie sie implementiert wird - jede zeile sperren, die von **SQLFetchScroll**zurückgegeben wird. Wenn die Isolationsstufe Serialisierbar ist, kann die Transaktion die gesamte Tabelle "Orders" sperren. In beiden Fällen gibt die Transaktion ihre Sperren nur frei, wenn sie festgeschrieben oder zurückgesetzt wird. Wenn der Benutzer also viel Zeit mit dem Lesen von Aufträgen und sehr wenig Zeit mit dem Aktualisieren, Löschen oder Einfügen verbringt, kann die Transaktion eine große Anzahl von Zeilen problemlos sperren, sodass sie für andere Benutzer nicht verfügbar sind.  
  
 Dies ist ein Problem, auch wenn der Cursor schreibgeschützt ist und die Anwendung dem Benutzer erlaubt, nur vorhandene Aufträge zu lesen. In diesem Fall überträgt die Anwendung die Transaktion und gibt Sperren frei, wenn sie **SQLCloseCursor** (im Auto-Commit-Modus) oder **SQLEndTran** (im manuellen Commit-Modus) aufruft.  
  
 In diesem Abschnitt werden die folgenden Themen behandelt:  
  
-   [Parallelitätstypen](../../../odbc/reference/develop-app/concurrency-types.md)  
  
-   [Optimistische Nebenläufigkeit](../../../odbc/reference/develop-app/optimistic-concurrency.md)
