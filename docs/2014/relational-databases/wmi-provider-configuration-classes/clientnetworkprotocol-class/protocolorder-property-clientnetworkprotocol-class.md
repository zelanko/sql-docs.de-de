---
title: ProtocolOrder-Eigenschaft (ClientNetworkProtocol-Klasse) | Microsoft Docs
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
- ProtocolOrder Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
caps.latest.revision: 34
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 388244724effee38b849742d211c446d3493d799
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048686"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a>ProtocolOrder-Eigenschaft (ClientNetworkProtocol-Klasse)
  Ruft die Nummer des derzeitig referenzierten Clients Netzwerkprotokoll entsprechend den Angaben von der [SetOrderValue-Methode (ClientNetworkProtocol-Klasse)](clientnetworkprotocol-class.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 A [ClientNetworkProtocol-Klassenobjekt](clientnetworkprotocol-class.md) , das das vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32` Wert, der angibt, die Nummer des derzeitig referenzierten clientnetzwerkprotokolls Isolationstransaktionen gemäß der `OrderValue` Methode. Wenn das Clientnetzwerkprotokoll deaktiviert ist, ist dieser Wert Null.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Clientprotokollen](http://technet.microsoft.com/library/ms181035.aspx)   
 [Konfigurieren von Clientnetzwerkprotokollen und Netzwerkbibliotheken](http://technet.microsoft.com/library/ms181035.aspx)  
  
  