---
title: Netzwerkkonfiguration für die Appliance - Analytics Platform System | Microsoft-Dokumentation
description: Das Analytics Platform System (APS)-Gerät ist erstellt und mit einem Satz Korrektur der IP-Adressen in der gesamten alle Server und die entsprechenden Geräte aus der IHV Herstellerstandort konfiguriert. Bei der Übermittlung des Geräts muss die externen (Ethernet) IP-Adressen neu konfiguriert werden, um den entsprechenden Kunden Data Center-Anforderungen zu erfüllen.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: dc0fbd64ac1179cc77e5b8a3cf9f0e5fed73d7fd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63276111"
---
# <a name="appliance-network-configuration-for-analytics-platform-system"></a>Appliance-Netzwerkkonfiguration für Analytics Platform System
Das Analytics Platform System (APS)-Gerät ist erstellt und mit einem Satz Korrektur der IP-Adressen in der gesamten alle Server und die entsprechenden Geräte aus der IHV Herstellerstandort konfiguriert. Bei der Übermittlung des Geräts muss die externen (Ethernet) IP-Adressen neu konfiguriert werden, um den entsprechenden Kunden Data Center-Anforderungen zu erfüllen.  
  
> [!NOTE]  
> PDW-V1 erforderlich 8 IP-externe (*Kunden zugängliche*) Adressen, geben Sie die externe Konnektivität auf die einzelnen des Steuerelements rack-Knoten. PDW-2012 (V2) verbessert die Netzwerkkommunikation durch jede Komponente der Anwendung extern über IP-Adressen verfügbar zu machen. Dieser Ansatz bietet einen robusteren Entwurf, die reduziert die Kosten, erhöht die Flexibilität, und verbessert die datenverschiebung, das Laden von Daten und die Hadoop-Integration. Die Anzahl der erforderlichen IP-Adressen richtet sich nach der Anzahl von Knoten in der Appliance. Um diesem größeren Block von IP-Adressen zu unterstützen, sollte der Kunde ein getrenntes Subnetz für PDW einrichten. In diesem Subnetz werden genügend IP-Adressraum (bis zu 250 Adressen), um die Komponenten von bis zu 5 PDW-Racks zu berücksichtigen.  
  
Die **Netzwerkkonfiguration** auf der Seite können Sie die externe Netzwerkeinstellungen für den Knoten für Ihre Analytics Platform System Appliance anzeigen. Diese Seite ist schreibgeschützt.  
  
![DWConfig Appliance Network](./media/appliance-network-configuration/SQL_Server_PDW_DWConfig_ApplTopNetwork.png "SQL_Server_PDW_DWConfig_ApplTopNetwork")  
  
## <a name="to-update-the-network-configuration-on-your-appliance"></a>Um die Netzwerkkonfiguration auf Ihrem Gerät zu aktualisieren.  
Ändern Sie die IP-Adressen der Fabric-Domäne und die Workload-Domäne durch Bearbeiten der **AplianceInfo.xml** -Datei, und klicken Sie dann Setup ausführen. Dies ist ein Offlinevorgang. Die PDW-Regionen werden automatisch während der Umstellung der IP-Adresse beendet.  
  
> [!NOTE]  
> Domänennamen werden während des Setups bereitgestellt und werden bis zu 6 alphanumerische Zeichen, beginnend mit einem Buchstaben angegeben. Einem Benennungssystem nach häufigen erstellt eine Fabric-Domäne, die beginnend mit F#, eine PDW-arbeitsauslastung-Domäne dabei ist P. Dieses Format wird davon ausgegangen, dass in den Hilfethemen für die Datei ist jedoch nicht erforderlich. <!-- MISSING LINKS For more information about the domain structure, see [PDW Domain Security &#40;SQL Server PDW&#41;](../sqlpdw/pdw-domain-security-sql-server-pdw.md) and [Understanding the Security Model of the HDInsight Region &#40;Analytics Platform System&#41;](../hdinsight/understanding-the-security-model-of-the-hdinsight-region.md)  -->  
  
#### <a name="to-change-the-ip-addresses-of-the-analytics-platform-system"></a>So ändern Sie die IP-Adressen das Analytics Platform System  
  
1.  Mithilfe der **Remotedesktop** -Anwendung Herstellen einer Verbindung mit **HST01** mit dem Domänenadministratorkonto für die arbeitsauslastung.  
  
2.  Öffnen Sie auf der Appliance-Infodatei auf dem Knoten HST01 **c:\pdwinst\media\AplianceInfo.xml**.  
  
    > [!NOTE]  
    > Wenn die Datei nicht vorhanden ist, müssen möglicherweise eine neue Datei erstellt werden.  
  
3.  Aktualisieren Sie die Ethernet-IP-Werte, je nach Bedarf, und speichern Sie die Datei.  
  
4.  Führen Sie in einem Eingabeaufforderungsfenster den folgenden Setupbefehl zum Aktualisieren der IP-Adressen für die PDW-Region, die mithilfe der P/F/H-Domänennamen und die Administratorkennwörter.  
  
    ```  
    c:\pdwinst\media\setup.exe /action="ConfigureEthernet" /DomainAdminPassword="<password>" /ApplianceInfoFile="C:\PDWINST\media\ApplianceInfo.xml"  
    ```  
  
## <a name="manufacturer-references"></a>Hersteller-Verweise  
Weitere Informationen zu Dell-Geräte finden Sie unter:  
  
-   PowerConnect Switch-Anweisungen [Dell PowerConnect 6200 Reihe System CLI Reference Guide](https://downloads.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_powerconnect/powerconnect-6224f_Reference%20Guide_en-us.pdf)  
  
-   iDRAC/BMC [integrierte Dell Remote Access Controller 7 (iDRAC7) Version 1.30.30-Benutzerhandbuch](https://downloads.dell.com/Manuals/all-products/esuprt_electronics/esuprt_software/esuprt_remote_ent_sys_mgmt/integrated-dell-remote-access-cntrllr-7-v1.30.30_User%27s%20Guide_en-us.pdf?c=us&l=en&cs=555&s=biz)  
  
-   Die Stromverteilereinheit **Dell gemessen Rack-PDU**`ftp://ftp.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_rack_infrastructure/dell-metered-pdu-led_User's%20Guide_en-us.pdf`  
  
## <a name="see-also"></a>Siehe auch  
[Starten Sie den Konfigurations-Manager &#40;Analytics Platform System&#41;](launch-the-configuration-manager.md)  
  
