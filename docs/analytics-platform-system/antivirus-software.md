---
title: Antivirus Software-Analytics Platform System (APS) | Microsoft-Dokumentation
description: Wenn Ihr Rechenzentrum Antivirensoftware erfordert, verwenden Sie diese Richtlinien zur Installation von Antivirensoftware auf dem Analytics Platform System (APS). Es wird empfohlen, die Antivirussoftware nur dann zu installieren, wenn Sie eine feste Anforderung Ihres Rechenzentrums ist
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 92a34405e75c37cd0347b15aa445b98d84ebcc2a
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176055"
---
# <a name="antivirus-software-for-analytics-platform-system-aps"></a>Antivirussoftware für Analytics Platform System (APS)
Wenn Ihr Rechenzentrum Antivirensoftware erfordert, verwenden Sie diese Richtlinien, um Antivirensoftware auf dem Analytics Platform System zu installieren. Es wird empfohlen, die Antivirussoftware nur dann zu installieren, wenn Sie eine feste Anforderung Ihres Rechenzentrums ist  
  
> [!WARNING]  
> Es wird dringend empfohlen, dass Sie das Sicherheitsrisiko für die einzelnen Computer und das Analytics-Platt Form System als Ganzes individuell bewerten und die Tools auswählen, die für die Sicherheitsrisiko Stufe der einzelnen Computer geeignet sind. Außerdem wird empfohlen, dass Sie vor dem Rollout eines Virenschutz Projekts das gesamte System mit einer vollständigen Auslastung testen, um Änderungen an der Stabilität und Leistung zu messen.  
>   
> Virenschutzsoftware erfordert einige Systemressourcen, die ausgeführt werden müssen. Sie müssen vor und nach der Installation der Antivirussoftware Tests durchführen, um zu ermitteln, ob es Leistungs Auswirkungen auf das Analytics-Platt Form System gibt.  
  
Dieses Thema basiert auf dem Leitfaden zum [Auswählen von Antivirussoftware für die Ausführung auf Computern mit SQL Server](https://support.microsoft.com/kb/309422) und [KB-Artikel 961804](https://support.microsoft.com/kb/961804/en-us).  
  
## <a name="exclusion-list-for-physical-hosts"></a>Ausschlussliste für physische Hosts  
Wenn Sie die Antivirussoftware auf den physischen Hosts installieren möchten, schließen Sie die folgende Liste der Verzeichnisse und Prozesse aus. Diese sollten nicht von der Antivirussoftware gescannt werden.  
  
**Diese Verzeichnisse ausschließen:**  
  
-   C:\ProgramData\Microsoft\Windows\Hyper-v-Konfiguration Verzeichnis der virtuellen Maschine  
  
-   C:\Users\Public\Documents\Hyper-v\virtuelle Festplatten-Standardverzeichnis des virtuellen Festplatten Laufwerks  
  
-   C:\ClusterStorage: Verzeichnisse für virtuelle Festplattenlaufwerke  
  
**Schließen Sie diese Prozesse aus:**  
  
-   Verwaltung virtueller Maschinen (vmms. exe)  
  
-   Arbeitsprozesse für virtuelle Maschinen (VMWP. exe)  
  
## <a name="exclusion-list-for-virtual-machines-vms"></a>Ausschlussliste für Virtual Machines (VMS)  
Um die Antivirussoftware auf den virtuellen Computern zu installieren, schließen Sie die folgende Liste der Verzeichnisse und Dateien aus. Diese sollten nicht von der Antivirussoftware gescannt werden.  
  
**_PDW_region_-CTL01**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
**_appliance_domain_-ad01** und  **_appliance_domain_-ad02**  
  
-   Keine Einschränkungen  
  
**Computeknoten-VMS**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
**_appliance_domain_-VMM**  
  
-   Keine Einschränkungen  
  
**_appliance_domain_-WDS**  
  
-   Keine Einschränkungen  
  
**_appliance_domain_-ISCSI01**  
  
-   C:\iscsitarget  
  
## <a name="see-also"></a>Siehe auch  
[Geräte Verwaltungsaufgaben &#40;Analytics-Platt Form System&#41;](appliance-management-tasks.md)  
  
