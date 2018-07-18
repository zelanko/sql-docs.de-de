---
title: PropertyIdx-Eigenschaftswert (ClientNetworkProtocolProperty-Klasse) | Microsoft-Dokumentation
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
- PropertyIdx Property (ClientNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyIdx property
ms.assetid: d7845962-ac68-4435-9c59-70ec450fec88
caps.latest.revision: 29
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 331827dfd16ed941d903b5e877cb9c31b7ccc621
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37186187"
---
# <a name="propertyidx-property-clientnetworkprotocolproperty-class"></a>PropertyIdx-Eigenschaft (ClientNetworkProtocolProperty-Klasse)
  Ruft den Indexwert der Eigenschaft in dem Eigenschaftsarray ab, auf das durch die [Properties-Eigenschaft (ClientNetworkProtocol-Klasse)](../clientnetworkprotocol-class/clientnetworkprotocol-class.md) des [ClientNetworkProtocol-Klassenobjekts](../clientnetworkprotocol-class/clientnetworkprotocol-class.md) verwiesen wird, oder legt diesen fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.PropertyIdx [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 A [ClientNetworkProtocolProperty-Klassenobjekt](clientnetworkprotocolproperty-class.md) , das ein Attribut des vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendeten Netzwerkprotokolls darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32`-Wert, der den Array-Indexwert der aktuellen Eigenschaft angibt.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Clientprotokollen](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
  
