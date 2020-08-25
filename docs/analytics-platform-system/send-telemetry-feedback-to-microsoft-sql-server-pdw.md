---
title: Telemetriefeedback
description: Senden Sie telemetriefeedback an Microsoft for Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 639eb4e9e5c531e154b9eb7f91165af365bc519f
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "74400362"
---
# <a name="send-telemetry-feedback-to-microsoft-for-analytics-platform-system"></a>Senden von telemetriefeedback an Microsoft for Analytics Platform System
Analytics Platform System verfügt über ein optionales telemetriefeature, mit dem Verwaltungs Konsolen Daten an Microsoft gesendet werden. 
  
> [!NOTE]  
> In dieser Version überwacht Microsoft die Telemetriedaten nicht aktiv. Die Daten werden nur zu Analysezwecken gesammelt.  
  
## <a name="privacy"></a><a name="privacy"></a>Datenschutz  
Um den maximalen Datenschutz zu gewährleisten, wird APS ohne Aktivierung der Telemetrie ausgeliefert. Bevor Sie dieses Feature aktivieren, überprüfen Sie zunächst die [Microsoft Analytics Platform System Datenschutzbestimmungen](https://go.microsoft.com/fwlink/?LinkId=400902). Führen Sie das unten beschriebene PowerShell-Skript aus, um sich zu entscheiden.  
  
## <a name="enable-telemetry"></a><a name="enable"></a>Aktivieren von Telemetrie  
**DNS-Weiterleitung:** Zum Senden von Telemetriedaten an Microsoft muss das Analytics Platform System über eine DNS-Weiterleitung eine Verbindung mit dem Internet herstellen. Zum Aktivieren dieses Features müssen Sie die DNS-Weiterleitung auf allen Hosts und Arbeits Auslastungs-VMS aktivieren. Rufen `Enable-RemoteMonitoring` Sie den Befehl mit der `SetupDnsForwarder` Option zum ordnungsgemäßen Konfigurieren der DNS-Weiterleitung und zum Aktivieren der Telemetrie auf Rufen `Enable-RemoteMonitoring` Sie den Befehl ohne die `SetupDnsForwarder` Option auf, wenn die DNS-Weiterleitung bereits konfiguriert ist und Sie nur die Takt Überwachung aktivieren möchten.  
  
> [!IMPORTANT]  
> Durch Aktivieren der DNS-Weiterleitung wird die Internetverbindung für alle Hosts und workloadvms geöffnet  
  
#### <a name="to-enable-feedback"></a>So aktivieren Sie Feedback  
  
1.  Stellen Sie mithilfe eines Appliance-Domänen Administrator Kontos eine Verbindung mit dem Steuerungs Knoten (<strong>*appliance_domain*-CTL01</strong>) her, und öffnen Sie mithilfe der Windows-Administrator Anmelde Informationen eine Eingabeaufforderung.  
  
2.  Navigieren Sie zum folgenden Verzeichnis: `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100` .  
  
3.  Importieren des Moduls `Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Zum Importieren von müssen Sie zwei Zeiträume im-Befehl verwenden.  
  
    **Beispiel:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Rufen Sie den `Enable-RemoteMonitoring` Befehl auf.  
  
    > [!NOTE]  
    > Das Skript geht davon aus, dass die Internetverbindung ordnungsgemäß funktioniert und die Internetverbindung nicht überprüft.  
  
    1.  Wenn Sie die Telemetrie zum ersten Mal aktivieren, verwenden Sie den folgenden Befehl, um sicherzustellen, dass alle DNS-Weiterleitungen ordnungsgemäß konfiguriert sind. Ersetzen Sie in diesem Beispiel die IP-Adresse des DNS-weitergeleiteten `xx.xx.xx.xx` durch die DNS-Weiterleitungs-IP-Adresse in Ihrer Umgebung.  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring -SetupDnsForwarder -DnsForwarderIp xx.xx.xx.xx  
        ```  
  
    2.  Wenn DNS-Weiterleitungen bereits konfiguriert sind, z. b. das erneute Aktivieren von zuvor deaktivierten Telemetriedaten, verwenden Sie den folgenden Befehl, um Telemetriedaten zu aktivieren, ohne  
  
        ```  
        PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Enable-RemoteMonitoring  
        ```  
  
5.  Sie werden aufgefordert, zu lesen und zu bestätigen, dass APS Informationen über die Appliance sammelt. Es gibt einen Link zu den Datenschutzbestimmungen von APS, die Sie kopieren und zur Überprüfung in einen beliebigen Internetbrowser einfügen können.  
  
6.  Geben Sie **Y** ein **, um das** Feedback zu akzeptieren und zu abonnieren.  
  
7.  Wenn Sie **Y** eingegeben haben, gibt es eine Reihe von Befehlen, die ausgeführt werden, um die Telemetrie (und optional das DNS-Weiterleitungs Feature) auf Ihrer Appliance zu aktivieren. Wenn Sie Fehler oder Informationen sehen, die Sie dazu führen, dass der Befehl nicht erfolgreich ist, wenden Sie sich an CSS, um Unterstützung zu erhalten.  
  
Wenn Sie " **N**" eingegeben haben, werden keine Befehle ausgeführt, und die Funktion wird nicht aktiviert, und Sie müssen nichts weiter tun.  
  
Es gibt keinen Schaden bei der mehrfach Ausführung des `Enable-RemoteMonitoring` Befehls. Wenn die DNS-Weiterleitung bereits festgelegt ist, erhalten Sie eine Warnmeldung, die angibt, dass dies der Fall ist.  
  
## <a name="disable-telemetry"></a><a name="disable"></a>Deaktivieren der Telemetrie  
Durch das Deaktivieren der Telemetrie werden alle Vorgänge angehalten, die Informationen über den Zustand des Geräts an den APS-Überwachungsdienst in der Cloud übermitteln.  
  
> [!IMPORTANT]  
> Wenn Sie diesen Vorgang ausführen, wird Ihre DNS-Weiterleitung oder Internetverbindung, die möglicherweise von anderen Features in der Appliance verwendet wird, nicht deaktiviert.  
  
#### <a name="to-disable-telemetry"></a>So deaktivieren Sie Telemetrie  
  
1.  Stellen Sie mithilfe eines Appliance-Domänen Administrator Kontos eine Verbindung mit dem Steuerungs Knoten (<strong>*appliance_domain*-CTL01</strong>) her, und öffnen Sie ein PowerShell-Fenster mit Administratorrechten.  
  
2.  Navigieren Sie zum folgenden Verzeichnis: `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100` .  
  
3.  Importieren des Moduls `Configure-RemoteMonitoring.ps1`  
  
    > [!NOTE]  
    > Zum Importieren von müssen Sie zwei Zeiträume im-Befehl verwenden.  
  
    **Beispiel:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> . .\Configure-RemoteMonitoring.ps1  
    ```  
  
4.  Rufen Sie den `Disable-RemoteMonitoring` Befehl ohne Parameter auf. Mit diesem Befehl wird das Senden von Feedback beendet. (Dies wirkt sich nicht auf die lokale Überwachung aus.) Der Befehl deaktiviert jedoch nicht die DNS-Weiterleitung und/oder deaktiviert jegliche Internet Konnektivität. Dies muss manuell nach der erfolgreichen Deaktivierung des Feedbacks erfolgen.  
  
    **Beispiel:**  
  
    ```  
    PS C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100> Disable-RemoteMonitoring  
    ```  
  
Wenn Sie Fehler oder Informationen sehen, die Sie dazu führen, dass der Befehl nicht erfolgreich ist, wenden Sie sich an CSS, um Unterstützung zu erhalten.  
  
Es gibt keinen Schaden bei der mehrfach Ausführung des `Disable-RemoteMonitoring` Befehls.  
  
## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen finden Sie unter
- [Überwachen Sie die Appliance mithilfe der Verwaltungskonsole &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)  
- [Überwachen der Appliance mithilfe von System Sichten &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-views.md)  
- [Überwachen Sie die Appliance mithilfe System Center Operations Manager &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-system-center-operations-manager.md)  
- [Verwenden Sie eine DNS-Weiterleitung zum Auflösen von DNS-Namen, die keine Appliance sind &#40;Analytics Platform System&#41;](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
  
