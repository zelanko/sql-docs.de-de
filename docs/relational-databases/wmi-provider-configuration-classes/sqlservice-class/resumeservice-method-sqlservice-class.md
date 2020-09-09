---
description: ResumeService-Methode (SqlService-Klasse)
title: ResumeService-Methode (SqlService)
ms.custom: seo-lt-2019
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ResumeService Method (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ResumeService method
ms.assetid: 0b0a5f08-b95e-4626-bf81-309da7a0aacd
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b5c533cde7bccdbf198e207e6026beb0404f19cd
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542828"
---
# <a name="resumeservice-method-sqlservice-class"></a>ResumeService-Methode (SqlService-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Versucht, den Dienst fortzusetzen.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.ResumeService()  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein uint32 -Wert, der 0 beträgt, wenn die **ResumeService** -Anforderung angenommen wurde. Der Wert beträgt 1, wenn die Anforderung nicht unterstützt wird; jede andere Zahl gibt einen Fehler an.  
  
## <a name="remarks"></a>Hinweise  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
