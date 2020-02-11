---
title: Konfigurieren des Netzwerks für die Appliance
description: Das Analytics Platform System (APS)-Gerät wird mit einem festen Satz von IP-Adressen auf allen Servern und anwendbaren Geräten aus dem Werk der IHV-Factory erstellt und konfiguriert. Bei der Übermittlung der Appliance muss die externe (Ethernet) IP-Adresse neu konfiguriert werden, damit Sie den Rechenzentrums Anforderungen des jeweiligen Kunden entspricht.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: af892cbb43b42953732bda59d371e3e22855413b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401408"
---
# <a name="appliance-network-configuration-for-analytics-platform-system"></a>Geräte Netzwerkkonfiguration für Analytics Platform System
Das Analytics Platform System (APS)-Gerät wird mit einem festen Satz von IP-Adressen auf allen Servern und anwendbaren Geräten aus dem Werk der IHV-Factory erstellt und konfiguriert. Bei der Übermittlung der Appliance muss die externe (Ethernet) IP-Adresse neu konfiguriert werden, damit Sie den Rechenzentrums Anforderungen des jeweiligen Kunden entspricht.  
  
> [!NOTE]  
> PDW V1 benötigte eine externe (*kundenorientierte*) IP-Adresse, um externe Konnektivität für die einzelnen Steuerungs Regal Knoten bereitzustellen. PDW 2012 (v2) erweiterte Netzwerkkommunikation, indem jede Komponente der Appliance extern über IP-Adressen verfügbar gemacht wird. Dieser Ansatz bietet einen robusteren Entwurf, der die Kosten reduziert und die Flexibilität erhöht und die Daten Verschiebung, das Laden von Daten und die Hadoop-Integration verbessert. Die Anzahl der erforderlichen IP-Adressen hängt von der Anzahl der Knoten in der Appliance ab. Um diesen größeren Block von IP-Adressen zu berücksichtigen, sollte der Kunde ein separates Subnetz für PDW einrichten. Innerhalb dieses Subnetzes gibt es ausreichend IP-Adressraum (bis zu 250 Adressen), um die Komponenten von bis zu 5 PDW-Racks zu berücksichtigen.  
  
Auf der Seite **Netzwerkkonfiguration** können Sie die extern ausgerichteten Netzwerkeinstellungen für die Knoten auf Ihrem Analytics Platform System-Gerät anzeigen. Diese Seite ist schreibgeschützt.  
  
![DWConfig, Anwendungsnetzwerk](./media/appliance-network-configuration/SQL_Server_PDW_DWConfig_ApplTopNetwork.png "SQL_Server_PDW_DWConfig_ApplTopNetwork")  
  
## <a name="to-update-the-network-configuration-on-your-appliance"></a>So aktualisieren Sie die Netzwerkkonfiguration auf Ihrem Gerät  
Ändern Sie die IP-Adressen der Fabric-Domäne und Arbeits Auslastungs Domäne, indem Sie die Datei " **aplianceinfo. XML** " Bearbeiten und dann Setup ausführen. Dies ist ein Offlinevorgang. Die PDW-Regionen werden während der Änderung der IP-Adresse automatisch beendet.  
  
> [!NOTE]  
> Domänen Namen werden während des Setups angegeben und als bis zu 6 alphanumerische Zeichen angegeben, beginnend mit einem Buchstaben. Ein häufiges Benennungs System erstellt eine Fabric-Domäne ab F, eine PDW-Arbeits Auslastungs Domäne, beginnend mit P. Dieses Format wird in den Themen der Hilfedateien angenommen, ist aber nicht erforderlich. <!-- MISSING LINKS For more information about the domain structure, see [PDW Domain Security &#40;SQL Server PDW&#41;](../sqlpdw/pdw-domain-security-sql-server-pdw.md) and [Understanding the Security Model of the HDInsight Region &#40;Analytics Platform System&#41;](../hdinsight/understanding-the-security-model-of-the-hdinsight-region.md)  -->  
  
#### <a name="to-change-the-ip-addresses-of-the-analytics-platform-system"></a>So ändern Sie die IP-Adressen des Analytics-plattformsystems  
  
1.  Stellen Sie mithilfe der **Remotedesktop** Anwendung eine Verbindung mit **HST01** her, indem Sie das Administrator Konto der Arbeitsauslastung verwenden.  
  
2.  Öffnen Sie auf dem Knoten HST01 die Geräte Informationsdatei unter **c:\pdwinst\media\aplianceinfo.XML**.  
  
    > [!NOTE]  
    > Wenn die Datei nicht vorhanden ist, muss möglicherweise eine neue Datei erstellt werden.  
  
3.  Aktualisieren Sie die Ethernet-IP-Werte nach Bedarf, und speichern Sie die Datei.  
  
4.  Führen Sie in einem Eingabe Aufforderungs Fenster den folgenden Setup Befehl aus, um die IP-Adressen für die PDW-Region mit den P/F/H-Domänen Namen und den Administrator Kennwörtern zu aktualisieren.  
  
    ```  
    c:\pdwinst\media\setup.exe /action="ConfigureEthernet" /DomainAdminPassword="<password>" /ApplianceInfoFile="C:\PDWINST\media\ApplianceInfo.xml"  
    ```  
  
## <a name="manufacturer-references"></a>Hersteller Verweise  
Weitere Informationen zu Dell-Geräten finden Sie unter:  
  
-   PowerConnect-Switch-Anweisungen [Dell PowerConnect 6200 Series System CLI-Referenzhandbuch](https://downloads.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_powerconnect/powerconnect-6224f_Reference%20Guide_en-us.pdf)  
  
-   Idrac/BMC [Integrated Dell Remote Access Controller 7 (iDRAC7) Version 1.30.30 Benutzerhandbuch](https://downloads.dell.com/Manuals/all-products/esuprt_electronics/esuprt_software/esuprt_remote_ent_sys_mgmt/integrated-dell-remote-access-cntrllr-7-v1.30.30_User%27s%20Guide_en-us.pdf?c=us&l=en&cs=555&s=biz)  
  
-   PDU ist das Dell-gemessene **Rack-PDU**`ftp://ftp.dell.com/Manuals/all-products/esuprt_ser_stor_net/esuprt_rack_infrastructure/dell-metered-pdu-led_User's%20Guide_en-us.pdf`  
  
## <a name="see-also"></a>Weitere Informationen  
[Starten Sie die Configuration Manager &#40;Analytics-Platt Form System&#41;](launch-the-configuration-manager.md)  
  
