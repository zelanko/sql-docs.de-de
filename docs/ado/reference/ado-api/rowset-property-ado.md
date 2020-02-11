---
title: Rowset-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction::PutRowset
- ADORecordsetConstruction::GetRowset
- ADORecordsetConstruction::Rowset
- ADORecordsetConstruction::put_Rowset
- ADORecordsetConstruction::get_Rowset
helpviewer_keywords:
- Rowset property [ADO]
ms.assetid: 7d359294-4ff2-47e0-8111-0c221b24d80e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 922f6690679d86bdb6cdafb721e3a5ed6bb674ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67917124"
---
# <a name="rowset-property-ado"></a>Rowset-Eigenschaft (ADO)
Ruft ein OLE DB Rowsetobjekt aus/in einem **adorecordsetconstruction** -Objekt ab oder legt dieses **fest** . Wenn Sie put_Rowset verwenden, wird das Rowset in ein ADO- **Recordset** -Objekt umgewandelt.  
  
 Lese-/Schreibzugriff.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT get_Rowset([out, retval] IUnknown** ppRowset);  
HRESULT put_Rowset([in] IUnknown* pRowset);  
```  
  
## <a name="parameters"></a>Parameter  
 *ppRowset*  
 Zeiger auf ein OLE DB **** Rowsetobjekt.  
  
 *Prowset*  
 Ein OLE DB **** Rowsetobjekt.  
  
## <a name="return-values"></a>Rückgabewerte  
 Diese Eigenschaften Methode gibt die HRESULT-Standardwerte zurück, einschließlich S_OK und E_FAIL.  
  
## <a name="applies-to"></a>Gilt für  
 [ADORecordsetConstruction-Schnittstelle](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
