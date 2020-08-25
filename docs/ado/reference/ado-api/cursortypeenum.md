---
description: CursorTypeEnum
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 9e0d37d5aad3f27a61cf3ae7c8dad9b27149e09b
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775469"
---
# <a name="cursortypeenum"></a>CursorTypeEnum
Gibt den Typ des Cursors an, der in einem [Recordset](./recordset-object-ado.md) -Objekt verwendet wird.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adOpenDynamic**|2|Verwendet einen dynamischen Cursor. Ergänzungen, Änderungen und Löschungen durch andere Benutzer sind sichtbar, und alle Arten von Verschiebungen durch das **Recordset** sind zulässig, mit Ausnahme von Lesezeichen, wenn der Anbieter Sie nicht unterstützt.|  
|**adOpenForwardOnly**|0|Standard. Verwendet einen Vorwärts Cursor. Identisch mit einem statischen Cursor, mit dem Unterschied, dass Sie nur vorwärts durch Datensätze scrollen können. Dadurch wird die Leistung verbessert, wenn nur ein **Recordset**durchlaufen werden muss.|  
|**adOpenKeyset**|1|Verwendet einen Keysetcursor. Wie bei einem dynamischen Cursor, **mit dem unter**schied, dass Sie keine Datensätze sehen können, die von anderen Benutzern hinzugefügt werden, auch wenn Datensätze, die von anderen Benutzern gelöscht werden, Datenänderungen durch andere Benutzer sind weiterhin sichtbar.|  
|**adopkostatic**|3|Verwendet einen statischen Cursor, bei dem es sich um eine statische Kopie eines Satzes von Datensätzen handelt, die Sie verwenden können, um Daten zu suchen oder Berichte zu generieren. Ergänzungen, Änderungen oder Löschungen durch andere Benutzer sind nicht sichtbar.|  
|**adopunspezifiziert**|-1|Gibt den Typ des Cursors nicht an.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoerums. Cursor Type. Dynamic|  
|Adoerums. Cursor Type. ForwardOnly|  
|AdoEnums. Cursor Type. Keyset|  
|Adoerums. Cursor Type. static|  
|Adoerums. Cursor Type. nicht angegeben|  
  
## <a name="applies-to"></a>Gilt für  
 [CursorType-Eigenschaft (ADO)](./cursortype-property-ado.md)