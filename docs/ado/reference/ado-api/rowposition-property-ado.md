---
description: RowPosition-Eigenschaft (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0f5f78843e38c2a3ff6b21c90bc9ed7f2c573ee4
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777609"
---
# <a name="rowposition-property-ado"></a>RowPosition-Eigenschaft (ADO)
Ruft ein OLE DB **RowPosition** -Objekt von/in einem **adorecordsetconstruction** -Objekt ab oder legt es fest. Wenn Sie **put_RowPosition** verwenden, um das **RowPosition** -Objekt festzulegen, verwendet das resultierende **Recordset** -Objekt das **RowPosition** -Objekt, um die aktuelle Zeile zu bestimmen.  
  
 Lese-/Schreibzugriff.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT get_RowPosition([out, retval] IUnknown** ppRowPos);  
HRESULT put_RowPosition([in] IUnknown* pRowPos);  
```  
  
## <a name="parameters"></a>Parameter  
 *pprowpos*  
 Zeiger auf ein OLE DB **RowPosition** -Objekt.  
  
 *Prowpos*  
 Ein OLE DB **RowPosition** -Objekt.  
  
## <a name="return-values"></a>Rückgabewerte  
 Diese Eigenschaften Methode gibt die HRESULT-Standardwerte zurück, einschließlich S_OK und E_FAIL.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn diese Eigenschaft festgelegt ist und sich **Rowset** das Rowsetobjekt für das **RowPosition** -Objekt vom Rowsetobjekt des **Recordset** -Objekts unterscheidet, überschreibt das erste das zweite. **Rowset** Das gleiche Verhalten gilt auch für das aktuelle **Kapitel** der **RowPosition** .  
  
## <a name="applies-to"></a>Gilt für  
 [ADORecordsetConstruction-Schnittstelle](./adorecordsetconstruction-interface.md)