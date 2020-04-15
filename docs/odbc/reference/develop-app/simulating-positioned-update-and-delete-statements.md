---
title: Simulieren von positionierten Aktualisierungs- und Löschanweisungen | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e1eb498a99180d145147e67c8955eeb7a0027024
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301991"
---
# <a name="simulating-positioned-update-and-delete-statements"></a>Simulieren von positionierten Aktualisierungen und DELETE-Anweisungen
Wenn die Datenquelle positionierte Aktualisierungs- und Löschanweisungen nicht unterstützt, kann der Treiber diese simulieren. Die ODBC-Cursorbibliothek simuliert beispielsweise positionierte Aktualisierungs- und Löschanweisungen. Die allgemeine Strategie zum Simulieren von positionierten Aktualisierungs- und Löschanweisungen besteht darin, positionierte Anweisungen in durchsuchte Zus. zu konvertieren. Dies geschieht, indem die **WHERE CURRENT OF-Klausel** durch eine durchsuchte **WHERE-Klausel** ersetzt wird, die die aktuelle Zeile identifiziert.  
  
 Da z. B. die CustID-Spalte jede Zeile in der Tabelle Customers eindeutig identifiziert, wird die positionierte delete-Anweisung  
  
```  
DELETE FROM Customers WHERE CURRENT OF CustCursor  
```  
  
 kann in  
  
```  
DELETE FROM Customers WHERE (CustID = ?)  
```  
  
 Der Treiber kann eine der folgenden *Zeilenbezeichner* in der **WHERE-Klausel** verwenden:  
  
-   Spalten, deren Werte dazu dienen, jede Zeile in der Tabelle eindeutig zu identifizieren. Wenn Sie z. B. **SQLSpecialColumns** mit SQL_BEST_ROWID aufrufen, wird die optimale Spalte oder der Satz von Spalten zurückgegeben, die diesem Zweck dienen.  
  
-   Pseudospalten, die von einigen Datenquellen bereitgestellt werden, um jede Zeile eindeutig zu identifizieren. Diese können auch durch Aufrufen von **SQLSpecialColumns**abgerufen werden.  
  
-   Ein eindeutiger Index, sofern verfügbar.  
  
-   Alle Spalten im Resultset.  
  
 Welche Spalten ein Treiber in der **WHERE-Klausel** verwenden soll, hängt vom Treiber ab. Bei einigen Datenquellen kann die Ermittlung eines Zeilenbezeichners kostspielig sein. Die Ausführung ist jedoch schneller und garantiert, dass eine simulierte Anweisung höchstens eine Zeile aktualisiert oder gelöscht wird. Abhängig von den Funktionen des zugrunde liegenden DBMS kann die Einrichtung mit einem Zeilenbezeichner teuer sein. Die Ausführung ist jedoch schneller und garantiert, dass eine simulierte Anweisung nur eine Zeile aktualisiert oder gelöscht wird. Die Möglichkeit, alle Spalten im Resultset zu verwenden, ist in der Regel viel einfacher einzurichten. Die Ausführung ist jedoch langsamer und kann, wenn die Spalten eine Zeile nicht eindeutig identifizieren, dazu führen, dass Zeilen unbeabsichtigt aktualisiert oder gelöscht werden, insbesondere wenn die Auswahlliste für das Resultset nicht alle Spalten enthält, die in der zugrunde liegenden Tabelle vorhanden sind.  
  
 Je nachdem, welche der vorherigen Strategien der Treiber unterstützt, kann eine Anwendung auswählen, welche Strategie der Treiber mit dem Attribut SQL_ATTR_SIMULATE_CURSOR-Anweisung verwenden soll. Obwohl es seltsam erscheinen mag, dass eine Anwendung gefahr ist, eine Zeile unbeabsichtigt zu aktualisieren oder zu löschen, kann die Anwendung dieses Risiko entfernen, indem sie sicherstellt, dass die Spalten im Resultset jede Zeile in der Ergebnismenge eindeutig identifizieren. Dies erspart dem Fahrer die Mühe, dies zu tun.  
  
 Wenn der Treiber einen Zeilenbezeichner verwendet, fängt er die **SELECT FOR UPDATE-Anweisung** ab, die das Resultset erstellt. Wenn die Spalten in der Auswahlliste eine Zeile nicht effektiv identifizieren, fügt der Treiber die erforderlichen Spalten am Ende der Auswahlliste hinzu. Einige Datenquellen verfügen über eine einzelne Spalte, die immer eine Zeile eindeutig identifiziert, z. B. die ROWID-Spalte in Oracle. Wenn eine solche Spalte verfügbar ist, verwendet der Treiber diese. Andernfalls ruft der Treiber **SQLSpecialColumns** für jede Tabelle in der **FROM-Klausel** auf, um eine Liste der Spalten abzurufen, die jede Zeile eindeutig identifizieren. Eine häufige Einschränkung, die sich aus dieser Technik ergibt, ist, dass die Cursorsimulation fehlschlägt, wenn die **FROM-Klausel** mehr als eine Tabelle enthält.  
  
 Unabhängig davon, wie der Treiber Zeilen identifiziert, wird die **FOR UPDATE OF-Klausel** in der Regel von der **SELECT FOR UPDATE-Anweisung** entfernt, bevor sie an die Datenquelle gesendet wird. Die **FOR UPDATE OF-Klausel** wird nur mit positionierten Aktualisierungs- und Löschanweisungen verwendet. Datenquellen, die positionierte Aktualisierungs- und Löschanweisungen nicht unterstützen, unterstützen sie im Allgemeinen nicht.  
  
 Wenn die Anwendung eine positionierte Aktualisierungs- oder Löschanweisung zur Ausführung sendet, ersetzt der Treiber die **WHERE CURRENT OF-Klausel** durch eine **WHERE-Klausel,** die den Zeilenbezeichner enthält. Die Werte dieser Spalten werden aus einem Cache abgerufen, der vom Treiber für jede Spalte verwaltet wird, die er in der **WHERE-Klausel** verwendet. Nachdem der Treiber die **WHERE-Klausel** ersetzt hat, sendet er die Anweisung zur Ausführung an die Datenquelle.  
  
 Angenommen, die Anwendung sendet die folgende Anweisung, um ein Resultset zu erstellen:  
  
```  
SELECT Name, Address, Phone FROM Customers FOR UPDATE OF Phone, Address  
```  
  
 Wenn die Anwendung SQL_ATTR_SIMULATE_CURSOR festgelegt hat, um eine Garantie für eindeutige Anforderungen anzufordern, und wenn die Datenquelle keine Pseudospalte enthält, die immer eine Zeile eindeutig identifiziert, ruft der Treiber **SQLSpecialColumns** für die Customers-Tabelle auf, erkennt, dass CustID der Schlüssel zur Tabelle Customers ist, und fügt diese der Auswahlliste hinzu, und entfernt die **FOR UPDATE OF-Klausel:**  
  
```  
SELECT Name, Address, Phone, CustID FROM Customers  
```  
  
 Wenn die Anwendung keine Garantie für Dieklichkeit angefordert hat, streift der Treiber nur die **FOR UPDATE OF-Klausel:**  
  
```  
SELECT Name, Address, Phone FROM Customers  
```  
  
 Angenommen, die Anwendung führt einen Bildlauf durch das Resultset durch und sendet die folgende positionierte Update-Anweisung zur Ausführung, wobei Cust der Name des Cursors über dem Resultset ist:  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE CURRENT OF Cust  
```  
  
 Wenn die Anwendung keine Garantie für eindeutige Eigenschaften angefordert hat, ersetzt der Treiber die **WHERE-Klausel** und bindet den CustID-Parameter an die Variable in seinem Cache:  
  
```  
UPDATE Customers SET Address = ?, Phone = ? WHERE (CustID = ?)  
```  
  
 Wenn die Anwendung keine Garantie für eindeutige Eigenschaften angefordert hat, ersetzt der Treiber die **WHERE-Klausel** und bindet die Parameter Name, Address und Phone in dieser Klausel an die Variablen in seinem Cache:  
  
```  
UPDATE Customers SET Address = ?, Phone = ?  
   WHERE (Name = ?) AND (Address = ?) AND (Phone = ?)  
```
