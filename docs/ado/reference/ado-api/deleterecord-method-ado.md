---
title: DeleteRecord-Methode (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_DeleteRecord
- _Record::DeleteRecord
helpviewer_keywords:
- DeleteRecord method [ADO]
ms.assetid: 2726498c-dbd8-4266-983b-ae7d62c39142
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23c66eb3ca786df27f856539e8bba026d2b1ea71
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63140189"
---
# <a name="deleterecord-method-ado"></a>DeleteRecord-Methode (ADO)
Löscht eine Entität, dargestellt durch eine [Datensatz](../../../ado/reference/ado-api/record-object-ado.md).  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Record.DeleteRecord Source, Async  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Dies ist optional. Ein **Zeichenfolge** -Wert mit einer URL identifiziert die Entität (z. B. die Datei oder Verzeichnis) gelöscht werden soll. Wenn *Quelle* ausgelassen wird, oder gibt eine leere Zeichenfolge, die Entität, die vom aktuellen [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) wird gelöscht. Wenn der Datensatz einen Datensatz für die Sammlung ist (["RecordType"](../../../ado/reference/ado-api/recordtype-property-ado.md) von **AdCollectionRecord**, z. B. einem Verzeichnis) alle untergeordneten Elemente (z. B. Unterverzeichnissen) werden ebenfalls gelöscht.  
  
 *Async*  
 Dies ist optional. Ein **booleschen** -Wert, wenn **"true"**, gibt an, dass der Löschvorgang asynchrone ist.  
  
## <a name="remarks"></a>Hinweise  
 Vorgänge für das Objekt, das dargestellt durch diese **Datensatz** kann fehlschlagen, nachdem diese Methode ausgeführt wird. Nach dem Aufruf **DeleteRecord**, wird die **Datensatz** sollte geschlossen werden, da das Verhalten der **Datensatz** können unvorhersehbare je nach der Anbieter wann aktualisiert werden kann die **Datensatz** mit der Datenquelle.  
  
 Wenn diese **Datensatz** aus abgerufen wurde eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), und klicken Sie dann die Ergebnisse dieses Vorgangs nicht sofort in werden reflektiert der **Recordset**. Aktualisieren der **Recordset** durch Schließen und erneut öffnen, oder durch Ausführen der **Recordset** [Requery](../../../ado/reference/ado-api/requery-method.md) -Methode, die [Update](../../../ado/reference/ado-api/update-method.md) -Methode, oder [Resync](../../../ado/reference/ado-api/resync-method.md) Methode.  
  
> [!NOTE]
>  URLs, die mit der HTTP-Schema werden automatisch aufgerufen, die [Microsoft OLE DB-Anbieter für Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [Absolute und Relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Delete-Methode (Fields-Collection – ADO)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete-Methode (ADO-Parameters-Auflistung)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete-Methode (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)
