---
description: MultiIpConfigurationSupport-Eigenschaft (ServerNetworkProtocol-Klasse)
title: MultiIpConfigurationSupport-Eigenschaft (ServerNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- MultiIpConfigurationSupport Property (ServerNetworkProtocol
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- MultiIpConfigurationSupport property
ms.assetid: 442c6133-4038-42db-a67d-2631285ac76b
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: da02aefabf6096712b4d6ccb06622892a20dbbed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472845"
---
# <a name="multiipconfigurationsupport-property-servernetworkprotocol-class"></a>MultiIpConfigurationSupport-Eigenschaft (ServerNetworkProtocol-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ruft die boolesche Eigenschaft ab, die angibt, ob mehrere IP-Adressen von einem Servernetzwerkprotokoll unterstützt werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.MultiIpConfigurationSupport [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [ProtocolName-Eingenschaftsobjekt (ServerNetworkProtocol-Klasse)](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/protocolname-property-servernetworkprotocol-class.md) , das das Netzwerkprotokoll darstellt, das von der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verwendet wird.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein boleescher Wert, der angibt, ob mehrere IP-Adressen vom Server-Netzwerkprotokoll unterstützt werden: **true** , wenn mehrere IP-Adressen vom Server-Netzwerkprotokoll unterstützt werden, bzw. **false** , wenn das Server-Netzwerkprotokoll nicht mehrere IP-Adressen unterstützt.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
