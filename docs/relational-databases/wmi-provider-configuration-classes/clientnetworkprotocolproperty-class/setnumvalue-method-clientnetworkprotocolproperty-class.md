---
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
ms.openlocfilehash: 4e359dddea783e1ff3e553e6454d97184ea3694f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73658816"
---
# <a name="setnumvalue-method-clientnetworkprotocolproperty-class"></a>SetNumValue-Methode (ClientNetworkProtocolProperty-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Legt den numerischen Wert der aktuellen Eigenschaft fest, auf die durch den [PropertyIdx-Eigenschaftswert (ClientNetworkProtocolProperty-Klasse)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/propertyidx-property-clientnetworkprotocolproperty-class.md) verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetNumValue [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *Objekt*  
 Ein [ClientNetworkProtocolProperty-Klassen](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) Objekt, das ein Attribut des vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client verwendeten Netzwerk Protokolls darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*Wert*|Ein u **uint32** -Wert, der den numerischen Wert der Eigenschaft angibt, auf die verwiesen wird.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **UInt32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird, und jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientprotokollen](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
