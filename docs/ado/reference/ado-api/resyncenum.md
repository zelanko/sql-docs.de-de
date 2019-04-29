---
title: ResyncEnum | Microsoft-Dokumentation
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ResyncEnum
helpviewer_keywords:
- ResyncEnum enumeration [ADO]
ms.assetid: d3df2c90-e570-4c40-a79a-25b3448a009c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: aaf396e8969d490933e26652e18c0c070e030785
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63060967"
---
# <a name="resyncenum"></a>ResyncEnum
Gibt an, ob die zugrunde liegende Werte überschrieben werden, durch einen Aufruf von [Resync](../../../ado/reference/ado-api/resync-method.md).  
  
|Konstante|Wert|Description|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|Standard. Daten werden überschrieben, und ausstehende Updates werden abgebrochen.|  
|**adResyncUnderlyingValues**|1|Daten nicht überschrieben, und ausstehende Updates nicht abgebrochen werden.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Package: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.Resync.ALLVALUES|  
|AdoEnums.Resync.UNDERLYINGVALUES|  
  
## <a name="applies-to"></a>Gilt für  
 [Resync-Methode](../../../ado/reference/ado-api/resync-method.md)
