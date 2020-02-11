---
title: Simulieren von positionierten Update-und DELETE-Anweisungen | Microsoft-Dokumentation
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
ms.openlocfilehash: 85d7642620d510ebba050a3fbc4348898e070070
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107533"
---
# <a name="simulating-positioned-update-and-delete-statements"></a>Simulieren von positionierten Aktualisierungen und DELETE-Anweisungen
Wenn die Datenquelle positionierte UPDATE-und DELETE-Anweisungen nicht unterstützt, kann der Treiber diese simulieren. Beispielsweise simuliert die ODBC-Cursor Bibliothek positionierte UPDATE-und DELETE-Anweisungen. Die allgemeine Strategie zum simulieren positionierter Update-und DELETE-Anweisungen besteht darin, positionierte Anweisungen in durchsuchte zu konvertieren. Dies erfolgt durch Ersetzen der **WHERE CURRENT of** -Klausel durch eine durchsuchte **Where** -Klausel, die die aktuelle Zeile identifiziert.  
  
 Da die CustID-Spalte beispielsweise jede Zeile in der Customers-Tabelle eindeutig identifiziert, wird die positionierte DELETE-Anweisung  
  
```  
DELETE FROM Customers WHERE CURRENT OF CustCursor  
```  
  
 kann konvertiert werden in  
  
```  
DELETE FROM Customers WHERE (CustID = ?)  
```  
  
 Der Treiber kann einen der folgenden *Zeilen* Bezeichner in der **Where** -Klausel verwenden:  
  
-   Spalten, deren Werte dienen, um jede Zeile in der Tabelle eindeutig zu identifizieren. Wenn Sie z. b. **SQLSpecialColumns** mit SQL_BEST_ROWID aufrufen, wird die optimale Spalte oder Gruppe von Spalten zurückgegeben, die diesen Zweck erfüllen.  
  
-   Pseudo Spalten, die von einigen Datenquellen bereitgestellt werden, um jede Zeile eindeutig zu identifizieren. Diese können auch durch Aufrufen von **SQLSpecialColumns**abgerufen werden.  
  
-   Ein eindeutiger Index, falls verfügbar.  
  
-   Alle Spalten im Resultset.  
  
 Welche Spalten ein Treiber in der **Where** -Klausel verwenden sollte, die er erstellt, hängt vom Treiber ab. Bei einigen Datenquellen kann das Ermitteln eines Zeilen Bezeichners kostspielig sein. Es ist jedoch schneller, Sie auszuführen und sicherzustellen, dass eine simulierte Anweisung höchstens eine Zeile aktualisiert oder löscht. Abhängig von den Funktionen des zugrunde liegenden DBMS kann die Einrichtung eines Zeilen Bezeichners teuer sein. Es ist jedoch schneller auszuführen und sicherzustellen, dass eine simulierte Anweisung nur eine Zeile aktualisiert oder löscht. Die Option, alle Spalten im Resultset zu verwenden, ist in der Regel viel einfacher einzurichten. Die Ausführung ist jedoch langsamer. wenn die Spalten eine Zeile nicht eindeutig identifizieren, kann dazu führen, dass Zeilen versehentlich aktualisiert oder gelöscht werden, insbesondere dann, wenn die Auswahlliste für das Resultset nicht alle Spalten enthält, die in der zugrunde liegenden Tabelle vorhanden sind.  
  
 Abhängig davon, welche der oben genannten Strategien der Treiber unterstützt, kann eine Anwendung auswählen, welche Strategie der Treiber mit dem SQL_ATTR_SIMULATE_CURSOR Statement-Attribut verwenden soll. Obwohl es für eine Anwendung möglicherweise unmerk würdig erscheint, eine Zeile versehentlich zu aktualisieren oder zu löschen, kann die Anwendung dieses Risiko entfernen, indem Sie sicherstellt, dass die Spalten im Resultset die einzelnen Zeilen im Resultset eindeutig identifizieren. Dies spart den Treiber, um dies zu tun.  
  
 Wenn der Treiber die Verwendung eines Zeilen Bezeichners auswählt, fängt er die **Select for Update** -Anweisung ab, die das Resultset erstellt. Wenn die Spalten in der SELECT-Liste eine Zeile nicht effektiv identifizieren, fügt der Treiber die erforderlichen Spalten am Ende der Auswahlliste hinzu. Einige Datenquellen verfügen über eine einzelne Spalte, die eine Zeile (z. b. die ROWID-Spalte in Oracle) immer eindeutig identifiziert. Wenn eine solche Spalte verfügbar ist, verwendet der Treiber diesen. Andernfalls ruft der Treiber **SQLSpecialColumns** für jede Tabelle in der **from** -Klausel auf, um eine Liste der Spalten abzurufen, die jede Zeile eindeutig identifizieren. Eine allgemeine Einschränkung, die sich aus dieser Technik ergibt, besteht darin, dass die Cursor Simulation fehlschlägt, wenn in der **from** -Klausel mehr als eine Tabelle vorhanden ist.  
  
 Unabhängig davon, wie der Treiber Zeilen identifiziert, wird die **for Update of** -Klausel in der Regel aus der **Select for Update** -Anweisung entfernt, bevor Sie an die Datenquelle gesendet wird. Die **for Update of** -Klausel wird nur für positionierte UPDATE-und DELETE-Anweisungen verwendet. Datenquellen, die positionierte UPDATE-und DELETE-Anweisungen nicht unterstützen, unterstützen Sie in der Regel nicht.  
  
 Wenn die Anwendung eine positionierte UPDATE-oder DELETE-Anweisung zur Ausführung übermittelt, ersetzt der Treiber die **WHERE CURRENT of** -Klausel durch eine **Where** -Klausel, die den Zeilen Bezeichner enthält. Die Werte dieser Spalten werden aus einem Cache abgerufen, der vom Treiber für jede Spalte, die in der **Where** -Klausel verwendet wird, verwaltet werden. Nachdem der Treiber die **Where** -Klausel ersetzt hat, sendet er die-Anweisung zur Ausführung an die Datenquelle.  
  
 Nehmen wir beispielsweise an, dass die Anwendung die folgende Anweisung übermittelt, um ein Resultset zu erstellen:  
  
```  
SELECT Name, Address, Phone FROM Customers FOR UPDATE OF Phone, Address  
```  
  
 Wenn die Anwendung SQL_ATTR_SIMULATE_CURSOR festgelegt hat, um eine Garantie der Eindeutigkeit anzufordern, und die Datenquelle keine Pseudo Spalte bereitstellt, die eine Zeile immer eindeutig identifiziert, ruft der Treiber **SQLSpecialColumns** für die Customers-Tabelle auf, ermittelt, dass CustID der Schlüssel für die Customers-Tabelle ist, und entfernt die **for Update of** -Klausel:  
  
```  
SELECT Name, Address, Phone, CustID FROM Customers  
```  
  
 Wenn die Anwendung keine Garantie für Eindeutigkeit angefordert hat, entfernt der Treiber nur die **for Update of** -Klausel:  
  
```  
SELECT Name, Address, Phone FROM Customers  
```  
  
 Angenommen, die Anwendung führt einen Bildlauf durch das Resultset durch und übermittelt die folgende positionierte UPDATE-Anweisung zur Ausführung, wobei cust der Name des Cursors über dem Resultset ist:  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust  
```  
  
 Wenn die Anwendung keine Garantie für Eindeutigkeit angefordert hat, ersetzt der Treiber die **Where** -Klausel und bindet den CustID-Parameter an die Variable im Cache:  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE (CustID = ?)  
```  
  
 Wenn die Anwendung keine Garantie der Eindeutigkeit angefordert hat, ersetzt der Treiber die **Where** -Klausel und bindet den Namen, die Adresse und die Telefon Parameter in dieser Klausel an die Variablen im Cache:  
  
```  
UPDATE Customers SET Address = ?, Phone = ?  
   WHERE (Name = ?) AND (Address = ?) AND (Phone = ?)  
```
