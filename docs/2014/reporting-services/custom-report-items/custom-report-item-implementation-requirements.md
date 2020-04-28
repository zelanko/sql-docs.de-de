---
title: Implementierungsanforderungen für benutzerdefinierte Berichtselemente | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/25/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items
ms.assetid: cfacd816-00d6-4a3d-be72-1bba6f7f6886
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0000e0c7a5933003544de22b60a8adc4d9c59c82
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "74684446"
---
# <a name="custom-report-item-implementation-requirements"></a>Implementierungsanforderungen für benutzerdefinierte Berichtselemente
  In diesem Thema werden die Voraussetzungen zur Entwicklung und Bereitstellung von benutzerdefinierten Berichtselementen erläutert.  
  
## <a name="development-and-deployment-requirements"></a>Entwicklungs- und Bereitstellungsanforderungen  
 Die Entwicklung eines benutzerdefinierten Berichtselements für [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] erfordert Folgendes:  
  
-   Administrativer Zugriff auf einen Server [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] auf [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]dem mit und ausgeführt wird.  
  
-   [!INCLUDE[vsprvsext](../../includes/vsprvsext-md.md)]oder höher mit [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] installiertem Software Development Kit (SDK).  
  
-   Zugriff auf die [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK-Dokumentation.  
  
-   Kenntnisse über die Komponentenerstellung und die Komponentenmodell-Namespaces in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Weitere Informationen finden Sie in "Erstellen von Komponenten" und "Namespaces für Komponentenmodelle in Visual Studio" auf msdn.microsoft.com.  
  
## <a name="language-and-namespace-requirements"></a>Sprach- und Namespace-Anforderungen  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Berichtselemente unterstützen [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] vollständig. Sie können benutzerdefinierte Berichtselemente mithilfe einer Auswahl .NET-konformer Sprachen entwickeln.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] enthält viele Tools und Funktionen für Entwickler, die die iterativen Zyklen, bestehend aus Codierung, Debugging und Testen, sowie die Bereitstellung vereinfachen und beschleunigen. Das [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK enthält [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] und C#-Compiler sowie zugehörige Tools.  
  
-   Benutzerdefinierte Berichtselemente verwenden die Namespaces `Microsoft.ReportDesigner` und <xref:Microsoft.ReportingServices.Interfaces>. Diese werden in den Assemblys „Microsoft.ReportingServices.Designer.DLL“ und „Microsoft.ReportingServices.Interfaces.DLL“ gespeichert, die als Teil von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] installiert werden.  
  
-   Benutzerdefinierte Berichtselement-Entwurfszeitkomponenten müssen Schnittstellen des <xref:System.ComponentModel>-Namespace in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] implementieren. <xref:System.ComponentModel> ist in der [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK-Dokumentation dokumentiert.  
  
> [!IMPORTANT]  
>  Standardmäßg wird [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]installiert, das [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] -SDK jedoch nicht. Die in diesem Abschnitt vorkommenden Links auf SDK-Inhalte funktionieren nur, wenn das SDK auf Ihrem Computer installiert und die SDK-Dokumentation in der Onlinedokumentation enthalten ist. Fügen Sie das SDK nach der Installation des [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK zur Onlinedokumentation und dem Inhaltsverzeichnis hinzu, indem Sie die Anweisungen unter [Hinzufügen oder Entfernen der Produktdokumentation für SQL Server](../../2014-toc/index.yml) befolgen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erstellen einer Laufzeitkomponente für ein benutzerdefiniertes Berichts Element](creating-a-custom-report-item-run-time-component.md)   
 [Erstellen einer Entwurfszeit Komponente für ein benutzerdefiniertes Berichts Element](creating-a-custom-report-item-design-time-component.md)   
 [Vorgehensweise: Bereitstellen eines benutzerdefinierten Berichts Elements](how-to-deploy-a-custom-report-item.md)   
 [Klassenbibliotheken für ein benutzerdefiniertes Berichtselement](custom-report-item-class-libraries.md)  
  
  
