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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9a0c29f72ab66f008dfe6ddfb87be054501aeb50
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545463"
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
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
