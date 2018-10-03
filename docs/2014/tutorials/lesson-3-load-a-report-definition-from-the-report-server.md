---
title: 'Lektion 3: Laden einer Berichtsdefinition vom Berichtsserver | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 5ad8b31c-43b0-4481-a31b-090cbed4a438
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 17d53c7a49afc61d3e43606ac3f805a5b21e6bd5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48208150"
---
# <a name="lesson-3-load-a-report-definition-from-the-report-server"></a>Lektion 3: Laden einer Berichtsdefinition vom Berichtsserver
  Nachdem Sie Ihr Projekt erstellt und die Klassen aus dem RDL-Schema generiert haben, können Sie eine Berichtsdefinition vom Berichtsserver laden.  
  
### <a name="to-load-a-report-definition"></a>So laden Sie eine Berichtsdefinition  
  
1.  Fügen Sie ein privates Feld am oberen Rand der `ReportUpdater` Klasse (Modul bei Verwendung von [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) für die `Report` Klasse. Mit diesem Feld wird für die Ausführungszeit der Anwendung ein Verweis auf den Bericht beibehalten, der vom Berichtsserver geladen wird.  
  
    ```csharp  
    private Report _report;  
    ```  
  
    ```vb  
    Private m_report As Report  
    ```  
  
2.  Ersetzen Sie den Code für die `LoadReportDefinition()`-Methode in der Datei Program.cs (Module1.vb für [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) durch folgenden Code:  
  
    ```csharp  
    private void LoadReportDefinition()  
    {  
        System.Console.WriteLine("Loading Report Definition");  
  
        string reportPath =   
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012";  
  
        // Retrieve the report defintion   
        // from the report server  
        byte[] bytes =   
            _reportService.GetItemDefinition(reportPath);  
  
        if (bytes != null)  
        {  
            XmlSerializer serializer =   
                new XmlSerializer(typeof(Report));  
  
            // Load the report bytes into a memory stream  
            using (MemoryStream stream = new MemoryStream(bytes))  
            {  
                // Deserialize the report stream to an   
                // instance of the Report class  
                _report = (Report)serializer.Deserialize(stream);  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub LoadReportDefinition()  
  
        System.Console.WriteLine("Loading Report Definition")  
  
        Dim reportPath As String = _  
            "/AdventureWorks 2012 Sample Reports/Company Sales 2012"  
  
        'Retrieve the report defintion   
        'from the report server  
        Dim bytes As Byte() = _  
            m_reportService.GetItemDefinition(reportPath)  
  
        If Not (bytes Is Nothing) Then  
  
            Dim serializer As XmlSerializer = _  
                New XmlSerializer(GetType(Report))  
  
            'Load the report bytes into a memory stream  
            Using stream As MemoryStream = New MemoryStream(bytes)  
  
                'Deserialize the report stream to an   
                'instance of the Report class  
                m_report = CType(serializer.Deserialize(stream), _  
                                 Report)  
  
            End Using  
  
        End If  
  
    End Sub  
    ```  
  
## <a name="next-lesson"></a>Nächste Lektion  
 In der nächsten Lektion schreiben Sie Code zum Aktualisieren der Berichtsdefinition, die vom Berichtsserver geladen wurde. Finden Sie unter [Lektion 4: Aktualisieren Sie die Berichtsdefinition programmgesteuert](../../2014/tutorials/lesson-4-update-the-report-definition-programmatically.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aktualisieren von Berichten mithilfe von Klassen, die aus dem RDL-Schema generiert &#40;SSRS-Tutorial&#41;](../../2014/tutorials/updating-reports-using-classes-generated-from-the-rdl-schema-ssrs-tutorial.md)   
 [Berichtsdefinitionssprache (SSRS)](../reporting-services/reports/report-definition-language-ssrs.md)  
  
  
