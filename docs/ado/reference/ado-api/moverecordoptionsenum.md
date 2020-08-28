---
description: MoveRecordOptionsEnum
title: "\"Thecordoptionsenum\" | Microsoft-Dokumentation"
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1fd6f68364f284e974d3564c8df3da5808683c3e
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990501"
---
# <a name="moverecordoptionsenum"></a>MoveRecordOptionsEnum
Gibt das Verhalten des [Daten Satz](./record-object-ado.md) Objekts [an](./moverecord-method-ado.md) .  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**admuveunspezifiziert**|-1|Standard. Führt den Standard Verschiebungs Vorgang aus: der Vorgang schlägt fehl, wenn die Zieldatei oder das Verzeichnis bereits vorhanden ist, und der Vorgang aktualisiert Hypertext Links.|  
|**admuveüberschreibung**|1|Überschreibt die Zieldatei oder das Zielverzeichnis, auch wenn Sie bereits vorhanden ist.|  
|**admuvedontupdatelinert**|2|Ändert das Standardverhalten der- **Methode von der-** Methode, indem die Hypertext Links des Quell **Datensatzes**nicht aktualisiert werden. Das Standardverhalten hängt von den Funktionen des Anbieters ab. Verschieben von Vorgangs Updates Links, wenn der Anbieter fähig ist. Wenn der Anbieter keine Links beheben kann oder wenn dieser Wert nicht angegeben ist, wird der Verschiebe Vorgang auch dann erfolgreich ausgeführt, wenn Verknüpfungen nicht korrigiert wurden.|  
|**admuvezuzustellung**|4|Fordert an, dass der Anbieter versucht, die Verschiebung zu simulieren (mit Download-, Upload-und DELETE-Vorgängen). Wenn der Versuch, den **Datensatz** zu verschieben, fehlschlägt, weil sich die Ziel-URL auf einem anderen Server befindet oder von einem anderen Anbieter als der Quelle bedient wird, kann dies aufgrund unterschiedlicher Anbieter Funktionen zum Verschieben von Ressourcen zwischen Anbietern zu erhöhter Latenz oder Datenverlusten führen.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Diese Konstanten haben keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [MoveRecord-Methode (ADO)](./moverecord-method-ado.md)