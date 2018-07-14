---
title: SupportAlias-Eigenschaft (ClientNetworkProtocol-Klasse) | Microsoft-Dokumentation
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
- SupportAlias Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SupportAlias property
ms.assetid: 1e7a2e87-c356-40a6-a6d9-e492467629f9
caps.latest.revision: 16
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: bd18c837ca94878887bdf30fc0412dddff59cb83
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327550"
---
# <a name="supportalias-property-clientnetworkprotocol-class"></a>SupportAlias-Eigenschaft (ClientNetworkProtocol-Klasse)
  Ruft die boolesche Eigenschaft ab, die angibt, ob das durch die [SetOrderValue-Methode (ClientNetworkProtocol-Klasse)](clientnetworkprotocol-class.md) angegebene aktuelle Netzwerkprotokoll Aliase unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SupportAlias [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [ClientNetworkProtocol-Klassenobjekt](clientnetworkprotocol-class.md) , das das vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein boolescher Wert, der angibt, ob das Clientnetzwerkprotokoll Aliase unterstützt.  
  
 Wenn der Wert "True" lautet, unterstützt das Clientnetzwerkprotokoll Aliase.  
  
 Wenn der Wert "False" lautet, unterstützt das Clientnetzwerkprotokoll keine Aliase.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Clientprotokollen](http://technet.microsoft.com/library/ms181035.aspx)  
  
  
