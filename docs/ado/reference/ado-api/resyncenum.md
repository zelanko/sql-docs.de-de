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
author: rothja
ms.author: jroth
ms.openlocfilehash: a53d2c64e961c1b46b2d170de712493cc06f3910
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82756238"
---
# <a name="resyncenum"></a>ResyncEnum
Gibt an, ob zugrunde liegende Werte durch einen Rückruf von [Resync](../../../ado/reference/ado-api/resync-method.md)überschrieben werden.  
  
|Konstante|Wert|BESCHREIBUNG|  
|--------------|-----------|-----------------|  
|**adResyncAllValues**|2|Standard. Überschreibt Daten, und ausstehende Updates werden abgebrochen.|  
|**adresyncunderlyingvalues**|1|Daten werden nicht überschrieben, und ausstehende Updates werden nicht abgebrochen.|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC-Entsprechung  
 Paket: **com. ms. wfc. Data**  
  
|Konstante|  
|--------------|  
|Adoenumerations. Resync. AllValues|  
|Adoenumerations. Resync. underlyingvalues|  
  
## <a name="applies-to"></a>Gilt für  
 [Resync-Methode](../../../ado/reference/ado-api/resync-method.md)
