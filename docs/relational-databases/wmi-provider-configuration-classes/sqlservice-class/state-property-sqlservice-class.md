---
description: State-Eigenschaft (SqlService-Klasse)
title: State-Eigenschaft (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- State Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 606c991cd1f5b20f888fc2a2bf9d500e4e5ec410
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88485074"
---
# <a name="state-property-sqlservice-class"></a>State-Eigenschaft (SqlService-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ruft den aktuellen Zustand des Diensts ab oder legt diesen fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.State [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein uint32-Wert, der den Zustand des Diensts angibt.  
  
 Folgende Werte sind möglich:  
  
 1  
 Beendet. Der -Dienst wurde beendet.  
  
 2  
 Start steht aus. Der Dienst wartet darauf, gestartet zu werden.  
  
 3  
 Beenden steht aus. Der Dienst wartet darauf, beendet zu werden.  
  
 4  
 Wird ausgeführt. Der Dienst wird ausgeführt.  
  
 5  
 Fortsetzung steht aus. Der Dienst wartet darauf, fortgesetzt zu werden.  
  
 6  
 Anhalten steht aus. Der Dienst wartet darauf, angehalten zu werden.  
  
 7  
 Angehalten. Der Dienst wurde angehalten.  
  
## <a name="remarks"></a>Bemerkungen  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
