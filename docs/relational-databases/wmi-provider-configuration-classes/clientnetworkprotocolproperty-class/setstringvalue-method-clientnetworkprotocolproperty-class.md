---
title: SetStringValue-Methode (ClientNetworkProtocolProperty)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetStringValue Method (ClientNetworkProtocolProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetStringValue method
ms.assetid: 88d67b22-0eea-48c9-ab73-e0b4907953df
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5d7a606931c6a3449f765590b9a2f90a65a67d15
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85759916"
---
# <a name="setstringvalue-method-clientnetworkprotocolproperty-class"></a>SetStringValue-Methode (ClientNetworkProtocolProperty-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Legt den Zeichenfolgenwert der aktuellen Eigenschaft fest, auf die durch den [PropertyIdx-Eigenschaftswert (ClientNetworkProtocolProperty-Klasse)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/propertyidx-property-clientnetworkprotocolproperty-class.md) verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetStringValue(StrValue)  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ClientNetworkProtocolProperty-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) , das ein Attribut des vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendeten Netzwerkprotokolls darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*StrValue*|Ein Zeichenfolgenwert, der den neuen Wert der aktuellen Eigenschaft angibt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientprotokollen](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
