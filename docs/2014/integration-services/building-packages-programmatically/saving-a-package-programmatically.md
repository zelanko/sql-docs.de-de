---
title: Programmgesteuertes Speichern von Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2879c4213b2c9c0bf395c103de0d1bc37e4daab
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439217"
---
# <a name="saving-a-package-programmatically"></a>Programmgesteuertes Speichern von Paketen
  Nachdem Sie ein neues Paket programmgesteuert erstellt oder ein vorhandenes geändert haben, sollten Sie Ihre Änderungen speichern.  
  
 Alle in diesem Thema erläuterten Methoden zum Speichern von Paketen erfordern einen Verweis auf die `Microsoft.SqlServer.ManagedDTS`-Assembly. Nachdem Sie den Verweis in einem neuen Projekt hinzugefügt haben, importieren Sie den <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace mit einer `using`- oder `Imports`-Anweisung.  
  
## <a name="saving-a-package-programmatically"></a>Programmgesteuertes Speichern von Paketen  
 Rufen Sie eine der folgenden Methoden der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse auf, um ein Paket programmgesteuert zu speichern:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|Datei|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> oder<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  Die Methoden der <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse zum Arbeiten mit dem SSIS-Paketspeicher unterstützen nur "." oder den Namen des lokalen Servers. "(local)" oder "localhost" können nicht verwendet werden.  
  
![Integration Services Symbol (klein)](../media/dts-16.gif "Integration Services (kleines Symbol)")immer auf**dem neuesten Stand bleiben mit Integration Services**  <br /> Die neuesten Downloads, Artikel, Beispiele und Videos von Microsoft sowie ausgewählte Lösungen aus der Community finden Sie auf MSDN auf der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] -Seite:<br /><br /> [Besuchen Sie die Integration Services-Seite auf MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Abonnieren Sie die auf der Seite verfügbaren RSS-Feeds, um automatische Benachrichtigungen zu diesen Updates zu erhalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Speichern von Paketen](../save-packages.md)  
  
  
