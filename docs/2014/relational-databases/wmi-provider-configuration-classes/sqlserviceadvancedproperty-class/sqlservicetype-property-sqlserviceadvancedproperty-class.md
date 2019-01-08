---
title: SqlServiceType-Eigenschaft (SqlServiceAdvancedProperty-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SqlServiceType Property (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServiceType property
ms.assetid: 20f1663a-9a14-4f14-8c1b-8aa133e272c3
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 769ffe6b74c5b1cc4a2f21842df3e88a9df5af73
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/13/2018
ms.locfileid: "53363429"
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a>SqlServiceType-Eigenschaft (SqlServiceAdvancedProperty-Klasse)
  Ruft den Typ des verwalteten Diensts ab, der der erweiterten Eigenschaft zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object  
.SetBoolValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein Objekt der [SqlServiceAdvancedProperty-Klasse](sqlserviceadvancedproperty-class.md) , das eine erweiterte Eigenschaft darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein uint32-Wert, der den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Diensttyp angibt.  
  
## <a name="remarks"></a>Hinweise  
 Folgenden Rückgabewerte sind möglich:  
  
|Typ|Definition|  
|----------|----------------|  
|*1*|MSSQLSERVER ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst.|  
|*2*|SQLSERVERAGENT ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent-Dienst.|  
|*3*|MSFTESQL ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst für die Volltextsuch-Engine.|  
|*4*|MsDtsServer ist der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Dienst.|  
|*5*|MSSQLServerOLAPService ist der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Dienst.|  
|*6*|ReportServer ist der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Dienst.|  
|*7*|SQLBrowser ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Browser-Dienst.|  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
