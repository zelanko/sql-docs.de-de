---
title: SetStringValue-Methode (ServerNetworkProtocolProperty-Klasse) | Microsoft-Dokumentation
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
- SetStringValue Method (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetStringValue method
ms.assetid: 0911df30-55f7-4fca-a1fb-01d2c91c1467
caps.latest.revision: 30
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 4bcb4cc8b3c5aee29dca2eee17b34992c93ff2d1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37264256"
---
# <a name="setstringvalue-method-servernetworkprotocolproperty-class"></a>SetStringValue-Methode (ServerNetworkProtocolProperty-Klasse)
  Legt den Zeichenfolgenwert der Eigenschaft fest, auf die verwiesen wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SetStringValue(  
StrValue  
)  
  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 A [ServerNetworkProtocolProperty-Klassenobjekt](servernetworkprotocolproperty-class.md) , das ein Attribut des Netzwerkprotokolls in der Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Description|  
|---------------|-----------------|  
|*StrValue gespeichert*|Ein Zeichenfolgenwert, der den neuen Wert der aktuellen Eigenschaft angibt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32` -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert 1, wenn die Anforderung nicht unterstützt wird, wurde, und jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](http://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
