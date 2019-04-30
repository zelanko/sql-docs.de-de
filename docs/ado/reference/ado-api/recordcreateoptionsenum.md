---
title: RecordCreateOptionsEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- RecordCreateOptionsEnum
helpviewer_keywords:
- RecordCreateOptionsEnum enumeration [ADO]
ms.assetid: 6d746670-0850-4065-9cd4-168dea1d3ea9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8574da628c4bc1af800635ed9228e074817adae9
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63239975"
---
# <a name="recordcreateoptionsenum"></a>RecordCreateOptionsEnum
Gibt an, ob ein vorhandenes **Datensatz** muss geöffnet sein oder ein neues **Datensatz** erstellt, die für die [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) Objekt [öffnen](../../../ado/reference/ado-api/open-method-ado-record.md) Methode. Die Werte können mit einer AND-Operator kombiniert werden.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adCreateCollection**|0x2000|Erstellt ein neues **Datensatz** unter dem Knoten anhand des *Quelle* Parameter, anstatt Sie zu öffnen, eine vorhandene **Datensatz**. Wenn die Quelle zu einem vorhandenen Knoten, verweist dann ein Laufzeitfehler tritt auf, es sei denn, **AdCreateCollection** mit kombiniert **AdOpenIfExists** oder **AdCreateOverwrite**.|  
|**adCreateNonCollection**|0|Erstellt ein neues **Datensatz** des Typs [AdSimpleRecord](../../../ado/reference/ado-api/recordtypeenum.md).|  
|**adCreateOverwrite**|0x4000000|Die erstellungs-Flags ändert **AdCreateCollection**, **AdCreateNonCollection**, und **AdCreateStructDoc**. Wenn oder mit diesem Wert und die Erstellung Flag-Werte verwendet wird, wenn die Quell-URL zu einem vorhandenen Knoten verweist oder **Datensatz**, und klicken Sie dann die vorhandene **Datensatz** überschrieben und durch einen neuen eine an seiner Stelle erstellt wird. Dieser Wert kann nicht verwendet werden, zusammen mit **AdOpenIfExists**.|  
|**adCreateStructDoc**|0x80000000|Erstellt ein neues **Datensatz** des Typs [AdStructDoc](../../../ado/reference/ado-api/recordtypeenum.md), anstatt Sie zu öffnen, eine vorhandene **Datensatz**.|  
|**adFailIfNotExists**|-1|Standard. Führt zu einem Laufzeitfehler, wenn *Quelle* verweist auf einen nicht vorhandenen Knoten.|  
|**adOpenIfExists**|0x2000000|Die erstellungs-Flags ändert **AdCreateCollection**, **AdCreateNonCollection**, und **AdCreateStructDoc**. Wenn oder mit diesem Wert und die Erstellung Flag-Werte verwendet wird, wenn die Quell-URL zu einem vorhandenen Knoten verweist oder **Datensatz** Objekt, und klicken Sie dann der Anbieter der vorhandenen öffnen muss **Datensatz** anstatt ein neues erstellen ein. Dieser Wert kann nicht verwendet werden, zusammen mit **AdCreateOverwrite**.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Diese Konstanten keine ADO/WFC-Entsprechungen.  
  
## <a name="applies-to"></a>Gilt für  
 [Open-Methode (ADO Record)](../../../ado/reference/ado-api/open-method-ado-record.md)
