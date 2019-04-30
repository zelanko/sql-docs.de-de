---
title: Delete-Methode (Fields-Collection – ADO) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 097286f14de4dead4490c322615a6405c157f118
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140253"
---
# <a name="delete-method-ado-fields-collection"></a>Delete-Methode (ADO-Fields-Collection)
Löscht ein Objekt aus der [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Fields.Delete Field  
```  
  
#### <a name="parameters"></a>Parameter  
 *Feld*  
 Ein **Variant** bestimmt, die [Feld](../../../ado/reference/ado-api/field-object.md) zu löschenden Objekts. Dieser Parameter kann den Namen des sein der **Feld** Objekt bzw. die Ordnungsposition des der **Feld** Objekt selbst.  
  
## <a name="remarks"></a>Hinweise  
 Aufrufen der **Fields.Delete** Methode auf einem geöffneten [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) verursacht einen Laufzeitfehler.  
  
## <a name="applies-to"></a>Gilt für  
 [Fields-Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Delete-Methode (ADO-Parameters-Auflistung)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete-Methode (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord-Methode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
