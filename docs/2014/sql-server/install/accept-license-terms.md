---
title: Akzeptieren der Lizenzbedingungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- license terms
helpviewer_keywords:
- Registration Information page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, Registration Information page
ms.assetid: 08dd739d-5817-4418-bcff-74ab7f8bbd33
caps.latest.revision: 38
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b060499f9b3a008e0106455afde5f1a7691d90f4
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37260093"
---
# <a name="accept-license-terms"></a>Akzeptieren von Lizenzbedingungen
  Verwenden der **Lizenzbedingungen akzeptieren** auf der Seite die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installations-Assistenten, akzeptieren die Lizenzbedingungen für diese Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Sie können den Lizenzvertrag drucken oder in die Zwischenablage kopieren. Akzeptieren Sie die Lizenzbedingungen, und klicken Sie dann auf **Weiter**, um den Vorgang fortzusetzen. Um die Installation zu beenden, klicken Sie auf **Abbrechen**.  
  
## <a name="customer-experience-improvement-program-ceip"></a>Customer Experience Improvement Program (CEIP)  
 Wenn Sie die Erstellung von CEIP-Berichten aktivieren, wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] so konfiguriert, dass in regelmäßigen Abständen ein Bericht an [!INCLUDE[msCoName](../../includes/msconame-md.md)] gesendet wird. Die Berichte enthalten Informationen zur Hardwarekonfiguration und zur Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und zugehörigen Komponenten. [!INCLUDE[msCoName](../../includes/msconame-md.md)] verwendet die Funktionsverwendungsdaten, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] weiter zu verbessern. Folgende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten werden von dieser Funktion überwacht:  
  
-   Die [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Replikation  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup  
  
 Informationen zur Funktionsverwendung werden an gesendet [!INCLUDE[msCoName](../../includes/msconame-md.md)]und dort mit eingeschränktem Zugriff gespeichert ist.  
  
 Um nach Abschluss des Setups CEIP-Berichten zu deaktivieren, verwenden die  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehler- und Verwendungsberichterstellung** tool die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Konfigurationstools** Menü.  
  
 Informationen zu Setupaktionen wie Installations-, Upgrade- oder Reparaturvorgängen usw. werden ausschließlich während der Ausführung des Setupprogramms erfasst und hochgeladen.  
  
 Für alle anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten werden einmal täglich Informationen zu allen aktivierten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] erfasst. Der Zeitpunkt der Erfassung ist standardmäßig Mitternacht, um die Belastung des Servers zu minimieren. Wenn Sie diesen Zeitpunkt ändern möchten, können Sie manuell den Registrierungsschlüssel bearbeiten, durch den die Erfassungszeit gesteuert wird. Jede Instanz des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hat ihren eigenen Registrierungsschlüssel:  
  
 HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< Instanz-ID > \CPE\TimeofReporting  
  
 Der Wert dieses Registrierungsschlüssels enthält den Ausführungszeitpunkt der Sammlung als Anzahl von Minuten ab 00:00 Uhr (Mitternacht). Bei einem Wert von 60 würde die Erfassung also beispielsweise um 1:00 Uhr ausgeführt werden, bei einem Wert von 1200 um 8:00 Uhr usw.  
  
## <a name="error-reporting"></a>Fehlerberichterstellung  
 Verwenden der **Fehler- und Einstellungen für Verwendungsberichte** auf der Seite die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installations-Assistenten zum Aktivieren der Fehler- oder Verwendungsberichte für Funktionen für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="options"></a>Tastatur  
 In der Standardeinstellung für deaktiviert die Auflistung von Funktionsverwendungsdaten und fehlerberichterstellung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sowie die entsprechenden Komponenten [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Fehlerberichterstellung  
 Wenn Sie die Funktion Fehlerberichterstellung aktivieren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ist zum Senden eines Berichts konfiguriert [!INCLUDE[msCoName](../../includes/msconame-md.md)] automatisch, wenn ein schwerwiegender Fehler, in der folgenden auftritt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Komponenten:  
  
-   Die [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Replikation  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] verwendet Fehlerberichte, zur Verbesserung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Funktionalität und behandelt alle Informationen vertraulich.  
  
 Informationen zu Fehlern werden über eine sichere Verbindung (https) an [!INCLUDE[msCoName](../../includes/msconame-md.md)] gesendet, wo sie mit eingeschränkten Zugriffsrechten gespeichert werden. Alternativ dazu können Sie die Fehlerberichte auch an Ihren Firmen-Fehlerberichtsserver senden.  
  
 Fehlerberichte enthalten die folgenden Informationen:  
  
-   Die Bedingung der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beim Auftreten des Problems.  
  
-   Version des Betriebssystems und Computerhardwareinformationen.  
  
-   Ihre digitale Product ID, die nicht zum Identifizieren Ihrer Lizenz verwendet wird.  
  
-   Die Netzwerk-IP-Adresse des Computers oder Proxyservers.  
  
-   Informationen aus dem Arbeitsspeicher oder aus Dateien zum Prozess, der den Fehler verursacht hat.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] sammelt nicht vorsätzlich Ihre Dateien, Name, Adresse, e-Mail-Adresse oder eine andere Form von personenbezogenen Daten. Der Fehlerbericht kann jedoch persönliche Informationen aus dem Arbeitsspeicher oder Dateien des Prozesses enthalten, der den Fehler verursacht hat. Mithilfe dieser Daten ist es möglich, Ihre Identität zu ermitteln. [!INCLUDE[msCoName](../../includes/msconame-md.md)] verwendet diese Daten jedoch nicht zu diesem Zweck.  
  
 Weitere Informationen zu den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenschutz- und Datensammlungsrichtlinie finden Sie unter [Datenschutzbestimmungen für Microsoft SQL Server](../../../2014/getting-started/microsoft-sql-server-privacy-statement.md).  
  
 Wenn Sie die Fehlerberichterstellung aktivieren und ein schwerwiegender Fehler auftritt, wird möglicherweise im Windows-Ereignisprotokoll eine Meldung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] mit einem Verweis auf einen [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base-Artikel zu dem entsprechenden Fehler angezeigt.  
  
 Zum Deaktivieren der Fehler- und Funktionsverwendungs-berichterstellung für alle Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und seine Komponenten aus, nachdem Setup abgeschlossen ist, fahren Sie mit der **Fehler- und Einstellungen für Verwendungsberichte** Dialogfeld und deaktivieren Sie die Kontrollkästchen für **Funktionsverwendung** . Wenn **Fehlerberichterstattung** aktiviert ist, für mehrere Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (die [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], sowie freigegebene Komponenten) Sie können die Fehlerberichterstattung deaktivieren, für jede Instanz eines einzelnen Komponenten sowie freigegebene Komponenten aufgeführt, als **andere**.  
  
## <a name="see-also"></a>Siehe auch  
 [Informationen zu den SQL Server-Lizenzbedingungen](../../../2014/getting-started/about-the-sql-server-license-terms.md)  
  
  
