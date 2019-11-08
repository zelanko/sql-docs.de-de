---
title: ProtocolDLL-Eigenschaft (ServerNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolDLL Property (ServerNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolDLL property
ms.assetid: ac386558-392e-46f3-97f8-382f267b7fca
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3cbf2d7968f1e0af97cf28604768b01fb27511cf
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2019
ms.locfileid: "73659444"
---
# <a name="protocoldll-property-servernetworkprotocol-class"></a>ProtocolDLL-Eigenschaft (ServerNetworkProtocol-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft den Namen der .dll-Datei ab, die von einem Servernetzwerkprotokoll benötigt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ProtocolDLL [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ServerNetworkProtocol-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocol-class/servernetworkprotocol-class.md) , das das Netzwerkprotokoll darstellt, das von der Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]verwendet wird.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Zeichenfolgewert, der den Namen der -dll-Datei angibt, die vom Server-Netzwerkprotokoll benötigt wird.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Server Netzwerkprotokollen und Netzwerk Bibliotheken](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
