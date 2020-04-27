---
title: Delete-Methode (ADO Fields-Auflistung) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Fields20::Delete
- Fields20::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 25bedc25-c51c-4cab-96ce-930b959965d9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9db49905b6548e5cb21cca976683c8b387017d32
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67919135"
---
# <a name="delete-method-ado-fields-collection"></a>Delete-Methode (ADO-Fields-Collection)
Löscht ein-Objekt aus der [Fields](../../../ado/reference/ado-api/fields-collection-ado.md) -Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Fields.Delete Field  
```  
  
#### <a name="parameters"></a>Parameter  
 *Feld*  
 Eine **Variante** , die das zu löschende [Feld](../../../ado/reference/ado-api/field-object.md) Objekt festlegt. Dieser Parameter kann der Name des **Feld** Objekts oder die Ordinalposition des **Feld** Objekts selbst sein.  
  
## <a name="remarks"></a>Hinweise  
 Das Aufrufen der **Fields. Delete** -Methode für ein geöffnetes [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) führt zu einem Laufzeitfehler.  
  
## <a name="applies-to"></a>Gilt für  
 [Fields-Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Delete-Methode (ADO Parameters-Sammlung)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete-Methode (ADO-Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord-Methode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
