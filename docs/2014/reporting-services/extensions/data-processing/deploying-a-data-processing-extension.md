---
title: Bereitstellen einer Datenverarbeitungserweiterung | Microsoft-Dokumentation
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
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 88fcfd2d87238a31562d17b0811d94485a9d1ad9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37242250"
---
# <a name="deploying-a-data-processing-extension"></a>Bereitstellen von Datenverarbeitungserweiterungen
  Wenn Sie die [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Datenverarbeitungserweiterung geschrieben und in eine [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Bibliothek kompiliert haben, müssen Sie sie für den Berichtsserver und den Berichts-Designer erkennbar machen. Dazu müssen Sie lediglich die Erweiterung in die entsprechenden Verzeichnisse kopieren und Einträge zu den zugehörigen [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-Konfigurationsdateien hinzufügen.  
  
## <a name="configuration-file-extension-element"></a>Extension-Element für die Konfigurationsdatei  
 Datenverarbeitungserweiterungen, die Sie für den Berichtsserver oder den Berichts-Designer bereitstellen, müssen in den Konfigurationsdateien als **Extension**-Elemente hinzugefügt werden. Bei diesen Dateien handelt es sich um RSReportServer.config für den Berichtsserver und RSReportDesigner.config für den Berichts-Designer.  
  
 In der folgenden Tabelle werden die Attribute für das **Extension**-Element für Datenverarbeitungserweiterungen beschrieben.  
  
|attribute|Description|  
|---------------|-----------------|  
|`Name`|Ein eindeutiger Name für die Erweiterung, z. B. "SQL" für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenverarbeitungserweiterung oder "OLEDB" für die OLE DB-Datenverarbeitungserweiterung. Die maximale Länge für das `Name`-Attribut beträgt 255 Zeichen. Der Name muss für sämtliche Einträge im **Extension** -Element einer Konfigurationsdatei eindeutig sein.|  
|`Type`|Eine durch Trennzeichen getrennte Liste, die den vollqualifizierten Namespace und den Namen der Assembly enthält|  
|`Visible`|Der Wert `false` gibt an, dass die Datenverarbeitungserweiterung auf Benutzeroberflächen nicht sichtbar sein soll. Wenn das Attribut nicht enthalten ist, wird der Standardwert ist `true`.|  
  
 Weitere Informationen über die Dateien „RSReportServer.config“ und „RSReportDesigner.config“ finden Sie unter [Reporting Services-Konfigurationsdateien](../../report-server/reporting-services-configuration-files.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Thema|Description|  
|-----------|-----------------|  
|[How to: Deploy a Data Processing Extension to a Report Server (Vorgehensweise: Bereitstellen einer Datenverarbeitungserweiterung für einen Berichtsserver)](deploying-a-data-processing-extension-to-a-report-server.md)|Beschreibt, wie Sie eine Datenverarbeitungserweiterung auf einem Berichtsserver bereitstellen|  
|[How to: Deploy a Data Processing Extension to Report Designer (Vorgehensweise: Bereitstellen einer Datenverarbeitungserweiterung für den Berichts-Designer)](deploying-a-data-processing-extension-to-report-designer.md)|Beschreibt, wie Sie eine Datenverarbeitungserweiterung für den Berichts-Designer bereitstellen|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweiterungen für Reporting Services](../reporting-services-extensions.md)   
 [Implementieren von Datenverarbeitungserweiterungen](implementing-a-data-processing-extension.md)   
 [Reporting Services Extension Library (Reporting Services-Erweiterungsbibliothek)](../reporting-services-extension-library.md)  
  
  
