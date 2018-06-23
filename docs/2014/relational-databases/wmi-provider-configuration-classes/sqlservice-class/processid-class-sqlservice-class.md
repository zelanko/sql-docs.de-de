---
title: ProcessId-Klasse (SqlService-Klasse) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ProcessId Class (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProcessId property
ms.assetid: 99b5a2e9-b44a-48a0-993e-04bd15c7fef4
caps.latest.revision: 35
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0acd413899fb51d5a5670352c4638f8f5552f59a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36161096"
---
# <a name="processid-class-sqlservice-class"></a>ProcessId-Klasse (SqlService-Klasse)
  Ruft die Systemprozess-ID ab, die einen Dienst eindeutig identifiziert.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.ProcessId [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SqlService-Klassenobjekt](sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein `uint32`-Wert, der die ID zur eindeutigen Kennzeichnung des Prozesses angibt.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
  
```  
mysqlservice.ProcessId = 324  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](http://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  