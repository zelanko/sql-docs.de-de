---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5fe89d90510e95468e18b0d744ff566f69654320
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932681"
---
# <a name="fieldenum"></a>FieldEnum
Gibt die speziellen Felder an, auf die in der [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung eines [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) -Objekts verwiesen wird.  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Konstanten stellen eine "Verknüpfung" für den Zugriff auf spezielle Felder bereit, die einem **Datensatz**zugeordnet sind. Rufen Sie das [Feld](../../../ado/reference/ado-api/field-object.md) Objekt aus der **Fields** -Auflistung ab, und rufen Sie dessen Inhalt mit der [value](../../../ado/reference/ado-api/value-property-ado.md) -Eigenschaft des **Field** -Objekts ab.  
  
|Dauerhaft|value|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|Verweist auf das Feld mit dem einem **Datensatz**zugeordneten [standardstreamobjekt](../../../ado/reference/ado-api/stream-object-ado.md) .|  
|**adRecordURL**|-2|Verweist auf das Feld, das die absolute URL Zeichenfolge für den aktuellen **Datensatz**enthält.|
