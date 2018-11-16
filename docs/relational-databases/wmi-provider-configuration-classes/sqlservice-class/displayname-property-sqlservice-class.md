---
title: DisplayName-Eigenschaft (SqlService-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- DisplayName Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- DisplayName property
ms.assetid: 49c408aa-6eb4-45cd-8d5c-60f065f24f5c
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: c4f58ea7caad7c07d0ab818627d2bbbb21632e5c
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51669710"
---
# <a name="displayname-property-sqlservice-class"></a>DisplayName-Eigenschaft (SqlService-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft den Anzeigenamen des Dienstes ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.DisplayName [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein Zeichenfolgenwert, der den Anzeigenamen des Diensts angibt.  
  
## <a name="remarks"></a>Hinweise  
 Die maximale Länge der Zeichenfolge beträgt 256 Zeichen. Die Schreibweise des Namens wird im [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Konfigurations-Manager beibehalten. Jedoch wird bei Vergleichen des Anzeigenamens immer nach Groß- und Kleinschreibung unterschieden.  
  
## <a name="example"></a>Beispiel  
  
```  
mysqlservice.DisplayName = "Atdisk"  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
