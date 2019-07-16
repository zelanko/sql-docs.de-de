---
title: ADORecordConstruction-Schnittstelle | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction
helpviewer_keywords:
- ADORecordConstruction interface [ADO]
ms.assetid: 52a5429e-5829-455e-be3b-31f05cbecf2d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c56ba0b9d7ebebbf4a9e4baf669bbdc6eb84355e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67920807"
---
# <a name="adorecordconstruction-interface"></a>ADORecordConstruction-Schnittstelle
Die **ADORecordConstruction**Schnittstelle wird verwendet, um eine ADO erstellen **Datensatz** Objekt von einem OLE DB **Zeile** Objekts in einer C/C++-Anwendung.  
  
 Diese Schnittstelle unterstützt die folgenden Eigenschaften:  
  
## <a name="properties"></a>Eigenschaften  
  
|||  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|Nur Schreibzugriff.<br />Legt den Container eines OLE DB **Zeile** dieser ADO-Objekt **Datensatz** Objekt.|  
|[Zeile](../../../ado/reference/ado-api/row-property-ado.md)|Lese-/Schreibzugriff.<br />Ruft ab oder legt ihn fest, eine OLE DB **Zeile** Objekt aus bzw. in dieser ADO **Datensatz** Objekt.|  
  
## <a name="methods"></a>Methoden  
 Keine  
  
## <a name="events"></a>Ereignisse  
 Keine  
  
## <a name="remarks"></a>Hinweise  
 Erhalten eine OLE DB **Zeile** Objekt (`pRow`), die zur Erstellung eines ADO **Datensatz** Objekt (`adoR`), die folgenden drei grundlegenden Schritten:  
  
1.  Erstellen Sie ein ADO **Datensatz** Objekt:  
  
    ```  
    _RecordPtr adoR;  
    adoRs.CreateInstance(__uuidof(_Record));  
    ```  
  
2.  Abfrage der **IADORecordConstruction** Schnittstelle, für die **Datensatz** Objekt:  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  Rufen Sie die **IADORecordConstruction::put_Row** -Methode zum Festlegen von OLE DB-Eigenschaft **Zeile** der ADO-Objekt **Datensatz** Objekt:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 Die resultierenden **AdoR** Objekt stellt nun das ADO **Datensatz** Objekt erstellt, die von der OLE DB **Zeile** Objekt.  
  
 Ein ADO **Datensatz** Objekt kann auch erstellt werden, aus dem Container des OLE DB **Zeile** Objekt.  
  
## <a name="requirements"></a>Anforderungen  
 **Version:** ADO, 2.0 und höher  
  
 **Bibliothek:** "MSADO15.dll"  
  
 **UUID:** 00000567-0000-0010-8000-00AA006D2EA4
