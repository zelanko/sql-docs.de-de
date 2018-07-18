---
title: GetChildren-Methode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a920d0e7b45394f5714cd8f9df83751a322b9401
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35278849"
---
# <a name="getchildren-method-ado"></a>GetChildren-Methode (ADO)
Gibt eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) , deren Zeilen darstellen, die untergeordneten Elemente einer Auflistung [Datensatz](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Ein **Recordset** für die jede Zeile steht für ein untergeordnetes Element des aktuellen Objekts **Datensatz** Objekt. Angenommen, die untergeordneten Elemente des eine **Datensatz** stellt ein Verzeichnis die Dateien und Unterverzeichnisse innerhalb des übergeordneten Verzeichnisses enthalten wäre.  
  
## <a name="remarks"></a>Hinweise  
 Der Anbieter bestimmt, welche Spalten im zurückgegebenen vorhanden **Recordset**. Ein Anbieter gibt z. B. immer eine Ressource **Recordset**.  
  
## <a name="applies-to"></a>Gilt für  
  
|||  
|-|-|  
|[Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
