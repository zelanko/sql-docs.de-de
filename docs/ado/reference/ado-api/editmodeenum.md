---
title: Editmodeerum | Microsoft-Dokumentation
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
author: rothja
ms.author: jroth
ms.openlocfilehash: e4e16cbdddf39ba6abb03f93c35b2c2243d1bd71
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765561"
---
# <a name="editmodeenum"></a>EditModeEnum
Gibt den Bearbeitungsstatus eines Datensatzes an.  
  
|Konstante|Wert|BESCHREIBUNG|  
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
