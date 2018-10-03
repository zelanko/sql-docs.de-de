---
title: ADORecordsetConstruction-Schnittstelle | Microsoft-Dokumentation
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 078b48c36d0ee2a1b3f368b8e6baf7346ed343fa
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634388"
---
# <a name="adorecordsetconstruction-interface"></a>ADORecordsetConstruction-Schnittstelle
Die **ADORecordsetConstruction** Schnittstelle wird verwendet, um eine ADO erstellen **Recordset** Objekt von einem OLE DB **Rowset** Objekts in einer C/C++-Anwendung.  
  
 Diese Schnittstelle unterstützt die folgenden Eigenschaften:  
  
## <a name="properties"></a>Eigenschaften  
  
|||  
|-|-|  
|[Kapitel](../../../ado/reference/ado-api/chapter-property-ado.md)|Lese-/Schreibzugriff.<br />Ruft ab oder legt ihn fest, eine OLE DB **Kapitel** Objekt aus bzw. in dieser ADO **Recordset** Objekt.|  
|[RowPosition](../../../ado/reference/ado-api/rowposition-property-ado.md)|Lese-/Schreibzugriff.<br />Ruft ab oder legt ihn fest, eine OLE DB **RowPosition** Objekt aus bzw. in dieser ADO **Recordset** Objekt.|  
|[Rowset](../../../ado/reference/ado-api/rowset-property-ado.md)|Lese-/Schreibzugriff.<br />Ruft ab oder legt ihn fest, eine OLE DB **Rowset** Objekt aus bzw. in dieser ADO **Recordset** Objekt.|  
  
## <a name="methods"></a>Methoden  
 Keine.  
  
## <a name="events"></a>Ereignisse  
 Keine.  
  
## <a name="remarks"></a>Hinweise  
 Erhalten eine OLE DB **Rowset** Objekt (`pRowset`), die zur Erstellung eines ADO **Recordset** Objekt (`adoRs`) die folgenden drei grundlegenden Schritten:  
  
1.  Erstellen Sie ein ADO **Recordset** Objekt:  
  
    ```  
    Recordset20Ptr adoRs;  
    adoRs.CreateInstance(__uuidof(Recordset));  
    ```  
  
2.  Abfrage der **IADORecordsetConstruction** Schnittstelle, für die **Recordset** Objekt:  
  
    ```  
    adoRecordsetConstructionPtr adoRsConstruct=NULL;  
    adoRs->QueryInterface(__uuidof(ADORecordsetConstruction),  
                         (void**)&adoRsConstruct);  
    ```  
  
3.  Rufen Sie die `IADORecordsetConstruction::put_Rowset` -Methode zum Festlegen von OLE DB-Eigenschaft `Rowset` der ADO-Objekt `Recordset` Objekt:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRsConstruct->put_Rowset(pUnk);  
    ```  
  
 Die resultierenden `adoRs` Objekt stellt nun das ADO **Recordset** Objekt erstellt, die von der OLE DB **Rowset** Objekt.  
  
 Sie können auch ein ADO erstellen **Recordset** Objekt von einem OLE DB **Kapitel** oder **RowPosition** Objekt.  
  
## <a name="requirements"></a>Anforderungen  
 **Version:** ADO 2.0 und höher  
  
 **Bibliothek:** "MSADO15.dll"  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>Siehe auch  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Rowset-Eigenschaft (ADO)](../../../ado/reference/ado-api/rowset-property-ado.md)
