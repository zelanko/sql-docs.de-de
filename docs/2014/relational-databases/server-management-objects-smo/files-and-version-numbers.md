---
title: Dateien und Versionsnummern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: f1a7286f15af28f97e488b8b40fd745a0d320108
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84997138"
---
# <a name="files-and-version-numbers"></a>Dateien und Versionsnummern
  Alle erforderlichen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects-Komponenten (SMO) werden als Teil einer Instanz des- [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Clients oder-Servers installiert. SMO ist in mehreren verwalteten Assemblys implementiert. Sie können SMO-Anwendungen entweder auf einem Client oder auf einem Server entwickeln.  
  
|Verzeichnis|Datei|BESCHREIBUNG|  
|---------------|----------|-----------------|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.ConnectionInfo.dll|Unterstützt das Herstellen von Verbindungen mit einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.ServiceBrokerEnum.dll|Unterstützt die Programmierung des [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service Broker. Dies ist nur in Programmen erforderlich, die auf Service Broker zugreifen.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.Smo.dll|Enthält einen Großteil der SMO-Klassen.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.SmoExtended.dll<br /><br /> Microsoft.SqlServer.Management.Sdk.Sfc.dll<br /><br /> Microsoft.SqlServer.SqlEnum.dll|Unterstützt die SMO-Klassen.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.WmiEnum.dll|Enthält die WMI-Anbieterklassen (Windows Management Instrumentation, Windows-Verwaltungsinstrumentation). Dies ist nur für Programme erforderlich, die die WMI-Anbieterklassen verwenden.|  
|[!INCLUDE[ssSampPathSDK](../../includes/sssamppathsdk-md.md)]|Microsoft.SqlServer.RegSvrEnum.dll|Enthält die Klassen, die den registrierten Server darstellen. Dies ist nur für Programme erforderlich, die die Klassen für den registrierten Server enthalten.|  
  
  
