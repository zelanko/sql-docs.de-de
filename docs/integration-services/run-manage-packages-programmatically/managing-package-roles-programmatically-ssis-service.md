---
description: Programmgesteuertes Verwalten von Paketrollen (SSIS-Dienst)
title: Programmgesteuertes Verwalten von Paketrollen (SSIS-Dienst) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 33922748916193e875799839fbbf6fe0f7a76a26
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2020
ms.locfileid: "88495521"
---
# <a name="managing-package-roles-programmatically-ssis-service"></a>Programmgesteuertes Verwalten von Paketrollen (SSIS-Dienst)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Wenn Sie programmgesteuert mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paketen arbeiten, möchten Sie möglicherweise bestimmen, welche Rollen für die Anwendung auf Pakete verfügbar sind, oder die Rollen, die auf ein einzelnes Paket angewendet werden, bestimmen oder festlegen. Die <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse des <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace stellt eine Reihe von Methoden bereit, die diese Anforderungen erfüllen.  
  
 Rollen gelten nur für Pakete, die in der -Datenbank [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb** gespeichert sind. Weitere Informationen zu Paketrollen finden Sie unter [Integration Services-Rollen &#40;SSIS-Dienst&#41;](../../integration-services/security/integration-services-roles-ssis-service.md).  
  
 Alle in diesem Thema erläuterten Methoden erfordern einen Verweis auf die **Microsoft.SqlServer.ManagedDTS** -Assembly. Nachdem Sie den Verweis in einem neuen Projekt hinzugefügt haben, importieren Sie den <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace mit einer **using**- oder **Imports**-Anweisung.  
  
> [!IMPORTANT]  
>  Die Methoden der <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse zum Arbeiten mit dem SSIS-Paketspeicher unterstützen nur „.“, localhost oder den Namen des lokalen Servers. Sie können "(local)" nicht verwenden.  
  
## <a name="determining-which-roles-are-available"></a>Bestimmen, welche Rollen verfügbar sind  
 Um zu bestimmen, welche Rollen für die auf einem bestimmten Server gespeicherten Pakete verfügbar sind, rufen Sie die <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse auf.  
  
## <a name="determining-which-roles-are-assigned"></a>Bestimmen, welche Rollen zugewiesen sind  
 Um zu bestimmen, welche Rollen einem bestimmten Paket bereits zugewiesen wurden, rufen Sie die <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A>-Methode auf. Rufen Sie die <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A>-Methode auf, um einem Paket Rollen zuzuweisen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration Services-Rollen &#40;SSIS-Dienst&#41;](../../integration-services/security/integration-services-roles-ssis-service.md)  
  
  
