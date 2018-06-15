---
title: Der ParentRow-Eigenschaft (ADO) | Microsoft Docs
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
- ADORecordConstruction::put_ParentRow
- ADORecordConstruction::ParentRow
- ADORecordConstruction::putParentRow
helpviewer_keywords:
- ParentRow property [ADO]
ms.assetid: 5ea8029b-eda4-490b-ae84-2ad036fb582f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 86122a7cb075816809dd8868c1db94adf1b81612
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2018
ms.locfileid: "35280559"
---
# <a name="parentrow-property-ado"></a>Der ParentRow-Eigenschaft (ADO)
Legt den Container eines OLE DB- **Zeile** -Objekt, auf ein **ADORecordConstruction** Objekt, sodass das übergeordnete Element der Zeile, in eine ADO aktiviert ist **Datensatz** Objekt.  
  
 Nur Schreibzugriff.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT put_ParentRow([in] IUnknown* pParent);  
```  
  
## <a name="parameters"></a>Parameter  
 *pParent*  
 Ein Container einer Zeile.  
  
## <a name="return-values"></a>Rückgabewerte  
 Diese Eigenschaftsmethode gibt die standardmäßige HRESULT-Werte, einschließlich S_OK und E_FAIL zurück.  
  
## <a name="applies-to"></a>Gilt für  
 [ADORecordConstruction-Schnittstelle](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
