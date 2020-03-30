---
title: Integrieren mit den Berichts-Viewer-Steuerelementen
description: Visual Studio bietet zwei Berichts-Viewer-Steuerelemente, mit denen Sie Berichtanzeigefunktionen in Ihre Anwendungen integrieren können.
ms.date: 09/18/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.custom: seo-lt-2019
ms.topic: reference
helpviewer_keywords:
- Report Viewer controls
- integrating reports [Reporting Services]
ms.assetid: 3ba47fb4-73a9-4059-89fd-329adebe94a8
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 1ce8530e2f7afb998c14838efb91c93d0b1cae3c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "74796863"
---
# <a name="integrate-reporting-services-using-report-viewer-controls"></a>Integrieren von Reporting Services mit Berichts-Viewer-Steuerelementen
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio 2015 bietet zwei Report Viewer-Steuerelemente, mit denen Sie Berichtanzeigefunktionen in Ihre Anwendungen integrieren können. Es gibt eine Version für Windows Forms-Anwendungen und eine für WebForms-Anwendungen. Jedes Steuerelement verfügt über ähnliche Funktionen, wurde jedoch im Hinblick auf deren individuelle Umgebung konzipiert. Beide Steuerelemente können Berichte verarbeiten, die auf einem Berichtsserver bereitgestellt (Remoteverarbeitungsmodus) oder auf einen Computer kopiert wurden, auf dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht installiert ist (lokaler Verarbeitungsmodus).  
  
 Das Report Viewer-Steuerelement enthält keine integrierte Unterstützung für die dynamische Anpassung an verschiedene Geräte mit unterschiedlichen Bildschirmauflösungen.  
  
## <a name="remote-processing-mode"></a>Remoteverarbeitungsmodus  
 Der Remoteverarbeitungsmodus ist die bevorzugte Methode für die Anzeige von Berichten, die auf einen Berichtsserver übertragen wurden. Der Remoteverarbeitungsmodus bietet folgende Vorteile:  
  
-   Remoteverarbeitung ist eine optimierte Lösung für die Ausführung von Berichten, da der Bericht vom Berichtsserver verarbeitet wird.  
  
-   Da die gesamte Verarbeitung vom Berichtsserver gehandhabt wird, kann eine Berichtsanforderung von verschiedenen Berichtsservern in einer Anwendung für horizontales Skalieren oder auf einem Server mit mehreren Prozessoren für zentrales Skalieren verarbeitet werden.  
  
 Außerdem können im Remotemodus ausgeführte Berichte die kompletten Funktionen des Berichtsservers nutzen, einschließlich aller Rendering- und Datenerweiterungen.  
  
> [!NOTE]  
>  Die Liste der Erweiterungen, die für das Report Viewer-Steuerelement im Remoteverarbeitungsmodus zur Verfügung stehen, richtet sich nach der Edition von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], die auf dem Berichtsserver installiert ist.  
  
## <a name="local-processing-mode"></a>Lokaler Verarbeitungsmodus  
 Der lokale Verarbeitungsmodus stellt eine alternative Methode zum Anzeigen und Rendern von Berichten dar, wenn [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] nicht installiert ist. Anders als bei der Remoteverarbeitung steht dem Steuerelement nur ein Teil der Funktionen zur Verfügung, die der Berichtsserver eigentlich enthält. Im lokalen Verarbeitungsmodus wird die Datenverarbeitung nicht vom Steuerelement gehandhabt, sondern sie wird von der Hostinganwendung implementiert. Die Berichtsverarbeitung wird jedoch vom Steuerelement selbst gehandhabt. Im lokalen Verarbeitungsmodus stehen nur die PDF-, Excel-, Word- und Bild-Renderingerweiterungen zur Verfügung.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Integration von Reporting Services in Anwendungen](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [Verwenden des Report Viewer-Steuerelements „WebForms“](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)   
 [Verwenden des Report Viewer-Steuerelements „WinForms“](../../reporting-services/application-integration/using-the-winforms-reportviewer-control.md)  

  
  
