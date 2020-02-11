---
title: Servereigenschaften (Seite Erweitert) – Reporting Services | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/18/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.advanced.f1
ms.assetid: 07b78a84-a6aa-4502-861d-349720ef790e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3991618e6f77eab9ae96b2879098f91dab5a748a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "66099655"
---
# <a name="server-properties-advanced-page---reporting-services"></a>Servereigenschaften (Seite Erweitert) – Reporting Services
  Verwenden Sie diese Seite, um Systemeigenschaften auf dem Berichtsserver festzulegen. Es gibt eine Anzahl von Möglichkeiten, Systemeigenschaften festzulegen. Dieses Tool stellt eine grafische Benutzeroberfläche bereit, so dass Sie Eigenschaften festlegen können, ohne Code schreiben zu müssen.  
  
 Öffnen Sie diese Seite, indem Sie [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]starten und eine Verbindung mit einer Berichtsserverinstanz herstellen. Klicken Sie mit der rechten Maustaste auf den Namen des Berichtsservers, und wählen Sie anschließend **Eigenschaften**aus. Klicken Sie auf **Erweitert** , um diese Seite zu öffnen.  
  
## <a name="options"></a>Tastatur  
 **Enablemyreports**  
 Gibt an, ob die Funktion <legacyBold>Meine Berichte</legacyBold> aktiviert ist. Der Wert `true` gibt an, dass die Funktion aktiviert ist.  
  
 **MyReportsRole**  
 Der Name der Rolle, die beim Erstellen von Sicherheitsrichtlinien für die Ordner <legacyBold>Meine Berichte</legacyBold> des Benutzers verwendet wird. Standardwert: `My Reports Role`.  
  
 **EnableClientPrinting**  
 Bestimmt, ob das RSClientPrint-ActiveX-Steuerelement zum Herunterladen vom Berichtsserver verfügbar ist. Gültige Werte sind `true` und `false`. Standardwert: `true`. Weitere Informationen zu zusätzlichen Einstellungen, die für dieses Steuerelement erforderlich sind, finden Sie unter [Aktivieren und Deaktivieren des clientseitigen Drucks für Reporting Services](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).  
  
 **EnableExecutionLogging**  
 Gibt an, ob die Protokollierung der Berichtsausführung aktiviert ist. Standardwert: `true`. Weitere Informationen zum Berichts Server-Ausführungs Protokoll finden Sie unter [Berichts Server-Ausführungs Protokoll und die ExecutionLog3-Sicht](../report-server/report-server-executionlog-and-the-executionlog3-view.md).  
  
 **Executionlogdaysaufbewahrt**  
 Die Anzahl von Tagen, in denen die Berichtsausführungsdaten im Ausführungsprotokoll verbleiben. Gültige Werte für diese Eigenschaft sind `-1` und `2`,`147`,`483`,`647`. Wenn der Wert `-1` ist, werden Einträge nicht aus der Ausführungsprotokolltabelle gelöscht. Standardwert: `60`.  
  
 **SessionTimeout**  
 Der Zeitraum in Sekunden, in dem die Sitzung aktiv bleibt. Standardwert: `600`.  
  
 **Sharepointintegratedmode**  
 Dies ist eine schreibgeschützte Eigenschaft, die den Servermodus angibt. Wenn dieser Wert False ist, wird der Berichtsserver im einheitlichen Modus ausgeführt.  
  
 **Sitename**  
 Der Name der Berichtsserversite, der im Seitentitel des Berichts-Managers angezeigt wird. Standardwert: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Diese Eigenschaft kann eine leere Zeichenfolge sein. Die maximale Länge beträgt 8,000 Zeichen.  
  
 **Storedparameterslifetime**  
 Gibt die maximale Anzahl von Tagen an, während derer ein gespeicherter Parameter gespeichert werden kann. Gültige Werte sind `-1`, `+1` und `2,147,483,647`. Der Standardwert ist `180` Tage.  
  
 **StoredParametersThreshold**  
 Gibt die maximale Anzahl von Parameterwerten an, die von dem Berichtsserver gespeichert werden können. Gültige Werte sind `-1`, `+1` und `2,147,483,647`. Standardwert: `1500`.  
  
 **"US-Sitzungs Cookies"**  
 Gibt an, ob der Berichtsserver beim Kommunizieren mit Clientbrowsern Sitzungscookies verwenden soll. Standardwert: `true`.  
  
 **Externalimagestimeout**  
 Legt den Zeitraum fest, innerhalb dessen eine externe Bilddatei abgerufen werden muss, bevor ein Timeout für die Verbindung vorliegt. Der Standardwert `600` ist Sekunden.  
  
 **Snapshotcompression**  
 Definiert, wie Momentaufnahmen komprimiert werden. Standardwert: `SQL`. Die folgenden Werte sind gültig:  
  
 **SQL =** Momentaufnahmen werden komprimiert, wenn Sie in der Berichts Server-Datenbank gespeichert werden. Dies ist das aktuelle Verhalten.  
  
 **None** = Momentaufnahmen werden nicht komprimiert.  
  
 **Alle =** Momentaufnahmen werden für alle Speicheroptionen komprimiert, einschließlich der Berichts Server-Datenbank oder des Dateisystems.  
  
 **Systemreporttimeout**  
 Der Standard-Timeoutwert für die Berichtsverarbeitung in Sekunden für alle im Berichtsserver-Namespace verwalteten Berichte. Dieser Wert kann auf Berichtsebene überschrieben werden. Ist diese Eigenschaft festgelegt, versucht der Berichtsserver, die Verarbeitung eines Berichts zu beenden, sobald der angegebene Zeitraum überschritten wird. Gültige Werte sind `-1` und `2`,`147`,`483`,`647`. Wenn der Wert `-1` ist, tritt bei Berichten im Namespace während der Verarbeitung kein Timeout auf. Standardwert: `1800`.  
  
 **Systemsnapshotlimit**  
 Die maximale Anzahl an Momentaufnahmen, die für einen Bericht gespeichert werden. Gültige Werte sind `-1` und `2`,`147`,`483`,`647`. Lautet der Wert `-1`, so ist die Anzahl der Momentaufnahmen nicht einschränkt.  
  
 **EnableIntegratedSecurity**  
 Bestimmt, ob die integrierte Sicherheit von Windows für Berichtsdatenquellen-Verbindungen unterstützt wird. Der Standardwert lautet `True`. Die folgenden Werte sind gültig:  
  
 
  `True` = Integrierte Sicherheit von Windows ist aktiviert.  
  
 
  `False` = Integrierte Sicherheit von Windows ist nicht aktiviert. Berichtsdatenquellen, die für die Verwendung der integrierten Sicherheit von Windows konfiguriert sind, werden nicht ausgeführt.  
  
 `EnableLoadReportDefinition`  
 Wählen Sie diese Option um anzugeben, ob Benutzer eine Ad-hoc-Berichtsausführung von einem Bericht des Berichts-Generators ausführen können. Durch Festlegen dieser Option wird der Wert der `EnableLoadReportDefinition`-Eigenschaft auf dem Berichtsserver bestimmt.  
  
 Wenn Sie diese Option deaktivieren, wird die Eigenschaft auf False festgelegt, und der Berichtsserver generiert keine Berichte mit Durchklicken für Berichte, die ein Berichtsmodell als Datenquelle verwenden. Alle Aufrufe der LoadReportDefinition-Methode werden blockiert.  
  
 Die Deaktivierung dieser Option führt zu einem Sicherheitsrisiko, weil böswillige Benutzer einen Denial-of-Service-Angriff ausführen können, bei dem der Berichtsserver mit LoadReportDefinition-Anforderungen überlastet wird.  
  
 **EnableRemoteErrors**  
 Nimmt externe Fehlerinformationen (beispielsweise Fehlerinformationen zu Berichtsdatenquellen) in die Fehlermeldungen auf, die für Benutzer zurückgegeben werden, die Berichte von Remotecomputern anfordern. Gültige Werte sind `true` und `false`. Standardwert: `false`. Weitere Informationen finden Sie unter [Aktivieren von Remotefehlern &#40;Reporting Services&#41;](../report-server/enable-remote-errors-reporting-services.md).  
  
 **EnableReportDesignClientDownload**  
 Gibt an, ob das Berichts-Generator-Installationspaket vom Berichtsserver heruntergeladen werden kann. Wenn Sie diese Einstellung deaktivieren, funktioniert die URL zum Berichts-Generator nicht. Weitere Informationen finden Sie unter [Konfigurieren des Berichts-Generator-Zugriffs](../report-server/configure-report-builder-access.md).  
  
 **Editessioncachelimit**  
 Gibt die Anzahl von Datencacheeinträgen an, die in einer Berichtsbearbeitungssitzung aktiv sein können. Die Standardanzahl ist 5.  
  
 **Ediungessiontimeout**  
 Gibt die Anzahl von Sekunden bis zum Timeout einer Berichts Bearbeitungs Sitzung an. Der Standardwert ist 7200 Sekunden (2 Stunden).  
  
 **Enabletestconnectiondetailederrors**  
 Gibt an, ob ausführliche Fehlermeldungen an den Clientcomputer gesendet werden, wenn Benutzer Datenquellverbindungen mit dem Berichtsserver testen. Standardwert: `true`. Wenn die Option auf `false` festgelegt wird, werden nur generische Fehlermeldungen gesendet.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Festlegen von Berichtsservereigenschaften &#40;Management Studio&#41;](set-report-server-properties-management-studio.md)   
 [Vorgehensweise: Herstellen einer Verbindung mit einem Berichtsserver in Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Eigenschaften von Reporting Services](../report-server-web-service/net-framework/reporting-services-properties.md)   
 [Berichtsserver im Management Studio (F1-Hilfe)](report-server-in-management-studio-f1-help.md)   
 [Berichts Server-System Eigenschaften](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)   
 [Skript Bereitstellungs-und Verwaltungsaufgaben](script-deployment-and-administrative-tasks.md)   
 [Aktivieren und Deaktivieren von "Meine Berichte"](../report-server/enable-and-disable-my-reports.md)  
  
  
