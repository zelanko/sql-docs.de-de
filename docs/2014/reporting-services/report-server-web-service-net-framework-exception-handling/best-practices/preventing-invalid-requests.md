---
title: Verhindern von ungültigen Anforderungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- invalid requests [Reporting Services]
- exceptions [Reporting Services], invalid requests
- valid requests [Reporting Services]
ms.assetid: 4a4a2d97-4c10-43a9-8298-ef5a820ea549
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d165b4137c8deb0afb232d58f0e19bb183ddf860
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48098750"
---
# <a name="preventing-invalid-requests"></a>Verhindern von ungültigen Anforderungen
  Sie können verhindern, dass bestimmte Ausnahmearten ausgelöst werden, indem Sie den Anwendungsablauf analysieren und sicherstellen, dass die an den Berichtsserver gesendeten Anforderungen gültig sind. In Anwendungen, in denen die Benutzer den Namen eines Berichts, einer Datenquelle oder eines anderen Berichtsserverelements ändern oder aktualisieren dürfen, sollten Sie beispielsweise den Text, den ein Benutzer eingeben kann, validieren. Sie sollten stets nach reservierten Zeichen suchen, bevor die Anforderung an einen Berichtsserver gesendet werden kann. Verwenden Sie bedingte **if**-Anweisungen oder andere logische Konstrukte im Code, um den Benutzer darauf aufmerksam zu machen, dass die erforderlichen Bedingungen für das Senden der Anforderung an den Berichtsserver nicht erfüllt sind.  
  
 Im folgenden vereinfachten C#-Beispiel erhalten die Benutzer eine freundliche Fehlermeldung, wenn Sie versuchen, einen Bericht mit einem Namen zu erstellen, der einen Schrägstrich (/) enthält.  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "see the help documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      FileStream stream = File.OpenRead("MyReport.rdl");  
      definition = new Byte[stream.Length];  
      stream.Read(definition, 0, (int) stream.Length);  
      stream.Close();  
      // Create report with user-defined name  
      rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
      MessageBox.Show("Report: {0} created successfully", name);  
   }  
}  
```  
  
 Weitere Informationen zu den verschiedenen Fehlerarten, die verhindert werden können, bevor Anforderungen an den Berichtsserver gesendet werden, finden Sie unter [Tabelle für SoapException-Fehler](../soapexception-class/soapexception-errors-table.md). Weitere Informationen zur Vertiefung des vorherigen Beispiels mithilfe von try/catch-Blöcken finden Sie unter [Verwenden von Try- und Catch-Blöcken](using-try-and-catch-blocks.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Introducing Exception Handling in Reporting Services (Einführung in die Ausnahmebehandlung in Reporting Services)](../introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException Class (Reporting Services-SoapException-Klasse)](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
