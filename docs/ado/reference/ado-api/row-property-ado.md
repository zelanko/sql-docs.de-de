---
title: Row-Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::PutRow
- ADORecordConstruction::GetRow
- ADORecordConstruction::get_Row
- ADORecordConstruction::Row
- ADORecordConstruction::put_Row
helpviewer_keywords:
- Row property [ADO]
ms.assetid: 21019d89-2dd1-4a26-ac6f-384b81d66949
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 041356f05daaaef50e6e81d995209ab5379fc901
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47747408"
---
# <a name="row-property-ado"></a>Row-Eigenschaft (ADO)
Ruft ab oder legt einen OLE DB **Zeile** Objekt aus, oder auf eine [ADORecordConstruction-Schnittstelle](../../../ado/reference/ado-api/adorecordconstruction-interface.md) Objekt. Bei Verwendung von **Put_Row** Festlegen einer **Zeile** Objekt, eine Zeile in eine ADO umgewandelt **Datensatz** Objekt.  
  
## <a name="readwritesyntax"></a>Lese-/Schreibzugriff. Die Syntax  
  
```  
HRESULT get_Row([out, retval] IUnknown** ppRow);  
HRESULT put_Row([in] IUnknown* pRow);  
```  
  
## <a name="parameters"></a>Parameter  
 *ppRow*  
 Zeiger auf eine OLE DB **Zeile** Objekt.  
  
 *pRow*  
 OLE DB **Zeile** Objekt.  
  
## <a name="return-values"></a>Rückgabewerte  
 Diese Eigenschaftsmethode gibt die standardmäßige HRESULT-Werte, einschließlich S_OK zurück, und E_FAIL zurück.  
  
## <a name="applies-to"></a>Gilt für  
 [ADORecordConstruction-Schnittstelle](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
