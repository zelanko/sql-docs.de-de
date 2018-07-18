---
title: SMO-Objektmodell | Microsoft-Dokumentation
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
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e31e4efa6ee0655d50567a7da73e85cc811c6692
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175867"
---
# <a name="smo-object-model"></a>SMO-Objektmodell
  Das SMO-Objektmodell besteht aus einer Hierarchie von Objekten. Das <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt ist das Objekt oberster Ebene, und alle Instanzklassenobjekte befinden sich unter dem <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Klasse ist eine Klasse oberster Ebene mit einer separaten Objekthierarchie. Die <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> -Objekt stellt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Diensten und Netzwerkeinstellungen, die über den WMI-Anbieter verfügbar.  
  
 Neben den <xref:Microsoft.SqlServer.Management.Smo.Server>- und <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Objekten gibt es mehrere Hilfsklassen, die Tasks oder Vorgänge darstellen, beispielsweise <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup> und <xref:Microsoft.SqlServer.Management.Smo.Restore>.  
  
 Das SMO-Objektmodell besteht aus mehreren Namespaces. Weitere Informationen finden Sie unter [SMO-Namespaces](smo-object-model-namespaces.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Diagramm des SMO-Objektmodells](smo-object-model-diagram.md)   
 [SMO-Namespaces](smo-object-model-namespaces.md)   
 [Konzepte des WMI-Anbieters für die Konfigurationsverwaltung](../wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
