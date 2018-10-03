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
manager: craigg
ms.openlocfilehash: 832372ee3f8e80a9da4a758c759d9b5399a20a57
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47614734"
---
# <a name="cursorlocationenum"></a>CursorLocationEnum
Gibt den Speicherort des Cursordiensts.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adUseClient**|3|Verwendet die clientseitigen Cursorn, die von einer lokalen Cursor-Bibliothek bereitgestellt. Lokale Cursor Services ermöglichen häufig viele Funktionen, die Cursor nicht der Fall, können daher mit dieser Einstellung einen Vorteil in Bezug auf Features können, die konfiguriert werden. Um Abwärtskompatibilität zu gewährleisten, das Synonym **AdUseClientBatch** wird ebenfalls unterstützt.|  
|**adUseNone**|1|Cursor-Dienste wird nicht verwendet werden. (Diese Konstante ist veraltet und wird nur aus Gründen der Abwärtskompatibilität angezeigt.)|  
|**adUseServer**|2|Standard. Wird verwendet, Cursor, die von den Datenanbieter oder Treiber bereitgestellt. Diese Cursor sind manchmal sehr flexibel und ermöglichen zusätzliche Sensitivität gegenüber Änderungen, die andere an der Datenquelle vornehmen. Jedoch einige Features von der [The Microsoft Cursor Service für OLE DB](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md), z. B. aufgehoben<br /><br /> [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekte kann nicht mit serverseitiger Cursor simuliert werden, und diese Features werden mit dieser Einstellung nicht verfügbar sein.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Paket: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.CursorLocation.CLIENT|  
|AdoEnums.CursorLocation.NONE|  
|AdoEnums.CursorLocation.SERVER|  
  
## <a name="applies-to"></a>Gilt für  
 [CursorLocation-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)
