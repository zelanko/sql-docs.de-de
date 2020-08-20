---
description: PropertyNumVal-Eigenschaft (ClientNetworkProtocolProperty-Klasse)
title: PropertyNumVal-Eigenschaft (ClientNetworkProtocolProperty)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- PropertyNumVal Property (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- PropertyNumVal property
ms.assetid: 12b02d97-702b-434f-baf6-e49a6b2cd4de
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b11713099134c61df82edda603796b2080494bb0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485229"
---
# <a name="propertynumval-property-clientnetworkprotocolproperty-class"></a>PropertyNumVal-Eigenschaft (ClientNetworkProtocolProperty-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ruft den numerischen Wert der aktuellen Eigenschaft ab, auf die durch den Wert der [PropertyIdx-Eigenschaft (ClientNetworkProtocolProperty-Klasse)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/propertyidx-property-clientnetworkprotocolproperty-class.md) verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.PropertyNumVal [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ClientNetworkProtocolProperty-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) , das ein Attribut des vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendeten Netzwerkprotokolls darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein u**int32** -Wert, der den numerischen Wert der aktuellen Eigenschaft angibt.  
  
## <a name="remarks"></a>Bemerkungen  
  
