---
title: Anbieter für die Strukturierung der Daten erforderlichen | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], data shaping
- data shaping [ADO], providers required
ms.assetid: d49d48d2-ac2d-4c11-895c-5a149b444620
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 482139f8aa3dc42bbd17593b58fcc8510f1fc9a8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47713838"
---
# <a name="required-providers-for-data-shaping"></a>Erforderliche Anbieter für die Datenstrukturierung
Strukturieren von Daten erfordert in der Regel zwei Anbieter. Der Dienstanbieter [Data Shaping Service für OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), der die Daten strukturieren, Funktionalität und einen Datenanbieter, wie z. B. der OLE DB-Anbieter für SQL Server bereitstellt, Zeilen mit Daten zum Auffüllen des geformten [Recordset ](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
 Der Name des Dienstanbieters (MSDataShape) kann angegeben werden, als Wert für die [Verbindung](../../../ado/reference/ado-api/connection-object-ado.md) Objekt [Anbieter](../../../ado/reference/ado-api/provider-property-ado.md) Eigenschaft oder das-Schlüsselwort der Verbindungszeichenfolge "Provider = MSDataShape;".  
  
 Der Name des Datenanbieters kann angegeben werden, als Wert für die **Datenanbieter** dynamische Eigenschaft, die hinzugefügt wird die **Verbindung** Objekt [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Sammlung der Data Shaping Service für OLE DB oder das-Schlüsselwort der Verbindungszeichenfolge "**Datenanbieter = *** Anbieter*".  
  
 Kein Datenanbieter ist erforderlich, wenn die **Recordset** nicht aufgefüllt wurde (z. B. wie eine erstellte **Recordset** , in Spalten mit dem neuen Schlüsselwort erstellt werden). Geben Sie in diesem Fall "**Datenanbieter =** none;".  
  
## <a name="example"></a>Beispiel  
  
```  
Dim cnn As New ADODB.Connection  
cnn.Provider = "MSDataShape"  
cnn.Open "Data Provider=SQLOLEDB;Integrated Security=SSPI;Database=Northwind"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiel für die datenstrukturierung](../../../ado/guide/data/data-shaping-example.md)   
 [Formale Grammatik für Formen](../../../ado/guide/data/formal-shape-grammar.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)
