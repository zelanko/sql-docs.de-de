---
title: Telemetriefeedback - Analytics Platform System | Microsoft-Dokumentation
description: Senden von telemetriefeedback an Microsoft zu Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 442505d470d1c7b7a82a02610d650d9f0b8c8d07
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591139"
---
# <a name="send-telemetry-feedback-to-microsoft-for-analytics-platform-system"></a>Senden von telemetriefeedback an Microsoft zu Analytics Platform System
Analytics Platform System verfügt über eine optionale telemetriefunktion, die Admin Console-Daten an Microsoft sendet. 
  
> [!NOTE]  
> In dieser Version überwacht Microsoft die Telemetriedaten nicht aktiv. Die Daten werden nur zu Analysezwecken gesammelt werden.  
  
## <a name="privacy"></a>Datenschutz  
Um die maximale Datenschutz bereitzustellen, wird Sie ohne Aktivieren der Telemetrie APS geliefert. Lesen Sie vor dem Aktivieren des Features zuerst die [Datenschutzbestimmungen von Microsoft Analytics Platform System](https://go.microsoft.com/fwlink/?LinkId=400902). Führen Sie zur Aktivierung der unten beschriebenen PowerShell-Skripts ein.  
  
## <a name="enable"></a>Aktivieren Sie die Telemetrie  
**DNS-Weiterleitung:** Senden von Telemetriedaten an Microsoft erfordert Analytics Platform System für die Verbindung mit dem Internet über eine DNS-Weiterleitung. Um dieses Feature zu aktivieren, müssen Sie DNS-Weiterleitung auf allen Hosts und Workload-VMs aktivieren. Rufen Sie die `Enable-RemoteMonitoring` -Befehl mit der `SetupDnsForwarder` Option aus, um ordnungsgemäß zu DNS-Weiterleitung konfigurieren und aktivieren die Telemetrie. Rufen Sie die `Enable-RemoteMonitoring` ohne die `SetupDnsForwarder` option, wenn die DNS-Weiterleitung bereits konfiguriert ist, und Sie nur die Taktüberwachung aktivieren möchten.  
  
> [!IMPORTANT]  
> DNS-Weiterleitung aktivieren, wird die Internetverbindung für alle Hosts und Workload-VMs geöffnet.  
  
#### <a name="to-enable-feedback"></a>Um Feedback zu aktivieren.  
  
1.  Mit einem Domänenadministratorkonto für die Anwendung und Herstellen einer Verbindung mit dem Steuerungsknoten (<strong>*Appliance_domain*-CTL01</strong>), und öffnen Sie eine Eingabeaufforderung unter Verwendung von Windows-Administratoranmeldeinformationen.  
  
2.  Navigieren Sie zum folgenden Verzeichnis: `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
3.  Importieren Sie das Modul `Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Sie importieren muss zwei Punkte im Befehl verwenden.  
  
    **Beispiel:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Rufen Sie die `Enable-RemoteMonitoring` Befehl.  
  
    > [!NOTE]  
    > Das Skript wird davon ausgegangen, dass die Internetverbindung ordnungsgemäß funktioniert, und nicht, dass die Internetverbindung überprüft.  
  
    1.  Verwenden Sie folgenden Befehl bei der ersten Aktivierung der Telemetriedaten, um sicherzustellen, dass alle DNS-Weiterleitungen ordnungsgemäß konfiguriert sind. In diesem Beispiel ersetzt die DNS-weitergeleiteten IP-Adresse `xx.xx.xx.xx` mit der DNS-Weiterleitung-IP-Adresse in Ihrer Umgebung.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring -SetupDnsForwarder -DnsForwarderIp xx.xx.xx.xx  
        ```  
  
    2.  Bei der DNS-Weiterleitungen bereits konfiguriert sind, wie z. B. Telemetriedaten Reaktivierung zuvor deaktiviert werden, verwenden Sie den folgenden Befehl zum Aktivieren der Telemetrie ohne DNS-Weiterleitung zu konfigurieren.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring  
        ```  
  
5.  Sie werden aufgefordert, die zum Lesen und bestätigen Sie, dass APS Informationen über die Appliance sammelt. Es wird ein Link in der APS-datenschutzerklärung an die Sie kopieren und fügen Sie in einem Internetbrowser zur Überprüfung können vorhanden sein.  
  
6.  Geben Sie **Y** zu übernehmen, und aktivieren Sie Feedback, oder geben **N** nicht zu akzeptieren.  
  
7.  Wenn Sie eingegeben haben **Y** stehen eine Reihe von Befehlen, die ausgeführt wird und die Telemetrie (und optional die DNS-Weiterleitung) aktiviert die Funktion auf Ihrem Gerät. Wenden Sie sich an CSS um Unterstützung zu erhalten, wenn alle Fehler, oder Informationen, die gelangen Sie zu der Annahme, dass der Befehl nicht erfolgreich war.  
  
Wenn Sie eingegeben haben **N**, werden keine Befehle ausgeführt werden und das Feature nicht aktiviert und ist es nicht mehr für Sie ausführen.  
  
Ist es nicht schädlich beim Ausführen der `Enable-RemoteMonitoring` Befehl mehrmals. Wenn die DNS-Weiterleitung bereits festgelegt ist, erhalten Sie eine Warnmeldung angezeigt, dass dies der Fall ist.  
  
## <a name="disable"></a>Deaktivieren der Telemetrie  
Deaktivieren der Telemetrie, werden alle Vorgänge beendet die Informationen über den Zustand des Geräts an den APS-Überwachungsdienst in der Cloud kommunizieren.  
  
> [!IMPORTANT]  
> Ausführen des Vorgangs wird nicht deaktiviert werden, Ihre DNS-Weiterleitung oder eine Internetverbindung, die möglicherweise von anderen Funktionen in das Gerät verwendet wird.  
  
#### <a name="to-disable-telemetry"></a>Zum Deaktivieren der Telemetrie  
  
1.  Mit einem Domänenadministratorkonto für die Anwendung und Herstellen einer Verbindung mit dem Steuerungsknoten (<strong>*Appliance_domain*-CTL01</strong>), und öffnen Sie ein PowerShell-Fenster mit Administratorrechten aus.  
  
2.  Navigieren Sie zum folgenden Verzeichnis: `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100`.  
  
3.  Importieren Sie das Modul `Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Sie importieren muss zwei Punkte im Befehl verwenden.  
  
    **Beispiel:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Rufen Sie die `Disable-RemoteMonitoring` -Befehl ohne Parameter. Mit diesem Befehl wird das Senden von Feedback beendet. (Diese lokale Überwachung wirkt sich nicht.) Der Befehl wird jedoch nicht die DNS-Weiterleitung deaktivieren und/oder Internetverbindung deaktivieren. Dies muss manuell durchgeführt werden, nach der Deaktivierung erfolgreich Feedback.  
  
    **Beispiel:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Disable-RemoteMonitoring  
    ```  
  
Wenden Sie sich an CSS um Unterstützung zu erhalten, wenn alle Fehler, oder Informationen, die gelangen Sie zu der Annahme, dass der Befehl nicht erfolgreich war.  
  
Ist es nicht schädlich beim Ausführen der `Disable-RemoteMonitoring` Befehl mehrmals.  
  
## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen finden Sie in den folgenden Themen:
- [Überwachen der Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
- [Überwachen der Appliance mithilfe von Systemansichten &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
- [Überwachen der Appliance mithilfe von System Center Operationsmanager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
- [Verwenden Sie eine DNS-Weiterleitung nicht zur Appliance gehört DNS-Namen auflösen &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
  
