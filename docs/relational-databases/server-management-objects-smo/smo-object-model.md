---
title: SMO-Objektmodell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 186343e4c9bc594593ff3efee40e6a09f68e5422
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86000306"
---
# <a name="smo-object-model"></a>SMO-Objektmodell
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Das SMO-Objektmodell besteht aus einer Hierarchie von Objekten. Das <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt ist das Objekt oberster Ebene, und alle Instanzklassenobjekte befinden sich unter dem <xref:Microsoft.SqlServer.Management.Smo.Server>-Objekt.  
  
 Die <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Klasse ist eine Klasse oberster Ebene mit einer separaten Objekthierarchie. Das <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> -Objekt stellt [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Dienste und Netzwerkeinstellungen dar, die über den WMI-Anbieter verfügbar sind.  
  
 Neben den <xref:Microsoft.SqlServer.Management.Smo.Server>- und <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>-Objekten gibt es mehrere Hilfsklassen, die Tasks oder Vorgänge darstellen, beispielsweise <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup> und <xref:Microsoft.SqlServer.Management.Smo.Restore>.  
  
 Das SMO-Objektmodell besteht aus mehreren Namespaces. Weitere Informationen finden Sie unter [SMO-Namespaces](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [SMO-Objektmodell Diagramm](../../relational-databases/server-management-objects-smo/smo-object-model-diagram.md)   
 [SMO-Namespaces](../../relational-databases/server-management-objects-smo/smo-object-model-namespaces.md)   
 [Konzepte des WMI-Anbieters für die Konfigurationsverwaltung](../../relational-databases/wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
