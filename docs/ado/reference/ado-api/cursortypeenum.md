---
title: CursorTypeEnum | Microsoft-Dokumentation
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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67933271"
---
# <a name="cursortypeenum"></a>CursorTypeEnum
Gibt den Typ des Cursors verwendet eine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) Objekt.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|Verwendet einen dynamischen Cursor. Hinzufügungen, Änderungen und löschungen von anderen Benutzern sind sichtbar, und alle Arten von Verkehr über den **Recordset** zulässig ist, mit Ausnahme von Lesezeichen, wenn der Anbieter diese nicht unterstützt.|  
|**adOpenForwardOnly**|0|Standard. Verwendet einen vorwärtsgerichteten Cursor. Identisch mit einem statischen Cursor, mit dem Unterschied, dass Sie nur vorwärts durch die Datensätze scrollen können. Dies verbessert die Leistung, wenn Sie nur eine durchlaufen müssen einer **Recordset**.|  
|**adOpenKeyset**|1|Verwendet einen Keyset-Cursor. Wie Sie einen dynamischen Cursor, mit dem Unterschied, dass Sie keine Datensätze, die andere Benutzer hinzufügen möchten anzeigen, obwohl Datensätze, die von anderen Benutzern gelöschten aus zugegriffen werden Ihre **Recordset**. Datenänderungen durch andere Benutzer sind immer noch sichtbar.|  
|**adOpenStatic**|3|Verwendet einen statischen Cursor, wird eine statische Kopie einer Gruppe von Datensätzen, die Sie zum Suchen von Daten oder zum Generieren von Berichten verwenden können. Ergänzungen, Änderungen oder löschungen durch andere Benutzer sind nicht sichtbar.|  
|**adOpenUnspecified**|-1|Gibt nicht den Typ des Cursors an.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.CursorType.DYNAMIC|  
|AdoEnums.CursorType.FORWARDONLY|  
|AdoEnums.CursorType.KEYSET|  
|AdoEnums.CursorType.STATIC|  
|AdoEnums.CursorType.UNSPECIFIED|  
  
## <a name="applies-to"></a>Gilt für  
 [CursorType-Eigenschaft (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
