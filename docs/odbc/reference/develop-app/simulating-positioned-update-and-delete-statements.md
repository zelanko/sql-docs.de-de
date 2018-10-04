---
title: Simulieren von positioniert, Update und Delete-Anweisungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- positioned deletes [ODBC]
- data updates [ODBC], positioned update or delete
- row identifiers [ODBC]
- positioned updates [ODBC]
- updating data [ODBC], positioned update or delete
ms.assetid: b24ed59f-f25b-4646-a135-5f3596abc1a4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d98d40ae24c68f90a304edb0293febfe76fac2c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47855218"
---
# <a name="simulating-positioned-update-and-delete-statements"></a>Simulieren von positionierten Aktualisierungen und DELETE-Anweisungen
Wenn die Datenquelle nicht positioniertes Update unterstützt und-Anweisungen DELETE, kann der Treiber diese simulieren. Beispielsweise wird die ODBC-Cursorbibliothek simuliert positioniertes Update und delete-Anweisungen. Die allgemeine Strategie zum Simulieren positionierte Update- und Delete-Anweisungen werden positionierte-Anweisungen zu komplexen zu konvertieren. Dies erfolgt durch Ersetzen der **WHERE CURRENT OF** -Klausel mit einer komplexen **, in denen** -Klausel, die die aktuelle Zeile angibt.  
  
 Z. B. weil der CustID-Spalte jeder Zeile in der Customers-Tabelle eindeutig identifiziert, löschen die positionierte-Anweisung  
  
```  
DELETE FROM Customers WHERE CURRENT OF CustCursor  
```  
  
 kann in konvertiert werden  
  
```  
DELETE FROM Customers WHERE (CustID = ?)  
```  
  
 Der Treiber möglicherweise verwenden Sie eine der folgenden *Zeilenbezeichner* in die **, in denen** Klausel:  
  
-   Spalten, deren Werte dienen, um eindeutig auf jede Zeile in der Tabelle zu identifizieren. Zum Beispiel der Aufruf **SQLSpecialColumns** mit SQL_BEST_ROWID gibt die optimale(n) Spalte(n) oder eine Gruppe von Spalten, die diesem Zweck dienen.  
  
-   Pseudo-Spalten zur Verfügung gestellt, von einigen Datenquellen im Rahmen, die jede Zeile eindeutig identifiziert. Dies können auch abgerufen werden durch Aufrufen von **SQLSpecialColumns**.  
  
-   Einen eindeutigen Index, sofern verfügbar.  
  
-   Alle Spalten im Resultset.  
  
 Genau die Spalten, die ein Treiber, in verwenden sollten der **, in denen** Klausel erstellt, hängt der Treiber. Für einige Daten können Datenquellen, das Festlegen eines zeilenbezeichners kostspielig sein. Es ist jedoch schneller ausgeführt und wird sichergestellt, dass eine simulierte-Anweisung aktualisiert oder löscht jeweils nur eine Zeile. Abhängig von den Funktionen des zugrunde liegenden DBMS kann die mithilfe eines zeilenbezeichners einrichten, aufwändig sein. Es ist jedoch schneller ausgeführt und wird sichergestellt, dass eine simulierte-Anweisung aktualisiert oder löscht nur eine Zeile. Die Möglichkeit, alle Spalten im Resultset ist in der Regel viel leichter einzurichten. Allerdings ist langsamer ausgeführt und, wenn die Spalten eine Zeile nicht eindeutig identifiziert, kann dazu führen, die Zeilen, die unabsichtlich aktualisiert oder gelöscht, insbesondere dann, wenn für das Ergebnis die select-Liste festgelegt enthält keine alle Spalten, die in der zugrunde liegenden Tabelle vorhanden.  
  
 Abhängig von dem der genannten Strategien des Treibers unterstützt, eine Anwendung kann auswählen, welche Strategie den Treiber mit der SQL_ATTR_SIMULATE_CURSOR-Anweisungsattribut verwendet werden sollen. Obwohl es merkwürdig für eine Anwendung, das Risiko des versehentlich aktualisieren oder Löschen einer Zeile erscheint, kann die Anwendung dieses Risiko entfernen, indem Sie sicherstellen, dass die Spalten im Resultset jede Zeile im Resultset eindeutig identifizieren. Hierdurch wird dem Treiber den Aufwand zu diesem Zweck müssen gespeichert.  
  
 Der Treiber gewählt, die eine Zeilen-ID verwenden, fängt die **SELECT FOR UPDATE** -Anweisung, die das Resultset erstellt. Wenn die Spalten in der select-Liste eine Zeile nicht effektiv identifizieren, fügt der Treiber die erforderlichen Spalten am Ende der select-Liste hinzu. Einige Datenquellen haben eine einzelne Spalte, die eine Zeile, z. B. die ROWID-Spalte in Oracle immer eindeutig identifiziert. Wenn eine solche Spalte verfügbar ist, verwendet der Treiber dies. Andernfalls ruft der Treiber **SQLSpecialColumns** für jede Tabelle in der **FROM** -Klausel, um eine Liste der Spalten abzurufen, die jede Zeile eindeutig identifizieren. Eine allgemeine Beschränkung, die durch dieses Verfahren entsteht ist, dass Cursor Simulation schlägt fehl, wenn es mehr als eine Tabelle in der **FROM** Klausel.  
  
 Unabhängig davon, wie Zeilen durch der Treiber identifiziert werden, in der Regel entfernt die **FOR UPDATE OF** Klausel aus der **SELECT FOR UPDATE** Anweisung vor dem Senden an die Datenquelle. Die **FOR UPDATE OF** -Klausel wird verwendet, nur mit, Update positioniert und-Anweisungen DELETE. Datenquellen, die nicht unterstützen positioniert, Update und Delete-Anweisungen in der Regel nicht unterstützt wird angezeigt.  
  
 Wenn die Anwendung ein positioniertes Update oder Delete-Anweisung für die Ausführung sendet, wird der Treiber ersetzt die **WHERE CURRENT OF** -Klausel mit einer **, in denen** Klausel, die die Zeilen-ID enthält. Die Werte dieser Spalten abgerufen werden, aus dem Cache verwaltet, die vom Treiber für jede Spalte, die verwendet wird, in der **, in denen** Klausel. Nachdem der Treiber ersetzt hat die **, in denen** -Klausel, sendet er die Anweisung an die Datenquelle für die Ausführung.  
  
 Nehmen wir beispielsweise an, dass die Anwendung die folgende Anweisung zum Erstellen eines Resultsets übermittelt:  
  
```  
SELECT Name, Address, Phone FROM Customers FOR UPDATE OF Phone, Address  
```  
  
 Wenn die Anwendung SQL_ATTR_SIMULATE_CURSOR zum Anfordern einer Garantie, dass der festgelegt wurde, und wenn die Datenquelle keine Pseudospalte, die eine Zeile immer eindeutig identifiziert bereitstellt, der Treiber ruft **SQLSpecialColumns** für die Customers-Tabelle ermittelt, dass CustID ist der Schlüssel zur Customers-Tabelle in der select-Liste hinzugefügt und entfernt die **FOR UPDATE OF** Klausel:  
  
```  
SELECT Name, Address, Phone, CustID FROM Customers  
```  
  
 Wenn eine Garantie, dass der nicht von die Anwendung angefordert hat, entfernt der Treiber nur die **FOR UPDATE OF** Klausel:  
  
```  
SELECT Name, Address, Phone FROM Customers  
```  
  
 Nehmen wir an die Anwendung führt einen Bildlauf durch die Ergebnisse und sendet die folgenden positioniertes Update-Anweisung für die Ausführung, wobei der Name des Cursors ist Cust, über das Resultset:  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust  
```  
  
 Wenn eine Garantie, dass der nicht von die Anwendung angefordert hat, wird der Treiber ersetzt die **, in denen** Klausel und bindet den CustID-Parameter an die Variable in seinem Cache:  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE (CustID = ?)  
```  
  
 Wenn eine Garantie, dass der nicht von die Anwendung angefordert hat, wird der Treiber ersetzt die **, in denen** -Klausel und die Parameter Name, Adresse und Telefonnummer in diese Klausel, um die Variablen in seinem Cache:  
  
```  
UPDATE Customers SET Address = ?, Phone = ?  
   WHERE (Name = ?) AND (Address = ?) AND (Phone = ?)  
```
