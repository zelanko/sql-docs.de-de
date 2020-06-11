---
title: 'Die Datenverbindung verwendet die Windows-Authentifizierung, und Benutzeranmeldeinformationen konnten nicht delegiert werden. Die folgenden Verbindungen wurden nicht aktualisiert: Power Pivot-Daten | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d2006df1-d244-4786-b272-49d8996cc88c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9611bc9d922caee25f841b709ee8a743cd539357
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547752"
---
# <a name="the-data-connection-uses-windows-authentication-and-user-credentials-could-not-be-delegated-the-following-connections-failed-to-refresh-powerpivot-data"></a>Die Datenverbindung verwendet die Windows-Authentifizierung, und Benutzeranmeldeinformationen konnten nicht delegiert werden. Die folgenden Verbindungen wurden nicht aktualisiert: PowerPivot-Daten
  Für Excel-Arbeitsmappen, die PowerPivot-Daten enthalten, gibt Excel Services diesen Fehler zurück, wenn keine Verbindung mit einer PowerPivot-Serverinstanz in SharePoint hergestellt werden kann.  
  
## <a name="details"></a>Details  
  
|||  
|-|-|  
|Gilt für:|PowerPivot für SharePoint|  
|Produktversion|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Ursache|Verbindungsfehler beim Versuch, einen PowerPivot-Datenanbieter zu verwenden.|  
|Meldungstext|Die Datenverbindung verwendet die Windows-Authentifizierung, und Benutzeranmeldeinformationen konnten nicht delegiert werden. Die folgenden Verbindungen wurden nicht aktualisiert: PowerPivot-Daten|  
  
## <a name="explanation"></a>Erklärung  
 Es gibt mehrere Ursachen für diese Fehlermeldung. Alle haben gemeinsam, dass Excel Services keine gültige Windows-Benutzeridentität von einem Claims-Token in SharePoint abrufen können. Bei Excel-Arbeitsmappen, die PowerPivot-Daten enthalten, tritt dieser Fehler auf, wenn eine der folgenden Bedingungen zutrifft:  
  
-   c2WTS (Claims to Windows Token Service) wird nicht ausgeführt. Sie können die Ursache dieses Fehlers überprüfen, indem Sie die SharePoint-Protokolldatei anzeigen. Wenn die SharePoint-Protokolle die Meldung enthalten, dass der Pipeendpunkt "net.pipe://localhost/s4u/022694f3-9fbd-422b-b4b2-312e25dae2a2" auf dem lokalen Computer nicht gefunden wurde, wird c2WTS (Claims to Windows Token Service) nicht ausgeführt. Um ihn zu starten, verwenden Sie die Zentraladministration und überprüfen dann, ob der Dienst in der Konsolenanwendung Dienste ausgeführt wird.  
  
-   Es ist kein Domänencontroller verfügbar, um die Benutzeridentität zu überprüfen. c2WTS (Claims to Windows Token Service) verwendet keine zwischengespeicherten Anmeldeinformationen. Er überprüft die Benutzeridentität für jede Verbindung. Sie können die Ursache dieses Fehlers überprüfen, indem Sie die SharePoint-Protokolldatei anzeigen. Wenn die SharePoint-Protokolle die Meldung "Fehler beim Abrufen von WindowsIdentity aus IClaimsIdentity" enthalten, konnte die Benutzeridentität nicht authentifiziert werden.  
  
-   Die Computer müssen Mitglieder derselben Domäne oder mehrerer Domänen sein, die sich gegenseitig vertrauen.  
  
-   Sie müssen Windows-Domänenbenutzerkonten verwenden. Die Konten müssen über einen Universal Principal Name (UPN) verfügen.  
  
-   Das Excel Services-Dienstkonto muss über Active Directory-Berechtigungen zur Abfrage des Objekts verfügen.  
  
## <a name="user-action"></a>Benutzeraktion  
 Befolgen Sie die nachfolgenden Anweisungen, um den Status von c2WTS (Claims to Windows Token Service) zu überprüfen.  
  
 Wenden Sie sich in allen anderen Fällen an den Netzwerkadministrator.  
  
#### <a name="enable-claims-to-windows-token-service"></a>Aktivieren von c2WTS (Claims to Windows Token Service)  
  
1.  Klicken Sie in der Zentraladministration unter Systemeinstellungen auf **Dienste auf dem Server verwalten**.  
  
2.  Wählen Sie **Claims to Windows Token Service**aus, und klicken Sie dann auf **Starten**.  
  
3.  Überprüfen Sie, ob der Dienst auch in der Konsole Dienste ausgeführt wird.  
  
    1.  Klicken Sie unter Verwaltung auf Dienste.  
  
    2.  Starten Sie c2WTS (Claims to Windows Token Service), falls er nicht ausgeführt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren von PowerPivot-Dienstkonten](configure-power-pivot-service-accounts.md)  
  
  
