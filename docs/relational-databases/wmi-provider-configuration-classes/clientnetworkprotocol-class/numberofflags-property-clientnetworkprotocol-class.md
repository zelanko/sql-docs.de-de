---
description: NumberOfFlags-Eigenschaft (ClientNetworkProtocol-Klasse)
title: Numofflags-Eigenschaft (ClientNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- NumberOfFlags Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- NumberOfFlags property
ms.assetid: 7a656644-2154-419f-9787-99877f597770
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9b56924909094c7bf99281118a1c4540dfa20129
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89522444"
---
# <a name="numberofflags-property-clientnetworkprotocol-class"></a>NumberOfFlags-Eigenschaft (ClientNetworkProtocol-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ruft die Anzahl der Flagoptionen ab, die das von der [SetOrderValue-Methode (ClientNetworkProtocol-Klasse)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md)angegeben Clientnetzwerkprotokoll erfordert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.NumberofFlags [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ClientNetworkProtocol-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , das das vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **Uint32** -Wert, der die Anzahl der Flagoptionen angibt, die das Clientnetzwerkprotokoll erfordert, auf das die **OrderValue** -Eigenschaft verweist.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
