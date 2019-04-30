---
title: MoveRecordOptionsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- MoveRecordOptionsEnum
helpviewer_keywords:
- MoveRecordOptionsEnum enumeration [ADO]
ms.assetid: f53c2ce4-1021-4a45-92b8-775e8bebad99
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eb86b01a42a097210801fd3654ff2af80df24e39
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63242450"
---
# <a name="moverecordoptionsenum"></a>MoveRecordOptionsEnum
Gibt das Verhalten der [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt [MoveRecord](../../../ado/reference/ado-api/moverecord-method-ado.md) Methode.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adMoveUnspecified**|-1|Standard. Führt den Standardvorgang für das Verschieben: Der Vorgang schlägt fehl, wenn die Zieldatei oder das Verzeichnis bereits vorhanden ist, und der Vorgang Hypertextlinks aktualisiert.|  
|**adMoveOverWrite**|1|Überschreibt die Zieldatei oder das Verzeichnis, auch wenn sie bereits vorhanden ist.|  
|**adMoveDontUpdateLinks**|2|Ändert das Standardverhalten des **MoveRecord** Methode, indem Sie nicht aktualisiert, Hypertextlinks der Quelle **Datensatz**. Das Standardverhalten hängt von den Funktionen des Anbieters ab. Move-Vorgang aktualisiert Links aus, wenn der Anbieter kann. Wenn der Anbieter Links nicht beheben kann, oder wenn dieser Wert nicht angegeben ist, ist erfolgreich, klicken Sie dann das Verschieben selbst wenn Links nicht behoben wurden.|  
|**adMoveAllowEmulation**|4|Fordert an, dass der Anbieter versucht wird, um das Verschieben (mit Download, Upload und Delete-Operationen) zu simulieren. Wenn der Versuch zum Verschieben der **Datensatz** schlägt fehl, da die Ziel-URL auf einem anderen Server wird oder von einem anderen Anbieter als die Quelle bedient werden, erhöhte Latenz oder Datenverlust aufgrund der Funktionen der anderen Anbieter Dadurch kann bei Verschieben von Ressourcen zwischen Anbietern.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [MoveRecord-Methode (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)
