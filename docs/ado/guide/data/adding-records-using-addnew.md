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
ms.openlocfilehash: 36f6bad9a8f0d74a81d02ce64c78d7a91ddc0fa8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926281"
---
# <a name="adding-records-using-addnew-method"></a>Hinzufügen von Datensätzen mithilfe der AddNew-Methode
Dies ist die grundlegende Syntax der **AddNew** -Methode:

 *Recordset*. AddNew *FieldList*, *Werte*

 Die Argumente *FieldList* und *Values* sind optional. *FieldList* ist entweder ein einzelner Name oder ein Array von Namen oder Ordinalpositionen der Felder im neuen Datensatz.

 Das *Values* -Argument ist entweder ein einzelner Wert oder ein Array von Werten für die Felder im neuen Datensatz.

 Wenn Sie einen einzelnen Datensatz hinzufügen möchten, wird in der Regel die **AddNew** -Methode ohne Argumente aufgerufen. Insbesondere wird **AddNew**; aufgerufen. Legen Sie den **Wert** jedes Felds im neuen Datensatz fest. und dann " **Update** " oder " **UpdateBatch**" oder beides aufrufen. Sie können sicherstellen, dass Ihr **Recordset** das Hinzufügen von neuen Datensätzen unterstützt, indem Sie die **unterstützte** Eigenschaft mit der **adAddNew** -Enumerationskonstante

 Der folgende Code verwendet dieses Verfahren zum Hinzufügen eines neuen Shippers zum **Recordset**-Beispiel. SQL Server stellt den Wert für das ShipperID-Feld automatisch bereit. Aus diesem Grund versucht der Code nicht, einen Feldwert für die neuen Datensätze bereitzustellen.

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

## <a name="remarks"></a>Bemerkungen
 Da in diesem Code ein nicht verbundenes **Recordset** mit einem Client seitigen Cursor im Batch Modus verwendet wird, müssen Sie das **Recordset** erneut mit der Datenquelle mit einem neuen **Verbindungs** Objekt verbinden, bevor Sie die **UpdateBatch** -Methode aufrufen können, um Änderungen an der Datenbank zu veröffentlichen. Dies kann problemlos mithilfe der neuen Funktion **getNewConnection**erreicht werden.
