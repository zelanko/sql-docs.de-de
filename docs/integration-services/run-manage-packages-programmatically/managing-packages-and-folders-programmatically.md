---
description: Programmgesteuerte Verwaltung von Paketen und Ordnern
title: Programmgesteuerte Verwaltung von Paketen und Ordnern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- enumerators [Integration Services]
- packages [Integration Services], managing
- custom enumerators [Integration Services]
ms.assetid: ec59b75d-ba09-44ac-9039-9d593bb462d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 56ebd88cab35af8dce81ba1fdabb26dc19845dae
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430142"
---
# <a name="managing-packages-and-folders-programmatically"></a>Programmgesteuerte Verwaltung von Paketen und Ordnern

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


<a name="top"></a> Beim programmgesteuerten Arbeiten mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]-Paketen möchten Sie vielleicht feststellen, ob ein einzelnes Paket oder ein einzelner Ordner vorhanden ist, oder Sie möchten die Ordner mit gespeicherten Paketen verwalten. Die <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse des <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace stellt eine Reihe von Methoden bereit, die diese Anforderungen erfüllen.    
    
##  <a name="determining-whether-a-package-or-folder-exists"></a><a name="exists"></a> Bestimmen, ob ein Paket oder ein Ordner vorhanden ist    
 Um programmgesteuert zu ermitteln, ob ein gespeichertes Paket vorhanden ist, rufen Sie eine der folgenden Methoden auf, bevor Sie versuchen, das Paket zu laden und auszuführen:    
    
|Speicherort|Aufzurufende Methode|    
|----------------------|--------------------|    
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.ExistsOnSqlServer%2A>|    
    
 Um programmgesteuert zu ermitteln, ob ein Ordner vorhanden ist, rufen Sie eine der folgenden Methoden auf, bevor Sie versuchen, die in dem Ordner gespeicherten Pakete aufzulisten:    
    
|Speicherort|Aufzurufende Methode|    
|----------------------|--------------------|    
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.FolderExistsOnSqlServer%2A>|    
    
 [Zurück nach oben](#top)    
    
##  <a name="managing-packages-and-folders"></a><a name="managing"></a> Verwalten von Paketen und Ordnern    
 Die <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse des <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace stellt zusätzliche Methoden zum Verwalten von Paketen und den Ordnern, in denen diese gespeichert sind, bereit.    
    
###  <a name="removing-a-package"></a><a name="managing_rempkg"></a> Entfernen eines Pakets    
 Rufen Sie zum programmgesteuerten Entfernen eines gespeicherten Pakets eine der folgenden Methoden auf:    
    
|Speicherort|Aufzurufende Methode|    
|----------------------|--------------------|    
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|    
    
 [Zurück nach oben](#top)    
    
###  <a name="creating-a-folder"></a><a name="managing_create"></a> Erstellen eines Ordners    
 Rufen Sie zum programmgesteuerten Erstellen eines Speicherordners eine der folgenden Methoden auf:    
    
|Speicherort|Aufzurufende Methode|    
|----------------------|--------------------|    
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|    
    
 [Zurück nach oben](#top)    
    
###  <a name="removing-a-folder"></a><a name="managing_remfldr"></a> Entfernen eines Ordners    
 Rufen Sie zum programmgesteuerten Entfernen eines Speicherordners eine der folgenden Methoden auf:    
    
|Speicherort|Aufzurufende Methode|    
|----------------------|--------------------|    
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|    
    
 [Zurück nach oben](#top)    
    
###  <a name="renaming-a-folder"></a><a name="managing_rename"></a> Umbenennen eines Ordners    
 Rufen Sie zum programmgesteuerten Umbenennen eines Speicherordners eine der folgenden Methoden auf:    
    
|Speicherort|Aufzurufende Methode|    
|----------------------|--------------------|    
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|    
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|    
    
 [Zurück nach oben](#top)    
    
## <a name="see-also"></a>Siehe auch    
 [Paketverwaltung &#40;SSIS-Dienst&#41;](../../integration-services/service/package-management-ssis-service.md)     
 [Enumerating Available Packages Programmatically](../../integration-services/run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)    
    
  
