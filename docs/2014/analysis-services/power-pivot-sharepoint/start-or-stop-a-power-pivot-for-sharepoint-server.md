---
title: Starten oder Beenden eines PowerPivot für SharePoint-Server | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e38e6366-9f20-4db0-b2a8-da7d5adf00eb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 312afc0336405ca530f731ad4fec55a26a960e7a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66071050"
---
# <a name="start-or-stop-a-powerpivot-for-sharepoint-server"></a>Starten oder Beenden eines PowerPivot für SharePoint-Servers
  PowerPivot-Systemdienst und [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] Instanz arbeiten zusammen mit dem gleichen lokalen Anwendungsserver, die koordinierte Anforderungs- und Datenverarbeitung in einer SharePoint-Farm zu unterstützen.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
 [Dienstabhängigkeiten](#dependencies)  
  
 [Starten oder Beenden der Dienste](#startstop)  
  
 [Auswirkungen beim Beenden eines PowerPivot-Servers](#effects)  
  
##  <a name="dependencies"></a> Dienstabhängigkeiten  
 Der PowerPivot-Systemdienst ist von der lokalen Analysis Services-Serverinstanz abhängig, die zusammen mit dem Dienst auf dem gleichen physischen Server installiert ist. Wenn Sie den PowerPivot-Systemdienst beenden, müssen Sie auch die lokale Analysis Services-Serverinstanz manuell beenden. Wenn ein Dienst ohne den anderen ausgeführt wird, treten Fehler bei der Zuordnung von Anforderungen für die PowerPivot-Datenverarbeitung auf.  
  
 Der Analysis Services-Server sollte nur zu Diagnosezwecken oder zur Problembehandlung isoliert ausgeführt werden. In allen anderen Fällen erfordert der Server den PowerPivot-Systemdienst, der lokal auf dem gleichen Server ausgeführt wird.  
  
##  <a name="startstop"></a> Starten oder Beenden der Dienste  
 Verwenden Sie immer die Zentraladministration, um den PowerPivot-Systemdienst oder die Analysis Services-Serverinstanz zu starten oder zu beenden. Mit der Zentraladministration können Sie die Dienste gleichzeitig auf der gleichen Seite starten oder beenden. Außerdem verwendet die Zentraladministration einen Zeitgeberauftrag namens **Mindestens ein Dienst wurde unerwartet gestartet oder beendet** , um Dienste neu zu starten, von denen sie annimmt, dass sie ausgeführt werden sollen. Wenn Sie den PowerPivot-Systemdienst oder Analysis Services mit einem Nicht-SharePoint-Tool beenden, werden die Dienste neu gestartet, wenn der Zeitgeberauftrag ausgeführt wird.  
  
 Das Starten und Beenden von Diensten ist eine Aktion, die sich auf eine physische Dienstinstanz bezieht. Wenn Sie über zusätzliche PowerPivot für SharePoint-Server in der Farm verfügen, akzeptieren die anderen Server innerhalb der Farm weiterhin Anforderungen für PowerPivot-Daten.  
  
 In der Farm können nicht alle physischen Dienste gleichzeitig gestartet oder beendet werden. Sie müssen jeden Server auswählen und dann einen bestimmten Dienst starten oder beenden.  
  
 Sie können einen PowerPivot-Systemdienst nicht für eine bestimmte Webanwendung starten, anhalten oder beenden, Sie können einen Dienst jedoch aus der Standardverbindungsliste entfernen, damit er nicht verfügbar ist. Weitere Informationen finden Sie unter [Verbinden einer PowerPivot-Dienstanwendung zu einer SharePoint-Webanwendung in der Zentraladministration](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md).  
  
1.  Klicken Sie in der Zentraladministration unter **Systemeinstellungen**auf **Dienste auf dem Server verwalten**.  
  
2.  Klicken Sie oben auf der Seite unter Server auf den Pfeil nach unten und dann auf **Server ändern**.  
  
3.  Wählen Sie den SharePoint-Server mit dem PowerPivot-Systemdienst oder der [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)]-Instanz aus, den bzw. die Sie starten oder beenden möchten.  
  
4.  Wählen Sie den Dienst aus, und klicken Sie dann auf die Aktion. Denken Sie daran, die Dienste paarweise zu starten oder zu beenden. Wenn Sie den PowerPivot-Systemdienst starten oder beenden, müssen Sie auch die Analysis Services-Serverinstanz, die auf dem gleichen Computer ausgeführt wird, starten oder beenden.  
  
##  <a name="effects"></a> Auswirkungen beim Beenden eines PowerPivot-Servers  
 In der folgenden Tabelle werden die Auswirkungen beschrieben, die das Beenden des PowerPivot-Systemdiensts und Analysis Services-Diensts auf einem SharePoint-Server hat.  
  
|Auswirkungen auf|Beschreibung|  
|---------------|-----------------|  
|Vorhandene Abfragen|Auf einem Analysis Services-Server ausgeführte Abfragen werden sofort beendet. Der Benutzer erhält eine Fehlermeldung, dass keine Daten oder keine Datenquellenverbindung gefunden wurde.|  
|Vorhandene Datenaktualisierungsaufträge, die gerade verarbeitet werden|Auf dem aktuellen Analysis Services-Server ausgeführte Aufträge werden sofort beendet. Die Datenaktualisierung schlägt fehl, und im Datenaktualisierungsverlauf wird ein Fehler protokolliert.<br /><br /> Sie können den Status der aktuellen Aufträge anzeigen, bevor Sie den Dienst mithilfe der Seite Auftragsstatus überprüfen in der SharePoint-Zentraladministration beenden.<br /><br /> Obwohl die derzeit verarbeiteten Aufträge ermittelt werden können, gibt es keine Möglichkeit, die Warteschlange selbst anzuzeigen, um festzustellen, ob andere Aufträge gerade gestartet werden.|  
|Vorhandene Datenaktualisierungsanforderungen in der Warteschlange|Geplante Datenaktualisierungsanforderungen verbleiben während eines vollständigen Zeitplanzyklus (d. h.bis zur nächsten Startzeit) in der Verarbeitungswarteschlange. Wenn der PowerPivot-Systemdienst bis zu diesem Zeitpunkt nicht wieder gestartet wurde, wird die Datenaktualisierungsanforderung gelöscht und ein Fehler protokolliert.|  
|Neue Abfrage- oder Datenaktualisierungsanforderungen|Wenn Sie den einzigen PowerPivot für SharePoint-Server in der Farm beenden, werden neue Anforderungen für PowerPivot-Daten nicht verarbeitet, und eine Datenanforderung verursacht den Fehler "Daten wurden nicht gefunden".<br /><br /> Wenn Sie über zusätzliche PowerPivot für SharePoint-Server verfügen, wird die Anforderung einen der verfügbaren Server weitergeleitet.|  
|Verwendungsdaten|Es werden keine Verwendungsdaten gesammelt, während die Dienste beendet sind.|  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von PowerPivot-Dienstkonten](configure-power-pivot-service-accounts.md)  
  
  
