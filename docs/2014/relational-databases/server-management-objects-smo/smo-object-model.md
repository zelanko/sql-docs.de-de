---
title: SMO-Objektmodell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 637c60fd6d7ba53087a145135d7152066983b644
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "63130617"
---
# <a name="smo-object-model"></a>SMO-Objektmodell
  Das SMO-Objektmodell besteht aus einer Hierarchie von Objekten. Das <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt ist das Objekt oberster Ebene, und alle Instanzklassenobjekte befinden sich unter dem <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Klasse ist eine Klasse oberster Ebene mit einer separaten Objekthierarchie. Das <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> -Objekt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stellt Dienste und Netzwerkeinstellungen dar, die über den WMI-Anbieter verfügbar sind.  
  
 Neben den <xref:Microsoft.SqlServer.Management.Smo.Server>- und <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Objekten gibt es mehrere Hilfsklassen, die Tasks oder Vorgänge darstellen, beispielsweise <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup> und <xref:Microsoft.SqlServer.Management.Smo.Restore>.  
  
 Das SMO-Objektmodell besteht aus mehreren Namespaces. Weitere Informationen finden Sie unter [SMO-Namespaces](smo-object-model-namespaces.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SMO-Objektmodell Diagramm](smo-object-model-diagram.md)   
 [SMO-Namespaces](smo-object-model-namespaces.md)   
 [Konzepte des WMI-Anbieters für die Konfigurationsverwaltung](../wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
