---
description: FieldEnum
title: Fieldenum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FieldEnum
helpviewer_keywords:
- FieldEnum enumeration [ADO]
ms.assetid: be4eda13-d4e4-4d6b-bb0d-3310b0a96fc2
author: rothja
ms.author: jroth
ms.openlocfilehash: cad540a13fbad480f795049df0d0150188df4283
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88775449"
---
# <a name="fieldenum"></a>FieldEnum
Gibt die speziellen Felder an, auf die in der [Felder](./fields-collection-ado.md) Auflistung eines [Datensatz](./record-object-ado.md) -Objekts verwiesen wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Konstanten stellen eine "Verknüpfung" für den Zugriff auf spezielle Felder bereit, die einem **Datensatz**zugeordnet sind. Rufen Sie das [Feld](./field-object.md) Objekt aus der **Fields** -Auflistung ab, und rufen Sie dessen Inhalt mit der [value](./value-property-ado.md) -Eigenschaft des **Field** -Objekts ab.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|Verweist auf das Feld mit dem einem **Datensatz**zugeordneten [standardstreamobjekt](./stream-object-ado.md) .|  
|**adRecordURL**|-2|Verweist auf das Feld, das die absolute URL Zeichenfolge für den aktuellen **Datensatz**enthält.|