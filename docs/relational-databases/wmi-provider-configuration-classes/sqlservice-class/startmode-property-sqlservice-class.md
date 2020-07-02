---
title: StartMode-Eigenschaft (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- StartMode Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- StartMode property
ms.assetid: c0c2c7f8-d4ae-44f2-ad8e-aecfcb7c2878
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 1adda63135bc85ae2d8a84a8e8744b04144781de
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85662119"
---
# <a name="startmode-property-sqlservice-class"></a>StartMode-Eigenschaft (SqlService-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/applies-to-version/sqlserver.md)]
  Ruft den Startmodus des Dienstes ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.StartMode [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein uint32-Wert, der den Modus des Diensts angibt.  
  
 Folgende Werte sind möglich:  
  
 Start  
 Wert = 0. Dienst wurde durch das Betriebssystemladeprogramm gestartet. Diese Option ist nur für Treiberdienste gültig.  
  
 System  
 Wert = 1. Der Dienst wurde von der **IoInitSystem** -Methode gestartet. Diese Option ist nur für Treiberdienste gültig.  
  
 Automatische  
 Wert = 2. Der Dienst soll während des Systemstarts automatisch vom Dienstkontroll-Manager gestartet werden.  
  
 Manuell  
 Wert = 3. Der Dienst, der vom Computer-Manager gestartet werden soll, wenn ein Prozess die **StartService** -Methode aufruft.  
  
 Disabled  
 Wert = 4. Der Dienst kann nicht gestartet werden.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
