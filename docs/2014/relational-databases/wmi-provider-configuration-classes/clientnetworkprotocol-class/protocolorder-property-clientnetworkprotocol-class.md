---
title: ProtocolOrder-Eigenschaft (ClientNetworkProtocol-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
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
ms.openlocfilehash: 0a0043e5a894e3f3f1b778a6f42fe6e3bacbbc78
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63192885"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a>ProtocolOrder-Eigenschaft (ClientNetworkProtocol-Klasse)
  Ruft die fortlaufende Nummer des Netzwerkprotokolls ab, auf das aktuell verwiesen wird. Dies erfolgt gemäß der [SetOrderValue-Methode (ClientNetworkProtocol Class)](clientnetworkprotocol-class.md) -Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 A [ClientNetworkProtocol-Klassenobjekt](clientnetworkprotocol-class.md) , das das vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32`-Wert, der die fortlaufende Nummer des derzeitig referenzierten Clientnetzwerkprotokolls angibt, das durch die `OrderValue`-Methode festgelegt ist. Wenn das Clientnetzwerkprotokoll deaktiviert ist, ist dieser Wert Null.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)   
 [Konfigurieren von Clientnetzwerkprotokollen und Netzwerkbibliotheken](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
