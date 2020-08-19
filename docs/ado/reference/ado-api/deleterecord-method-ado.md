---
description: DeleteRecord-Methode (ADO)
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 94423c36dd89d6ea14ea39b7546ef1a5bef7c620
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88444102"
---
# <a name="deleterecord-method-ado"></a>DeleteRecord-Methode (ADO)
Löscht eine durch einen [Datensatz](../../../ado/reference/ado-api/record-object-ado.md)dargestellte Entität.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
Record.DeleteRecord Source, Async  
```  
  
#### <a name="parameters"></a>Parameter  
 *Quelle*  
 Optional. Ein **Zeichen** folgen Wert, der eine URL enthält, die die Entität identifiziert (z. b. die Datei oder das Verzeichnis), die gelöscht werden soll. Wenn die *Quelle* weggelassen wird oder eine leere Zeichenfolge angibt, wird die durch den aktuellen [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) dargestellte Entität gelöscht. Wenn der Datensatz ein Sammlungs Daten Satz ([RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md) von **adcollectionrecord**, z. b. ein Verzeichnis) ist, werden alle untergeordneten Elemente (z. b. Unterverzeichnisse) ebenfalls gelöscht.  
  
 *Asynchron*  
 Optional. Ein **boolescher** Wert, der, wenn **true**, angibt, dass der Löschvorgang asynchron ist.  
  
## <a name="remarks"></a>Bemerkungen  
 Vorgänge für das Objekt, das durch diesen **Datensatz** dargestellt wird, können nach Abschluss dieser Methode fehlschlagen. Nach dem Aufruf von **DeleteRecord**sollte der **Datensatz** geschlossen werden, da das Verhalten des **Datensatzes** möglicherweise unvorhersehbar wird, je nachdem, wann der Anbieter den **Datensatz** mit der Datenquelle aktualisiert.  
  
 Wenn dieser **Datensatz** von einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)abgerufen wurde, werden die Ergebnisse dieses Vorgangs nicht sofort in das **Recordset**reflektiert. Aktualisieren Sie das **Recordset** , indem Sie es schließen und erneut öffnen oder indem Sie die Methode **Recordset** [Requery](../../../ado/reference/ado-api/requery-method.md) , die [Update](../../../ado/reference/ado-api/update-method.md) -Methode oder die [Resync](../../../ado/reference/ado-api/resync-method.md) -Methode ausführen.  
  
> [!NOTE]
>  URLs, die das http-Schema verwenden, rufen automatisch den [Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Weitere Informationen finden Sie unter [absolute und relative URLs](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>Gilt für  
 [Record-Objekt (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Delete-Methode (ADO Fields-Auflistung)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete-Methode (ADO Parameters-Sammlung)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete-Methode (ADO-Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)
