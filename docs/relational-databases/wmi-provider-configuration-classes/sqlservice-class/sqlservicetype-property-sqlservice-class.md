---
description: SqlServiceType-Eigenschaft (SqlService-Klasse)
title: SqlServiceType-Eigenschaft (SqlService)
ms.custom: seo-lt-2019
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 685fb402647c7a757f7a894705cf7754d696b24d
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542811"
---
# <a name="sqlservicetype-property-sqlservice-class"></a>SqlServiceType-Eigenschaft (SqlService-Klasse)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Ruft den Typ des verwalteten Diensts ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SqlServiceType [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *object*  
 Ein [SqlService-Klassenobjekt](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) , das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein uint32-Wert, der den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Diensttyp angibt.  
  
## <a name="remarks"></a>Hinweise  
 Folgenden Rückgabewerte sind möglich:  
  
|type|Definition|  
|----------|----------------|  
|*1*|MSSQLSERVER ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst.|  
|*2*|SQLSERVERAGENT ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent-Dienst.|  
|*3*|MSFTESQL ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst für die Volltextsuch-Engine.|  
|*4*|MsDtsServer ist der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Dienst.|  
|*5*|MSSQLServerOLAPService ist der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Dienst.|  
|*6*|ReportServer ist der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Dienst.|  
|*7*|SQLBrowser ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Browser-Dienst.|  
|*8*|NSService ist der [!INCLUDE[ssNoVersion](../../../includes/ssns-md.md)] Benachrichtigungsdienst.|  
|*9*|MSSQLFDLauncher ist der Start Programm [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Dienst des Volltextfilterdaemons.|  
|*10*|Sqlpbengine ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] polybase-Engine-Dienst.|  
|*11*|Sqlpbdms ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] polybase-Daten Verschiebungs Dienst.|  
|*12*|Mssqllaunchpad ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Launchpad-Dienst.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
