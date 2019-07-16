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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932507"
---
# <a name="getchildren-method-ado"></a>GetChildren-Methode (ADO)
Gibt eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) , deren Zeilen darstellt, die untergeordneten Elemente einer Auflistung [Datensatz](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **Recordset** für die jede Zeile steht für ein untergeordnetes Element des aktuellen Objekts **Datensatz** Objekt. Z. B. die untergeordneten Elemente ein **Datensatz** stellt ein Verzeichnis die Dateien und Unterverzeichnisse innerhalb des übergeordneten Verzeichnisses enthalten wäre.  
  
## <a name="remarks"></a>Hinweise  
 Der Anbieter bestimmt, welche Spalten vorhanden sind, in der zurückgegebenen **Recordset**. Ein Anbieter gibt z. B. immer eine Ressource **Recordset**.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
