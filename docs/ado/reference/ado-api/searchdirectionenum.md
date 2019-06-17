---
title: SearchDirectionEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- SearchDirectionEnum
helpviewer_keywords:
- SearchDirectionEnum enumeration [ADO]
ms.assetid: 81272ae3-2165-4f4e-adfe-9ede0368cb17
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a5c1c3869b144bb770ca893595986288b07aa596
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711446"
---
# <a name="searchdirectionenum"></a>SearchDirectionEnum
Gibt die Richtung des einem Datensatz suchen innerhalb einer [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md).  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adSearchBackward**|-1|Sucht nach hinten, beenden am Anfang der **Recordset**. Wenn eine Übereinstimmung nicht gefunden wird, wird an der Datensatzzeiger positioniert [BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
|**adSearchForward**|1|Sucht vorwärts und hält am Ende der **Recordset**. Wenn eine Übereinstimmung nicht gefunden wird, wird an der Datensatzzeiger positioniert [EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md).|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.SearchDirection.BACKWARD|  
|AdoEnums.SearchDirection.FORWARD|  
  
## <a name="applies-to"></a>Gilt für  
 [Find-Methode (ADO)](../../../ado/reference/ado-api/find-method-ado.md)
