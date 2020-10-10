---
description: ProtocolOrder-Eigenschaft (ClientNetworkProtocol-Klasse)
title: ProtocolOrder-Eigenschaft (ClientNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolOrder Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolOrder property
ms.assetid: aa09b8ab-37db-4406-8973-acf503855fd2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 40ebe80960ca238cce4ff923a2e2457c45cd77f5
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91889174"
---
# <a name="protocolorder-property-clientnetworkprotocol-class"></a>ProtocolOrder-Eigenschaft (ClientNetworkProtocol-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ruft die fortlaufende Nummer des Netzwerkprotokolls ab, auf das aktuell verwiesen wird. Dies erfolgt gemäß der [SetOrderValue-Methode (ClientNetworkProtocol Class)](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/setordervalue-method-clientnetworkprotocol-class.md) -Methode.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ProtocolOrder [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ClientNetworkProtocol-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , das das vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der die fortlaufende Nummer des derzeitig referenzierten Clientnetzwerkprotokolls angibt, das durch die **OrderValue** -Methode festgelegt ist. Wenn das Clientnetzwerkprotokoll deaktiviert ist, ist dieser Wert Null.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Client Protokollen](../../../database-engine/configure-windows/configure-client-protocols.md)   
 [Konfigurieren von Clientnetzwerkprotokollen und Netzwerkbibliotheken](../../../database-engine/configure-windows/configure-client-protocols.md)  
  
