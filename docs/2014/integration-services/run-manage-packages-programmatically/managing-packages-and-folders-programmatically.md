---
title: Programmgesteuerte Verwaltung von Paketen und Ordnern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 5baa8949fc74d92c3a4bcae46dbe4f9c7e1b9f40
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85422697"
---
# <a name="managing-packages-and-folders-programmatically"></a>Programmgesteuerte Verwaltung von Paketen und Ordnern
  Beim programmgesteuerten Arbeiten mit [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Paketen möchten Sie möglicherweise feststellen, ob ein einzelnes Paket oder ein einzelner Ordner vorhanden ist, oder Sie möchten die Ordner mit gespeicherten Paketen verwalten. Die <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse des <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace stellt eine Reihe von Methoden bereit, die diese Anforderungen erfüllen.  
  
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
  

  
##  <a name="managing-packages-and-folders"></a><a name="managing"></a> Verwalten von Paketen und Ordnern  
 Die <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse des <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace stellt zusätzliche Methoden zum Verwalten von Paketen und den Ordnern, in denen diese gespeichert sind, bereit.  
  
###  <a name="removing-a-package"></a><a name="managing_rempkg"></a> Entfernen eines Pakets  
 Rufen Sie zum programmgesteuerten Entfernen eines gespeicherten Pakets eine der folgenden Methoden auf:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFromSqlServer%2A>|  
  

  
###  <a name="creating-a-folder"></a><a name="managing_create"></a> Erstellen eines Ordners  
 Rufen Sie zum programmgesteuerten Erstellen eines Speicherordners eine der folgenden Methoden auf:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.CreateFolderOnSqlServer%2A>|  
  

  
###  <a name="removing-a-folder"></a><a name="managing_remfldr"></a> Entfernen eines Ordners  
 Rufen Sie zum programmgesteuerten Entfernen eines Speicherordners eine der folgenden Methoden auf:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RemoveFolderFromSqlServer%2A>|  
  
  
  
###  <a name="renaming-a-folder"></a><a name="managing_rename"></a> Umbenennen eines Ordners  
 Rufen Sie zum programmgesteuerten Umbenennen eines Speicherordners eine der folgenden Methoden auf:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.RenameFolderOnSqlServer%2A>|  
  

  
![Integration Services Symbol (klein)](../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Paketverwaltung &#40;SSIS-Dienst&#41;](../service/package-management-ssis-service.md)   
 [Enumerating Available Packages Programmatically](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
