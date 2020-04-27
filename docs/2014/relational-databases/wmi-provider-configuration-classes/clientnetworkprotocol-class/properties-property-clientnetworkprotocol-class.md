---
title: Properties-Eigenschaft (ClientNetworkProtocol-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Properties Property (ClientNetworkProtocol Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Properties property
ms.assetid: 7e0a4e38-4555-4750-8fd3-4425b29e6aa1
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: d6c2dbfb1254260f5c92df5f1da33ba26e368aa7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63192050"
---
# <a name="properties-property-clientnetworkprotocol-class"></a>Properties-Eigenschaft (ClientNetworkProtocol-Klasse)
  Ruft die Eigenschaften ab, die dem aktuellen Clientnetzwerkprotokoll zugeordnet sind, das in [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)angegeben ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.Properties [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ClientNetworkProtocol-Klassenobjekt](clientnetworkprotocol-class.md) , das das vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Array von [ClientNetworkProtocolProperty-Klassen](../clientnetworkprotocolproperty-class/clientnetworkprotocolproperty-class.md) Objekten, die die Eigenschaften darstellen, die vom aktuellen Client Netzwerkprotokoll unterstützt werden `OrderValue` , auf das von der-Eigenschaft verwiesen wird.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientnetzwerkprotokollen und Netzwerkbibliotheken](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
