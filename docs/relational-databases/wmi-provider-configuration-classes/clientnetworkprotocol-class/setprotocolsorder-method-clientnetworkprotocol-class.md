---
title: SetProtocolsOrder-Methode (ClientNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetProtocolsOrder Method (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetProtocolsOrder method
ms.assetid: b86d98b9-aae4-4e74-b4da-1ec984d5c8b4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 93c4b91d6091cf8ed60cf7923d31460f37d5f4bb
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881058"
---
# <a name="setprotocolsorder-method-clientnetworkprotocol-class"></a>SetProtocolsOrder-Methode (ClientNetworkProtocol-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ändert die Reihenfolge der Protokollliste.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetProtocolsOrder(ProtocolOrderList)  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ClientNetworkProtocol-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , das das vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*Protocolorderlist*|Eine Zeichenfolgenarray, das die Clientnetzwerkprotokolle in der neuen Reihenfolge auflistet.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Client Protokollen](https://technet.microsoft.com/library/ms181035.aspx)   
 [Konfigurieren von Clientnetzwerkprotokollen und Netzwerkbibliotheken](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
