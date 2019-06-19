---
title: Programmgesteuertes Speichern von Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 07c926a292c657eecceb13ca1cdc1d3f8dcc5a71
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "65729262"
---
# <a name="saving-a-package-programmatically"></a>Programmgesteuertes Speichern von Paketen

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Nachdem Sie ein neues Paket programmgesteuert erstellt oder ein vorhandenes geändert haben, sollten Sie Ihre Änderungen speichern.  
  
 Alle in diesem Thema erläuterten Methoden zum Speichern von Paketen erfordern einen Verweis auf die **Microsoft.SqlServer.ManagedDTS** -Assembly. Nachdem Sie den Verweis in einem neuen Projekt hinzugefügt haben, importieren Sie den <xref:Microsoft.SqlServer.Dts.Runtime>-Namespace mit einer **using**- oder **Imports**-Anweisung.  
  
## <a name="saving-a-package-programmatically"></a>Programmgesteuertes Speichern von Paketen  
 Rufen Sie eine der folgenden Methoden der [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse auf, um ein Paket programmgesteuert zu speichern:  
  
|Speicherort|Aufzurufende Methode|  
|----------------------|--------------------|  
|File|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|SSIS-Paketspeicher|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> oder<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  Die Methoden der <xref:Microsoft.SqlServer.Dts.Runtime.Application>-Klasse zum Arbeiten mit dem SSIS-Paketspeicher unterstützen nur "." oder den Namen des lokalen Servers. "(local)" oder "localhost" können nicht verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Speichern von Paketen](../../integration-services/save-packages.md)  
  
  
