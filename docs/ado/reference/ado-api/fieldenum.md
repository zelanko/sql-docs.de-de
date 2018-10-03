---
title: FieldEnum | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 204ffb54eb0a48f55d4ec1974b123ed4a0e430be
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741578"
---
# <a name="fieldenum"></a>FieldEnum
Gibt an, die spezielle Felder, die auf die verwiesen wird einem [Datensatz](../../../ado/reference/ado-api/record-object-ado.md) des Objekts [Felder](../../../ado/reference/ado-api/fields-collection-ado.md) Auflistung.  
  
## <a name="remarks"></a>Hinweise  
 Diese Konstanten stellen eine "Verknüpfung" für den Zugriff auf spezielle Felder im Zusammenhang mit einem **Datensatz**. Abrufen der [Feld](../../../ado/reference/ado-api/field-object.md) -Objekt aus der **Felder** -Auflistung, und rufen Sie dann seinen Inhalt mit der **Feld** des Objekts [Wert](../../../ado/reference/ado-api/value-property-ado.md) Eigenschaft.  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adDefaultStream**|-1|Verweist auf das Feld mit der standardmäßigen [Stream](../../../ado/reference/ado-api/stream-object-ado.md) zugeordnete Objekt ein **Datensatz**.|  
|**adRecordURL**|-2|Verweist auf das Feld mit der absoluten URL-Zeichenfolge für den aktuellen **Datensatz**.|
