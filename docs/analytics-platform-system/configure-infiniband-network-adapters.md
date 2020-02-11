---
title: InfiniBand konfigurieren
description: In diesem Thema wird beschrieben, wie die InfiniBand-Netzwerkadapter auf einem Client Server ohne Appliance konfiguriert werden, um eine Verbindung mit dem Steuer Knoten für parallele Data Warehouse (PDW) herzustellen. Verwenden Sie diese Anweisungen, um grundlegende Konnektivität und hohe Verfügbarkeit zu erhalten, sodass das Laden, sichern und andere Prozesse automatisch eine Verbindung mit dem aktiven InfiniBand-Netzwerk herstellen.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 583d7617c0620d5d1ec24d60fbf10435a547616d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401293"
---
# <a name="configure-infiniband-network-adapters-for-analytics-platform-system"></a>Konfigurieren von InfiniBand-Netzwerkadaptern für Analytics Platform System
In diesem Thema wird beschrieben, wie die InfiniBand-Netzwerkadapter auf einem Client Server ohne Appliance konfiguriert werden, um eine Verbindung mit dem Steuer Knoten für parallele Data Warehouse (PDW) herzustellen. Verwenden Sie diese Anweisungen, um grundlegende Konnektivität und hohe Verfügbarkeit zu erhalten, sodass das Laden, sichern und andere Prozesse automatisch eine Verbindung mit dem aktiven InfiniBand-Netzwerk herstellen.  
  
## <a name="Basics"></a>BESCHREIBUNG  
Diese Anweisungen veranschaulichen, wie Sie die richtigen InfiniBand-IP-Adressen und Subnetzmasken auf dem mit InfiniBand verbundenen Server finden und dann festlegen. Außerdem wird erläutert, wie der Server für die Verwendung des APS-Appliance-DNS festgelegt wird, damit Ihre Verbindung in das aktive InfiniBand-Netzwerk aufgelöst wird.  
  
Für hohe Verfügbarkeit verfügt APS über zwei InfiniBand-Netzwerke, eine aktiv und eine passive. Jedes InfiniBand-Netzwerk verfügt über eine andere IP-Adresse für den Steuer Knoten. Wenn das aktive InfiniBand-Netzwerk ausfällt, wird das passive InfiniBand-Netzwerk zum aktiven Netzwerk. Wenn dies geschieht, stellt ein Skript oder ein Prozess automatisch eine Verbindung mit dem aktiven InfiniBand-Netzwerk her, ohne die Skript Parameter zu ändern.  
  
In diesem Artikel haben Sie insbesondere Folgendes:  
  
1.  Suchen Sie die InfiniBand-IP-Adressen der APS-DNS-Server (appliance_domain-ad01 und appliance_domain *-ad02). Dazu melden Sie sich bei den ad01-und ad02-Servern an und erhalten die IP-Adressen für jedes InfiniBand-Netzwerk. Die InfiniBand-IP-Adressen auf dem AD-Knoten sind die DNS-IP-Adressen.  
  
2.  Konfigurieren Sie jeden Netzwerkadapter für die Verwendung einer verfügbaren IP-Adresse in den APS InfiniBand-Netzwerken.  
  
    1.  Wenn Sie über zwei InfiniBand-Netzwerkadapter verfügen, konfigurieren Sie einen Adapter mit einer verfügbaren IP-Adresse im ersten InfiniBand-Netzwerk mit dem Namen "TeamIB1" und dem anderen Adapter mit einer verfügbaren IP-Adresse im zweiten InfiniBand-Netzwerk mit dem Namen "TeamIB2". Verwenden Sie die IP-Adresse appliance_domain-ad01 TeamIB1 als bevorzugten DNS-Server und appliance_domain-ad02 TeamIB1 IP-Adresse als alternativen DNS-Server für TeamIB1 Network Adapter. Verwenden Sie die IP-Adresse appliance_domain-ad01 TeamIB2 als bevorzugten DNS-Server und appliance_domain-ad02 TeamIB2 IP-Adresse als alternativen DNS-Server für TeamIB2 Network Adapter.  
  
    2.  Wenn Sie nur einen InfiniBand-Netzwerkadapter haben, konfigurieren Sie den Adapter mit einer verfügbaren IP-Adresse aus einem der InfiniBand-Netzwerke. Anschließend konfigurieren Sie die bevorzugten und alternativen DNS-Server auf diesem Adapter entweder mithilfe appliance_domain-ad01 TeamIB1 und appliance_domain-ad02 TeamIB1 oder mithilfe appliance_domain-ad01 TeamIB2 und appliance_domain-ad02 TeamIB2, je nachdem, welcher Wert gleich ist. Netzwerk als konfigurierter Adapter als bevorzugter bzw. alternativer DNS-Server.  
  
3.  Konfigurieren Sie den InfiniBand-Netzwerkadapter für die Verwendung von APS-DNS-Servern, um die Verbindung mit dem aktiven InfiniBand-Netzwerk aufzulösen.  
  
    1.  Um dies zu konfigurieren, verwenden Sie die erweiterten TCP/IP-Einstellungen, um das Appliance Domain DNS Suffix dem Anfang der Liste der DNS-Suffixe auf dem Client Server hinzuzufügen. Dies muss nur auf einem der Netzwerkadapter konfiguriert werden. die Einstellung gilt für beide Adapter.  
  
Nach dem Konfigurieren der InfiniBand-Netzwerkadapter können Client Prozesse eine Verbindung mit dem Steuerungs Knoten im InfiniBand-Netzwerk `PDW_region-SQLCTL01` herstellen, indem Sie für die Adresse des Servers verwenden. Der Server fügt das DNS-Suffix des Analytics Platform System an, oder Sie können die komplette Adresse eingeben `PDW_region-SQLCTL01.appliance_domain.pdw.local`.  
  
Wenn der Name Ihrer PDW-Region beispielsweise mypdw lautet und der Gerätename myaps lautet, ist die "dwloader-Server Spezifikation zum Laden von Daten eine der folgenden:  
  
-   `dwloader -S MYPDW-SQLCTL01.MyAPS.pdw.local`  
  
-   `dwloader -S MYPDW-SQLCTL01`  
  
## <a name="BeforeBegin"></a>Bevor Sie beginnen  
  
### <a name="requirements"></a>Requirements (Anforderungen)  
Sie benötigen ein APS-Appliance-Domänen Konto, um sich beim ad01-Knoten anzumelden. Beispiel: F12345 * \administrator "  
  
Sie benötigen ein Windows-Konto auf dem Client Server, das über die Berechtigung zum Konfigurieren der Netzwerkadapter verfügt.  
  
### <a name="prerequisites"></a>Voraussetzungen  
Bei diesen Anweisungen wird vorausgesetzt, dass der Client Server bereits in das InfiniBand-Netzwerk der Anwendung rackt und verkabelt ist. Informationen zu Racken und Verkabelung finden Sie unter [erwerben und Konfigurieren eines Lade Servers](acquire-and-configure-loading-server.md).  
  
### <a name="general-remarks"></a>Allgemeine Hinweise  
Mithilfe von SQLCTL01 verbindet der Analytics Platform System-DNS Ihren Client Server mithilfe des aktiven InfiniBand-Netzwerks mit dem Steuer Knoten. Dies gilt nur für das Herstellen einer Verbindung. Wenn das InfiniBand-Netzwerk während eines Ladens oder einer Sicherung ausfällt, müssen Sie den Prozess neu starten.  
  
Um Ihre eigenen geschäftlichen Anforderungen zu erfüllen, können Sie den Client Server auch mit ihrer eigenen nicht-Appliance-Arbeitsgruppe oder Windows-Domäne verknüpfen.  
  
## <a name="Sec1"></a>Schritt 1: Abrufen der InfiniBand-Netzwerkeinstellungen für die Anwendung  
*So rufen Sie die InfiniBand-Netzwerkeinstellungen des Geräts ab*  
  
1.  Melden Sie sich mit dem appliance_domain \administrator-Konto am Knoten Appliance ad01 an.  
  
2.  Öffnen Sie die Systemsteuerung auf dem Knoten Appliance ad01, wählen Sie Netzwerk und Internet aus, wählen Sie Netzwerk-und Freigabe Center * aus, und wählen Sie dann Adapter Einstellungen ändern aus.  
  
3.  Klicken Sie im Fenster Netzwerkverbindungen mit der rechten Maustaste auf Team IB1, und wählen Sie Eigenschaften aus.  
  
    ![InfiniBand-Verbindungen auf dem Knoten "Verwaltung"](media/network-teamib.png "InfiniBand-Verbindungen auf dem Knoten "Verwaltung"")  
  
4.  Notieren Sie die Werte für die **IP-Adresse** und die **Subnetzmaske**aus dem Eigenschaftenfenster Internet Protokoll Version 4 (TCP/IPv4).  Die IP-Adresse des Knotens " ** _Appliance\_Domäne_-ad01** " ist die IP-Adresse des DNS-Servers des Analytics Platform System.  
  
5.  Wiederholen Sie die Schritte 1-5 oben für den TeamIB1-Adapter auf der ** _Appliance\_Domain_-ad02** Server.  
  
    ![PDW-Verwaltungs Knoten InfiniBand 1-Eigenschaften](media/network-ip1-properties.png "PDW-Verwaltungs Knoten InfiniBand 1-Eigenschaften")  
  
6.  Klicken Sie auf Abbrechen, um das Fenster zu schließen.  
  
7.  Suchen Sie im TeamIB1-Netzwerk eine nicht verwendete IP-Adresse, und notieren Sie Sie.  
  
    Um eine nicht verwendete IP-Adresse zu finden, öffnen Sie ein Befehlsfenster, und versuchen Sie, IP-Adressen innerhalb des Adress Bereichs für Ihre Appliance zu pingen. In diesem Beispiel lautet die IP-Adresse des TeamIB1-Netzwerks 172.16.14.30. Suchen Sie nach einer IP-Adresse, die mit 172.16.14 beginnt, der nicht verwendet wird. Geben Sie z. b. in der Befehlszeile "Ping 172.16.14.254" ein. Wenn die Ping-Anforderung nicht erfolgreich ist, ist die IP-Adresse verfügbar.  
  
8.  Gehen Sie für TeamIB2 genauso vor. Klicken Sie im Fenster Netzwerkverbindungen mit der rechten Maustaste auf Team IB2, und wählen Sie Eigenschaften aus.  
  
9. Notieren Sie die Werte für die IP-Adresse und die Subnetzmaske für TeamIB2 aus dem Eigenschaftenfenster Internet Protokoll Version 4 (TCP/IPv4).  
  
10. Wiederholen Sie die Schritte 8-9 oben für den TeamIB2-Adapter auf appliance_domain-ad02-Server.  
  
    ![Eigenschaften für TeamIB2](media/network-ip2-properties.png "Eigenschaften für TeamIB2")  
  
11. Suchen Sie im **TeamIB2** -Netzwerk eine nicht verwendete IP-Adresse, und notieren Sie Sie.  
  
    Um eine nicht verwendete IP-Adresse zu finden, öffnen Sie ein Befehlsfenster, und versuchen Sie, IP-Adressen innerhalb des Adress Bereichs für Ihre Appliance zu pingen. In diesem Beispiel lautet die IP-Adresse des TeamIB2-Netzwerks 172.16.18.30. Suchen Sie nach einer IP-Adresse, die mit 172.16.18 beginnt, der nicht verwendet wird. Geben Sie z. b. in der Befehlszeile "Ping 172.16.18.254" ein. Wenn die Ping-Anforderung nicht erfolgreich ist, ist die IP-Adresse verfügbar.  
  
## <a name="Sec2"></a>Schritt 2: Konfigurieren der InfiniBand-Netzwerk Adapter Einstellungen auf dem Client Server  

### <a name="notes"></a>Notizen  
  
-   In den folgenden Schritten wird gezeigt, wie Sie Ihren Server bei den APS-DNS-Servern registrieren.  
  
-   Um Ihre eigenen Netzwerk Anforderungen zu erfüllen, können Sie den Client Server auch mit ihrer eigenen nicht-Appliance-Arbeitsgruppe oder Windows-Domäne verknüpfen.  
  
-   In diesem Abschnitt werden die Schritte zum Konfigurieren von zwei Netzwerkadaptern auf jedem Server beschrieben.  Wenn Sie nur über einen Netzwerkadapter verfügen, wählen Sie eines der Netzwerke aus, die auf dem Netzwerkadapter konfiguriert werden sollen, und fügen Sie dann die zweite DNS-IP-Adresse als alternativen DNS-Server hinzu.  
  
### <a name="to-configure-the-infiniband-network-adapter-settings-on-your-client-server"></a>So konfigurieren Sie die InfiniBand-Netzwerkadapter Einstellungen auf dem Client Server  
  
1.  Melden Sie sich als Windows-Administrator bei Ihrem Lade-, Sicherungs-oder anderen Client Server im InfiniBand-Netzwerk der Anwendung an.  
  
2.  Öffnen Sie den Steuerungs Bereich *, wählen Sie Netzwerk-und Freigabe Center aus, und wählen Sie dann Adapter Einstellungen ändern aus.  
  
### <a name="to-configure-the-first-network-adapter"></a>So konfigurieren Sie den ersten Netzwerkadapter  
  
1.  Klicken Sie im Fenster Netzwerkverbindungen mit der rechten Maustaste auf einen der nicht identifizierten Netzwerk Slots für den Mellanox-Adapter, und wählen Sie Eigenschaften aus.  
  
    ![InfiniBand-Netzwerke auswählen](media/network-connections.png "InfiniBand-Netzwerke auswählen")  
  
2.  Im Eigenschaftenfenster  
  
    1.  Legen Sie auf der Registerkarte Allgemein die IP-Adresse auf die IP-Adresse fest, die Sie im Ping-Test für TeamIB1 als frei überprüft haben. In den Beispiel Werten, die in diesem Artikel verwendet werden, geben Sie 172.16.14.254 ein.  
  
    2.  Legen Sie die Subnetzmaske auf die Subnetzmaske fest, die Sie für TeamIB1 notiert haben.  
  
    3.  Legen Sie den bevorzugten DNS-Server auf die IP-Adresse von TeamIB1 fest, die Sie zuvor aus dem Knoten appliance_domain *-ad01 notiert haben.  
  
    4.  Legen Sie den alternativen DNS-Server auf die IP-Adresse von TeamIB1 fest, die Sie zuvor aus dem Knoten appliance_domain *-ad02 notiert haben.  
  
        ![InfiniBand 1-Netzwerk Adapter Eigenschaften](media/network-ib1-properties.png "SQL_Server_PDW_Network_IB1_properties")  
  
    5.  Klicken Sie auf OK, um die Änderungen zu übernehmen.  
  
### <a name="to-configure-the-second-network-adapter"></a>So konfigurieren Sie den zweiten Netzwerkadapter  
  
1.  Überspringen Sie diesen Abschnitt, wenn Sie nur über einen Netzwerkadapter verfügen.  
  
2.  Klicken Sie im Fenster Netzwerkverbindungen mit der rechten Maustaste auf den zweiten nicht identifizierten Netzwerk Slot für den Mellanox-Adapter, und wählen Sie Eigenschaften aus.  
  
    ![InfiniBand-Netzwerke auswählen](media/network-connections.png "InfiniBand-Netzwerke auswählen")  
  
3.  Im Eigenschaftenfenster  
  
    1.  Legen Sie auf der Registerkarte Allgemein die IP-Adresse auf die IP-Adresse fest, die Sie im Ping-Test für TeamIB2 als frei überprüft haben. In den Beispiel Werten, die in diesem Artikel verwendet werden, geben Sie 172.16.18.254 ein.  
  
    2.  Legen Sie die Subnetzmaske auf die Subnetzmaske fest, die Sie für TeamIB2 notiert haben.  
  
    3.  Legen Sie den bevorzugten DNS-Server auf die IP-Adresse von TeamIB2 fest, die Sie zuvor aus dem Knoten appliance_domain *-ad01 notiert haben.  
  
    4.  Legen Sie den alternativen DNS-Server auf die IP-Adresse von TeamIB2 fest, die Sie zuvor aus dem Knoten appliance_domain *-ad02 notiert haben.  
  
        > [!NOTE]  
        > Wenn Sie nur über einen Netzwerkadapter verfügen, konfigurieren Sie die bevorzugten und alternativen DNS-Server, indem Sie entweder die Appliance ad01 TeamIB1 und Appliance ad02 TeamIB1 als bevorzugten bzw. die alternativen DNS-Server verwenden, oder verwenden Sie die Appliance ad01 TeamIB2 und Appliance ad02 TeamIB2 als bevorzugte und die alternativen DNS-Server in Abhängigkeit davon, ob für den virtuellen AD-Computer ein Failover durchgeführt wurde.  
  
        ![InfiniBand 1-Netzwerk Adapter Eigenschaften](media/network-ib1-properties.png "InfiniBand 1-Netzwerk Adapter Eigenschaften")  
  
    5.  Klicken Sie auf OK, um die Änderungen zu übernehmen.  
  
### <a name="to-configure-the-dns-suffix"></a>So konfigurieren Sie das DNS-Suffix  
  
1.  Klicken Sie im Fenster Netzwerkverbindungen mit der rechten Maustaste auf einen der Netzwerk Slots für den Mellanox-Adapter, und wählen Sie Eigenschaften aus.  
  
2.  Klicken Sie auf erweitert... gedrückt.  
  
3.  Wenn im Fenster Erweiterte TCP/IP-Einstellungen die Option Diese DNS-Suffixe anfügen (in der angegebenen Reihenfolge) nicht abgeblendet ist, aktivieren Sie das Kontrollkästchen Diese DNS-Suffixe anfügen (in der angegebenen Reihenfolge):, wählen Sie das Appliance-Domänen Suffix aus, und klicken Sie auf hinzufügen.... Das Appliance-Domänen Suffix ist`appliance_domain.local`  
  
4.  Wenn diese DNS-Suffixe anfügen (in der angegebenen Reihenfolge): die Option ist ausgegraut, können Sie die APS-Domäne zu diesem Server hinzufügen, indem Sie den Registrierungsschlüssel HKEY_LOCAL_MACHINE \software\policies\microsoft\windows NT\DNSClient.  
  
    ![TCP/IP-Einstellungen](media/network-tcpip.png "TCP/IP-Einstellungen")  
  
5.  Für eine schnellere Adress Auflösung empfiehlt es sich, das Appliance-Suffix an den Anfang der Liste zu verschieben.  
  
6.  Klicken Sie auf OK.  
  
7.  Nun können Sie mit oder einfach `PDW_region-SQLCTL01.appliance_domain.local` `appliance_domain-SQLCTL01`eine Verbindung mit dem InfiniBand-Anwendungs Netzwerk herstellen. Die Verbindung wird möglicherweise schneller hergestellt, wenn Sie eine Verbindung mit dem vollständigen Namen und dem DNS-Suffix herstellen.  
  
    Beispiele für ein Gerät mit dem Namen myaps mit einer mypdw-PDW-Region:  
  
    -   Mypdw-SQLCTL01. myaps. local  
  
    -   Mypdw-SQLCTL01  
  
## <a name="see-also"></a>Weitere Informationen  
[Erwerben und Konfigurieren eines Lade Servers](acquire-and-configure-loading-server.md)  
  
