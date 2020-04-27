---
title: State-Eigenschaft (SqlService-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- State Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- State property
ms.assetid: 9e09f419-947c-4d4b-9a49-2d3396c847cd
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: cc1484a09929f4e4a8534b2c2acac2089adfbb97
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62912185"
---
# <a name="state-property-sqlservice-class"></a>State-Eigenschaft (SqlService-Klasse)
  Ruft den aktuellen Zustand des Diensts ab oder legt diesen fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.State [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SqlService-Klassenobjekt](sqlservice-class.md) , das den Dienst darstellt.  
  
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
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
