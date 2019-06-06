---
title: RecordOpenOptionsEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordOpenOptionsEnum
helpviewer_keywords:
- RecordOpenOptionsEnum enumeration [ADO]
ms.assetid: 9028aba4-90fc-4dfc-88e4-fa8a7b6fedee
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c0ed637d8e77ef7fc152f994da81db010fa80900
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66712160"
---
# <a name="recordopenoptionsenum"></a>RecordOpenOptionsEnum
Gibt Optionen zum Öffnen einer [Datensatz](../../../ado/reference/ado-api/record-object-ado.md). Diese Werte können kombiniert werden, mithilfe von oder.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adDelayFetchFields**|0x8000|Gibt an, an den Anbieter, die mit die Feldern verknüpft die **Datensatz** zunächst nicht abgerufen werden müssen, aber beim ersten Versuch Zugriff auf das Feld abgerufen werden können. Das Standardverhalten, das durch das Fehlen des dieses Flag angegeben wird, um alle abzurufen der **Datensatz** Objekt Felder.|  
|**adDelayFetchStream**|0x4000|Gibt an, an den Anbieter, die der Standarddatenstrom mit verknüpft die **Datensatz** zunächst nicht abgerufen werden müssen. Das Standardverhalten, das durch das Fehlen des dieses Flag angegeben ist, zum Abrufen von des Standard-Streams, der für die **Datensatz** Objekt.|  
|**adOpenAsync**|0x1000|Gibt an, dass die **Datensatz** Objekt im asynchronen Modus geöffnet wird.|  
|**adOpenExecuteCommand**|0x10000|Gibt an, dass die Quellzeichenfolge-Befehlstext enthält, die ausgeführt werden soll. Dieser Wert entspricht der **AdCmdText** option **Recordset.Open**.|  
|**adOpenRecordUnspecified**|-1|Standard. Gibt an, dass keine Optionen angegeben sind.|  
|**adOpenOutput**|0x800000|Gibt an, dass, wenn die Quelle zu einem Knoten verweist, der ein ausführbares Skript enthält (z. B. ein. ASP-Seite), klicken Sie dann auf die geöffnete **Datensatz** enthält die Ergebnisse der ausgeführten Skripts. Dieser Wert ist nur gültig mit nicht-Auflistungstyp Datensätze.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [Open-Methode (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)
