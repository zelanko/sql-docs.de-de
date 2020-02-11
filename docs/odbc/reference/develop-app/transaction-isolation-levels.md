---
title: Transaktions Isolations Stufen (ODBC) | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e11a0d76fc4a2daece7b6f4f50761d40933792be
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73637210"
---
# <a name="transaction-isolation-levels-odbc"></a>Transaktions Isolations Stufen (ODBC)
*Transaktions Isolations Stufen* sind ein Maß für den Umfang, in dem die Transaktions Isolation erfolgreich ist. Die Transaktions Isolations Stufen werden insbesondere durch das vorhanden sein oder Fehlen der folgenden Phänomene definiert:  
  
-   **Dirty Reads** Eine *Dirty Read* tritt auf, wenn eine Transaktion Daten liest, für die noch kein Commit ausgeführt wurde. Angenommen, Transaktion 1 aktualisiert eine Zeile. Transaktion 2 liest die aktualisierte Zeile, bevor von Transaktion 1 ein Commit für das Update ausgeführt wird. Wenn Transaktion 1 ein Rollback der Änderung ausführt, verfügt Transaction 2 über gelesene Daten, die als nie vorhanden angesehen werden.  
  
-   **Nicht wiederholbare Lesevorgänge** Ein *nicht wiederholbarer Lese* Vorgang tritt auf, wenn eine Transaktion die gleiche Zeile zweimal liest, aber jedes Mal andere Daten abruft. Angenommen, Transaktion 1 liest eine Zeile. Transaktion 2 aktualisiert oder löscht diese Zeile und führt einen Commit für das Update oder den Löschvorgang aus. Wenn Transaktion 1 die Zeile erneut registriert, ruft Sie andere Zeilen Werte ab oder ermittelt, dass die Zeile gelöscht wurde.  
  
-   **Phantoms** Ein *Phantom* ist eine Zeile, die den Suchkriterien entspricht, jedoch nicht anfänglich angezeigt wird. Angenommen, Transaktion 1 liest einen Satz von Zeilen, die einige Suchkriterien erfüllen. Transaktion 2 generiert eine neue Zeile (entweder über ein Update oder eine Einfügung), die den Suchkriterien für Transaktion 1 entspricht. Wenn Transaktion 1 die Anweisung, die die Zeilen liest, erneut ausführt, erhält Sie einen anderen Satz von Zeilen.  
  
 Die vier Transaktions Isolations Stufen (wie von SQL-92 definiert) werden im Hinblick auf diese Phänomene definiert. In der folgenden Tabelle markiert ein "X" die einzelnen vorkommen, die auftreten können.  
  
|Transaktions Isolationsstufe|Dirty Reads|Nicht wiederholbare Lesevorgänge|Phantome|  
|---------------------------------|-----------------|-------------------------|--------------|  
|Read Uncommitted|X|X|X|  
|Read Committed|--|X|X|  
|Repeatable Read|--|--|X|  
|Serialisierbar|--|--|--|  
  
 In der folgenden Tabelle werden einfache Möglichkeiten beschrieben, mit denen ein DBMS die Transaktions Isolations Stufen implementieren kann.  
  
> [!IMPORTANT]  
>  Die meisten DBMSs verwenden komplexere Schemas als diese, um die Parallelität zu erhöhen. Diese Beispiele dienen nur zur Veranschaulichung. Insbesondere gibt ODBC nicht an, wie bestimmte DBMSs Transaktionen voneinander isolieren.  
  
|Transaktions Isolation|Mögliche Implementierung|  
|---------------------------|-----------------------------|  
|Read Uncommitted|Transaktionen sind nicht voneinander isoliert. Wenn das DBMS andere Transaktions Isolations Stufen unterstützt, ignoriert es den Mechanismus, mit dem diese Ebenen implementiert werden. Damit Sie keine negativen Auswirkungen auf andere Transaktionen haben, sind Transaktionen, die auf der Ebene Read nicht Commit ausgeführt werden, in der Regel schreibgeschützt.|  
|Read Committed|Die Transaktion wartet, bis Zeilen, die von anderen Transaktionen geschrieben wurden, entsperrt werden. Dadurch wird verhindert, dass Daten geändert werden.<br /><br /> Die Transaktion enthält eine Lesesperre (wenn Sie nur die Zeile liest) oder eine Schreibsperre (wenn Sie die Zeile aktualisiert oder löscht) in der aktuellen Zeile, um zu verhindern, dass andere Transaktionen Sie aktualisieren oder löschen. Die Transaktion gibt Lese Sperren frei, wenn Sie von der aktuellen Zeile verschoben wird. Sie enthält Schreib sperren, bis ein Commit oder ein Rollback ausgeführt wird.|  
|Repeatable Read|Die Transaktion wartet, bis Zeilen, die von anderen Transaktionen geschrieben wurden, entsperrt werden. Dadurch wird verhindert, dass Daten geändert werden.<br /><br /> Die Transaktion enthält Lese Sperren für alle Zeilen, die an die Anwendung zurückgegeben werden, und schreibt Sperren für alle Zeilen, die eingefügt, aktualisiert oder gelöscht werden. Wenn die Transaktion z. b. die SQL- **Anweisung \* SELECT FROM Orders**enthält, sperrt die Transaktion Zeilen, während Sie von der Anwendung abgerufen werden. Wenn die Transaktion die SQL-Anweisung **Delete aus Orders mit dem Status = ' Closed '** enthält, sperrt die Transaktion Zeilen, während Sie gelöscht wird.<br /><br /> Da andere Transaktionen diese Zeilen nicht aktualisieren oder löschen können, vermeidet die aktuelle Transaktion alle nicht wiederholbaren Lesevorgänge. Die Transaktion gibt die Sperren frei, wenn ein Commit oder ein Rollback ausgeführt wird.|  
|Serialisierbar|Die Transaktion wartet, bis Zeilen, die von anderen Transaktionen geschrieben wurden, entsperrt werden. Dadurch wird verhindert, dass Daten geändert werden.<br /><br /> Die Transaktion enthält eine Lesesperre (wenn Sie nur Zeilen liest) oder eine Schreibsperre (wenn Sie Zeilen aktualisieren oder löschen kann) für den Bereich der Zeilen, auf den Sie sich auswirkt. Wenn die Transaktion z. b. die SQL- **Anweisung \* SELECT FROM Orders**enthält, entspricht der Bereich der gesamten Orders-Tabelle. die Transaktion ledert die Tabelle und lässt keine neuen Zeilen in die Tabelle ein. Wenn die Transaktion die SQL-Anweisung **Delete aus Orders enthält, wobei Status = ' Closed '** ist, beträgt der Bereich alle Zeilen mit dem Status ' Closed '; beim Schreiben der Transaktion werden alle Zeilen in der Orders-Tabelle mit dem Status "Closed" gesperrt, und es ist nicht zulässig, dass Zeilen eingefügt oder aktualisiert werden, sodass die resultierende Zeile den Status "geschlossen" aufweist.<br /><br /> Da andere Transaktionen die Zeilen im Bereich nicht aktualisieren oder löschen können, vermeidet die aktuelle Transaktion alle nicht wiederholbaren Lesevorgänge. Da andere Transaktionen keine Zeilen im Bereich einfügen können, vermeidet die aktuelle Transaktion alle Phantome. Die Sperre wird von der Transaktion freigegeben, wenn ein Commit oder ein Rollback ausgeführt wird.|  
  
 Beachten Sie, dass sich die Transaktions Isolationsstufe nicht auf die Fähigkeit einer Transaktion auswirkt, eigene Änderungen anzuzeigen. Transaktionen können immer alle Änderungen sehen, die Sie vornehmen. Eine Transaktion kann z. b. aus zwei **Update** -Anweisungen bestehen, wobei der erste Wert alle Mitarbeiter um 10 Prozent erhöht und der zweite die Bezahlung aller Mitarbeiter für einen maximalen Betrag auf diesen Betrag festlegt. Dies ist nur eine einzige Transaktion, da die zweite **Update** -Anweisung die Ergebnisse der ersten-Anweisung sehen kann.
