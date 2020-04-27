---
title: Para Row-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::put_ParentRow
- ADORecordConstruction::ParentRow
- ADORecordConstruction::putParentRow
helpviewer_keywords:
- ParentRow property [ADO]
ms.assetid: 5ea8029b-eda4-490b-ae84-2ad036fb582f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a81eb6ee58d942547a159728b9c3edf9a30f1ece
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "67917671"
---
# <a name="parentrow-property-ado"></a>ParentRow-Eigenschaft (ADO)
Legt den Container eines OLE DB **Row** -Objekts für ein **adorecordconstruction** -Objekt fest, damit das übergeordnete Element der Zeile in ein ADO- **Daten Satz** Objekt umgewandelt wird.  
  
 Nur Schreibzugriff.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT put_ParentRow([in] IUnknown* pParent);  
```  
  
## <a name="parameters"></a>Parameter  
 *pparent*  
 Ein Container einer Zeile.  
  
## <a name="return-values"></a>Rückgabewerte  
 Diese Eigenschaften Methode gibt die HRESULT-Standardwerte zurück, einschließlich S_OK und E_FAIL.  
  
## <a name="applies-to"></a>Gilt für  
 [ADORecordConstruction-Schnittstelle](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
