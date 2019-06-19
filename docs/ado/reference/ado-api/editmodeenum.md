---
title: EditModeEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- EditModeEnum
helpviewer_keywords:
- EditModeEnum enumeration [ADO]
ms.assetid: 45d54b6e-db2c-4553-9fd0-528147d6da2f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d98e6d27de571bc799cc8442fbe6ef9debc0beaa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695245"
---
# <a name="editmodeenum"></a>EditModeEnum
Gibt den Bearbeitungsstatus eines Datensatzes an.  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adEditNone**|0|Gibt an, dass keine Bearbeitungsvorgang ausgeführt wird.|  
|**adEditInProgress**|1|Gibt an, dass die Daten im aktuellen Datensatz geändert, aber nicht gespeichert wurde.|  
|**adEditAdd**|2|Gibt an, dass die [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) Methode aufgerufen wurde, und der aktuelle Datensatz in der Kopierpuffer ist ein neuer Datensatz, der nicht in der Datenbank gespeichert wurde.|  
|**adEditDelete**|4|Gibt an, dass der aktuelle Datensatz gelöscht wurde.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.EditMode.NONE|  
|AdoEnums.EditMode.INPROGRESS|  
|AdoEnums.EditMode.ADD|  
|AdoEnums.EditMode.DELETE|  
  
## <a name="applies-to"></a>Gilt für  
 [EditMode-Eigenschaft](../../../ado/reference/ado-api/editmode-property.md)
