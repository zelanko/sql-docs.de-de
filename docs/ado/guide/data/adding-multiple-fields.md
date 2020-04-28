---
title: Hinzufügen mehrerer Felder | Microsoft-Dokumentation
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
- editing data [ADO], adding multiple fields
- editing data [ADO], AddNew method
ms.assetid: f3648ef4-9f36-4991-a868-83a617389844
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 07a1a3723b4169872c1b8aa872457e67a60d1f71
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926275"
---
# <a name="adding-multiple-fields-and-values"></a>Hinzufügen mehrerer Felder und Werte
Gelegentlich ist es möglicherweise effizienter, ein Array von Feldern und ihre entsprechenden Werte an die **AddNew** -Methode zu übergeben, anstatt für jedes neue Feld einen **Wert** mehrmals festzulegen. Wenn *FieldList* ein Array ist, müssen die *Werte* auch ein Array mit derselben Anzahl von Membern sein. Andernfalls tritt ein Fehler auf. Die Reihenfolge der Feldnamen muss der Reihenfolge der Feldwerte in jedem Array entsprechen. Der folgende Code übergibt ein Array von Feldern und ein Array von Werten an die **AddNew** -Methode.

```
'BeginAddNew2
    Dim avarFldNames As Variant
    Dim avarFldValues As Variant

    avarFldNames = Array("CompanyName", "Phone")
    avarFldValues = Array("Sample Shipper 2", "(931) 555-6334")

    If objRs1.Supports(adAddNew) Then
        objRs1.AddNew avarFldNames, avarFldValues
    End If

    'Re-establish a Connection and update
    Set objRs1.ActiveConnection = GetNewConnection
    objRs1.UpdateBatch
'EndAddNew2
```
