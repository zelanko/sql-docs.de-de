---
description: Resync Command – dynamische Eigenschaft (ADO)
title: Resync Command Property-Dynamic (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Resync Command property [ADO]
ms.assetid: 4e2bb601-0fe8-4d61-b00e-38341d85a6bb
author: rothja
ms.author: jroth
ms.openlocfilehash: 2e882a9c65bf0d54dc9bd9e160edbc67f4e7996b
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88989511"
---
# <a name="resync-command-property-dynamic-ado"></a>Resync Command – dynamische Eigenschaft (ADO)
Gibt eine vom Benutzer bereitgestellte Befehls Zeichenfolge an, mit der die Methode für die [erneute Synchronisierung](./resync-method.md) die Daten in der in der dynamischen Eigenschaft [Unique Table](./unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) genannten Tabelle aktualisiert.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest, der eine Befehls Zeichenfolge ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Das [Recordset](./recordset-object-ado.md) -Objekt ist das Ergebnis einer Verknüpfungs Operation, die für mehrere Basistabellen ausgeführt wird. Die betroffenen Zeilen hängen vom *affectrecords* -Parameter der [Resync](./resync-method.md) -Methode ab. Die Standardmethode für die **Neusynchronisierung** wird ausgeführt, wenn die Eigenschaften [Unique Table](./unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) und **Resync Command** nicht festgelegt sind.  
  
 Die Befehls Zeichenfolge der **Resync-Befehls** Eigenschaft ist ein parametrisierter Befehl oder eine gespeicherte Prozedur, die die zu Aktualisier Ende Zeile eindeutig identifiziert und eine einzelne Zeile zurückgibt, die die gleiche Anzahl und Reihenfolge der Spalten wie die zu Aktualisier Ende Zeile enthält. Die Befehls Zeichenfolge enthält einen Parameter für jede Primärschlüssel Spalte in der **eindeutigen Tabelle**. Andernfalls wird ein Laufzeitfehler zurückgegeben. Die Parameter werden automatisch mit Primärschlüssel Werten aus der Zeile aufgefüllt, die aktualisiert werden soll.  
  
 Im folgenden finden Sie zwei Beispiele, die auf SQL basieren:  
  
 1 \) das **Recordset** wird durch einen Befehl definiert:  
  
```  
SELECT * FROM Customers JOIN Orders ON   
   Customers.CustomerID = Orders.CustomerID  
   WHERE city = 'Seattle'  
   ORDER BY CustomerID  
```  
  
 Die Eigenschaft für den **Resync-Befehl** ist auf Folgendes festgelegt:  
  
```  
"SELECT * FROM   
   (SELECT * FROM Customers JOIN Orders   
   ON Customers.CustomerID = Orders.CustomerID  
   city = 'Seattle' ORDER BY CustomerID)  
WHERE Orders.OrderID = ?"  
```  
  
 Die **eindeutige Tabelle** ist *Orders* , und der zugehörige Primärschlüssel *OrderID*ist parametrisiert. Die untergeordnete SELECT-Methode bietet eine einfache Möglichkeit, Programm gesteuert sicherzustellen, dass die gleiche Anzahl und Reihenfolge der Spalten wie durch den ursprünglichen Befehl zurückgegeben wird.  
  
 2 \) das **Recordset** wird durch eine gespeicherte Prozedur definiert:  
  
```  
CREATE PROC Custorders @CustomerID char(5) AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID   
WHERE Customers.CustomerID = @CustomerID  
```  
  
 Die **Resync** -Methode sollte die folgende gespeicherte Prozedur ausführen:  
  
```  
CREATE PROC CustordersResync @ordid int AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID  
WHERE Orders.ordid  = @ordid  
```  
  
 Die Eigenschaft für den **Resync-Befehl** ist auf Folgendes festgelegt:  
  
```  
"{call CustordersResync (?)}"  
```  
  
 Auch hier ist die **eindeutige Tabelle** *Orders* , und der zugehörige Primärschlüssel *OrderID*ist parametrisiert.  
  
 Der **Befehl Resync** ist eine dynamische Eigenschaft, die an die Auflistung der **Recordset** -Objekt [Eigenschaften](./properties-collection-ado.md) angehängt wird, wenn die Eigenschaft [Cursor Location](./cursorlocation-property-ado.md) auf **adUseClient**festgelegt ist.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)