---
title: Properties-Eigenschaft (ServerNetworkProtocol-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ae37baf258fc5dee6b5adc75be7f2637e22a0353
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48121890"
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
  
