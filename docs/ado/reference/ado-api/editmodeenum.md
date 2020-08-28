---
description: EditModeEnum
title: Editmodeerum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 7e10479aca06eab4a7aa5215f0016dd1f82eab1c
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88973851"
---
# <a name="editmodeenum"></a>EditModeEnum
Gibt den Bearbeitungsstatus eines Datensatzes an.  
  
|Konstante|Wert|Beschreibung|  
|--------------|-----------|-----------------|  
|**adEditNone**|0|Gibt an, dass kein Bearbeitungsvorgang ausgeführt wird.|  
|**adEditInProgress**|1|Gibt an, dass die Daten im aktuellen Datensatz geändert, aber nicht gespeichert wurden.|  
|**adEditAdd**|2|Gibt an, dass die [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md) -Methode aufgerufen wurde und der aktuelle Datensatz im Kopier Puffer ein neuer Datensatz ist, der nicht in der Datenbank gespeichert wurde.|  
|**adeditdelete**|4|Gibt an, dass der aktuelle Datensatz gelöscht wurde.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|AdoEnums. EditMode. None|  
|AdoEnums. EditMode. InProgress|  
|AdoEnums. EditMode. Add|  
|AdoEnums. EditMode. Delete|  
  
## <a name="applies-to"></a>Gilt für  
 [EditMode-Eigenschaft](../../../ado/reference/ado-api/editmode-property.md)
