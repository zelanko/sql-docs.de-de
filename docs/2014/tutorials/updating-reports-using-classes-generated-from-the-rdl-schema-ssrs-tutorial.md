---
title: Aktualisieren von Berichten mithilfe von Klassen, die aus dem RDL-Schema (SSRS-Lernprogramm) generierten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- RDL [Reporting Services], generating
- RDL [Reporting Services], tutorials
- RDL [Reporting Services], serializing
ms.assetid: 8f81d48f-7ab9-4ef8-bce0-7d16d9a47fbd
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 361f3094e1a40cbfc6075888b2be13f42d74c8bd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48136050"
---
# <a name="updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial"></a>Aktualisieren von Berichten mithilfe von Klassen, die aus dem RDL-Schema generiert wurden (SSRS-Lernprogramm)
  Dieses Tutorial veranschaulicht, wie das XML Schema Definition Tool (Xsd.exe) Klassen generieren, mit denen Sie zum Serialisieren und Deserialisieren von Berichtsdefinitionsdateien (RDL- und RDLC) mit der [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] <xref:System.Xml.Serialization.XmlSerializer> Klasse.  
  
## <a name="what-you-will-learn"></a>Lernziele  
 Im Rahmen dieses Lernprogramms führen Sie folgende Aufgaben aus:  
  
-   Erstellen Sie eine Anwendung mit der [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Konsolenanwendung-Projektvorlage.  
  
-   Generieren von Klassen aus der Berichtsdefinitionssprache (Report Definition Language, RDL)-Schema mithilfe der **Xsd** Tool.  
  
-   Sie stellen eine Verbindung mit einem Berichtsserver her und rufen eine Berichtsdefinition ab.  
  
-   Sie schreiben Code zum Aktualisieren der Berichtsdefinitionsdatei.  
  
-   Sie speichern die aktualisierte Berichtsdefinition wieder auf dem Berichtsserver.  
  
-   Sie führen die RDL-Schema-Anwendung (VB/C#) aus.  
  
> [!NOTE]  
>  Bei Berichten ohne Beschreibung verursachen die in diesem Lernprogramm bereitgestellten Codebeispiele u. U. einen Fehler. Dies liegt daran, dass für Berichte, für die keine Beschreibung angegeben wurde, keine Beschreibungseigenschaft vorhanden ist.  
  
## <a name="requirements"></a>Anforderungen  
 Für die vollständige Bearbeitung des Lernprogramms benötigen Sie Folgendes:  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
-   Ausreichende Berechtigungen für den Zugriff auf Berichte sowie zum Veröffentlichen von Berichten für den Berichtsserver-Webdienst auf dem Computer, auf dem sich der Berichtsserver befindet.  
  
-   Eine Installation der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]-Beispieldatenbank auf einer [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]-Instanz.  
  
-   Einen auf Ihrem Berichtsserver installierten Bericht. Für dieses Lernprogramm wird der Beispielbericht Company Sales 2012 verwendet. Weitere Informationen zu Beispielberichten finden Sie unter [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
> [!NOTE]  
>  Die Beispiele werden nicht automatisch beim Setup installiert. Sie können sie jedoch jederzeit installieren. Weitere Informationen zu Beispielen finden Sie unter [SQL Server Product Samples](http://go.microsoft.com/fwlink/?LinkId=182887).  
  
 **Ungefähre Dauer dieses Tutorials:** 30 Minuten  
  
## <a name="tasks"></a>Aufgaben  
 [Lektion 1: Erstellen des RDL-Schema-Projekts in Visual Studio](../../2014/tutorials/lesson-1-create-the-rdl-schema-visual-studio-project.md)  
  
 [Lektion 2: Generieren von Klassen aus dem RDL-Schema mithilfe des XSD-Tools](../../2014/tutorials/lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool.md)  
  
 [Lektion 3: Laden einer Berichtsdefinition vom Berichtsserver](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md)  
  
 [Lektion 4: Programmgesteuertes Update der Berichtsdefinition](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md)  
  
 [Lektion 5: Veröffentlichen der Berichtsdefinition auf dem Berichtsserver](../../2014/tutorials/lesson-5-publish-the-report-definition-to-the-report-server.md)  
  
 [Lektion 6: Ausführen die RDL-Schema-Anwendung &#40;VB-C&#35;&#41;](../../2014/tutorials/lesson-6-run-the-rdl-schema-application-vb-csharp.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Berichtsdefinitionssprache (SSRS)](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
