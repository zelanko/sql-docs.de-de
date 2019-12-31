---
title: Softwarewartung
description: Software Wartung in Analytics Platform System (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 4325dfa9c16edba12c2bba694b47c1b0875c7c6f
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400314"
---
# <a name="software-servicing-in-analytics-platform-system"></a>Software Wartung in Analytics Platform System
In diesem Abschnitt werden die Anforderungen an die Softwarewartung für Analytics-Plattformsysteme zusammengefasst, einschließlich WSUS-und Analytics-Plattformsystem-Hotfixes  
  
## <a name="Basics"></a>Grundlagen der Software Wartung  
**WSUS:** Ihre Analytics-Platt Form System Appliance muss so konfiguriert werden, dass Sie Updates von Windows Server Update Services (WSUS) empfängt. Diese Updates enthalten wichtige Änderungen an der Geräte Software. Nachdem Sie konfiguriert wurden, werden viele Updates automatisch installiert und erfordern keine praktische Verwaltung. In der Regel werden WSUS-Updates während des Setups der neuen Appliance [Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform&#41;System](configure-windows-server-update-services-wsus.md) konfiguriert. Andernfalls kann dieser Konfigurationsschritt später ausgeführt werden. Weitere Informationen zu WSUS finden Sie im [WSUS-Website Handbuch](https://go.microsoft.com/fwlink/?LinkId=202417).  
  
**Hotfixes:** Außerdem müssen Sie möglicherweise Analytics-Platt Form System-Hotfixes anwenden. Ein *Hotfix* ist ein Software Update, das für einen bestimmten Kunden erstellt wird, um ein Problem mit der Analytics-Platt Form System Software zu beheben. Jeder Hotfix ist eine ausführbare Datei, die die Behebung für das kundenspezifische Problem installiert. Jeder Hotfix enthält auch eine Ansammlung aller bereits veröffentlichten Software Updates für Windows, SQL Server und Analytics Platform System. Wenn Sie einen Hotfix installieren müssen, stellt Ihnen der Microsoft-Support den Hotfix und die Anweisungen zur Verfügung.  
  
**Umfang der Updates:** Wenn Sie einen Hotfix oder Service Pack auf das Analytics Platform System anwenden, muss das gesamte Gerät offline geschaltet werden.  
  
**SSIS-Ziel Adapter und-Client Tools:** Wenn Sie einen Hotfix anwenden, der Änderungen an der MSI-oder Client Tools-MSI des SSIS-Ziel Adapters umfasst, werden die MSI-Dateien im Verzeichnis " **c:\pdwinst\clienttools** " auf dem Knoten "Steuerelement" aktualisiert. Der Hotfix installiert die Komponenten nicht automatisch aus den aktualisierten MSI-Dateien. Um diese Komponenten zu aktualisieren, muss der Kunde die alten Versionen der Komponenten deinstallieren und die neuen Versionen aus den aktualisierten MSI-Dateien installieren. Beim Deinstallieren eines Hotfixes, der Änderungen an der MSI-oder Client Tools-MSI des SSIS-Ziel Adapters umfasst, werden die MSI-Dateien für diese Komponenten auf die vorherigen Versionen zurückgesetzt. Um diese Komponenten auf eine frühere Version zurückzusetzen, muss der Kunde die vorhandenen (neueren) Versionen der Komponenten deinstallieren und die älteren Versionen aus den wiederhergestellten MSI-Dateien neu installieren.  
  
## <a name="software-servicing-topics"></a>Themen zur Software Wartung  
In den folgenden Themen wird beschrieben, wie Sie die Softwarewartung auf dem Gerät verwalten:  
  
-   [Herunterladen und Anwenden von Microsoft Updates &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
  
-   [Deinstallieren von Microsoft Updates &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
  
-   [Anwenden von Analytics-Plattformsystem-Hotfixes &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
  
-   [Deinstallieren Sie die Analytics Platform System-Hotfixes &#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
