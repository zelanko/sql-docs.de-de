---
title: Cursor typeumum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorTypeEnum
helpviewer_keywords:
- CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6333934997c9de38b8df1dd08849886ff3dd7f2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933271"
---
# <a name="cursortypeenum"></a>CursorTypeEnum
Gibt den Typ des Cursors an, der in einem [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) -Objekt verwendet wird.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|Verwendet einen dynamischen Cursor. Ergänzungen, Änderungen und Löschungen durch andere Benutzer sind sichtbar, und alle Arten von Verschiebungen durch das **Recordset** sind zulässig, mit Ausnahme von Lesezeichen, wenn der Anbieter Sie nicht unterstützt.|  
|**adOpenForwardOnly**|0|Default. Verwendet einen Vorwärts Cursor. Identisch mit einem statischen Cursor, mit dem Unterschied, dass Sie nur vorwärts durch Datensätze scrollen können. Dadurch wird die Leistung verbessert, wenn nur ein **Recordset**durchlaufen werden muss.|  
|**adOpenKeyset**|1|Verwendet einen Keysetcursor. Wie bei einem dynamischen Cursor, **mit dem unter**schied, dass Sie keine Datensätze sehen können, die von anderen Benutzern hinzugefügt werden, auch wenn Datensätze, die von anderen Benutzern gelöscht werden, Datenänderungen durch andere Benutzer sind weiterhin sichtbar.|  
|**adopkostatic**|3|Verwendet einen statischen Cursor, bei dem es sich um eine statische Kopie eines Satzes von Datensätzen handelt, die Sie verwenden können, um Daten zu suchen oder Berichte zu generieren. Ergänzungen, Änderungen oder Löschungen durch andere Benutzer sind nicht sichtbar.|  
|**adopunspezifiziert**|-1|Gibt den Typ des Cursors nicht an.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Dauerhaft|  
|--------------|  
|Adoerums. Cursor Type. Dynamic|  
|Adoerums. Cursor Type. ForwardOnly|  
|AdoEnums. Cursor Type. Keyset|  
|Adoerums. Cursor Type. static|  
|Adoerums. Cursor Type. nicht angegeben|  
  
## <a name="applies-to"></a>Gilt für  
 [CursorType-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
