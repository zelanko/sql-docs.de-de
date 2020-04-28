---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 84f1a2f7a80e17571f1b8ad3e63db640fb58dc19
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67932507"
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
  
|||  
|-|-|  
|[Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
