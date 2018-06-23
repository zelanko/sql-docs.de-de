---
title: Entfernen von Renderingerweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
caps.latest.revision: 37
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c8ad34be5d818d70b8c46d82dbf348b9d0814824
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36047771"
---
# <a name="removing-a-rendering-extension"></a>Entfernen von Renderingerweiterungen
  So entfernen Sie eine [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Renderingerweiterung, entfernen Sie einfach die `Extension` -Element für Ihre Renderingerweiterung aus der Datei "rsreportserver.config" in **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\< Instanzname > \reporting** Ordner. Wenn Sie Einträge für einen Berichts-Designer als auch auf einem Berichtsserver vorgenommen haben, entfernen Sie die `Extension` Element aus der [RSReportDesigner-Konfigurationsdatei](../../report-server/rsreportdesigner-configuration-file.md) ebenfalls. Nachdem Sie die Konfigurationsdaten entfernt haben, steht die Renderingerweiterung nicht mehr für die Komponente zur Verfügung.  
  
## <a name="see-also"></a>Siehe auch  
 [Reporting Services-Konfigurationsdateien](../../report-server/reporting-services-configuration-files.md)   
 [Implementing a Rendering Extension (Implementieren von Renderingerweiterungen)](implementing-a-rendering-extension.md)   
 [Übersicht über Renderingerweiterungen](rendering-extensions-overview.md)   
 [Implementieren der IRenderingExtension-Schnittstelle](implementing-the-irenderingextension-interface.md)   
 [Überlegungen zur Sicherheit von Erweiterungen](../security-considerations-for-extensions.md)   
 [Bereitstellen von Renderingerweiterungen](deploying-a-rendering-extension.md)  
  
  