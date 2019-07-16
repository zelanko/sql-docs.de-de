---
title: Softwarewartung - Analytics Platform System | Microsoft-Dokumentation
description: Softwarewartung in Analytics Platform System (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 97f0ccaed9cded73241f473d81400b30acbe402c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960087"
---
# <a name="software-servicing-in-analytics-platform-system"></a>Softwarewartung in Analytics Platform System
In diesem Abschnitt werden die wartungsanforderungen für Analytics Platform System-Anwendungen, einschließlich der Hotfixes für WSUS und Analytics Platform System Software zusammengefasst.  
  
## <a name="Basics"></a>Wartungsgrundlagen Software  
**WSUS:** Ihre Analytics Platform System Appliance muss konfiguriert werden, um Updates von Windows Server Update Services (WSUS) zu erhalten. Diese Updates enthalten wichtige Änderungen an Software Appliance. Nachdem sie konfiguriert wurden, werden viele Updates werden automatisch installiert und erfordern keine praktische Management. In der Regel werden während der WSUS-Updates konfiguriert die [Konfigurieren von Windows Server Update Services &#40;WSUS&#41; &#40;Analytics Platform System&#41; ](configure-windows-server-update-services-wsus.md) Schritt ausgeführt wird, während der Installation der neuen Anwendung. Wenn dies nicht der Fall ist, kann dieser Konfigurationsschritt später ausgeführt werden. Weitere Informationen zu WSUS, finden Sie unter den [Anleitung für WSUS-Website](https://go.microsoft.com/fwlink/?LinkId=202417).  
  
**Hotfixes:** Darüber hinaus müssen Sie möglicherweise die Hotfixes für Analytics Platform System anzuwenden. Ein *Hotfix* ist ein Softwareupdate, das für einen bestimmten Kunden zur Behebung eines Problems mit der Software Analytics Platform System erstellt wird. Jeder Hotfix wird eine ausführbare Datei, die die Korrektur des Problems kundenspezifischen installiert wird. Jeder Hotfix enthält auch eine Häufung von alle zuvor veröffentlichten Updates für Windows, SQL Server und Analytics Platform System. Wenn Sie einen Hotfix installieren möchten, stellt Microsoft-Support Sie mit dem Hotfix und Anweisungen bereit.  
  
**Der Bereich von Updates:** Einen Hotfix oder Service Pack, das Analytics Platform System anwenden muss die gesamte Anwendung offline schalten.  
  
**SSIS-Zieladapter und Clienttools:** Wenn Sie einen Hotfix anwenden, die Änderungen an der SSIS-Ziel Adapter MSI enthält oder Client Tools-MSI-Datei wird die MSI-Dateien werden im aktualisiert die **C:\PDWINST\ClientTools** Verzeichnis auf dem steuerknoten. Der Hotfix installiert die Komponenten nicht automatisch aus den aktualisierten MSI-Dateien. Um diese Komponenten zu aktualisieren, muss der Kunde deinstallieren Sie ältere Versionen der Komponenten, und installieren die neuen Versionen aus der aktualisierten MSI-Dateien. Bei der Deinstallation eines Hotfixes enthält, die Änderungen an der SSIS-Ziel Adapter MSI oder Client Tools MSI-Datei wird die MSI-Dateien für diese Komponenten werden auf die früheren Versionen zurückgesetzt werden. Diese Komponenten auf eine vorherige Version zurücksetzen möchten, muss Kunden die vorhandenen (neueren) Versionen der Komponenten deinstallieren und installieren die älteren Versionen aus den wiederhergestellten MSI-Dateien.  
  
## <a name="software-servicing-topics"></a>Software, die Wartung von Themen  
In den folgenden Themen wird beschrieben, wie zum Verwalten von Software auf dem Gerät verarbeitet:  
  
-   [Microsoft-Updates herunterzuladen und anzuwenden &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
  
-   [Deinstallieren von Microsoft-Updates &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
  
-   [Anwenden von Hotfixes für Analytics Platform System &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
  
-   [Deinstallieren von Hotfixes für Analytics Platform System &#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
  
<!-- MISSING LINKS ## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  -->  
  
