---
title: IPADRESSEN-Eigenschaft (ServerNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- IpAddresses Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- IpAddresses property
ms.assetid: e5d66f7e-9719-436e-b723-12d56f914a05
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5e4f3b59530d7c0a9674a8070387c846d3d1fdd9
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85750063"
---
# <a name="ipaddresses-property-servernetworkprotocol-class"></a>IpAddresses-Eigenschaft (ServerNetworkProtocol-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Ruft die IP-Adressen ab, die dem Servernetzwerkprotokoll zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.IpAddresses [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein **ServerNetworkProtocol** -Objekt, das das Netzwerkprotokoll darstellt, das von der Instanz von verwendet wird [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Array von [ServerNetworkProtocolIPAdress-Klassenobjekten](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) , die die vom Server-Netzwerkprotokoll unterstützten IP-Adressen darstellen.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
