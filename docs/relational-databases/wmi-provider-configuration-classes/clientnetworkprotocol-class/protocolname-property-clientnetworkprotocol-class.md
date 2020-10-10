---
description: ProtocolName-Eigenschaft (ClientNetworkProtocol-Klasse)
title: ProtocolName-Eigenschaft (ClientNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolName Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolName property
ms.assetid: f8527121-fbcd-4d30-9b4a-1461149cb5a8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1323d4c47555bfebb717ba1627e6b4fc7c22c94b
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91888948"
---
# <a name="protocolname-property-clientnetworkprotocol-class"></a>ProtocolName-Eigenschaft (ClientNetworkProtocol-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ruft den Namen des aktuellen Netzwerkprotokolls ab, das in [Konfigurieren von Clientprotokollen](../../../database-engine/configure-windows/configure-client-protocols.md)angegeben ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ProtocolName [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ClientNetworkProtocol-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , das das vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Zeichenfolgenwert, der den Namen des aktuellen Clientnetzwerkprotokolls angibt, auf das in der [SetOrderValue-Methode (ClientNetworkProtocol-Klasse)](./setordervalue-method-clientnetworkprotocol-class.md)verwiesen wird.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientnetzwerkprotokollen und Netzwerkbibliotheken](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
