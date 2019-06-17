---
title: Hierarchische Recordsets Erfahrung | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Recordset fabrication [ADO]
- hierarchical Recordsets [ADO]
- fabricating hierarchical Recordsets [ADO]
- data shaping [ADO], hierarchical Recordsets
ms.assetid: a584e642-a4a3-418e-bc20-3aff81a5625a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a5dc84c5bacca8951576e572b90fa28a8408e48d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700726"
---
# <a name="fabricating-hierarchical-recordsets"></a>Herstellen hierarchischer Recordsets
Das folgende Beispiel zeigt, wie Sie ein hierarchisches Recordset ohne die zugrunde liegenden Datenquelle zu erstellen, mit die Grammatik, die zum Definieren von Spalten für die übergeordneten und untergeordneten "Enkel" für die datenstrukturierung **Recordsets**.  
  
 Um eine hierarchische erstellt **Recordset**, müssen Sie angeben der [Microsoft Data Shaping Service für OLE DB (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) (MSDataShape), und Sie können angeben, einen Datenanbieter-Wert ' None ' in der der Parameter der Verbindungszeichenfolge der [öffnen](../../../ado/reference/ado-api/open-method-ado-connection.md) -Methode der der [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt. Weitere Informationen finden Sie unter [erforderliche Anbieter für die Datenstrukturierung](../../../ado/guide/data/required-providers-for-data-shaping.md).  
  
```  
Dim cn As New ADODB.Connection  
Dim rsCustomers As New ADODB.Recordset  
  
cn.Open "Provider=MSDataShape;Data Provider=NONE;"  
  
strShape = _  
"SHAPE APPEND NEW adInteger AS CustID," & _  
            " NEW adChar(25) AS FirstName," & _  
            " NEW adChar(25) AS LastName," & _  
            " NEW adChar(12) AS SSN," & _  
            " NEW adChar(50) AS Address," & _  
         " ((SHAPE APPEND NEW adChar(80) AS VIN_NO," & _  
                        " NEW adInteger AS CustID," & _  
                        " NEW adChar(20) AS BodyColor, " & _  
                     " ((SHAPE APPEND NEW adChar(80) AS VIN_NO," & _  
                                    " NEW adChar(20) AS Make, " & _  
                                    " NEW adChar(20) AS Model," & _  
                                    " NEW adChar(4) AS Year) " & _  
                        " AS VINS RELATE VIN_NO TO VIN_NO))" & _  
            " AS Vehicles RELATE CustID TO CustID) "  
  
rsCustomers.Open strShape, cn, adOpenStatic, adLockOptimistic, -1  
```  
  
 Sobald die **Recordset** wurde erstellt, es kann sein aufgefüllt, bearbeitet oder in einer Datei gespeichert.  
  
## <a name="see-also"></a>Siehe auch  
 [Zugreifen auf Zeilen in einem hierarchischen Recordset](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [Formale Grammatik für Formen](../../../ado/guide/data/formal-shape-grammar.md)   
 [Erforderliche Anbieter für die Strukturierung der Daten](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [Shape APPEND-Klausel](../../../ado/guide/data/shape-append-clause.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)
