---
title: Dateien und Versionsnummern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, versions
- components [SMO]
- files [SMO], components
- SMO [SQL Server], versions
- versions [SMO]
ms.assetid: 510907b6-e7a9-41bd-b892-d6d99a5118e1
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 6d682ca3d6768da16d43c3c09471a6c722561dd3
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "86008622"
---
# <a name="files-and-version-numbers"></a>Dateien und Versionsnummern
[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Alle erforderlichen SQL Server Management Object (SMO)-Komponenten sind im nuget-Paket Microsoft. SqlServer. sqlmanagementobjects enthalten. SMO ist in mehreren verwalteten Assemblys implementiert. Sie können SMO-Anwendungen entweder auf einem Client oder auf einem Server entwickeln.  

> > [!Important]
> > Die Dateiversion der SMO-Assemblys wird als Hauptversion angezeigt. **0**. Build. Revision. Die eingebettete Assemblyversion ist jedoch sehr groß. **100**. Build. Revision. Dies geschieht, um die Version von SMO zu verwenden, die in jeder Anwendung verwendet wird, sodass Updates zu einem anderen nicht betroffen sind.
> > 
> > Aus diesem Grund sollten Sie diese Versionen der Assemblys **nicht** im globalen Assemblycache (GAC) installieren. Dies könnte dazu führen, dass andere Anwendungen, wie z [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . b. Management Studio, unterbrechen. 
  
|Datei|BESCHREIBUNG|  
|-----------|-----------------|  
|Microsoft.SqlServer.ConnectionInfo.dll|Unterstützt das Herstellen von Verbindungen mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Microsoft.SqlServer.ServiceBrokerEnum.dll|Unterstützt die Programmierung des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker. Dies ist nur in Programmen erforderlich, die auf Service Broker zugreifen.|  
|Microsoft.SqlServer.Smo.dll|Enthält einen Großteil der SMO-Klassen.|  
|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|Unterstützt die SMO-Klassen.|  
|Microsoft.SqlServer.WmiEnum.dll|Enthält die WMI-Anbieterklassen (Windows Management Instrumentation, Windows-Verwaltungsinstrumentation). Dies ist nur für Programme erforderlich, die die WMI-Anbieterklassen verwenden.|  
|Microsoft.SqlServer.RegSvrEnum.dll|Enthält die Klassen, die den registrierten Server darstellen. Dies ist nur für Programme erforderlich, die die Klassen für den registrierten Server enthalten.|  
  
  
