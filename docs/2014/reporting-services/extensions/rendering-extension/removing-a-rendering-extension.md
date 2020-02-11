---
title: Entfernen von Renderingerweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77a8a9ac44b35f338f978913985617e4f264ddb7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62988062"
---
# <a name="removing-a-rendering-extension"></a>Entfernen von Renderingerweiterungen
  Um eine [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Renderingerweiterung zu entfernen, `Extension` entfernen Sie einfach das-Element für Ihre Renderingerweiterung aus der Datei RSReportServer. config, die sich im Verzeichnis **%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 befindet.\< Instanzname> Ordner \Reporting Services\ReportServer** . Wenn Sie Einträge für eine Berichts-Designer und einen Berichts Server erstellt haben, entfernen Sie auch `Extension` das-Element aus der [RSReportDesigner-Konfigurationsdatei](../../report-server/rsreportdesigner-configuration-file.md) . Nachdem Sie die Konfigurationsdaten entfernt haben, steht die Renderingerweiterung nicht mehr für die Komponente zur Verfügung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Reporting Services-Konfigurationsdateien](../../report-server/reporting-services-configuration-files.md)   
 [Implementing a Rendering Extension (Implementieren von Renderingerweiterungen)](implementing-a-rendering-extension.md)   
 [Übersicht über Renderingerweiterungen](rendering-extensions-overview.md)   
 [Implementieren der IRenderingExtension-Schnittstelle](implementing-the-irenderingextension-interface.md)   
 [Überlegungen zur Sicherheit von Erweiterungen](../security-considerations-for-extensions.md)   
 [Bereitstellen von Renderingerweiterungen](deploying-a-rendering-extension.md)  
  
  
