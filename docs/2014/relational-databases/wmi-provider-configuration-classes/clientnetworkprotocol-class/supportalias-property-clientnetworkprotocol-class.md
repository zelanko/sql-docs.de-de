---
title: SupportAlias-Eigenschaft (ClientNetworkProtocol-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
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
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d28ec166f8954b874f98b7f9f441280ab9064f1f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62826756"
---
# <a name="supportalias-property-clientnetworkprotocol-class"></a>SupportAlias-Eigenschaft (ClientNetworkProtocol-Klasse)
  Ruft die boolesche Eigenschaft ab, die angibt, ob das durch die [SetOrderValue-Methode (ClientNetworkProtocol-Klasse)](clientnetworkprotocol-class.md) angegebene aktuelle Netzwerkprotokoll Aliase unterstützt.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SupportAlias [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *Objekt*  
 Ein [ClientNetworkProtocol-Klassenobjekt](clientnetworkprotocol-class.md) , das das vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein boolescher Wert, der angibt, ob das Clientnetzwerkprotokoll Aliase unterstützt.  
  
 Wenn der Wert "True" lautet, unterstützt das Clientnetzwerkprotokoll Aliase.  
  
 Wenn der Wert "False" lautet, unterstützt das Clientnetzwerkprotokoll keine Aliase.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
