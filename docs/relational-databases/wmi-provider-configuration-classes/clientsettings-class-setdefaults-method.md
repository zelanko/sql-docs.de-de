---
title: SetDefaults-Methode (Client Settings)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (ClientSettings Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: 056508f3-a5c8-467c-a196-dc1ef1f5178f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ee4fec9752a83fdda757b6ac50f5afddcdcb1efa
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85759889"
---
# <a name="clientsettings-class---setdefaults-method"></a>ClientSettings-Klasse – SetDefaults-Methode
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]
  Legt alle Standardwerte für die Instanz des- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Clients fest, wobei die Option zum Überschreiben vorhandener Daten besteht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein **ClientSettings** -Objekt, das eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clientinstanz darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*Overschreiteall*|Ein boolescher Wert, der angibt, ob vorhandene Werte für die Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clients überschrieben werden sollen. **true** , um vorhandene Daten zu überschreiben, **false** , wenn vorhandene Daten nicht überschrieben werden sollen.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
