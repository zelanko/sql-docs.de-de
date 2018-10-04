---
title: Resync-Befehl dynamische Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Resync Command property [ADO]
ms.assetid: 4e2bb601-0fe8-4d61-b00e-38341d85a6bb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5567bf3cc460aac6abfc2979a14e124bfd9d4cac
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47789288"
---
# <a name="resync-command-property-dynamic-ado"></a>Resync Command – dynamische Eigenschaft (ADO)
Gibt an, ein benutzerdefinierten Befehl-Zeichenfolge, die [Resync](../../../ado/reference/ado-api/resync-method.md) Probleme der Methode zum Aktualisieren der Daten in der Tabelle, die mit dem Namen in der [eindeutige Tabelle](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) dynamische Eigenschaft.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **Zeichenfolge** Wert, der eine Befehlszeichenfolge ist.  
  
## <a name="remarks"></a>Hinweise  
 Die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt ist das Ergebnis einer JOIN-Operation, die auf mehrere Basistabellen ausgeführt. Abhängig von die betroffenen Zeilen die *AffectRecords* Parameter der [Resync](../../../ado/reference/ado-api/resync-method.md) Methode. Der Standard **Resync** Methode wird ausgeführt, wenn die [eindeutige Tabelle](../../../ado/reference/ado-api/unique-table-unique-schema-unique-catalog-properties-dynamic-ado.md) und **Resync Command** -Eigenschaft nicht festgelegt wurde.  
  
 Die Befehlszeichenfolge, die von der **Resync Command** Eigenschaft ist ein parametrisierter Befehl oder gespeicherte Prozedur, die die zu aktualisierende Zeile eindeutig identifiziert und gibt eine einzelne Zeile mit die gleiche Anzahl und Reihenfolge der Spalten der Zeile sein aktualisiert. Enthält die Befehlszeichenfolge einen Parameter für jede primäre Schlüsselspalte in der **eindeutige Tabelle**ist, andernfalls ein Laufzeitfehler wird zurückgegeben. Die Parameter werden mit Primärschlüsselwerten, die aus der Zeile aktualisiert werden automatisch ausgefüllt.  
  
 Hier sind zwei Beispiele, die basierend auf SQL aus:  
  
 1\) der **Recordset** wird durch einen Befehl definiert:  
  
```  
SELECT * FROM Customers JOIN Orders ON   
   Customers.CustomerID = Orders.CustomerID  
   WHERE city = 'Seattle'  
   ORDER BY CustomerID  
```  
  
 Die **Resync Command** Eigenschaft auf festgelegt ist:  
  
```  
"SELECT * FROM   
   (SELECT * FROM Customers JOIN Orders   
   ON Customers.CustomerID = Orders.CustomerID  
   city = 'Seattle' ORDER BY CustomerID)  
WHERE Orders.OrderID = ?"  
```  
  
 Die **eindeutige Tabelle** ist *Bestellungen* und der Primärschlüssel, *"OrderID"*, parametrisiert wird. Der untergeordneten Select bietet eine einfache Möglichkeit, programmgesteuert sicherstellen, dass die gleiche Anzahl und Reihenfolge der Spalten, wie Sie mit dem ursprünglichen Befehl zurückgegeben werden.  
  
 2\) der **Recordset** wird durch eine gespeicherte Prozedur definiert:  
  
```  
CREATE PROC Custorders @CustomerID char(5) AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID   
WHERE Customers.CustomerID = @CustomerID  
```  
  
 Die **Resync** Methode sollte die folgende gespeicherte Prozedur auszuführen:  
  
```  
CREATE PROC CustordersResync @ordid int AS   
SELECT * FROM Customers JOIN Orders ON   
Customers.CustomerID = Orders.CustomerID  
WHERE Orders.ordid  = @ordid  
```  
  
 Die **Resync Command** Eigenschaft auf festgelegt ist:  
  
```  
"{call CustordersResync (?)}"  
```  
  
 Auch hier die **eindeutige Tabelle** ist *Bestellungen* und der Primärschlüssel, *"OrderID"*, parametrisiert wird.  
  
 **Resync-Befehl** wird eine dynamische Eigenschaft angefügt der **Recordset** Objekt [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung bei der [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaftensatz auf **AdUseClient**.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
