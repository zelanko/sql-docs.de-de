---
description: ADOStreamConstruction-Schnittstelle
title: Adostreamconstruction-Schnittstelle | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADOStreamConstruction
helpviewer_keywords:
- ADOStreamConstruction interface [ADO]
ms.assetid: 92f5a939-3e1a-4b14-a9dd-90e6ce2dec74
author: rothja
ms.author: jroth
ms.openlocfilehash: 144965d31dbb11da6cbc9a3ee6b23cd79cda800e
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88776629"
---
# <a name="adostreamconstruction-interface"></a>ADOStreamConstruction-Schnittstelle
Die **adostreamconstruction** -Schnittstelle wird verwendet, um **ein ADO-Streamobjekt** aus einem OLE DB **IStream** -Objekt in einer C/C++-Anwendung zu erstellen.  
  
## <a name="properties"></a>Eigenschaften  
  
|Eigenschaft|Beschreibung|  
|-|-|  
|[Stream](./stream-property.md)|Lesen/Schreiben Ruft ein OLE DB **Stream** -Objekt ab oder legt es fest.|  
  
## <a name="methods"></a>Methoden  
 Keine.  
  
## <a name="events"></a>Events  
 Keine.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn ein OLE DB **IStream** -Objekt ( `pStream` ) angegeben wird, ist die Erstellung eines ADO- **Streamobjekts** ( `adoStr` ) auf die folgenden drei grundlegenden Vorgänge zu finden:  
  
1.  Erstellen Sie ein ADO- **Stream** -Objekt:  
  
    ```  
    Stream20Ptr adoStr;  
    adoStr.CreateInstance(__uuidof(Stream));  
    ```  
  
2.  Abfragen der **iadostreamconstruction** -Schnittstelle für das **Stream** -Objekt:  
  
    ```  
    adoStreamConstructionPtr adoStrConstruct=NULL;  
    adoStr->QueryInterface(__uuidof(ADOStreamConstruction),  
                         (void**)&adoStrConstruct);  
    ```  
  
 Wenden Sie die- `IADOStreamConstruction::get_Stream` Eigenschaften Methode an, um das OLE DB **IStream** -Objekt für das ADO- **Streamobjekt** festzulegen:  
  
```  
IUnknown *pUnk=NULL;  
pRowset->QueryInterface(IID_IUnknown, (void**)&pUnk);  
adoStrConstruct->put_Stream(pUnk);  
```  
  
 Das resultierende `adoStr` Objekt stellt nun das ADO- **Stream** -Objekt dar, das aus dem OLE DB **IStream** -Objekt erstellt wurde.  
  
## <a name="requirements"></a>Anforderungen  
 **Version:** ADO 2,0 oder eine höhere Version  
  
 **Bibliothek:** msado15.dll  
  
 **UUID:** 00000283-0000-0010-8000-00AA006D2EA4  
  
## <a name="see-also"></a>Weitere Informationen  
 [ADO – API-Referenz](./ado-api-reference.md)