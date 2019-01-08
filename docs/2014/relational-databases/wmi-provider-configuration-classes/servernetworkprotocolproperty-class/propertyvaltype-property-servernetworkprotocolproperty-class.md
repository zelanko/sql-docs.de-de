---
title: PropertyValType-Eigenschaft (ServerNetworkProtocolProperty-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- PropertyValType Property (ServerNetworkProtocolProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyValType property
ms.assetid: fbd42e8e-0642-4a19-b3c8-6ce88345145f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 4a69cb8f0817c086537381a87b96dfb237b8d59c
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53359002"
---
# <a name="propertyvaltype-property-servernetworkprotocolproperty-class"></a>PropertyValType-Eigenschaft (ServerNetworkProtocolProperty-Klasse)
  Ruft den Datentyp des Werts ab, der in der referenzierten Eigenschaft enthalten ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.PropertyValType [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 A [ServerNetworkProtocolProperty-Klassenobjekt](servernetworkprotocolproperty-class.md) , das ein Attribut des Netzwerkprotokolls in der Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32`-Wert, der den Datentyp des Eigenschaftswerts angibt. Bei einem Zeichenfolgenwert wird 0 und bei einem numerischen Typ 1 zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
