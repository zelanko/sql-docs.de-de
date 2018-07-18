---
title: Properties-Eigenschaft (ServerNetworkProtocol-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Properties Property (ServerNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Properties property
ms.assetid: 6c971bfc-c277-4c1e-a06e-146dcc34e759
caps.latest.revision: 29
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cf3384908284cb25a59c35451706b0e3e535e345
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157871"
---
# <a name="properties-property-servernetworkprotocol-class"></a>Properties-Eigenschaft (ServerNetworkProtocol-Klasse)
  Ruft die Eigenschaften ab, die dem Servernetzwerkprotokoll zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.Properties [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [ServerNetworkProtocol-Klassenobjekt](servernetworkprotocol-class.md) , das das Netzwerkprotokoll darstellt, das von der Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verwendet wird.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Array von [ServerNetworkProtocolProperty-Klassenobjekten](../servernetworkprotocolproperty-class/servernetworkprotocolproperty-class.md) , die die vom Server-Netzwerkprotokoll unterstützten Eigenschaften darstellen.  
  
## <a name="remarks"></a>Hinweise  
  
