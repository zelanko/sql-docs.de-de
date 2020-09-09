---
description: Properties-Eigenschaft (ClientNetworkProtocol-Klasse)
title: Properties-Eigenschaft (ClientNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Properties Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Properties property
ms.assetid: 7e0a4e38-4555-4750-8fd3-4425b29e6aa1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ed706ebdeb3151911d20ba76c7317bdac3b27f58
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89537259"
---
# <a name="properties-property-clientnetworkprotocol-class"></a>Properties-Eigenschaft (ClientNetworkProtocol-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ruft die Eigenschaften ab, die dem aktuellen Clientnetzwerkprotokoll zugeordnet sind, das in [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)angegeben ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Properties [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ClientNetworkProtocol-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , das das vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Array von [ClientNetworkProtocolProperty-Klassenobjekten](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) , die die vom aktuellen Clientnetzwerkprotokoll, auf das durch die **OrderValue** -Eingenschaft verwiesen wird, unterstützten Eigenschaften darstellen.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientnetzwerkprotokollen und Netzwerkbibliotheken](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
