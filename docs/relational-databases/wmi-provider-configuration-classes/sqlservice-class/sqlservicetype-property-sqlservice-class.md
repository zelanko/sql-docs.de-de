---
title: SqlServiceType-Eigenschaft (SqlService-Klasse) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- SqlServiceType Property (SqlService Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- SqlServiceType property
ms.assetid: dbff2968-3011-41d6-a141-52d814af0213
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 778316994f607201d45f93c60f9c57a9dce4160c
ms.sourcegitcommit: 20d24654e056561fc33cadc25eca8b4e7f214b1b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67351595"
---
# <a name="sqlservicetype-property-sqlservice-class"></a>SqlServiceType-Eigenschaft (SqlService-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft den Typ des verwalteten Diensts ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SqlServiceType [= value]  
```  
  
## <a name="parts"></a>Teile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
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
  
  
