---
title: RowPosition-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::put_RowPosition
- ADORecordConstruction::PutRowPosition
- ADORecordConstruction::GetRowPosition
- ADORecordConstruction::RowPosition
- ADORecordConstruction::get_RowPosition
helpviewer_keywords:
- RowPosition property [ADO]
ms.assetid: 9d068fed-39bf-4842-afc3-686a2af2145d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e2e8bab73bfe93e8a78e013572a376b608ca9a3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63180613"
---
# <a name="rowposition-property-ado"></a>RowPosition-Eigenschaft (ADO)
Ruft ab oder legt einen OLE DB **RowPosition** Objekt aus, bzw. auf eine **ADORecordsetConstruction** Objekt. Bei Verwendung von **Put_RowPosition** Festlegen der **RowPosition** -Objekt, das resultierende **Recordset** -Objekt verwendet die **RowPosition** -Objekt Bestimmen der aktuellen Zeile.  
  
 Lese-/Schreibzugriff.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT get_RowPosition([out, retval] IUnknown** ppRowPos);  
HRESULT put_RowPosition([in] IUnknown* pRowPos);  
```  
  
## <a name="parameters"></a>Parameter  
 *ppRowPos*  
 Zeiger auf eine OLE DB **RowPosition** Objekt.  
  
 *PRowPos*  
 OLE DB **RowPosition** Objekt.  
  
## <a name="return-values"></a>Rückgabewerte  
 Diese Eigenschaftsmethode gibt die standardmäßige HRESULT-Werte, einschließlich S_OK zurück, und E_FAIL zurück.  
  
## <a name="remarks"></a>Hinweise  
 Wenn diese Eigenschaft festgelegt ist, wenn die **Rowset** -Objekt die **RowPosition** Objekt unterscheidet sich von der **Rowset** -Objekt die **Recordset**Objekt ist, wird die erste der letzteren überschreibt. Das gleiche Verhalten trifft auf den aktuellen **Kapitel** von der **RowPosition** ebenfalls.  
  
## <a name="applies-to"></a>Gilt für  
 [ADORecordsetConstruction-Schnittstelle](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
