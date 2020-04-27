---
title: Integrieren von Reporting Services mithilfe der ReportViewer-Steuerelemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- ReportViewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cbaa41c75297d62e84cfc808463214d19c4ff8fa
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "63126271"
---
# <a name="integrating-reporting-services-using-the-reportviewer-controls"></a>Integrieren von Reporting Services mit den ReportViewer-Steuerelementen
  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vsOrcas](../../includes/vsorcas-md.md)] bietet zwei Report Viewer-Steuerelemente für die Integration der Berichts Anzeigefunktionen in Ihre Anwendungen. Es gibt eine Version für Windows Forms-Anwendungen und eine für WebForms-Anwendungen. Jedes Steuerelement verfügt über ähnliche Funktionen, wurde jedoch im Hinblick auf deren individuelle Umgebung konzipiert. Beide Steuerelemente können Berichte verarbeiten, die auf einem Berichts Server bereitgestellt wurden (Remote Verarbeitungsmodus) oder auf einen Computer kopiert wurden [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , auf dem nicht installiert ist (lokaler Verarbeitungsmodus).  
  
 DAs ReportViewer-Steuerelement enthält keine integrierte Unterstützung für dynamische Anpassung an verschiedene Geräte mit unterschiedlichen Bildschirmauflösungen.  
  
## <a name="remote-processing-mode"></a>Remoteverarbeitungsmodus  
 Der Remoteverarbeitungsmodus ist die bevorzugte Methode für die Anzeige von Berichten, die auf einen Berichtsserver übertragen wurden. Der Remoteverarbeitungsmodus bietet folgende Vorteile:  
  
-   Remoteverarbeitung ist eine optimierte Lösung für die Ausführung von Berichten, da der Bericht vom Berichtsserver verarbeitet wird.  
  
-   Da die gesamte Verarbeitung vom Berichtsserver gehandhabt wird, kann eine Berichtsanforderung von verschiedenen Berichtsservern in einer Anwendung für horizontales Skalieren oder auf einem Server mit mehreren Prozessoren für zentrales Skalieren verarbeitet werden.  
  
 Außerdem können im Remotemodus ausgeführte Berichte die kompletten Funktionen des Berichtsservers nutzen, einschließlich aller Rendering- und Datenerweiterungen.  
  
> [!NOTE]  
>  Die Liste der Erweiterungen, die für das Steuerelement ReportViewer im Remoteverarbeitungsmodus zur Verfügung stehen, hängt davon ab, welche Ausgabe von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf dem Berichtsserver installiert ist.  
  
## <a name="local-processing-mode"></a>Lokaler Verarbeitungsmodus  
 Der lokale Verarbeitungsmodus stellt eine alternative Methode zum Anzeigen und Rendern von Berichten dar, wenn [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht installiert ist. Anders als bei der Remoteverarbeitung steht dem Steuerelement nur ein Teil der Funktionen zur Verfügung, die der Berichtsserver eigentlich enthält. Im lokalen Verarbeitungsmodus wird die Datenverarbeitung nicht vom Steuerelement gehandhabt, sondern sie wird von der Hostinganwendung implementiert. Die Berichtsverarbeitung wird jedoch vom Steuerelement selbst gehandhabt. Im lokalen Verarbeitungsmodus stehen nur die PDF-, Excel-, Word- und Bild-Renderingerweiterungen zur Verfügung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integrieren von Reporting Services in Anwendungen](../application-integration/integrating-reporting-services-into-applications.md)   
 [Erstellen von SSRS-Berichten mithilfe von Visual Studio (Blog)](https://jwcooney.com/2015/01/07/ssrs-basics-set-up-visual-studio-to-write-a-new-ssrs-report/)  
  
  
