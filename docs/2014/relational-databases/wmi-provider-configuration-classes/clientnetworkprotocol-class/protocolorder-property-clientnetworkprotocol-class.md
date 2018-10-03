---
title: ProtocolOrder-Eigenschaft (ClientNetworkProtocol-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
api_name:
- ProtocolOrder Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: de7284c4023f7e658c37794d670356fd5b9c4025
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152460"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a>ProtocolOrder-Eigenschaft (ClientNetworkProtocol-Klasse)
  Ruft die fortlaufende Nummer des derzeitig referenzierten Client-Netzwerkprotokoll gemäß der [SetOrderValue-Methode (ClientNetworkProtocol Class)](clientnetworkprotocol-class.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 A [ClientNetworkProtocol-Klassenobjekt](clientnetworkprotocol-class.md) , das das vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32` Wert, der die fortlaufende Nummer des derzeitig referenzierten clientnetzwerkprotokolls angibt, mit der `OrderValue` Methode. Wenn das Clientnetzwerkprotokoll deaktiviert ist, ist dieser Wert Null.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Clientprotokollen](http://technet.microsoft.com/library/ms181035.aspx)   
 [Konfigurieren von Clientnetzwerkprotokollen und Netzwerkbibliotheken](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
