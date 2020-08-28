---
description: Delete-Methode (ADO-Fields-Collection)
title: Delete-Methode (ADO Fields-Auflistung) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 11499e3483af13ce5fc9edea8fd69694d36be9c7
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974131"
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
  
## <a name="remarks"></a>Bemerkungen  
 Das Aufrufen der **Fields. Delete** -Methode für ein geöffnetes [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) führt zu einem Laufzeitfehler.  
  
## <a name="applies-to"></a>Gilt für  
 [Fields-Collection (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Delete-Methode (ADO Parameters-Sammlung)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete-Methode (ADO-Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord-Methode (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
