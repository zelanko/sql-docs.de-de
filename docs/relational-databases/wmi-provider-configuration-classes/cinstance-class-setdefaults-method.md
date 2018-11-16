---
title: SetDefaults-Methode (CInstance-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetDefaults Method (CInstance Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 021d213ac83c02be7811fa3b5ea1ec470dfd527e
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51664330"
---
# <a name="cinstance-class---setdefaults-method"></a>CInstance-Klasse – SetDefaults-Methode
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Legt alle Standardwerte für die Instanz des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clients fest, wobei die Option zum Überschreiben vorhandener Daten besteht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [CInstance-Klassenobjekt](../../relational-databases/wmi-provider-configuration-classes/cinstance-class.md) , das eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clientinstanz darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Description|  
|---------------|-----------------|  
|*OverwriteAll*|Ein boleescher Wert, der angibt, ob vorhandene Werte in der Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clients überschreiben werden sollen: **true** zum Überschreiben bestehender Daten oder **false** , wenn vorhandene Daten nicht überschrieben werden sollen.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
