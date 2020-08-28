---
description: StayInSync-Eigenschaft
title: StayInSync-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 9677a776273e83ad31fecde3a7ea436138d3784e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88988621"
---
# <a name="stayinsync-property"></a>StayInSync-Eigenschaft
Gibt in einem hierarchischen [Recordsetobjekt](./recordset-object-ado.md) an, ob sich der Verweis auf die zugrunde liegenden untergeordneten Datensätze (d. h. das *Kapitel*) ändert, wenn sich die Position der übergeordneten Zeile ändert.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **booleschen** Wert fest oder gibt diesen zurück. Der Standardwert ist **True**. **True**gibt an, dass das Kapitel aktualisiert wird, wenn sich das übergeordnete **Recordset** -Objekt an der Zeilen Position ändert. Wenn der Wert **false**ist, verweist das Kapitel weiterhin auf Daten im vorherigen Kapitel, auch wenn das übergeordnete **Recordset** -Objekt die Zeilen Position geändert hat.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Eigenschaft gilt für hierarchische Recordsets, z. b. diejenigen, die vom Microsoft-Daten Strukturierungs [Dienst für OLE DB](../../guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)unterstützt werden, und muss für das übergeordnete **Recordset** festgelegt werden, bevor das untergeordnete **Recordset** abgerufen wird. Diese Eigenschaft vereinfacht das Navigieren in hierarchischen Recordsets.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [Beispiel für die StayInSync-Eigenschaft (VB)](./stayinsync-property-example-vb.md)   
 [Microsoft-Daten Strukturierungs Dienst für OLE DB (ADO-Dienstanbieter)](../../guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)