---
title: Transaktionsisolationsstufen (ODBC) | Microsoft Docs
ms.custom: seo-dt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- dirty reads [ODBC]
- isolation levels [ODBC]
- nonrepeatable reads [ODBC]
- read uncommitted [ODBC]
- read committed [ODBC]
- serializable reads [ODBC]
- phantoms [ODBC]
- transaction isolation [ODBC]
- repeatable reads [ODBC]
- transactions [ODBC], isolation
ms.assetid: 0d638d55-ffd0-48fb-834b-406f466214d4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 622b4cd7f0db259b5ecfd5be63b27df64be965e7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298033"
---
# <a name="transaction-isolation-levels-odbc"></a>Transaktionsisolationsstufen (ODBC)
*Transaktionsisolationsebenen* sind ein Maß für das Ausmaß, in dem die Transaktionsisolation erfolgreich ist. Insbesondere werden Transaktionsisolationsstufen durch das Vorhandensein oder Fehlen der folgenden Phänomene definiert:  
  
-   **Dirty Reads** Ein *schmutziger Lesevorgang* tritt auf, wenn eine Transaktion Daten liest, die noch nicht festgeschrieben wurden. Angenommen, Transaktion 1 aktualisiert eine Zeile. Transaktion 2 liest die aktualisierte Zeile, bevor Transaktion 1 die Aktualisierung überträgt. Wenn Transaktion 1 die Änderung zurücksetzt, enthält Transaktion 2 Lesedaten, die als nie vorhanden gelten.  
  
-   **Nicht wiederholbare Lesevorgänge** Ein *nicht wiederholbarer Lesevorgang* tritt auf, wenn eine Transaktion dieselbe Zeile zweimal liest, aber jedes Mal unterschiedliche Daten erhält. Angenommen, Transaktion 1 liest eine Zeile. Transaktion 2 aktualisiert oder löscht diese Zeile und überträgt die Aktualisierung oder das Löschen. Wenn Transaktion 1 die Zeile erneut liest, ruft sie unterschiedliche Zeilenwerte ab oder stellt fest, dass die Zeile gelöscht wurde.  
  
-   **Phantoms** Ein *Phantom* ist eine Zeile, die den Suchkriterien entspricht, aber zunächst nicht angezeigt wird. Angenommen, Transaktion 1 liest eine Reihe von Zeilen, die einige Suchkriterien erfüllen. Transaktion 2 generiert eine neue Zeile (entweder durch eine Aktualisierung oder eine Einfügung), die den Suchkriterien für Transaktion 1 entspricht. Wenn Transaktion 1 die Anweisung, die die Zeilen liest, erneut ausführt, ruft sie einen anderen Satz von Zeilen ab.  
  
 Die vier Transaktionsisolationsstufen (wie in SQL-92 definiert) werden in Bezug auf diese Phänomene definiert. In der folgenden Tabelle kennzeichnet ein "X" jedes Phänomen, das auftreten kann.  
  
|Transaktionsisolationsstufe|Schmutzige Lesevorgänge|Nicht wiederholbare Lesevorgänge|Phantome|  
|---------------------------------|-----------------|-------------------------|--------------|  
|Read Uncommitted|X|X|X|  
|Read Committed|--|X|X|  
|Repeatable Read|--|--|X|  
|Serialisierbar|--|--|--|  
  
 In der folgenden Tabelle werden einfache Möglichkeiten beschrieben, wie ein DBMS die Transaktionsisolationsstufen implementieren kann.  
  
> [!IMPORTANT]  
>  Die meisten DBMS verwenden komplexere Schemata als diese, um die Parallelität zu erhöhen. Diese Beispiele dienen nur zur Veranschaulichung. Insbesondere schreibt ODBC nicht vor, wie bestimmte DBMS Transaktionen voneinander isolieren.  
  
|Transaktionsisolation|Mögliche Umsetzung|  
|---------------------------|-----------------------------|  
|Read Uncommitted|Transaktionen sind nicht voneinander isoliert. Wenn das DBMS andere Transaktionsisolationsebenen unterstützt, ignoriert es den Mechanismus, den es zum Implementieren dieser Ebenen verwendet. Damit sie sich nicht negativ auf andere Transaktionen auswirken, sind Transaktionen, die auf der Ebene "Nicht festschreiben lesen" ausgeführt werden, in der Regel schreibgeschützt.|  
|Read Committed|Die Transaktion wartet, bis Zeilen, die von anderen Transaktionen gesperrt sind, entsperrt sind. Dadurch wird verhindert, dass "schmutzige" Daten gelesen werden.<br /><br /> Die Transaktion enthält eine Lesesperre (wenn sie nur die Zeile liest) oder schreibsperre (wenn sie die Zeile aktualisiert oder löscht) in der aktuellen Zeile, um zu verhindern, dass andere Transaktionen sie aktualisieren oder löschen. Die Transaktion gibt Lesesperren frei, wenn sie sich aus der aktuellen Zeile entfernt. Es hält Schreibsperren, bis es festgeschrieben oder zurückgesetzt wird.|  
|Repeatable Read|Die Transaktion wartet, bis Zeilen, die von anderen Transaktionen gesperrt sind, entsperrt sind. Dadurch wird verhindert, dass "schmutzige" Daten gelesen werden.<br /><br /> Die Transaktion enthält Lesesperren für alle Zeilen, die sie an die Anwendung zurückgibt, und Schreibsperren für alle Zeilen, die sie einfügt, aktualisiert oder löscht. Wenn die Transaktion beispielsweise die SQL-Anweisung **SELECT \* FROM Orders**enthält, sperrt die Transaktion Zeilen, während die Anwendung sie abruft. Wenn die Transaktion die SQL-Anweisung **DELETE FROM Orders WHERE Status = 'CLOSED'** enthält, sperrt die Transaktion Zeilen, während sie sie löscht.<br /><br /> Da andere Transaktionen diese Zeilen nicht aktualisieren oder löschen können, vermeidet die aktuelle Transaktion nicht wiederholbare Lesevorgänge. Die Transaktion gibt ihre Sperren frei, wenn sie festgeschrieben oder zurückgesetzt wird.|  
|Serialisierbar|Die Transaktion wartet, bis Zeilen, die von anderen Transaktionen gesperrt sind, entsperrt sind. Dadurch wird verhindert, dass "schmutzige" Daten gelesen werden.<br /><br /> Die Transaktion enthält eine Lesesperre (wenn sie nur Zeilen liest) oder Schreibsperre (wenn sie Zeilen aktualisieren oder löschen kann) für den Bereich der Zeilen, auf die sie sich auswirkt. Wenn die Transaktion z. B. die SQL-Anweisung **SELECT \* FROM Orders**enthält, ist der Bereich die gesamte Tabelle "Orders". Die Transaktion sperrt die Tabelle und lässt keine neuen Zeilen in die Tabelle ein. Wenn die Transaktion die SQL-Anweisung **DELETE FROM Orders WHERE Status = 'CLOSED'** enthält, ist der Bereich alle Zeilen mit dem Status "GESCHLOSSEN"; Die Transaktion schreibsperrt alle Zeilen in der Tabelle Orders mit dem Status "GESCHLOSSEN" und lässt nicht zu, dass Zeilen eingefügt oder aktualisiert werden, sodass die resultierende Zeile den Status "GESCHLOSSEN" hat.<br /><br /> Da andere Transaktionen die Zeilen im Bereich nicht aktualisieren oder löschen können, vermeidet die aktuelle Transaktion nicht wiederholbare Lesevorgänge. Da andere Transaktionen keine Zeilen in den Bereich einfügen können, vermeidet die aktuelle Transaktion Phantome. Die Transaktion löst ihre Sperre, wenn sie festgeschrieben oder zurückgesetzt wird.|  
  
 Es ist wichtig zu beachten, dass die Transaktionsisolationsstufe die Fähigkeit einer Transaktion, eigene Änderungen zu sehen, nicht beeinträchtigt. Transaktionen können immer alle Änderungen sehen, die sie vornehmen. Eine Transaktion kann z. **UPDATE** B. aus zwei UPDATE-Auszügen bestehen, von denen der erste die Vergütung aller Mitarbeiter um 10 Prozent erhöht und der zweite die Vergütung von Mitarbeitern über einen Höchstbetrag auf diesen Betrag festlegt. Dies ist nur als einzelne Transaktion erfolgreich, da die zweite **UPDATE-Anweisung** die Ergebnisse der ersten Transaktion sehen kann.
