---
title: Properties-Eigenschaft (ServerNetworkProtocol-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
apiname:
- Properties Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Properties property
ms.assetid: 6c971bfc-c277-4c1e-a06e-146dcc34e759
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 534841fba53cff3f06204b1acecb1e33e77f6248
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810288"
---
# <a name="properties-property-servernetworkprotocol-class"></a>Properties-Eigenschaft (ServerNetworkProtocol-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft die Eigenschaften ab, die dem Servernetzwerkprotokoll zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Properties [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [ServerNetworkProtocol-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md) , das das Netzwerkprotokoll darstellt, das von der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verwendet wird.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Array von [ServerNetworkProtocolProperty-Klassenobjekten](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolproperty-class/servernetworkprotocolproperty-class.md) , die die vom Server-Netzwerkprotokoll unterstützten Eigenschaften darstellen.  
  
## <a name="remarks"></a>Hinweise  
  
