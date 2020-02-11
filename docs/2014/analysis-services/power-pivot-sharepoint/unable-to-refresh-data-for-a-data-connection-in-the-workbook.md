---
title: 'Daten können nicht für eine Datenverbindung in der Arbeitsmappe aktualisiert werden. Versuchen Sie es erneut, oder wenden Sie sich an den Systemadministrator. Die folgenden Verbindungen wurden nicht aktualisiert: Power Pivot-Daten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0f6fd52d-ac72-43e3-aa08-05a2d2bb873d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 81e99fc17cb8f369967ff4c26699e67f0ed91d33
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070935"
---
# <a name="unable-to-refresh-data-for-a-data-connection-in-the-workbook-try-again-or-contact-your-system-administrator-the-following-connections-failed-to-refresh-powerpivot-data"></a>Daten können nicht für eine Datenverbindung in der Arbeitsmappe aktualisiert werden. Versuchen Sie es erneut, oder wenden Sie sich an den Systemadministrator. Die folgenden Verbindungen wurden nicht aktualisiert: PowerPivot-Daten
  Excel Services gibt diesen Fehler für Excel-Arbeitsmappen zurück, die PowerPivot-Daten enthalten, wenn es eine Verbindungsanforderung an einen PowerPivot-Server sendet und die Anforderung fehlschlägt.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Gilt für:|PowerPivot für SharePoint-Installation|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|Siehe unten.|  
|Meldungstext|Daten können nicht für eine Datenverbindung in der Arbeitsmappe aktualisiert werden. Versuchen Sie es erneut, oder wenden Sie sich an den Systemadministrator. Die folgenden Verbindungen wurden nicht aktualisiert: PowerPivot-Daten|  
  
## <a name="explanation-and-resolution"></a>Erklärung und Behebung  
 Mit Excel Services kann keine Verbindung mit den PowerPivot-Daten hergestellt werden, oder die PowerPivot-Daten können nicht geladen werden. Bedingungen, die zum Auftreten dieses Fehlers führen:  
  
 **Szenario 1: der Dienst wurde nicht gestartet.**  
  
 Die SQL Server Analysis Services (PowerPivot)-Instanz wurde nicht gestartet. Ein abgelaufenes Kennwort führt zum Anhalten der Ausführung des Diensts. Weitere Informationen zum Ändern des Kennworts finden Sie unter [Konfigurieren von Power Pivot-Dienst Konten](configure-power-pivot-service-accounts.md) und [starten oder Starten eines PowerPivot für SharePoint Servers](start-or-stop-a-power-pivot-for-sharepoint-server.md).  
  
 **Szenario 2a: Öffnen einer früheren Version der Arbeitsmappe auf dem Server**  
  
 Die Arbeitsmappe, die Sie zu öffnen versuchen, könnte in der SQL Server 2008 R2-Version von PowerPivot für Excel erstellt worden sein. Höchstwahrscheinlich ist der in der Datenverbindungszeichenfolge angegebene Analysis Service-Datenanbieter nicht auf dem Computer vorhanden, auf dem die Abfrage verarbeitet wird.  
  
 Wenn dies der Fall ist, wird diese Meldung im ULS-Protokoll angezeigt: "Fehler beim Aktualisieren von ' Power Pivot-Daten ' in der Arbeitsmappe\<' URL zu Arbeitsmappe '> '", gefolgt von "die Verbindung konnte nicht hergestellt werden".  
  
 Um die Version der Arbeitsmappe zu bestimmen, öffnen Sie sie in Excel, und überprüfen Sie, welcher Datenanbieter in der Verbindungszeichenfolge angegeben ist. Eine SQL Server 2008 R2-Arbeitsmappe verwendet MSOLAP.4 als Datenanbieter.  
  
 Um dieses Problem zu umgehen, können Sie die Arbeitsmappe aktualisieren. Alternativ können Sie Clientbibliotheken von der SQL Server 2008 R2-Version von Analysis Services auf den physischen Computern installieren, die PowerPivot für SharePoint oder Excel Services ausführen:  
  
 [Installieren des OLE DB-Anbieters für Analysis Services auf SharePoint-Servern](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md)  
  
 **Szenario 2B: Excel Services werden auf einem Anwendungsserver ausgeführt, der die falsche Version der Client Bibliotheken aufweist**  
  
 Standardmäßig wird von SharePoint Server 2010 die SQL Server 2008-Version vom OLE DB-Anbieter für Analysis Services auf Anwendungsservern installiert, auf denen Excel Services ausgeführt wird. In einer Farm, die PowerPivot-Datenzugriff unterstützt, müssen alle physischen Server, die Anwendungen ausführen, die PowerPivot-Daten anfordern, z. B. Excel Services und PowerPivot für SharePoint, eine höhere Version des Datenanbieters verwenden.  
  
 Server, auf denen PowerPivot für SharePoint ausgeführt wird, erhalten automatisch den aktualisierten OLE DB-Datenanbieter. Andere Server, beispielsweise solche, auf denen eine eigenständige Excel Services-Instanz ohne PowerPivot für SharePoint auf dem gleichen Computer ausgeführt wird, müssen für die Verwendung neuerer Clientbibliotheken gepatcht werden. Weitere Informationen finden Sie unter [Installieren des OLE DB-Anbieters für Analysis Services auf SharePoint-Servern](../../sql-server/install/install-the-analysis-services-ole-db-provider-on-sharepoint-servers.md).  
  
 **Szenario 3: Domänen Controller ist nicht verfügbar**  
  
 Eine mögliche Ursache ist, dass kein Domänencontroller verfügbar ist, um die Benutzeridentität zu überprüfen. Ein Domänencontroller ist für den Claims to Windows Token Service erforderlich, um den SharePoint-Benutzer für jede Verbindung zu authentifizieren. c2WTS (Claims to Windows Token Service) verwendet keine zwischengespeicherten Anmeldeinformationen. Er überprüft die Benutzeridentität für jede Verbindung.  
  
 Sie können die Ursache dieses Fehlers überprüfen, indem Sie die SharePoint-Protokolldatei anzeigen. Wenn die SharePoint-Protokolle die Meldung "Fehler beim Abrufen von WindowsIdentity aus IClaimsIdentity" enthalten, konnte die Benutzeridentität nicht authentifiziert werden.  
  
 Um dieses Problem zu umgehen, fügen Sie den Computer der gleichen Domäne wie der des PowerPivot-Servers hinzu, oder installieren Sie auf dem lokalen Computer einen Domänencontroller. Für die zweite Lösung, die Installation des Domänencontrollers, müssen Sie lokale Domänenkonten für alle Dienste und Benutzer erstellen. Sie müssen Dienstkonten und SharePoint-Berechtigungen für die Konten konfigurieren, die Sie definieren.  
  
 Die Installation eines Domänencontrollers auf Ihrem Computer ist nützlich, wenn die Zielsetzung darin besteht, PowerPivot für SharePoint in einem Offlinestatus zu verwenden. Ausführliche Anweisungen zur Offline Verwendung von Power Pivot finden Sie im Blogeintrag "Power Pivot-Server aus dem Netzwerk machen" unter [http://www.powerpivotgeek.com](https://go.microsoft.com/fwlink/?LinkId=184241).  
  
 **Szenario 4: instabiler Server**  
  
 Ein oder mehrere Dienste könnten sich in einem inkonsistenten Status befinden. In einigen Fällen kann das Problem durch Ausführen von IISRESET behoben werden.  
  
  
