---
title: StayInSync-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::StayInSync
- Recordset20::put_StayInSync
- Recordset20::PutStayInSync
- Recordset20::get_StayInSync
- Recordset20::GetStayInSync
helpviewer_keywords:
- StayInSync property
ms.assetid: 502d69b5-dc9a-455d-b115-a03bd39a552b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 98a0cc1df12f905cd0d22d05b162983742d0f355
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710786"
---
# <a name="stayinsync-property"></a>StayInSync-Eigenschaft
Gibt an, in einer hierarchischen [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt, gibt an, ob den Verweis auf die zugrunde liegenden untergeordneten Datensätze (d. h. die *Kapitel*) ändert sich, wenn die übergeordnete Zeile positionieren, Änderungen.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt fest oder gibt einen **booleschen** Wert. Der Standardwert lautet **True**. Wenn **"true"** , im Kapitel über das aktualisiert werden, wenn das übergeordnete Element **Recordset** objektänderungen Zeile Position aus, wenn **"false"** , weiterhin im Kapitel über das Verweisen auf Daten in dem vorhergehenden Kapitel Obwohl das übergeordnete Element **Recordset** -Objekt Zeilenposition geändert hat.  
  
## <a name="remarks"></a>Hinweise  
 Diese Eigenschaft gilt für hierarchische Recordsets, z. B. diejenigen, die von unterstützt die [Microsoft Data Shaping Service für OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md), muss festgelegt werden, auf dem übergeordneten Element **Recordset** vor untergeordneten  **Recordset** abgerufen wird. Diese Eigenschaft wird das Navigieren in hierarchischen Recordsets vereinfacht.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [StayInSync-Eigenschaft – Beispiel (VB)](../../../ado/reference/ado-api/stayinsync-property-example-vb.md)   
 [Microsoft Data Shaping Service für OLE DB (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)
