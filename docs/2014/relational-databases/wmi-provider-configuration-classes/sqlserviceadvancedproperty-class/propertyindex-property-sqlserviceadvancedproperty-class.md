---
title: PropertyIndex-Eigenschaft (SqlServiceAdvancedProperty-Klasse) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- PropertyIndex Property (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PropertyIndex property
ms.assetid: b18b45a2-e187-44f5-a8c9-26fd9828b6c6
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 81dca1e193545f060b3030c4c85e0f9765ee9b67
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36049865"
---
# <a name="propertyindex-property-sqlserviceadvancedproperty-class"></a>PropertyIndex-Eigenschaft (SqlServiceAdvancedProperty-Klasse)
  Ruft den Eigenschaftsindex ab, der die Position einer erweiterten Eigenschaft in einem Array erweiterter Eigenschaften angibt, das zu einem referenzierten Dienst gehört, oder legt diesen fest.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.PropertyIndex [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein Objekt der [SqlServiceAdvancedProperty-Klasse](sqlserviceadvancedproperty-class.md) , das eine erweiterte Eigenschaft darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32` Wert, der die Position der erweiterten Eigenschaft in dem Array erweiterter Eigenschaften angibt, die zu einem referenzierten Dienst gehört.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  