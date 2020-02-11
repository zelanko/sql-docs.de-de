---
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: db0a9b0d2461e392f981ba3699a9efd3c1f3f8f3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "73660877"
---
# <a name="sqlservicetype-property-sqlservice-class"></a>SqlServiceType-Eigenschaft (SqlService-Klasse)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Ruft den Typ des verwalteten Diensts ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
  
object.SqlServiceType [= value]  
```  
  
## <a name="parts"></a>Bestandteile  
 *Objekt*  
 Ein [SqlService-Klassen](../../../relational-databases/wmi-provider-configuration-classes/sqlservice-class/sqlservice-class.md) Objekt, das den Dienst darstellt.  
  
## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert  
 Ein uint32-Wert, der den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Diensttyp angibt.  
  
## <a name="remarks"></a>Bemerkungen  
 Folgenden Rückgabewerte sind möglich:  
  
|type|Definition|  
|----------|----------------|  
|*1*|MSSQLSERVER ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst.|  
|*2*|SQLSERVERAGENT ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Agent-Dienst.|  
|*€*|MSFTESQL ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Dienst für die Volltextsuch-Engine.|  
|*4*|MsDtsServer ist der [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] -Dienst.|  
|*5@@*|MSSQLServerOLAPService ist der [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] -Dienst.|  
|*6*|ReportServer ist der [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] -Dienst.|  
|*19.00*|SQLBrowser ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Browser-Dienst.|  
|*88*|NSService ist der [!INCLUDE[ssNoVersion](../../../includes/ssns-md.md)] Benachrichtigungsdienst.|  
|*21.00*|MSSQLFDLauncher ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Start Programm Dienst des Volltextfilterdaemons.|  
|*€*|Sqlpbengine ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] polybase-Engine-Dienst.|  
|*11*|Sqlpbdms ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] polybase-Daten Verschiebungs Dienst.|  
|*12*|Mssqllaunchpad ist der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Launchpad-Dienst.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Starten und Beenden von Diensten](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
