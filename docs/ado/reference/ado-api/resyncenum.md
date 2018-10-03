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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47632548"
---
# <a name="resyncenum"></a>ResyncEnum
Gibt an, ob die zugrunde liegende Werte überschrieben werden, durch einen Aufruf von [Resync](../../../ado/reference/ado-api/resync-method.md).  
  
|Konstante|value|Description|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|Standard. Daten werden überschrieben, und ausstehende Updates werden abgebrochen.|  
|**adResyncUnderlyingValues**|1|Daten nicht überschrieben, und ausstehende Updates nicht abgebrochen werden.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-äquivalent  
 Paket: **com.ms.wfc.data**  
  
|Konstante|  
|--------------|  
|AdoEnums.Resync.ALLVALUES|  
|AdoEnums.Resync.UNDERLYINGVALUES|  
  
## <a name="applies-to"></a>Gilt für  
 [Resync-Methode](../../../ado/reference/ado-api/resync-method.md)
