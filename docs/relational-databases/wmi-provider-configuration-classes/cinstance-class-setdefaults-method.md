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
ms.openlocfilehash: 2a99b8bbc94bf8e62cd8125e01327a4691a296cb
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545313"
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
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von Clientprotokollen](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
