---
title: Transaktionsisolationsstufen | Microsoft-Dokumentation
ms.custom: ''
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
ms.openlocfilehash: 83197b1b487db6c52a8fe9b7a57dd6af55c33571
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67985107"
---
# <a name="transaction-isolation-levels"></a>Transaktionsisolationsstufen
*Transaktionsisolationsstufen von Cursorn* sind eine Maßeinheit für den Umfang für die Transaktion isoliert ist erfolgreich. Insbesondere werden die Isolationsstufen von Transaktionen durch das Vorhandensein oder fehlen, der die folgende Phänomene definiert:  
  
-   **Dirty Reads** ein *dirty Read* tritt auf, wenn eine Transaktion Daten liest, die noch kein Commit ausgeführt wurde. Nehmen wir beispielsweise an Transaktion 1 Updates einer Zeile. Transaktion 2 liest die aktualisierte Zeile vor dem Commit der Transaktion 1-Update. Wenn die Transaktion 1 die Änderung ein Rollback ausgeführt, verfügen Transaktion 2 liest Daten, die als betrachtet ist nicht vorhanden sind.  
  
-   **Nicht wiederholbaren Lesevorgängen** ein *nicht wiederholbarer Lesevorgang* tritt auf, wenn eine Transaktion zweimal die gleiche Zeile liest aber verschiedene Daten jedes Mal ruft. Nehmen wir beispielsweise an Transaktion 1 liest eine Zeile. Transaktion 2 aktualisiert oder löscht die Zeile, und führt einen Commit für die Update- oder Delete. Wenn Transaktion 1 Zeile filtereinstellungen, andere Zeilenwerte abgerufen oder erkennt, dass die Zeile gelöscht wurde.  
  
-   **Phantome** ein *phantom* ist eine Zeile, die den Suchkriterien entspricht, jedoch wird anfänglich nicht angezeigt. Nehmen wir beispielsweise an, dass die Transaktion 1 einen Satz von Zeilen liest, die einige Suchkriterien erfüllen. Transaktion 2 generiert eine neue Zeile (entweder durch ein Update oder Insert), die den Suchkriterien für die Transaktion 1 entspricht. Wenn die Transaktion 1 die Anweisung reexecutes, die die Zeilen liest, ruft er einen anderen Satz von Zeilen ab.  
  
 Die vier Transaktionsisolationsstufen (wie SQL-92 definiert) werden in Bezug auf diese Phänomene definiert. In der folgenden Tabelle ist kennzeichnet ein "X" jedes Phänomen, die auftreten können.  
  
|Transaktionsisolationsstufe|Unsauberes lesen|Nicht wiederholbaren Lesevorgängen|Phantome|  
|---------------------------------|-----------------|-------------------------|--------------|  
|Read Uncommitted|X|X|X|  
|Read Committed|--|X|X|  
|Repeatable Read|--|--|X|  
|Serializable|--|--|--|  
  
 Die folgende Tabelle beschreibt auf einfache Weise, dass ein DBMS Isolationsstufen von Transaktionen implementieren kann.  
  
> [!IMPORTANT]  
>  Die meisten DBMS-Systeme können, dass komplexere Schemas als diese um Parallelität zu erhöhen. Diese Beispiele dienen lediglich zur Veranschaulichung. ODBC ist vor allem nicht beschreiten wie bestimmte DBMS Transaktionen voneinander isolieren.  
  
|Transaktionsisolation|Mögliche Implementierung|  
|---------------------------|-----------------------------|  
|Read Uncommitted|Transaktionen sind nicht voneinander isoliert. Falls das DBMS anderen Isolationsstufen von Transaktionen unterstützt, wird es geeigneter Mechanismus, der ihn verwendet, um diese Ebenen implementieren ignoriert. Damit sie andere Transaktionen nicht negativ auswirken, sind Transaktionen, die auf der Read Uncommitted-Ebene in der Regel schreibgeschützt.|  
|Read Committed|Die Transaktion wird gewartet, bis für den Schreibzugriff gesperrt durch andere Transaktionen Zeilen entsperrt werden; Dies verhindert, dass es keine "dirty" Daten lesen.<br /><br /> Die Transaktion enthält ein Lesesperre (Wenn sie nur die Zeile liest) oder der Schreibvorgang sperren (Wenn sie aktualisiert oder löscht die Zeile) für die aktuelle Zeile aus, um zu verhindern, dass andere Transaktionen aktualisieren oder löschen. Die Transaktion gibt Lesesperren frei, wenn sie aus der aktuellen Zeile bewegt wird. Sie enthält Schreibsperren, bis sie ein Commit oder Rollback ausgeführt.|  
|Repeatable Read|Die Transaktion wird gewartet, bis für den Schreibzugriff gesperrt durch andere Transaktionen Zeilen entsperrt werden; Dies verhindert, dass es keine "dirty" Daten lesen.<br /><br /> Die Transaktion sperrt Lesen alle Zeilen, die er an die Anwendung "und" Write-Sperren für alle Zeilen zurückgibt, sie einfügungen, Updates oder löscht. Wenn die Transaktion, die SQL-Anweisung enthält z. B. **wählen \* FROM Orders**, Zeilen die Transaktionssperren-lesen, wie die Anwendung diese abruft. Wenn die Transaktion, die SQL-Anweisung umfasst **löschen aus, in dem Status der Bestellung = 'Geschlossen'** , Transaktion-Schreibsperren Zeilen, da sie gelöscht.<br /><br /> Da andere Transaktionen nicht aktualisieren oder löschen diese Zeilen, wird die aktuelle Transaktion nicht wiederholbaren Lesevorgängen vermieden. Die Transaktion gibt ihre Sperren frei, wenn sie ein Commit oder Rollback ausgeführt.|  
|Serializable|Die Transaktion wird gewartet, bis für den Schreibzugriff gesperrt durch andere Transaktionen Zeilen entsperrt werden; Dies verhindert, dass es keine "dirty" Daten lesen.<br /><br /> Die Transaktion enthält eine Lesesperre (Wenn sie nur Zeilen liest) oder Schreibsperre (Wenn sie später aktualisieren oder Löschen von Zeilen) für den Bereich der Zeilen beeinflusst. Wenn die Transaktion, die SQL-Anweisung enthält z. B. **wählen \* FROM Orders**, der Bereich ist die gesamte Tabelle "Orders", die Read-Transaktionssperren der Tabelle und wird nicht zu, dass alle neuen Zeilen in diese eingefügt werden soll. Wenn die Transaktion, die SQL-Anweisung enthält **Löschen von Aufträgen, in dem Status "Geschlossen" =** , Bereich alle Zeilen mit dem Status "CLOSED" bildet die Transaktionssperren-Schreibvorgänge aller Zeilen in die Aufträge Tabelle mit dem Status "Geschlossen" und wird nicht ermöglichen, dass alle Zeilen eingefügt oder aktualisiert, dass die daraus resultierende Zeile den Status "Geschlossen" aufweist.<br /><br /> Da andere Transaktionen nicht aktualisieren oder Löschen von Zeilen in den Bereich, wird die aktuelle Transaktion nicht wiederholbaren Lesevorgängen vermieden. Da andere Transaktionen Zeilen im Bereich einfügen können, wird die aktuelle Transaktion Phantome vermieden. Die Transaktion gibt die Sperre frei, wenn sie ein Commit oder Rollback.|  
  
 Es ist wichtig zu beachten, dass die Isolationsstufe der Transaktion nicht auf einer Transaktion können eigene Änderungen sehen auswirkt; Transaktionen können immer alle Änderungen angezeigt, die sie vornehmen. Beispielsweise kann eine Transaktion von zwei bestehen **UPDATE** Anweisungen, die das erste Argument löst die Zahlung aller Mitarbeiter aus, um 10 Prozent und dem zweiten wird die Zahlung von Mitarbeitern über einige maximale Einzug für den angegebenen. Dies als einzelne Transaktion erfolgreich ist, da nur die zweite **UPDATE** Anweisung sehen die Ergebnisse der ersten.
