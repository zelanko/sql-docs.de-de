---
title: Implementierungsanforderungen für benutzerdefinierte Berichtselemente | Microsoft-Dokumentation
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.topic: reference
helpviewer_keywords:
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e25938d690d6e1046d1d0e75ae5a4952b05d4615
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2019
ms.locfileid: "73594510"
---
# <a name="custom-report-item-implementation-requirements"></a>Implementierungsanforderungen für benutzerdefinierte Berichtselemente
  In diesem Thema werden die Voraussetzungen zur Entwicklung und Bereitstellung von benutzerdefinierten Berichtselementen erläutert.  
  
## <a name="development-and-deployment-requirements"></a>Entwicklungs- und Bereitstellungsanforderungen  
 Die Entwicklung eines benutzerdefinierten Berichtselements für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erfordert Folgendes:  
  
-   Administratorzugriff auf einen Server, auf dem [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mit [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] und [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ausgeführt wird.  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)] oder höher, auf dem das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Software Development Kit (SDK) installiert ist.  
  
-   Zugriff auf die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK-Dokumentation.  
  
-   Kenntnisse über die Komponentenerstellung und die Komponentenmodell-Namespaces in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="language-and-namespace-requirements"></a>Sprach- und Namespace-Anforderungen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Berichtselemente unterstützen [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] vollständig. Sie können benutzerdefinierte Berichtselemente mithilfe einer Auswahl .NET-konformer Sprachen entwickeln.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] enthält viele Tools und Funktionen für Entwickler, die die iterativen Zyklen, bestehend aus Codierung, Debugging und Testen, sowie die Bereitstellung vereinfachen und beschleunigen. Das [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK enthält [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] und C#-Compiler sowie zugehörige Tools.  
  
-   Benutzerdefinierte Berichtselemente verwenden **Microsoft.ReportDesigner** und <xref:Microsoft.ReportingServices.Interfaces>-Namespaces. Diese werden in den Assemblys „Microsoft.ReportingServices.Designer.DLL“ und „Microsoft.ReportingServices.Interfaces.DLL“ gespeichert, die als Teil von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installiert werden.  
  
-   Benutzerdefinierte Berichtselement-Entwurfszeitkomponenten müssen Schnittstellen des <xref:System.ComponentModel>-Namespace in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] implementieren. <xref:System.ComponentModel> ist in der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK-Dokumentation dokumentiert.  

## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Laufzeitkomponente für ein benutzerdefiniertes Berichtselement](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [Erstellen einer Entwurfszeitkomponente für ein benutzerdefiniertes Berichtselement](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)   
 [How to: Deploy a Custom Report Item (Vorgehensweise: Bereitstellen eines benutzerdefinierten Berichtselements)](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)   
 [Custom Report Item Class Libraries (Klassenbibliotheken für ein benutzerdefiniertes Berichtselement)](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
  
  
