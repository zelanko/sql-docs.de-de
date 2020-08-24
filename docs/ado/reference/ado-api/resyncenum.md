---
description: ResyncEnum
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
ms.openlocfilehash: addaaa07b14b88ed7d72714ba8698da1f2ef2ac9
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2020
ms.locfileid: "88777639"
---
# <a name="resyncenum"></a>ResyncEnum
Gibt an, ob zugrunde liegende Werte durch einen Rückruf von [Resync](./resync-method.md)überschrieben werden.  
  
|Konstante|Wert|Beschreibung|  
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
 [Resync-Methode](./resync-method.md)