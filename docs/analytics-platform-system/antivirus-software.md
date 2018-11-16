---
title: Antivirus-Software - Analytics Platform System | Microsoft-Dokumentation
description: Wenn Ihr Rechenzentrum antivirus-Software erfordert, verwenden Sie diese Richtlinien, um die antivirus-Software in Analytics Platform System zu installieren. Es wird empfohlen, antivirus-Software nicht installiert, es sei denn, es sich um eine feste Anforderung Ihres Rechenzentrums ist.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2bf94fb04bd6f96de019c7e8543b8a626cebe439
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51699119"
---
# <a name="antivirus-software-for-analytics-platform-system"></a>Antivirus-Software für Analytics Platform System
Wenn Ihr Rechenzentrum antivirus-Software erfordert, verwenden Sie diese Richtlinien, um die antivirus-Software in Analytics Platform System zu installieren. Es wird empfohlen, antivirus-Software nicht installiert, es sei denn, es sich um eine feste Anforderung Ihres Rechenzentrums ist.  
  
> [!WARNING]  
> Es wird dringend empfohlen, dass Sie einzeln über das Sicherheitsrisiko für jeden Computer und für Analytics Platform System als Ganzes bewerten und Sie die Tools auswählen, die für die Sicherheitsrisiko Ebene der einzelnen Computer geeignet sind. Darüber hinaus empfehlen wir, dass vor dem Rollout Virenschutz Projekte, testen Sie des gesamten Systems unter voller Auslastung Änderungen hinsichtlich der Stabilität und Leistung zu messen.  
>   
> Virenschutzsoftware erfordert einige Systemressourcen ausgeführt. Sie müssen ausführen, testen, bevor und nachdem Sie Ihre antivirus-Software um zu bestimmen, ob es Auswirkung auf die Leistung in den Analytics Platform System ist installieren.  
  
Dieses Thema bezieht sich auf die Anleitung im [antivirus-Software auf Computern ausführen, auf denen SQL Server auswählen](https://support.microsoft.com/kb/309422) und [KB-Artikel 961804](https://support.microsoft.com/kb/961804/en-us).  
  
## <a name="exclusion-list-for-physical-hosts"></a>Ausschlussliste für die physischen Hosts  
Um die antivirus-Software auf physischen Hosts installieren möchten, schließen Sie die folgende Liste der Verzeichnisse und Prozesse. Diese sollte nicht von der Antivirussoftware überprüft.  
  
**Schließen Sie diese Verzeichnisse:**  
  
-   C:\ProgramData\Microsoft\Windows\Hyper-V - VM-Konfigurationsverzeichnis  
  
-   C:\Users\Public\Documents\Hyper-V\Virtual Festplatten - Standardverzeichnis für die virtuelle Festplatte  
  
-   C:\clusterStorage - Verzeichnisse der virtuellen Festplatte  
  
**Schließen Sie diese Prozesse aus:**  
  
-   Verwaltung virtueller Computer (Vmms.exe)  
  
-   VM-workprozesse (Vmwp.exe)  
  
## <a name="exclusion-list-for-virtual-machines-vms"></a>Ausschlussliste für virtuelle Computer (VMs)  
Um die antivirus-Software auf den virtuellen Computern zu installieren, schließen Sie die folgende Liste von Verzeichnissen und Dateien. Diese sollte nicht von der Antivirussoftware überprüft.  
  
***PDW_region*-CTL01**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***Appliance_domain *-AD01** und ***Appliance_domain *-AD02**  
  
-   Keine Einschränkungen  
  
**Computeknoten-VMs**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***Appliance_domain * – VMM**  
  
-   Keine Einschränkungen  
  
***Appliance_domain *-WDS**  
  
-   Keine Einschränkungen  
  
***Appliance_domain *-ISCSI01**  
  
-   C:\iscsitarget  
  
## <a name="see-also"></a>Siehe auch  
[Tasks zur applianceverwaltung &#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
