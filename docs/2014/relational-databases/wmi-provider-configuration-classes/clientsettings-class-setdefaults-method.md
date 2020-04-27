---
title: SetDefaults-Methode (ClientSettings-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (ClientSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: 056508f3-a5c8-467c-a196-dc1ef1f5178f
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: ce71d591dc8f72e6826f7bcd96628fb1898fd7bd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63242952"
---
# <a name="setdefaults-method-clientsettings-class"></a>SetDefaults-Methode (ClientSettings-Klasse)
  Legt alle Standardwerte für die Instanz des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clients fest, wobei die Option zum Überschreiben vorhandener Daten besteht.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein `ClientSettings`-Objekt, das eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Clientinstanz darstellt.  
  
#### <a name="parameters"></a>Parameter  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|*Overschreiteall*|Ein boolescher Wert, der angibt, ob vorhandene Werte für die Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Clients überschrieben werden sollen. `true`, um vorhandene Daten zu überschreiben, `false`, wenn vorhandene Daten nicht überschrieben werden sollen.|  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32`-Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
