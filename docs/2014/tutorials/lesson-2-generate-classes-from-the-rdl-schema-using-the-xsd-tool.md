---
title: 'Lektion 2: Generieren von Klassen aus dem RDL-Schema mithilfe des XSD-Tools | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a81c87f1-7977-4b30-b6ac-b38b3e2b6398
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: f5f74c6621d329885e9149fce9a37c7418d9c37b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "62653752"
---
# <a name="lesson-2-generate-classes-from-the-rdl-schema-using-the-xsd-tool"></a>Lektion 2: Generieren von Klassen aus dem RDL-Schema mithilfe des XSD-Tools
  Nachdem Sie das [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projekt erstellt haben, rufen Sie eine lokale Kopie des Berichtsdefinitionsschemas ab, und führen Sie das XML-Schemadefinitionstool (Xsd.exe) aus.  
  
### <a name="to-generate-the-rdl-classes"></a>So generieren Sie RDL-Klassen  
  
1.  Öffnen Sie eine Instanz [!INCLUDE[msCoName](../includes/msconame-md.md)] von Internet Explorer (oder einen entsprechenden Webbrowser), und navigieren Sie zur folgenden URL:  
  
    ```  
    https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition/ReportDefinition.xsd  
    ```  
  
2.  Nachdem das RDL-Schema im Browser geöffnet wurde, klicken Sie auf das Menü **Datei** , und wählen Sie **Speichern unter**aus.  
  
3.  Navigieren Sie zu dem Speicherort, an dem Sie das [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Projekt erstellt haben, und speichern Sie das Schema unter dem Dateinamen ReportDefinition.xsd.  
  
4.  Nachdem die Datei gespeichert wurde, öffnen Sie eine Instanz der [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] -Eingabeaufforderung. Zum Öffnen einer Instanz der Eingabeaufforderung klicken Sie auf das Startmenü, zeigen Sie auf **Alle Programme**, zeigen Sie auf **Microsoft Visual Studio 2010**, zeigen Sie auf **Visual Studio-Tools** , und klicken Sie auf **Visual Studio-Eingabeaufforderung (2010)**.  
  
5.  Ändern Sie den aktuellen Pfad in den Speicherort, an dem Sie die Datei ReportDefinition.xsd gespeichert haben:  
  
     `CD\<ReportDefinition.xsd Path>`  
  
6.  Generieren Sie mit dem folgenden Befehl die Datei ReportDefinition.cs, in der die Klassen für das RDL-Schema enthalten sind:  
  
     `xsd /c /n:SampleRDLSchema ReportDefinition.xsd`  
  
     Verwenden Sie zum Generieren der Datei ReportDefinition.vb folgenden Befehl:  
  
     `xsd /c /l:VB /n:SampleRDLSchema ReportDefinition.xsd`  
  
7.  Fügen Sie dem Projekt ReportDefinition.xsd hinzu. Klicken Sie im Menü **Projekt** auf **Vorhandenes Element hinzufügen**. Navigieren Sie zum Speicherort der Datei ReportDefinition.xsd, wählen Sie ReportDefinition.xsd aus, und klicken Sie auf **Hinzufügen**.  
  
    > [!NOTE]  
    >  Nachdem Sie dem Projekt die Datei ReportDefinition. xsd hinzugefügt haben, werden Sie in **Projektmappen-Explorer** bemerken, dass die ReportDefinition.cs-Datei (. vb) nicht vorhanden ist. Um die Datei anzuzeigen, klicken Sie neben der Datei ReportDefinition.xsd auf die Schaltfläche zum Erweitern/Reduzieren.  
  
## <a name="next-lesson"></a>Nächste Lektion  
 In der nächsten Lektion schreiben Sie Code, um eine Berichtsdefinition mithilfe der aus dem RDL-Schema generierten Klassen von einem Berichtsserver zu laden. Siehe [Lesson 3: Load a Report Definition from the Report Server](../../2014/tutorials/lesson-3-load-a-report-definition-from-the-report-server.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktualisieren von Berichten mithilfe von Klassen, die aus dem RDL-Schema &#40;SSRS-Tutorial generiert wurden&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Berichtsdefinitionssprache (SSRS)](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
