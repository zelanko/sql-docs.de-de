---
title: Webdienst (Task) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicetask.f1
helpviewer_keywords:
- Web Service task [Integration Services]
ms.assetid: 5c7206f1-7d6a-4923-8dff-3c4912da4157
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f21a5f938b2dcd7b90fa71ab946d2986b0633987
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "62829404"
---
# <a name="web-service-task"></a>Webdienst (Task)
  Der Task "Webdienst" führt eine Webdienstmethode aus. Der Task "Webdienst" kann für folgende Zwecke verwendet werden:  
  
-   Schreiben der von einer Webdienstmethode zurückgegebenen Werte in eine Variable. Beispielsweise können Sie die Tageshöchsttemperatur von einer Webdienstmethode abrufen und dann mit diesem Wert eine Variable aktualisieren, die in einem Ausdruck zum Festlegen eines Spaltenwertes verwendet wird.  
  
-   Schreiben der von einer Webdienstmethode zurückgegebenen Werte in eine Datei. Beispielsweise kann eine Liste potenzieller Kunden in eine Datei geschrieben werden. Diese Datei kann dann in einem Paket als Datenquelle verwendet werden, mit dem die Daten vor dem Schreiben in eine Datenbank bereinigt werden.  
  
## <a name="wsdl-file"></a>WSDL-Datei  
 Der Task "Webdienst" verwendet einen HTTP-Verbindungs-Manager, um eine Verbindung mit dem Webdienst herzustellen. Der HTTP-Verbindungs-Manager wird separat vom Task Webdienst konfiguriert, und im Task wird dann darauf verwiesen. Der HTTP-Verbindungs-Manager gibt die Serverproxyeinstellungen an, wie z. B. die Server-URL, Anmeldeinformationen für den Zugriff auf den Webdiensteserver und die Timeoutlänge. Weitere Informationen finden Sie unter [HTTP-Verbindungs-Manager](../connection-manager/http-connection-manager.md).  
  
> [!IMPORTANT]  
>  Der HTTP-Verbindungs-Manager unterstützt nur die anonyme Authentifizierung und die Standardauthentifizierung. Er unterstützt keine Windows-Authentifizierung.  
  
 Der HTTP-Verbindungs-Manager kann auf eine Website oder eine WSDL-Datei (Web Service Description Language) zeigen. Die URL des HTTP-Verbindungs-Managers, die auf eine WSDL-Datei zeigt, enthält den `?WSDL` -Parameter: beispielsweise `http://MyServer/MyWebService/MyPage.asmx?WSDL`.  
  
 Die WSDL-Datei muss lokal verfügbar sein, um den Task Webdienst mithilfe des Dialogfelds **Editor für den Task Webdienst** des [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designers zu konfigurieren.  
  
-   Falls der HTTP-Verbindungs-Manager auf eine Website zeigt, muss die WSDL-Datei manuell auf einen lokalen Computer kopiert werden.  
  
-   Falls der HTTP-Verbindungs-Manager auf eine WSDL-Datei zeigt, kann mit dem Task Webdienst die Datei von der Website in eine lokale Datei heruntergeladen werden.  
  
 In der WSDL-Datei sind die Methoden des Webdienstes, die für die Methoden erforderlichen Eingabeparameter, die von den Methoden zurückgegebenen Antworten und die Kommunikationsmethode mit dem Webdienst aufgelistet.  
  
 Falls die Methode Eingabeparameter verwendet, erfordert der Task Webdienst Parameterwerte. Beispielsweise muss für eine Webdienstmethode, die anhand Ihrer Größe die zu kaufende Skilänge empfiehlt, Ihre Größe mithilfe eines Eingabeparameters übergeben werden. Die Parameterwerte können entweder über im Task definierte Zeichenfolgen oder über im Bereich des Tasks bzw. im übergeordneten Container definierte Variablen übergeben werden. Die Verwendung von Variablen bietet den Vorteil, dass die Parameterwerte über Paketkonfigurationen oder Skripts dynamisch aktualisiert werden können. Weitere Informationen finden Sie unter [Integration Services-Variablen &#40;SSIS&#41;](../integration-services-ssis-variables.md) und [Paketkonfigurationen](../package-configurations.md).  
  
 Viele Webdienstmethoden verwenden keine Eingabeparameter. Beispielsweise ist für eine Webdienstmethode, die die Namen der im aktuellen Monat geborenen Präsidenten abruft, kein Eingabeparameter notwendig, weil der Webdienst den aktuellen Monat lokal bestimmen kann.  
  
 Die Ergebnisse der Webdienstmethode können in eine Variable oder eine Datei geschrieben werden. Mit dem Dateiverbindungs-Manager geben Sie entweder die Datei an oder stellen den Namen der Variablen bereit, in die die Ergebnisse geschrieben werden sollen. Weitere Informationen finden Sie unter [File Connection Manager](../connection-manager/file-connection-manager.md) und [Integration Services-Variablen &#40;SSIS&#41;](../integration-services-ssis-variables.md).  
  
## <a name="custom-logging-messages-available-on-the-web-service-task"></a>Verfügbare benutzerdefinierte Meldungen für die Protokollierung für den Task 'Webdienst'  
 In der folgenden Tabelle werden die benutzerdefinierten Protokolleinträge aufgelistet, die für den Task 'Webdienst' aktiviert werden können. Weitere Informationen finden Sie unter [Integration Services-Protokollierung &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) und [Benutzerdefinierte Meldungen für die Protokollierung](../custom-messages-for-logging.md).  
  
|Protokolleintrag|BESCHREIBUNG|  
|---------------|-----------------|  
|`WSTaskBegin`|Der Zugriff auf einen Webdienst wurde begonnen.|  
|`WSTaskEnd`|Eine Webdienstmethode wurde beendet.|  
|`WSTaskInfo`|Beschreibende Informationen zum Task.|  
  
## <a name="configuration-of-the-web-service-task"></a>Konfiguration der Task "Webdienst"  
 Sie können Eigenschaften mit dem [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer oder programmgesteuert festlegen.  
  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zu den Eigenschaften zu erhalten, die Sie im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer festlegen können:  
  
-   [Editor für den Task „Webdienst“ &#40;Seite „Allgemein“&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Editor für den Task „Webdienst“ &#40;Seite „Eingabe“&#41;](../web-service-task-editor-input-page.md)  
  
-   [Editor für den Task „Webdienst“ &#40;Seite „Ausgabe“&#41;](../web-service-task-editor-output-page.md)  
  
-   [Seite Ausdrücke](../expressions/expressions-page.md)  
  
 Klicken Sie auf das folgende Thema, um weitere Informationen zum Festlegen dieser Eigenschaften im [!INCLUDE[ssIS](../../includes/ssis-md.md)] -Designer zu erhalten:  
  
-   [Festlegen der Eigenschaften eines Tasks oder Containers](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-web-service-task"></a>Programmgesteuerte Konfiguration des Task "Webdienst"  
 Klicken Sie auf eines der folgenden Themen, um weitere Informationen zum programmgesteuerten Festlegen dieser Eigenschaften zu erhalten:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WebServiceTask.WebServiceTask>  
  
## <a name="related-content"></a>Verwandte Inhalte  
 Video [Vorgehensweise: Aufrufen eines Webdiensts mit dem Task 'Webdienst' (SQL Server-Video)](https://go.microsoft.com/fwlink/?LinkId=259642)auf technet.microsoft.com.  
  
 Verwenden des [Webdiensts über das SSIS-Paket](https://www.c-sharpcorner.com/article/how-to-consume-web-service-through-ssis-package/).  
  
  
