---
title: Adorecordconstruction-Schnittstelle | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4dca796e9ba3c353d48fd3620c34a141c35a3fe8
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242830"
---
# <a name="adorecordconstruction-interface"></a>ADORecordConstruction-Schnittstelle
Die **adorecordconstruction**-Schnittstelle wird verwendet, um ein ADO- **Datensatz** -Objekt aus einem OLE DB **Row** -Objekt in einer C/C++-Anwendung zu erstellen.  
  
 Diese Schnittstelle unterstützt die folgenden Eigenschaften:  
  
## <a name="properties"></a>Eigenschaften  
  
|Eigenschaft|BESCHREIBUNG|  
|-|-|  
|[ParentRow](../../../ado/reference/ado-api/parentrow-property-ado.md)|Nur Schreibzugriff.<br />Legt den Container eines OLE DB **Row** -Objekts für dieses ADO- **Daten Satz** Objekt fest.|  
|[Zeile](../../../ado/reference/ado-api/row-property-ado.md)|Lesen/Schreiben<br />Ruft ein OLE DB **Zeilen** Objekt aus/für dieses ADO- **Daten Satz** Objekt ab oder legt es fest.|  
  
## <a name="methods"></a>Methoden  
 Keine.  
  
## <a name="events"></a>Events  
 Keine.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein OLE DB **Row** -Objekt ( `pRow` ) angegeben wird, wird die Erstellung eines ADO- **Daten Satz** Objekts ( `adoR` ) auf die folgenden drei grundlegenden Vorgänge festgestellt:  
  
1.  Erstellen Sie ein ADO- **Datensatz** -Objekt:  
  
    ```  
    _RecordPtr adoR;  
    adoRs.CreateInstance(__uuidof(_Record));  
    ```  
  
2.  Abfragen der **iadorecordconstruction** -Schnittstelle für das **Datensatz** -Objekt:  
  
    ```  
    adoRecordConstructionPtr adoRConstruct=NULL;  
    adoR->QueryInterface(__uuidof(ADORecordConstruction),  
                        (void**)&adoRConstruct);  
    ```  
  
3.  Wenden Sie die Methode **iadorecordconstruction::p ut_Row** Property an, um das OLE DB **Row** -Objekt für das ADO- **Daten** Satz Objekt festzulegen:  
  
    ```  
    IUnknown *pUnk=NULL;  
    pRow->QueryInterface(IID_IUnknown, (void**)&pUnk);  
    adoRConstruct->put_Row(pUnk);  
    ```  
  
 Das resultierende **adoR** -Objekt stellt nun das ADO- **Daten Satz** Objekt dar, das vom OLE DB **Row** -Objekt erstellt wurde.  
  
 Ein ADO- **Datensatz** -Objekt kann auch aus dem Container eines OLE DB **Row** -Objekts erstellt werden.  
  
## <a name="requirements"></a>Anforderungen  
 **Version:** ADO 2,0 und höher  
  
 **Bibliothek:** msado15.dll  
  
 **UUID:** 00000567-0000-0010-8000-00AA006D2EA4
