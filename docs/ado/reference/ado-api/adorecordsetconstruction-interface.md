---
description: ADORecordsetConstruction-Schnittstelle
title: Adorecordsetconstruction-Schnittstelle | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordsetConstruction
helpviewer_keywords:
- ADORecordsetConstruction interface [ADO]
ms.assetid: 08386eba-f1f7-4879-8ffd-8733930ecb2f
author: rothja
ms.author: jroth
ms.openlocfilehash: c17ccfe0a31714d5e2b3945960a4ff3d2ad55d1e
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776639"
---
# <a name="adorecordsetconstruction-interface"></a>ADORecordsetConstruction-Schnittstelle
Die **adorecordsetconstruction** -Schnittstelle wird verwendet, um ein ADO- **Recordset** -Objekt aus einem OLE DB Rowsetobjekt in einer C/C++-Anwendung zu erstellen. **Rowset**  
  
 Diese Schnittstelle unterstützt die folgenden Eigenschaften:  
  
## <a name="properties"></a>Eigenschaften  
  
|Eigenschaft|Beschreibung|  
|-|-|  
|[Kapitel](./chapter-property-ado.md)|Lesen/Schreiben<br />Ruft ein OLE DB **Kapitel** Objekt aus/für dieses ADO- **Recordset** -Objekt ab oder legt es fest.|  
|[RowPosition](./rowposition-property-ado.md)|Lesen/Schreiben<br />Ruft ein OLE DB **RowPosition** -Objekt von/für dieses ADO- **Recordset** -Objekt ab oder legt es fest.|  
|[Rowset](./rowset-property-ado.md)|Lesen/Schreiben<br />Ruft ein OLE DB Rowsetobjekt aus/für dieses ADO- **Recordset** -Objekt ab oder legt dieses **fest** .|  
  
## <a name="methods"></a>Methoden  
 Keine.  
  
## <a name="events"></a>Events  
 Keine.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein OLE DB **Rowset** Rowsetobjekt ( `pRowset` ) angegeben wird, wird die Erstellung eines ADO- **Recordset** -Objekts ( `adoRs` ) auf die folgenden drei grundlegenden Vorgänge festgelegt:  
  
1.  Erstellen Sie ein ADO- **Recordset** -Objekt:  
  
    ```  
    Recordset20Ptr adoRs;  
    adoRs.CreateInstance(__uuidof(Recordset));  
    ```  
  
2.  Abfragen der **IADORecordsetConstruction** -Schnittstelle für das **Recordset** -Objekt:  
  
    ```  
    adoRecordsetConstructionPtr adoRsConstruct=NULL;  
    adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),  
                         (void**)&adoRsConstruct);  
    ```  
  
3.  Mit der- `IADORecordsetConstruction::put_Rowset` Eigenschaft können Sie das OLE DB- `Rowset` Objekt für das ADO- `Recordset` Objekt festlegen:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 Das resultierende `adoRs` Objekt stellt nun das ADO- **Recordset** -Objekt dar, das aus dem OLE DB Rowsetobjekt erstellt **wurde**  
  
 Sie können auch ein ADO- **Recordset** -Objekt aus einem OLE DB **Kapitel** oder einem **RowPosition** -Objekt erstellen.  
  
## <a name="requirements"></a>Anforderungen  
 **Version:** ADO 2,0 und höher  
  
 **Bibliothek:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>Weitere Informationen  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)   
 [Rowset-Eigenschaft (ADO)](./rowset-property-ado.md)