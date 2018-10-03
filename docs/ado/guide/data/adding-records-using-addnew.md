---
title: Hinzufügen von Datensätzen mit AddNew | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- AddNew method [ADO]
- ADO, adding data
- editing data [ADO], AddNew method
ms.assetid: cab4adff-f22f-4fb1-9217-f8138c795268
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 68b1a34a5d23d9aab32b6216eda3b3ef8f977e79
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47819524"
---
# <a name="adding-records-using-addnew-method"></a>Hinzufügen von Datensätzen mit der AddNew-Methode
Dies ist die grundlegende Syntax von der **AddNew** Methode:

 *Recordset*. AddNew *FieldList*, *Werte*

 Die *FieldList* und *Werte* Argumente sind optional. *Feldliste* ist entweder ein einzelner Name oder ein Array von Namen oder die Ordnungspositionen der Felder im neuen Datensatz.

 Die *Werte* Argument ist entweder einen einzelnen Wert oder ein Array von Werten für die Felder im neuen Datensatz.

 In der Regel, wenn Sie beabsichtigen, einen einzelnen Datensatz hinzuzufügen, rufen Sie die **AddNew** -Methode ohne Argumente. Rufen Sie insbesondere **AddNew**; Set der **Wert** jedes Feld im neuen Datensatz; und rufen dann **Update** oder **UpdateBatch**, oder beide. Sie können sicherstellen, dass Ihre **Recordset** unterstützt das Hinzufügen von neuen Datensätzen mithilfe der **unterstützt** Eigenschaft mit dem die **AdAddNew** Enumerationskonstante.

 Der folgende Code verwendet diese Technik des Beispiels ein neues Versandunternehmen hinzuzufügende **Recordset**. Den Wert des Felds Firmen-Nr wird automatisch von SQL Server bereitgestellt. Aus diesem Grund versucht der Code nicht, einen Feldwert für die neuen Datensätze angeben.

```
'BeginAddNew1.1
If objRs.Supports(adAddNew) Then
    With objRs
        .AddNew
        .Fields("CompanyName") = "Sample Shipper"
        .Fields("Phone") = "(931) 555-6334"
        .Update
    End With
End If
'EndAddNew1.1
```

## <a name="remarks"></a>Hinweise
 Da dieser Code verwendet, das einem nicht verbundenen **Recordset** mit einem clientseitigen Cursor im Batchmodus, verbinden Sie die **Recordset** an die Datenquelle mit einem neuen **Verbindung** Objekt, bevor Sie aufrufen können, die **UpdateBatch** Methode, um Änderungen an der Datenbank veröffentlichen. Dies erfolgt einfach mithilfe der neuen Funktion **GetNewConnection**.
