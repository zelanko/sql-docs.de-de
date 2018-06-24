---
title: ProtocolDLL-Eigenschaft (ClientNetworkProtocol-Klasse) | Microsoft Docs
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
- ProtocolDLL Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProtocolDLL property
ms.assetid: fe8650d5-7b9d-46f8-bf74-baf1d9d2a06a
caps.latest.revision: 36
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 74bbd7e6129856a915ff6c0205e85b68605e0b15
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048688"
---
# <a name="protocoldll-property-clientnetworkprotocol-class"></a>ProtocolDLL-Eigenschaft (ClientNetworkProtocol-Klasse)
  Ruft den Namen der DLL-Datei ab, die von dem in [Konfigurieren von Clientprotokollen](http://technet.microsoft.com/library/ms181035.aspx)angegebenen Netzwerkprotokoll benötigt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.ProtocolDLL [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 A [ClientNetworkProtocol-Klassenobjekt](clientnetworkprotocol-class.md) , das das vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Zeichenfolgewert, der den Namen der -dll-Datei angibt, die vom Clientnetzwerkprotokoll benötigt wird.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Clientnetzwerkprotokollen und Netzwerkbibliotheken](http://technet.microsoft.com/library/ms181035.aspx)  
  
  