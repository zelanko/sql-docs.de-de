---
title: PropertyNumVal-Eigenschaft (ClientNetworkProtocolProperty-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- PropertyNumVal Property (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyNumVal property
ms.assetid: 12b02d97-702b-434f-baf6-e49a6b2cd4de
caps.latest.revision: 28
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d43ef33a5ab4a1d516910edf62fd44017b4eee19
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37309350"
---
# <a name="propertynumval-property-clientnetworkprotocolproperty-class"></a>PropertyNumVal-Eigenschaft (ClientNetworkProtocolProperty-Klasse)
  Ruft den numerischen Wert der aktuellen Eigenschaft ab, auf die durch den Wert der [PropertyIdx-Eigenschaft (ClientNetworkProtocolProperty-Klasse)](clientnetworkprotocolproperty-class.md) verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.PropertyNumVal [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [ClientNetworkProtocolProperty-Klassenobjekt](clientnetworkprotocolproperty-class.md) , das ein Attribut des vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendeten Netzwerkprotokolls darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein u`int32`-Wert, der den numerischen Wert der aktuellen Eigenschaft angibt.  
  
## <a name="remarks"></a>Hinweise  
  
