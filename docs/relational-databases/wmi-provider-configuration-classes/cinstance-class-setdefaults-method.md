---
description: CInstance-Klasse – SetDefaults-Methode
title: SetDefaults-Methode (CInstance)
ms.custom: seo-lt-2019
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 99771d12be4c10d8d4b823ceb788e9722d417fca
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2020
ms.locfileid: "91890980"
---
# <a name="cinstance-class---setdefaults-method"></a>CInstance-Klasse – SetDefaults-Methode
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Legt alle Standardwerte für die Instanz des- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Clients fest, wobei die Option zum Überschreiben vorhandener Daten besteht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetDefaults(OverwriteAll)  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [CInstance-Klassenobjekt](../../relational-databases/wmi-provider-configuration-classes/cinstance-class.md) , das eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clientinstanz darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|*Overschreiteall*|Ein boleescher Wert, der angibt, ob vorhandene Werte in der Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clients überschreiben werden sollen: **true** zum Überschreiben bestehender Daten oder **false** , wenn vorhandene Daten nicht überschrieben werden sollen.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientprotokollen](../../database-engine/configure-windows/configure-client-protocols.md)  
  
