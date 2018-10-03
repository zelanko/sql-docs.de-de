---
title: Bereitstellen von Renderingerweiterungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 665b13c8a163c67a800ee0a1771da46af58ab67c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113698"
---
# <a name="implementing-a-rendering-extension"></a>Implementieren von Renderingerweiterungen
  Eine Renderingerweiterung stellt eine Komponente oder ein Modul eines Berichtsservers dar, mit dem Daten- und Layoutinformationen in ein gerätespezifisches Format umgewandelt werden. SQL Server Reporting Services enthält sechs Renderingerweiterungen: HTML, Excel, Word, CSV oder Text, XML, Image und PDF. Sie können zusätzliche Renderingerweiterungen erstellen, um Berichte in anderen Formaten zu generieren.  
  
> [!NOTE]  
>  Welche Renderingerweiterungen zur Verfügung stehen, sehen Sie auf der Liste der installierten Erweiterungen in der Datei RSReportServer.config.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Rendering Extensions Overview (Übersicht über Renderingerweiterungen)](rendering-extensions-overview.md)  
 Erläutert, wie eine benutzerdefinierte Renderingerweiterung für [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] geschrieben wird.  
  
 [Implementing the IRenderingExtension Interface (Implementieren der IRenderingExtension-Schnittstelle)](implementing-the-irenderingextension-interface.md)  
 Beschreibt die Attribute einer Renderingerweiterung.  
  
 [Bereitstellen von Renderingerweiterungen](deploying-a-rendering-extension.md)  
 Beschreibt, wie Sie eine Renderingerweiterung auf einem Berichtsserver bereitstellen  
  
 [Removing a Rendering Extension (Entfernen von Renderingerweiterungen)](removing-a-rendering-extension.md)  
 Beschreibt, wie Sie eine Renderingerweiterung von einem Berichtsserver entfernen  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungen für Reporting Services](../reporting-services-extensions.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
