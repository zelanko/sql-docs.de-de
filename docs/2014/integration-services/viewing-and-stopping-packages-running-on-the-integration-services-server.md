---
title: Anzeigen und Beenden von Paketen, die unter der Integration Services-Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing running packages [Integration Services]
- packages [Integration Services], running
- running package [Integration Services], managing
ms.assetid: 11bf44e6-f6b0-475f-b816-40e914dbac80
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 993f5cc3cba13e9a7d2c6380f719d5e7b24ca0a1
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48140560"
---
# <a name="viewing-and-stopping-packages-running-on-the-integration-services-server"></a>Anzeigen und Beenden von auf dem Integration Services-Server ausgeführten Paketen
  Die `SSISDB` Datenbank speichert den Ausführungsverlauf in internen Tabellen, die nicht für Benutzer sichtbar sind. Es werden jedoch Informationen verfügbar gemacht, die für öffentliche Sichten benötigt werden, die Sie abfragen können. Außerdem werden gespeicherte Prozeduren bereitgestellt, die Sie aufrufen können, um allgemeine Aufgaben im Zusammenhang mit Paketen auszuführen.  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Objekte auf dem Server werden i. d. R. in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]verwaltet. Sie können jedoch auch die Datenbanksichten abfragen und gespeicherte Prozeduren direkt aufrufen oder benutzerdefinierten Code schreiben, mit dem die verwaltete API aufgerufen wird. [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] und die verwaltete API Abfrage der Sichten und gespeicherte Prozeduren zum Durchführen vieler Aufgaben aufrufen. Sie können beispielsweise die Liste der [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] -Pakete anzeigen, die derzeit auf dem Server ausgeführt werden, und bei Bedarf einzelne Pakete anhalten.  
  
## <a name="viewing-the-list-of-running-packages"></a>Anzeigen der Liste ausgeführter Pakete  
 Sie können die Liste der momentan auf dem Server ausgeführten Pakete im Dialogfeld **Aktive Vorgänge** anzeigen. Weitere Informationen finden Sie unter [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).  
  
 Informationen zu weiteren Methoden, mit denen Sie die Liste der ausgeführten Pakete anzeigen können, finden Sie in den folgenden Themen.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)]-Zugriff  
 Fragen Sie die Sicht [catalog.executions &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database) nach Paketen ab, die einen Status von 2 aufweisen, um die Liste der Pakete anzuzeigen, die auf dem Server ausgeführt werden.  
  
 Programmgesteuerter Zugriff auf die verwaltete API  
 Weitere Details finden Sie in den Informationen zum <xref:Microsoft.SqlServer.Management.IntegrationServices>-Namespace und den zugehörigen Klassen.  
  
## <a name="stopping-a-running-package"></a>Beenden eines ausgeführten Pakets  
 Sie können die Beendigung eines ausgeführten Pakets im Dialogfeld **Aktive Vorgänge** anfordern. Weitere Informationen finden Sie unter [Active Operations Dialog Box](../../2014/integration-services/active-operations-dialog-box.md).  
  
 Informationen zu weiteren Methoden, mit denen Sie Pakete beenden können, die derzeit ausgeführt werden, finden Sie in den folgenden Themen.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)]-Zugriff  
 Rufen Sie die gespeicherte Prozedur [catalog.stop_operation &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-stored-procedures/catalog-stop-operation-ssisdb-database) auf, um ein Paket zu beenden, das auf dem Server ausgeführt wird.  
  
 Programmgesteuerter Zugriff auf die verwaltete API  
 Weitere Details finden Sie in den Informationen zum <xref:Microsoft.SqlServer.Management.IntegrationServices>-Namespace und den zugehörigen Klassen.  
  
## <a name="viewing-the-history-of-packages-that-have-run"></a>Anzeigen des Verlaufs ausgeführter Pakete  
 Verwenden Sie den Bericht [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]Alle Ausführungen **, um den Verlauf der Pakete anzuzeigen, die in** ausgeführt wurden. Weitere Informationen zum Bericht **Alle Ausführungen** und zu anderen Standardberichten finden Sie unter [Berichte für den Integration Services-Server](../../2014/integration-services/reports-for-the-integration-services-server.md).  
  
 Informationen zu weiteren Methoden, mit denen Sie den Verlauf der ausgeführten Pakete anzeigen können, finden Sie in den folgenden Themen.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)]-Zugriff  
 Um Informationen zu Paketen anzuzeigen, die ausgeführt wurden, fragen Sie die Sicht [catalog.executions &#40;SSISDB-Datenbank&#41;](/sql/integration-services/system-views/catalog-executions-ssisdb-database) ab.  
  
 Programmgesteuerter Zugriff auf die verwaltete API  
 Weitere Details finden Sie in den Informationen zum <xref:Microsoft.SqlServer.Management.IntegrationServices>-Namespace und den zugehörigen Klassen.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführung von Projekten und Paketen](packages/run-integration-services-ssis-packages.md)   
 [Behandlung von Problemen in Berichten für die Paketausführung](troubleshooting/troubleshooting-reports-for-package-execution.md)  
  
  
