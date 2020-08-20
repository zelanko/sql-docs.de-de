---
description: SetServiceAccountPassword-Methode (SqlService-Klasse)
title: SetServiceAccountPassword-Methode (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SetServiceAccountPassword Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SetServiceAccountPassword method
ms.assetid: e577a1ac-985c-4799-bb38-9393efc3def2
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 18f83f130abc935bdfcff62d2f3b46087ee83a48
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488374"
---
# <a name="setserviceaccountpassword-method-sqlservice-class"></a>SetServiceAccountPassword-Methode (SqlService-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ändert das Kennwort für das Konto, unter dem der referenzierte Dienst ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetServiceAccountPassword(AccountOldPassword , ServiceStartPassword)  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
#### <a name="parameters"></a>Parameter  
 *Accountoldpassword*  
 Ein Zeichenfolgenwert, der das bestehende Kennwort für das Konto angibt.  
  
 *Servicestartpassword*  
 Ein Zeichenfolgenwert, der das neue Kennwort für das Konto angibt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein **uint32** -Wert, der 0 beträgt, wenn der Dienst erfolgreich geändert wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Bemerkungen  
  
