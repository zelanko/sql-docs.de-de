---
title: DataMember-Eigenschaft | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset20::DataMember
helpviewer_keywords:
- DataMember property
ms.assetid: 2c8fb09e-10ad-49b5-ab41-2603771780d9
author: rothja
ms.author: jroth
ms.openlocfilehash: 87d525907edde2e3dc99b78eb827c571c604d8b7
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82763481"
---
# <a name="datamember-property"></a>DataMember-Eigenschaft
Gibt den Namen des Datenmembers an, der aus dem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) abgerufen wird, auf das von der [DataSource](../../../ado/reference/ado-api/datasource-property-ado.md) -Eigenschaft verwiesen wird.  
  
## <a name="settings-and-return-values"></a>Einstellungen und Rückgabewerte  
 Legt einen **Zeichen** folgen Wert fest oder gibt ihn zurück. Bei dem Namen wird die Groß- und Kleinschreibung nicht berücksichtigt.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Eigenschaft wird verwendet, um Daten gebundene Steuerelemente mit der Daten Umgebung zu erstellen. In der Daten Umgebung werden Auflistungen von Daten (Datenquellen) verwaltet, die benannte Objekte (Datenmember) enthalten, die als [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt dargestellt werden.  
  
 Die Eigenschaften **DataMember** und **DataSource** müssen gleichzeitig verwendet werden.  
  
 Die **DataMember** -Eigenschaft bestimmt, welches von der **DataSource** -Eigenschaft angegebene Objekt als **Recordset** -Objekt dargestellt wird. Das **Recordset** -Objekt muss geschlossen werden, bevor diese Eigenschaft festgelegt wird. Ein Fehler wird generiert, wenn die **DataMember** -Eigenschaft nicht vor der **DataSource** -Eigenschaft festgelegt ist oder wenn der **DataMember** -Name nicht durch das in der **DataSource** -Eigenschaft angegebene Objekt erkannt wird.  
  
## <a name="usage"></a>Verwendung  
  
```  
Dim rs as New ADODB.Recordset  
rs.DataMember = "Command"     'Name of the rowset to bind to  
Set rs.DataSource = myDE      'Name of the object containing an IRowset  
```  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Weitere Informationen  
 [DataSource-Eigenschaft (ADO)](../../../ado/reference/ado-api/datasource-property-ado.md)
