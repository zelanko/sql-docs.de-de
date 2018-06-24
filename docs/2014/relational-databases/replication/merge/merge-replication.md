---
title: Mergereplikation | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- merge replication [SQL Server replication], about merge replication
- merge replication [SQL Server replication]
ms.assetid: ff87c368-4c00-4e48-809d-ea752839551e
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6d3dbfcb8cfa2be632f593bece964c67fadcc47a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36050292"
---
# <a name="merge-replication"></a>Mergereplikation
  Die Mergereplikation beginnt in der Regel, wie die Transaktionsreplikation auch, mit einer Momentaufnahme der Veröffentlichungsdatenbankobjekte und -daten. Spätere Daten- und Schemaänderungen, die auf dem Verleger und den Abonnenten vorgenommen werden, werden mit Triggern nachverfolgt. Ist eine Verbindung mit dem Netzwerk vorhanden, nimmt der Abonnent eine Synchronisierung mit dem Verleger vor und tauscht alle Zeilen aus, die sich seit der letzten Synchronisierung auf dem Verleger und dem Abonnenten geändert haben.  
  
 Die Mergereplikation wird typischerweise in Server-und-Client-Umgebungen verwendet. Ihre Verwendung empfiehlt sich in den folgenden Situationen:  
  
-   Mehrere Abonnenten aktualisieren dieselben Daten zu verschiedenen Zeitpunkten und geben diese Änderungen an den Verleger und an andere Abonnenten weiter.  
  
-   Abonnenten müssen Daten empfangen, Änderungen offline vornehmen und Änderungen später mit dem Verleger und anderen Abonnenten synchronisieren.  
  
-   Jeder Abonnent benötigt eine andere Datenpartition.  
  
-   Es kann zu Konflikten kommen, und Sie müssen in der Lage sein, die Konflikte zu erkennen und zu lösen.  
  
-   Die Anwendung muss nicht auf die einzelnen Zwischenstufen von Datenänderungen, sondern nur auf das endgültige Ergebnis der Datenänderung zugreifen können. Wenn sich eine Zeile auf dem Abonnenten z. B. fünfmal ändert, bevor sie mit einem Verleger synchronisiert wird, ändert sich die Zeile auf dem Verleger lediglich einmal und übernimmt so nur die endgültige Änderung (in diesem Fall also den fünften Wert).  
  
 Die Mergereplikation ermöglicht es verschiedenen Standorten, autonom zu arbeiten und die Updates zu einem späteren Zeitpunkt zu einem einzelnen, einheitlichen Ergebnis zusammenzuführen. Da Updates auf mehr als einem Knoten ausgeführt werden, sind dieselben Daten möglicherweise vom Verleger und von mindestens einem Abonnenten aktualisiert worden. Daher kann es beim Zusammenführen von Updates zu Konflikten kommen, für deren Lösung die Mergereplikation aber eine Reihe von Möglichkeiten bietet.  
  
 Die Mergereplikation wird vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Momentaufnahme-Agent und dem Merge-Agent implementiert. Wenn die Veröffentlichung ungefiltert ist oder statische Filter verwendet, erstellt der Momentaufnahme-Agent eine einzelne Momentaufnahme. Wenn die Veröffentlichung parametrisierte Filter verwendet, erstellt der Momentaufnahme-Agent eine Momentaufnahme für jede Datenpartition. Der Merge-Agent weist die Anfangsmomentaufnahmen den Abonnenten zu. Er führt außerdem inkrementelle Datenänderungen zusammen, die beim Verleger oder bei den Abonnenten ausgeführt wurden, nachdem die Anfangsmomentaufnahme erstellt wurde, und erkennt und löst Konflikte entsprechend den von Ihnen konfigurierten Regeln.  
  
 Damit Änderungen nachverfolgt werden können, müssen Mergereplikationen (und Transaktionsreplikationen) mit Abonnements mit verzögertem Update jede Zeile in jeder veröffentlichten Tabelle eindeutig identifizieren können. Bei der Mergereplikation wird jeder Tabelle die `rowguid`-Spalte hinzugefügt, es sei denn, die Tabelle verfügt bereits über eine Spalte vom Datentyp `uniqueidentifier` mit festgelegter `ROWGUIDCOL`-Eigenschaft (in dem Fall wird diese Spalte verwendet). Wenn die Tabelle, aus der Veröffentlichung gelöscht wird der `rowguid` Spalte entfernt; Wenn Sie eine vorhandene Spalte zur nachverfolgung verwendet wurde, wird die Spalte nicht entfernt. Ein Filter muss die von der Replikation verwendete `rowguidcol` nicht einschließen, um Zeilen zu identifizieren. Die `newid()`-Funktion wird als der Standard für die Spalte `rowguid` bereitgestellt, Kunden können jedoch für jede Zeile nach Bedarf einen guid-Wert verwenden. Verwenden Sie jedoch nicht den Wert 00000000-0000-0000-0000-000000000000.  
  
 Im folgenden Diagramm werden die in der Mergereplikation verwendeten Komponenten dargestellt.  
  
 ![Komponenten und Datenfluss der Mergereplikation](../media/merge.gif "Merge replication components and data flow")  
  
  