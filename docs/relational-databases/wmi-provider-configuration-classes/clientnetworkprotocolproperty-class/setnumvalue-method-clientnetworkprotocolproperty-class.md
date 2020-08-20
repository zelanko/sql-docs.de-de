---
description: SetNumValue-Methode (ClientNetworkProtocolProperty-Klasse)
title: SetNumValue-Methode (ClientNetworkProtocolProperty)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetNumValue Method (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetNumValue method
ms.assetid: c292e2ae-6d0a-44ad-ba54-5b0bd705ef37
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7a40a838f9df9621314b87048ec4b5e143f692ce
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472888"
---
# <a name="setnumvalue-method-clientnetworkprotocolproperty-class"></a>SetNumValue-Methode (ClientNetworkProtocolProperty-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Legt den numerischen Wert der aktuellen Eigenschaft fest, auf die durch den [PropertyIdx-Eigenschaftswert (ClientNetworkProtocolProperty-Klasse)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/propertyidx-property-clientnetworkprotocolproperty-class.md) verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetNumValue [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ClientNetworkProtocolProperty-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) , das ein Attribut des vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendeten Netzwerkprotokolls darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*value*|Ein u **uint32** -Wert, der den numerischen Wert der Eigenschaft angibt, auf die verwiesen wird.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientprotokollen](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
