---
title: Reshape Name dynamische Eigenschaft (ADO) | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Reshape Name property [ADO]
ms.assetid: 690229d1-46cc-42e6-a57d-4438251fe248
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6a07ec878b1198fbf23bfb251460d83869313c83
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47696829"
---
# <a name="reshape-name-property-dynamic-ado"></a>Reshape Name – dynamische Eigenschaft (ADO)
Gibt einen Namen für die [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
## <a name="return-values"></a>Rückgabewerte  
 Gibt eine **Zeichenfolge** Wert, der den Namen der **Recordset**.  
  
## <a name="remarks"></a>Hinweise  
 Beibehalten von Namen für die Dauer der Verbindung oder bis die **Recordset** geschlossen wird.  
  
 Die **Reshape Name** Eigenschaft ist hauptsächlich für die Verwendung mit dem Feature neu strukturieren der [Microsoft Data Shaping Service für OLE DB](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md) Dienstanbieter. Namen müssen zur Teilnahme an neu strukturieren eindeutig sein.  
  
 Diese Eigenschaft ist schreibgeschützt, aber können indirekt festgelegt werden, wenn eine **Recordset** erstellt wird. Z. B. wenn eine Klausel dieses Shape-Befehl erstellt eine **Recordset** und weist ihm einen Aliasnamen mithilfe der **AS** -Schlüsselwort, der Alias zugewiesen wird die **Reshape Name** Eigenschaft. Wenn kein Alias deklariert wird, die **Reshape Name** Eigenschaft erhält einen eindeutigen Namen, die von der Data shaping Dienst generiert. Der Name eines vorhandenen identisch ist der Aliasname **Recordset**, weder **Recordset** können umgeformt werden, bis eine von ihnen aufgehoben wird. Das Standardverhalten kann geändert werden, indem Sie einen eindeutigen Namen der [Reshape Name](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md) Eigenschaft für die ADO-Verbindung mit **"true"**. Durch Festlegen dieser Eigenschaft können die Daten strukturieren der Dienst die Berechtigung zum Ändern Sie des zugewiesenen Benutzernamen ein, falls erforderlich, um die Eindeutigkeit sicherzustellen. Weitere Informationen zum Ändern der Form, finden Sie unter [Microsoft Data Shaping Service für OLE DB (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md).  
  
 Verwenden der **Reshape Name** Eigenschaft, wenn Sie möchten eine **Recordset** in einem Shape-Befehl, oder wenn Sie den Namen nicht kennen, da er durch den Data Shaping Service generiert wurde. In diesem Fall konnte Sie einen SHAPE-Befehl generieren, indem Sie den Befehl aus, schließen Sie die zurückgegebene Zeichenfolge Verketten der **Reshape Name** Eigenschaft.  
  
 **Reshape Name** wird eine dynamische Eigenschaft angefügt der **Recordset** des Objekts [Eigenschaften](../../../ado/reference/ado-api/properties-collection-ado.md) Auflistung bei der [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) -Eigenschaftensatz auf **AdUseClient**.  
  
## <a name="applies-to"></a>Gilt für  
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Microsoft Data Shaping Service für OLE DB (ADO-Dienstanbieter)](../../../ado/guide/appendixes/microsoft-data-shaping-service-for-ole-db-ado-service-provider.md)   
 [Shape-Befehle im Allgemeinen](../../../ado/guide/data/shape-commands-in-general.md)   
 [Recordset-Objekt (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
