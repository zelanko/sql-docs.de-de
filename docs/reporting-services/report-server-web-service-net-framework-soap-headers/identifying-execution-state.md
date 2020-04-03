---
title: Identifizieren des Ausführungsstatus | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie die Reporting Services verwenden, um den Ausführungsstatus abzurufen, sodass Sie mit einem Bericht auf verschiedene Weise interagieren können.
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-soap-headers
ms.topic: reference
helpviewer_keywords:
- session states [Reporting Services]
- lifetimes [Reporting Services]
- sessions [Reporting Services]
- SessionHeader SOAP header
ms.assetid: d8143a4b-08a1-4c38-9d00-8e50818ee380
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0977cc384dac80f28d6b7c5b7a0149ba200f1794
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "80215599"
---
# <a name="identifying-execution-state"></a>Identifizieren des Ausführungsstatus
  HTTP (Hypertext Transfer Protocol) ist ein verbindungs- und statusfreies Protokoll, d. h. es gibt nicht automatisch an, ob unterschiedliche Anforderungen vom selben Client stammen oder ob eine einzelne Browserinstanz eine Webseite immer noch aktiv anzeigt. In Sitzungen wird eine logische Verbindung erstellt, um den Status zwischen Server und Client über HTTP beizubehalten. Die benutzerspezifischen Informationen einer bestimmten Sitzung werden als Sitzungsstatus bezeichnet.  
  
 Die Sitzungsverwaltung umfasst die Korrelation einer HTTP-Anforderung mit anderen, früheren Anforderungen, die von der gleichen Sitzung generiert wurden. Ohne Sitzungsverwaltung werden diese Anforderungen aufgrund der verbindungs- und statuslosen Natur des HTTP-Protokolls ohne Beziehung zum Berichtsserver-Webdienst angezeigt.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] stellt kein holistisches Konzept des Sitzungsstatus bereit, wie es z.B. [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] macht. Bei der Ausführung von Berichten behält der Berichtsserver jedoch den Status zwischen den Methodenaufrufen in Form einer **Ausführung**bei. Mithilfe einer Ausführung kann der Benutzer auf verschiedene Arten mit dem Bericht interagieren. Dazu gehört das Laden des Berichts vom Berichtsserver, die Einstellung der Anmeldeinformationen und Parameter für den Bericht sowie das Rendern des Berichts.  
  
 Während die Clients mit einem Berichtsserver kommunizieren, verwenden sie die Ausführung, um die Berichtsanzeige und Benutzernavigation auf anderen Seiten in einem Bericht zu verwalten oder um bestimmte Abschnitte eines Berichts auszublenden. Eine eindeutige Ausführung ist für jeden Bericht vorhanden, den die Clientanwendung ausführt.  
  
 Normalerweise beginnt die Lebensdauer einer Ausführung, wenn ein Benutzer zum Browser oder zur Clientanwendung navigiert und einen Bericht für die Anzeige auswählt. Die Ausführung wird nach einem kurzen Timeout verworfen, nachdem die letzte Anforderung an die Ausführung eingegangen ist (der Standard-Timeout beträgt 20 Minuten).  
  
 Von der Perspektive eines Webdiensts beginnt die Lebensdauer, wenn die Berichtsserver-Webdienstmethoden <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A>, <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> oder <xref:ReportExecution2005.ReportExecutionService.Render%2A> aufgerufen werden. Die Anwendung kann andere Methoden zur Bearbeitung der aktiven Ausführung verwenden (z. B. Einstellen von Parametern und Datenquellen). Die Ausführung wird nach einem kurzen Timeout verworfen, nachdem die letzte Anforderung an die Ausführung eingegangen ist (der Standard-Timeout beträgt 20 Minuten).  
  
 Eine Anwendung verfolgt mehrere aktive Ausführungen zwischen den Aufrufen an die Webdienstmethoden <xref:ReportExecution2005.ReportExecutionService.Render%2A> und <xref:ReportExecution2005.ReportExecutionService.RenderStream%2A>, indem <xref:ReportExecution2005.ExecutionHeader.ExecutionID%2A> gespeichert wird, was im SOAP-Header von den Methoden <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> und <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> zurückgegeben wird.  
  
 Das folgende Diagramm zeigt den Verarbeitungs- und Renderingpfad für Berichte.  
  
 ![Verarbeitungs-/Renderingpfad für Berichte](../../reporting-services/report-server-web-service-net-framework-soap-headers/media/rs-render-process-diagram.gif "Verarbeitungs-/Renderingpfad für Berichte")  
  
 Um die oben genannten Funktionen zu unterstützen, wurde die aktuelle SOAP-Render-Methode in mehrere Methoden aufgeteilt, die die Phasen der Ausführungsinitialisierung, der Verarbeitung und des Rendering umfassen.  
  
 Um programmgesteuert einen Bericht zu rendern, müssen Sie Folgendes tun:  
  
-   Laden Sie den Bericht oder die Berichtsdefinition mit <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> oder <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A>.  
  
-   Prüfen Sie, ob der Bericht Anmeldeinformationen oder Parameter benötigt, indem Sie die Werte <xref:ReportExecution2005.ExecutionInfo.CredentialsRequired%2A> und die Eigenschaften <xref:ReportExecution2005.ExecutionInfo.ParametersRequired%2A> des <xref:ReportExecution2005.ExecutionInfo>-Objekts prüfen, das von <xref:ReportExecution2005.ReportExecutionService.LoadReport%2A> oder <xref:ReportExecution2005.ReportExecutionService.LoadReportDefinition%2A> zurückgegeben wird.  
  
-   Falls notwendig, legen Sie die Anmeldeinformationen und/oder die Parameter fest, indem Sie die Methoden <xref:ReportExecution2005.ReportExecutionService.SetExecutionCredentials%2A> und <xref:ReportExecution2005.ReportExecutionService.SetExecutionParameters%2A> verwenden.  
  
-   Rufen Sie die Methode <xref:ReportExecution2005.ReportExecutionService.Render%2A> zum Rendern des Berichts auf.  
  
 Während sich ein Bericht in einer Sitzung befindet, kann sich der in der Berichtsserver-Datenbank gespeicherte zugrundeliegende Bericht ändern. Beispiel: Die Berichtsdefinition kann sich ändern, der Bericht kann gelöscht oder verschoben werden, oder die Benutzerberechtigung kann sich ändern. Wenn sich der Bericht in einer aktiven Sitzung befindet, ist er von den Änderungen am zugrundeliegenden Bericht (also dem in der Berichtsserver-Datenbank gespeicherten Bericht) nicht betroffen.  
  
 Sie können eine Berichtssitzung auch mit URL-Zugriffsbefehlen verwalten.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:ReportExecution2005.ReportExecutionService.Render%2A>   
 [Technische Referenz (SSRS)](../../reporting-services/technical-reference-ssrs.md)   
 [Using Reporting Services SOAP Headers (Verwenden von Reporting Services SOAP-Headern)](../../reporting-services/report-server-web-service-net-framework-soap-headers/using-reporting-services-soap-headers.md)  
  
  
