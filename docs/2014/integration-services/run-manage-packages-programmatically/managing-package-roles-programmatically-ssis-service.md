---
title: Programmgesteuertes Verwalten von Paketrollen (SSIS-Dienst) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: dff54f3f90d9e008ae21c83c2a8fdc3f7440a5c3
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85422707"
---
# <a name="managing-package-roles-programmatically-ssis-service"></a>Programmgesteuertes Verwalten von Paketrollen (SSIS-Dienst)
  Wenn Sie programmgesteuert mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paketen arbeiten, möchten Sie möglicherweise bestimmen, welche Rollen für die Anwendung auf Pakete verfügbar sind, oder die Rollen, die auf ein einzelnes Paket angewendet werden, bestimmen oder festlegen. Die <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse des <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace stellt eine Reihe von Methoden bereit, die diese Anforderungen erfüllen.

 Rollen gelten nur für Pakete, die in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbank **msdb** gespeichert sind. Weitere Informationen zu Paketrollen finden Sie unter [Integration Services-Rollen &#40;SSIS-Dienst&#41;](../security/integration-services-roles-ssis-service.md).

 Alle in diesem Thema erläuterten Methoden erfordern einen Verweis auf die `Microsoft.SqlServer.ManagedDTS`-Assembly. Nachdem Sie den Verweis in einem neuen Projekt hinzugefügt haben, importieren Sie den <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace mithilfe einer `using`- oder `Imports`-Anweisung.

> [!IMPORTANT]
>  Die Methoden der <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse zum Arbeiten mit dem SSIS-Paketspeicher unterstützen nur „.“, localhost oder den Namen des lokalen Servers. Sie können "(local)" nicht verwenden.

## <a name="determining-which-roles-are-available"></a>Bestimmen, welche Rollen verfügbar sind
 Um zu bestimmen, welche Rollen für die auf einem bestimmten Server gespeicherten Pakete verfügbar sind, rufen Sie die <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A>-Methode der <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse auf.

## <a name="determining-which-roles-are-assigned"></a>Bestimmen, welche Rollen zugewiesen sind
 Um zu bestimmen, welche Rollen einem bestimmten Paket bereits zugewiesen wurden, rufen Sie die <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A>-Methode auf. Rufen Sie die <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A>-Methode auf, um einem Paket Rollen zuzuweisen.

![Integration Services Symbol (klein)](../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.

## <a name="see-also"></a>Weitere Informationen
 [Integration Services-Rollen &#40;SSIS-Dienst&#41;](../security/integration-services-roles-ssis-service.md)


