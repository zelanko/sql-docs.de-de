---
title: Konfigurieren von InfiniBand - Analytics Platform System | Microsoft-Dokumentation
description: Beschreibt, wie die InfiniBand-Netzwerkadapter auf einem Clientserver nicht zur Appliance gehört-für die Verbindung mit dem Steuerungsknoten auf Parallel Data Warehouse (PDW) zu konfigurieren. Verwenden Sie diese Anweisungen für eine hohe Verfügbarkeit und Konnektivität, sodass laden, Sicherung und andere Prozesse automatisch mit dem aktiven InfiniBand-Netzwerk zu verbinden.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 9e52e3962fa1928d7f7680a750d6c1efe5201c6f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63057185"
---
# <a name="configure-infiniband-network-adapters-for-analytics-platform-system"></a>Konfigurieren von InfiniBand-Netzwerkadapter für Analytics Platform System
Beschreibt, wie die InfiniBand-Netzwerkadapter auf einem Clientserver nicht zur Appliance gehört-für die Verbindung mit dem Steuerungsknoten auf Parallel Data Warehouse (PDW) zu konfigurieren. Verwenden Sie diese Anweisungen für eine hohe Verfügbarkeit und Konnektivität, sodass laden, Sicherung und andere Prozesse automatisch mit dem aktiven InfiniBand-Netzwerk zu verbinden.  
  
## <a name="Basics"></a>Beschreibung  
Diese Anleitungen zeigen Sie Informationen zum Suchen, und legen Sie dann die richtige InfiniBand IP-Adressen und Subnetzmasken auf dem Server mit InfiniBand-Verbindung. Sie wird auch erläutert, wie Konfigurieren des Servers für die APS-Appliance DNS verwenden, damit die Verbindung mit dem aktiven InfiniBand-Netzwerk aufgelöst wird.  
  
Für hohe Verfügbarkeit hat die APS zwei InfiniBand-Netzwerken: einen aktiven und eine Passive. Jedes InfiniBand-Netzwerk verfügt über eine andere IP-Adresse für den Steuerelementknoten aus. Fällt der aktive InfiniBand-Netzwerk aus, wird die passive InfiniBand-Netzwerk das aktive Netzwerk an. In diesem Fall verbindet sich ein Skript oder der Prozess automatisch mit dem aktiven InfiniBand-Netzwerk ohne die Skriptparameter an.  
  
Insbesondere in diesem Artikel Sie:  
  
1.  Suchen Sie die InfiniBand IP-Adressen von der APS-DNS-Servern (Appliance_domain-AD01 und Appliance_domain *-AD02). Dazu melden Sie sich bei dem AD01 und AD02-Server und die IP-Adressen für jedes InfiniBand-Netzwerk zu erhalten. Die InfiniBand IP-Adressen auf dem AD-Knoten sind die DNS IP-Adressen.  
  
2.  Konfigurieren Sie jeden Netzwerkadapter, um eine verfügbare IP-Adresse in der APS-InfiniBand-Netzwerken verwenden.  
  
    1.  Wenn Sie zwei InfiniBand-Netzwerkadapter haben, konfigurieren Sie einen Adapter einer verfügbaren IP-Adresse in das erste InfiniBand-Netzwerk TeamIB1 und der andere Adapter mit einer verfügbaren IP-Adresse in das zweite InfiniBand-Netzwerk heißt die TeamIB2 aufgerufen wird. Verwenden der Appliance_domain-AD01 TeamIB1 IP-Adresse als bevorzugter DNS-Server und Appliance_domain-AD02 TeamIB1 IP-Adresse wie der alternativen DNS-Server für den Netzwerkadapter-TeamIB1. Verwenden der Appliance_domain-AD01 TeamIB2 IP-Adresse als bevorzugter DNS-Server und Appliance_domain-AD02 TeamIB2 IP-Adresse wie der alternativen DNS-Server für TeamIB2-Netzwerkadapter.  
  
    2.  Wenn Sie nur ein InfiniBand-Netzwerkadapter haben, konfigurieren Sie den Adapter mit einer verfügbaren IP-Adresse eines InfiniBand-Netzwerke. Anschließend konfigurieren Sie die bevorzugte und alternative DNS-Server auf diesem Adapter entweder Appliance_domain-AD01 TeamIB1 und Appliance_domain-AD02 TeamIB1 oder Appliance_domain-AD01 TeamIB2 und Appliance_domain-AD02 TeamIB2 je nachdem, was auf dem gleichen ist das Netzwerk als der konfigurierte Adapter als die bevorzugte und alternative DNS-Server bzw.  
  
3.  Konfigurieren Sie Ihre InfiniBand-Netzwerkadapter zum APS DNS-Server verwenden, um die Verbindung mit dem aktiven InfiniBand-Netzwerk zu beheben.  
  
    1.  Für diese Konfiguration verwenden Sie die erweiterten TCP/IP-Einstellungen auf der Appliance-Domäne-DNS-Suffix an den Anfang der Liste der DNS-Suffixe auf Ihrem Clientserver hinzufügen. Dies muss nur auf einem Netzwerkadapter konfiguriert werden; die Einstellung gilt für beide Adapter.  
  
Nach dem Konfigurieren Ihrer InfiniBand-Netzwerkadapter, Clientprozesse können eine Verbindung mit dem Steuerungsknoten auf das InfiniBand-Netzwerk `PDW_region-SQLCTL01` für die Adresse des Servers. Ihr Server Fügt das Analytics Platform System, DNS-Suffix an, oder die vollständige Adresse handelt es sich eingeben `PDW_region-SQLCTL01.appliance_domain.pdw.local`.  
  
Beispielsweise ist, wenn der Name des PDW-Region MyPDW ist und ist der Name des MyAPS, Dwloader Serverspezifikation zum Laden von Daten eine der folgenden:  
  
-   `dwloader -S MYPDW-SQLCTL01.MyAPS.pdw.local`  
  
-   `dwloader -S MYPDW-SQLCTL01`  
  
## <a name="BeforeBegin"></a>Vorbereitungen  
  
### <a name="requirements"></a>Anforderungen  
Sie benötigen ein APS-Appliance-Domänenkonto auf den Knoten AD01 anmelden. Z. B. F12345 * \Administrator.  
  
Sie benötigen ein Windows-Konto auf dem Clientserver, der Berechtigung zum Konfigurieren der Netzwerkadapter hat.  
  
### <a name="prerequisites"></a>Erforderliche Komponenten  
Diese Anweisungen setzen voraus, der Clientserver ist bereits installiert und mit dem Gerät InfiniBand-Netzwerk installiert. Rer-nachverfolgung und Verkabelung Anweisungen finden Sie [abrufen und Konfigurieren eines Servers geladen](acquire-and-configure-loading-server.md).  
  
### <a name="general-remarks"></a>Allgemeine Hinweise  
Mithilfe von SQLCTL01 verbindet die DNS Analytics Platform System mit dem Steuerungsknoten Ihre Clientserver mithilfe der aktiven InfiniBand-Netzwerks an. Dies gilt nur für die erste verbunden; Wenn das InfiniBand-Netzwerk, während eines Auslastungstests ausfällt oder sichern, Sie den Prozess neu starten müssen.  
  
Um Ihre eigenen geschäftlichen Anforderungen zu erfüllen, können Sie die Clientserver auch Ihre eigenen nicht zur Appliance gehört Arbeitsgruppe oder einer Windows-Domäne verknüpfen.  
  
## <a name="Sec1"></a>Schritt 1: Abrufen der Appliances InfiniBand-Netzwerkeinstellungen  
*Die Appliance InfiniBand-Netzwerk-Einstellungen abrufen*  
  
1.  Melden Sie sich an das Gerät AD01 Knoten mit dem Appliance_domain\Administrator an.  
  
2.  Öffnen Sie auf dem Gerät AD01-Knoten die Systemsteuerung, wählen Sie, Netzwerk und Internet, auf Netzwerk und Freigabe Center *, und wählen Sie die Adaptereinstellungen ändern.  
  
3.  Klicken Sie im Fenster Netzwerkverbindungen mit der rechten Maustaste auf das Team IB1, und wählen Sie Eigenschaften.  
  
    ![InfiniBand-Verbindungen auf dem Verwaltungsknoten](media/network-teamib.png "InfiniBand-Verbindungen auf dem Verwaltungsknoten")  
  
4.  Aus dem Fenster Eigenschaften von Internetprotokoll Version 4 (TCP/IPv4) Notieren Sie sich die Werte für die **IP-Adresse** und **Subnetzmaske**.  Die IP-Adresse der  **_Appliance\_Domäne_-AD01** Knoten ist die IP-Adresse des Analytics Platform System, DNS-Servers.  
  
5.  Wiederholen Sie die Schritte 1 bis 5 oben für den Adapter TeamIB1 auf  **_Appliance\_Domäne_-AD02** Server.  
  
    ![PDW-Knoten InfiniBand 1 Verwaltungseigenschaften](media/network-ip1-properties.png "PDW Verwaltungseigenschaften Knoten InfiniBand 1")  
  
6.  Klicken Sie auf "Abbrechen", um das Fenster schließen.  
  
7.  Suchen Sie eine nicht verwendete IP-Adresse im Netzwerk TeamIB1, und notieren Sie ihn.  
  
    Um eine nicht verwendete IP-Adresse zu suchen, öffnen Sie ein Befehlsfenster, und versuchen Sie, IP-Adressen innerhalb des Bereichs von Adressen für Ihr Gerät zu pingen. In diesem Beispiel ist die IP-Adresse des Netzwerks TeamIB1 172.16.14.30. Suchen Sie eine IP-Adresse, die mit 172.16.14 beginnt, die nicht verwendet wird. Geben Sie über die Befehlszeile z. B. "ping 172.16.14.254". Wenn der Ping-Anforderung nicht erfolgreich ist, ist die IP-Adresse verfügbar.  
  
8.  Führen Sie dieselben Schritte für TeamIB2. In der * im Fenster Netzwerkverbindungen mit der rechten Maustaste auf das Team IB2, und wählen Sie Eigenschaften.  
  
9. Schreiben Sie aus dem Fenster Eigenschaften von Internetprotokoll Version 4 (TCP/IPv4) die Werte für die IP-Adresse und Subnetzmaske für TeamIB2.  
  
10. Wiederholen Sie die Schritte 8 bis 9 oben für den Adapter TeamIB2 auf Appliance_domain AD02 Server.  
  
    ![Eigenschaften für TeamIB2](media/network-ip2-properties.png "Eigenschaften für TeamIB2")  
  
11. Finden Sie eine nicht verwendete IP-Adresse auf die **TeamIB2** Netzwerk aus, und notieren Sie ihn.  
  
    Um eine nicht verwendete IP-Adresse zu suchen, öffnen Sie ein Befehlsfenster, und versuchen Sie, IP-Adressen innerhalb des Bereichs von Adressen für Ihr Gerät zu pingen. In diesem Beispiel ist die IP-Adresse des Netzwerks TeamIB2 172.16.18.30. Suchen Sie eine IP-Adresse, die mit 172.16.18 beginnt, die nicht verwendet wird. Geben Sie über die Befehlszeile z. B. "ping 172.16.18.254". Wenn der Ping-Anforderung nicht erfolgreich ist, ist die IP-Adresse verfügbar.  
  
## <a name="Sec2"></a>Schritt 2: Konfigurieren Sie die Adaptereinstellungen InfiniBand-Netzwerk, auf dem Clientserver  

### <a name="notes"></a>Hinweise  
  
-   Diese Schritte veranschaulichen, wie zum Registrieren Ihres Servers mit den APS DNS-Servern.  
  
-   Um Ihre eigenen netzwerkanforderungen zu erfüllen, können Sie die Clientserver auch Ihre eigenen nicht zur Appliance gehört Arbeitsgruppe oder einer Windows-Domäne verknüpfen.  
  
-   Die Anweisungen schrittweise Konfigurieren von zwei Netzwerkadaptern auf jedem Server aus.  Wenn Sie nur einen Netzwerkadapter verfügen, wählen Sie eines der Netzwerke an, auf dem Netzwerkadapter konfigurieren, und klicken Sie dann die zweite DNS IP-Adresse als alternative DNS-Server hinzufügen.  
  
### <a name="to-configure-the-infiniband-network-adapter-settings-on-your-client-server"></a>So konfigurieren Sie die InfiniBand-Einstellungen des Netzwerkadapters auf dem Clientserver  
  
1.  Melden Sie sich als Windows-Administrator Ihr laden, die Sicherung oder andere Clientserver, auf dem Gerät InfiniBand-Netzwerk.  
  
2.  Öffnen Sie das Steuerelement Bereich * Wählen Sie, Netzwerk- und Freigabecenter, und wählen Sie die Adaptereinstellungen ändern.  
  
### <a name="to-configure-the-first-network-adapter"></a>Den ersten Netzwerkadapter konfigurieren  
  
1.  Klicken Sie im Fenster Netzwerkverbindungen mit der rechten Maustaste auf einen der Slots nicht identifiziertes Netzwerk für den Mellanox-Adapter, und wählen Sie Eigenschaften.  
  
    ![Wählen Sie die InfiniBand-Netzwerke](media/network-connections.png "InfiniBand-Netzwerke auswählen")  
  
2.  Im Eigenschaftenfenster  
  
    1.  Legen Sie auf der Registerkarte "Allgemein" die IP-Adresse, auf die IP-Adresse, die Sie als "frei" in der Ping-Test für TeamIB1 überprüft. Für die Beispielwerte, die in diesem Artikel verwendeten würden Sie 172.16.14.254 eingeben.  
  
    2.  Legen Sie die Subnetzmaske, auf die Subnetzmaske, die Sie für TeamIB1 notiert.  
  
    3.  Legen Sie den bevorzugten DNS-Server die IP-Adresse TeamIB1, die zuvor von der Appliance_domain * notiert-AD01-Knoten.  
  
    4.  Legen Sie den alternativen DNS-Server die IP-Adresse TeamIB1, die zuvor von der Appliance_domain * notiert-AD02-Knoten.  
  
        ![InfiniBand 1 Netzwerkadaptereigenschaften](media/network-ib1-properties.png "SQL_Server_PDW_Network_IB1_properties")  
  
    5.  Klicken Sie auf OK, um die Änderungen zu übernehmen.  
  
### <a name="to-configure-the-second-network-adapter"></a>So konfigurieren Sie die zweite Netzwerkkarte  
  
1.  Überspringen Sie diesen Abschnitt, wenn Sie nur einen Netzwerkadapter verfügen.  
  
2.  Klicken Sie im Fenster Netzwerkverbindungen mit der rechten Maustaste im zweiten Steckplatz der nicht identifizierten Netzwerk für den Mellanox-Adapter, und wählen Sie Eigenschaften.  
  
    ![Wählen Sie die InfiniBand-Netzwerke](media/network-connections.png "InfiniBand-Netzwerke auswählen")  
  
3.  Im Eigenschaftenfenster  
  
    1.  Legen Sie auf der Registerkarte "Allgemein" die IP-Adresse, auf die IP-Adresse, die Sie als "frei" in der Ping-Test für TeamIB2 überprüft. Für die Beispielwerte, die in diesem Artikel verwendeten würden Sie 172.16.18.254 eingeben.  
  
    2.  Legen Sie die Subnetzmaske, auf die Subnetzmaske, die Sie für TeamIB2 notiert.  
  
    3.  Legen Sie den bevorzugten DNS-Server die IP-Adresse TeamIB2, die zuvor von der Appliance_domain * notiert-AD01-Knoten.  
  
    4.  Legen Sie den alternativen DNS-Server die IP-Adresse TeamIB2, die zuvor von der Appliance_domain * notiert-AD02-Knoten.  
  
        > [!NOTE]  
        > Wenn nur einen Netzwerkadapter, die bevorzugte und alternative DNS-Server verwenden entweder die Appliance AD01 TeamIB1 und Appliance AD02 TeamIB1 als die bevorzugte und alternative DNS-Server konfigurieren oder verwenden Sie die Appliance AD01 TeamIB2 und Appliance AD02 TeamIB2 als die bevorzugte und alternative DNS-Server durch, je nachdem, ob verfügt über die AD-Computer Failover ausgeführt.  
  
        ![InfiniBand 1 Netzwerkadaptereigenschaften](media/network-ib1-properties.png "InfiniBand 1 Netzwerkadaptereigenschaften")  
  
    5.  Klicken Sie auf OK, um die Änderungen zu übernehmen.  
  
### <a name="to-configure-the-dns-suffix"></a>So konfigurieren Sie das DNS-suffix  
  
1.  Klicken Sie im Fenster Netzwerkverbindungen mit der rechten Maustaste auf einen der Slots Netzwerk für den Mellanox-Adapter, und wählen Sie Eigenschaften.  
  
2.  Klicken Sie auf die erweiterten....  
  
3.  Im Fenster "Erweiterte TCP/IP-Einstellungen", wenn der Anfügevorgang diese DNS-Suffixe anhängen (in Reihenfolge)-Option nicht, abgeblendet dargestellt ist überprüfen Sie das Feld namens diese DNS-Suffixe anhängen (in Reihenfolge): Wählen Sie das Domänensuffix des Geräts, und klicken Sie auf Hinzufügen... Das Domänensuffix Appliance ist `appliance_domain.local`  
  
4.  Wenn der Anfügevorgang diese DNS-Suffixe (in Reihenfolge): Option abgeblendet ist, Sie können die APS-Domäne auf diesem Server hinzufügen, indem Sie den Registrierungsschlüssel HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows NT\DNSClient ändern.  
  
    ![TCP/IP-Einstellungen](media/network-tcpip.png "TCP/IP-Einstellungen")  
  
5.  Es wird empfohlen, zur schnelleren problemlösung Adresse der Appliance-Suffix an den Anfang der Liste verschieben.  
  
6.  Klicken Sie auf OK.  
  
7.  Sie können nun mit dem Gerät Infiniband-Netzwerk verbinden, mit `PDW_region-SQLCTL01.appliance_domain.local`, oder einfach `appliance_domain-SQLCTL01`. Die Verbindung möglicherweise schneller hergestellt werden, wenn Sie eine Verbindung mit dem vollständigen Namen und die DNS-Suffix herstellen.  
  
    Beispiele für ein Gerät namens MyAPS mit einer MyPDW PDW-Region an:  
  
    -   MyPDW-SQLCTL01.MyAPS.local  
  
    -   MyPDW-SQLCTL01  
  
## <a name="see-also"></a>Siehe auch  
[Abrufen und Konfigurieren eines ladenden Servers](acquire-and-configure-loading-server.md)  
  
