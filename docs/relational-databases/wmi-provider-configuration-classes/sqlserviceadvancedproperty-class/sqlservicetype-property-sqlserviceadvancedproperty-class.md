---
title: SqlServiceType-Eigenschaft (SqlServiceAdvancedProperty-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SqlServiceType Property (SqlServiceAdvancedProperty Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServiceType property
ms.assetid: 20f1663a-9a14-4f14-8c1b-8aa133e272c3
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 440d7a0d90887d6a1bbeb9553306c5453c514d02
ms.sourcegitcommit: 20d24654e056561fc33cadc25eca8b4e7f214b1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67351577"
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a>SqlServiceType-Eigenschaft (SqlServiceAdvancedProperty-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft den Typ des verwalteten Diensts ab, der der erweiterten Eigenschaft zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SetBoolValue(NumValue)  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein Objekt der [SqlServiceAdvancedProperty-Klasse](../../../relational-databases/wmi-provider-configuration-classes/sqlserviceadvancedproperty-class/sqlserviceadvancedproperty-class.md) , das eine erweiterte Eigenschaft darstellt.  
  
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
|*8*|NsService ist die [!INCLUDE[ssNoVersion](../../../includes/ssns-md.md)] Benachrichtigungsdienst.|  
|*9*|MSSQLFDLauncher ist die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Volltext-Volltextfilterdaemon-Startprogrammdienst.|  
|*10*|SQLPBENGINE ist die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Polybase-Engine-Dienst.|  
|*11*|SQLPBDMS ist die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Polybase-datenverschiebung.|  
|*12*|MSSQLLaunchpad ist die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Launchpad-Dienst.|  
  
## <a name="see-also"></a>Siehe auch  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
