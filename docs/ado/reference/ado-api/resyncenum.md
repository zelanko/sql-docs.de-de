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
ms.openlocfilehash: 4a872ee5f4af49d9fbe97621a5d2549fd9472202
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "67931245"
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
