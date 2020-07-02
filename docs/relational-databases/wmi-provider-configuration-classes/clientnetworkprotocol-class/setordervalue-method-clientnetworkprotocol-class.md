---
title: Setup Value-Methode (ClientNetworkProtocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetOrderValue Method (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetOrderValue method
ms.assetid: 15f693fd-37f6-41d9-9dab-d2c93db19895
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6ee8f5897a8a5e1fed47005220321be98eca92ae
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85756597"
---
# <a name="setordervalue-method-clientnetworkprotocol-class"></a>SetOrderValue-Methode (ClientNetworkProtocol-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Wählt das Protokoll mit dem angegebenen Reihenfolgenwert aus der Clientprotokollliste aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetOrderValue(OrderValue)  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 A [ClientNetworkProtocol-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , das das vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*OrderValue*|Ein u**int32** -Wert, der den Reihenfolgenwert festlegt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Eigenschaften der Clientprotokolle (Registerkarte Reihenfolge)](https://technet.microsoft.com/library/ms187884.aspx)  
  
  
