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
ms.openlocfilehash: 0438ea784bc8d1521455e0d5e7b9970dafe02fd4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73660087"
---
# <a name="setordervalue-method-clientnetworkprotocol-class"></a>SetOrderValue-Methode (ClientNetworkProtocol-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Wählt das Protokoll mit dem angegebenen Reihenfolgenwert aus der Clientprotokollliste aus.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetOrderValue(OrderValue)  
```  
  
## <a name="parts"></a>Bestandteile  
 *Objekt*  
 Ein [ClientNetworkProtocol-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , das das vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Client verwendete Netzwerkprotokoll darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*OrderValue*|Ein u**int32** -Wert, der den Reihenfolgenwert festlegt.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **UInt32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird, und jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Eigenschaften der Clientprotokolle (Registerkarte Reihenfolge)](https://technet.microsoft.com/library/ms187884.aspx)  
  
  
