---
title: Aktivierte Eigenschaft (ServerNetworkProtocolIPAddress)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- Enabled Property (ServerNetworkProtocolIpAddress Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- Enabled property
ms.assetid: 870fd4d0-6c77-462a-b480-d42eb044b2e7
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a6a033243b552495734a9a3cc9aad69e0518d2c2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85786060"
---
# <a name="enabled-property-servernetworkprotocolipaddress-class"></a>Enabled-Eigenschaft (ServerNetworkProtocolIpAddress-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Ruft die boolesche Eigenschaft ab, die angibt, ob eine IP-Adresse aktiviert ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.Enabled [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ServerNetworkProtocolIPAdress-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/servernetworkprotocolipaddress-class/servernetworkprotocolipaddress-class.md) , das eine IP-Adresse für das Netzwerkprotokoll in der Instanz von [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein boleescher Wert, der angibt, ob die IP-Adresse aktiviert ist: **true** , wenn die IP-Adresse aktiviert ist, bzw. **false** , wenn die IP-Adresse deaktiviert ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Servernetzwerkprotokollen und Netzwerkbibliotheken](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
