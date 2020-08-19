---
description: GetChildren-Methode (ADO)
title: GetChildren-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
author: rothja
ms.author: jroth
ms.openlocfilehash: 906c20d19143f4f1e8fe0b6c1e91585893acfa5d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88443582"
---
# <a name="getchildren-method-ado"></a>GetChildren-Methode (ADO)
Gibt ein [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) zurück, dessen Zeilen die untergeordneten Elemente eines Sammlungs [Datensatzes](../../../ado/reference/ado-api/record-object-ado.md)darstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **Recordset** -Objekt, für das jede Zeile ein untergeordnetes Element des aktuellen **Daten Satz** Objekts darstellt. Die untergeordneten Elemente eines **Datensatzes** , der ein Verzeichnis darstellt, sind z. b. die Dateien und Unterverzeichnisse, die im übergeordneten Verzeichnis enthalten sind.  
  
## <a name="remarks"></a>Bemerkungen  
 Der Anbieter bestimmt, welche Spalten im zurückgegebenen **Recordset**vorhanden sind. Beispielsweise gibt ein Dokument Quellen Anbieter immer ein Ressourcen- **Recordset**zurück.  
  
## <a name="applies-to"></a>Gilt für  

:::row:::
    :::column:::
        [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
    :::column-end:::
    :::column:::
        [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
    :::column-end:::
:::row-end:::
