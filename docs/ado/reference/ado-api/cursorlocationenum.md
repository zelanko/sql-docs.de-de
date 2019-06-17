---
title: CursorLocationEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorLocationEnum
helpviewer_keywords:
- CursorLocationEnum enumeration [ADO]
ms.assetid: acb255ff-1734-4b70-89bb-aef862b4c63b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 43c2043917d6b21293fea71566dfdf1202b6f59e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695655"
---
# <a name="cursorlocationenum"></a>CursorLocationEnum
Gibt den Speicherort des Cursordiensts.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adUseClient**|3|Verwendet die clientseitigen Cursorn, die von einer lokalen Cursor-Bibliothek bereitgestellt. Lokale Cursor Services ermöglichen häufig viele Funktionen, die Cursor nicht der Fall, können daher mit dieser Einstellung einen Vorteil in Bezug auf Features können, die konfiguriert werden. Um Abwärtskompatibilität zu gewährleisten, das Synonym **AdUseClientBatch** wird ebenfalls unterstützt.|  
|**adUseNone**|1|Cursor-Dienste wird nicht verwendet werden. (Diese Konstante ist veraltet und wird nur aus Gründen der Abwärtskompatibilität angezeigt.)|  
|**adUseServer**|2|Standard. Wird verwendet, Cursor, die von den Datenanbieter oder Treiber bereitgestellt. Diese Cursor sind manchmal sehr flexibel und ermöglichen zusätzliche Sensitivität gegenüber Änderungen, die andere an der Datenquelle vornehmen. Jedoch einige Features von der [The Microsoft Cursor Service für OLE DB](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md), z. B. aufgehoben<br /><br /> [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekte kann nicht mit serverseitiger Cursor simuliert werden, und diese Features werden mit dieser Einstellung nicht verfügbar sein.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.CursorLocation.CLIENT|  
|AdoEnums.CursorLocation.NONE|  
|AdoEnums.CursorLocation.SERVER|  
  
## <a name="applies-to"></a>Gilt für  
 [CursorLocation-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)
