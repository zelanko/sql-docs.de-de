---
title: Akzeptieren der Lizenzbedingungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- license terms
helpviewer_keywords:
- Registration Information page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, Registration Information page
ms.assetid: 08dd739d-5817-4418-bcff-74ab7f8bbd33
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 6d41879b84d98f72e570b00a61341a53d2e6187a
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85046450"
---
# <a name="accept-license-terms"></a>Akzeptieren von Lizenzbedingungen
  Mithilfe der Seite **Lizenzbedingungen akzeptieren** des Installations-Assistenten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können Sie die Lizenzbedingungen für diese Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]akzeptieren.  
  
 Sie können den Lizenzvertrag drucken oder in die Zwischenablage kopieren. Akzeptieren Sie die Lizenzbedingungen, und klicken Sie dann auf **Weiter**, um den Vorgang fortzusetzen. Um die Installation zu beenden, klicken Sie auf **Abbrechen**.  
  
## <a name="customer-experience-improvement-program-ceip"></a>Customer Experience Improvement Program (CEIP)  
 Wenn Sie die Erstellung von CEIP-Berichten aktivieren, wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] so konfiguriert, dass in regelmäßigen Abständen ein Bericht an [!INCLUDE[msCoName](../../includes/msconame-md.md)]gesendet wird. Die Berichte enthalten Informationen zur Hardwarekonfiguration und zur Verwendung von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und zugehörigen Komponenten. [!INCLUDE[msCoName](../../includes/msconame-md.md)] verwendet die Funktionsverwendungsdaten, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] weiter zu verbessern. Folgende [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Komponenten werden von dieser Funktion überwacht:  
  
-   Das [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Replikation  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setup  
  
 Informationen zur Funktionsverwendung werden an [!INCLUDE[msCoName](../../includes/msconame-md.md)]gesendet und dort mit eingeschränktem Zugriff gespeichert.  
  
 Um die CEIP-Berichterstellung nach Abschluss des Setups zu deaktivieren, verwenden Sie das Tool ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Fehler-und Verwendungs Bericht** Erstellung im [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Menü **Konfigurationstools** .  
  
 Informationen zu Setupaktionen wie Installations-, Upgrade- oder Reparaturvorgängen usw. werden ausschließlich während der Ausführung des Setupprogramms erfasst und hochgeladen.  
  
 Für alle anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten werden einmal täglich Informationen zu allen aktivierten Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]erfasst. Der Zeitpunkt der Erfassung ist standardmäßig Mitternacht, um die Belastung des Servers zu minimieren. Wenn Sie diesen Zeitpunkt ändern möchten, können Sie manuell den Registrierungsschlüssel bearbeiten, durch den die Erfassungszeit gesteuert wird. Jede Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] hat ihren eigenen Registrierungsschlüssel:  
  
 HKLM\Software \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \mssql12. \<INSTANCEID> \Cpeer \timeofreporting  
  
 Der Wert dieses Registrierungsschlüssels enthält den Ausführungszeitpunkt der Sammlung als Anzahl von Minuten ab 00:00 Uhr (Mitternacht). Bei einem Wert von 60 würde die Erfassung also beispielsweise um 1:00 Uhr ausgeführt werden, bei einem Wert von 1200 um 8:00 Uhr usw.  
  
## <a name="error-reporting"></a>Fehlerberichterstellung  
 Verwenden Sie die Seite **Einstellungen für Fehler- und Verwendungsberichte** des Installations-Assistenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , um die Funktionalität für Fehler- oder Verwendungsberichte für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]zu aktivieren.  
  
### <a name="options"></a>Optionen  
 In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sind die Funktionen zur Auflistung von Funktionsverwendungsdaten und zur Fehlerberichterstellung für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]sowie die entsprechenden Komponenten standardmäßig deaktiviert.  
  
 Fehlerberichterstellung  
 Wenn Sie die Funktion Fehlerberichterstellung aktivieren, wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] so konfiguriert, dass automatisch ein Bericht an [!INCLUDE[msCoName](../../includes/msconame-md.md)] gesendet wird, sobald ein schwerwiegender Fehler in einer der folgenden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Komponenten auftritt:  
  
-   Das [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Replikation  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] verwendet Fehlerberichte, um die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Funktionalität zu verbessern, und behandelt alle Informationen vertraulich.  
  
 Informationen zu Fehlern werden über eine sichere Verbindung (https) an [!INCLUDE[msCoName](../../includes/msconame-md.md)]gesendet, wo sie mit eingeschränkten Zugriffsrechten gespeichert werden. Alternativ dazu können Sie die Fehlerberichte auch an Ihren Firmen-Fehlerberichtsserver senden.  
  
 Fehlerberichte enthalten die folgenden Informationen:  
  
-   Zustand von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beim Auftreten des Problems.  
  
-   Version des Betriebssystems und Computerhardwareinformationen.  
  
-   Ihre digitale Product ID, die nicht zum Identifizieren Ihrer Lizenz verwendet wird.  
  
-   Die Netzwerk-IP-Adresse des Computers oder Proxyservers.  
  
-   Informationen aus dem Arbeitsspeicher oder aus Dateien zum Prozess, der den Fehler verursacht hat.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] verfolgt nicht die Absicht, Dateien, Namen, Adresse, E-Mail-Adresse oder andere persönliche Daten von Ihnen zu erfassen. Der Fehlerbericht kann jedoch persönliche Informationen aus dem Arbeitsspeicher oder Dateien des Prozesses enthalten, der den Fehler verursacht hat. Mithilfe dieser Daten ist es möglich, Ihre Identität zu ermitteln. [!INCLUDE[msCoName](../../includes/msconame-md.md)] verwendet diese Daten jedoch nicht zu diesem Zweck.  
  
 Weitere Informationen über die Datenschutz- und Datensammlungsrichtlinie für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] finden Sie unter [Microsoft SQL Server-Datenschutzbestimmungen](../../../2014/getting-started/microsoft-sql-server-privacy-statement.md).  
  
 Wenn Sie die Fehlerberichterstellung aktivieren und ein schwerwiegender Fehler auftritt, wird möglicherweise im Windows-Ereignisprotokoll eine Meldung von [!INCLUDE[msCoName](../../includes/msconame-md.md)] mit einem Verweis auf einen [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base-Artikel zu dem entsprechenden Fehler angezeigt.  
  
 Um nach Abschluss des Setups die Fehler- und Funktionsverwendungs-Berichterstellung für alle Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und die dazugehörigen Komponenten zu deaktivieren, wechseln Sie in das Dialogfeld **Einstellungen für Fehler- und Verwendungsberichte** , und deaktivieren Sie die Kontrollkästchen für die **Funktionsverwendung**. Wenn die **Fehlerberichterstattung** für mehrere Komponenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (die freigegebenen [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] Komponenten,, und) aktiviert ist [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , können Sie die Fehlerberichterstattung für jede Instanz einer einzelnen Komponente sowie für freigegebene Komponenten, die als **andere**aufgelistet sind, deaktivieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Informationen zu den SQL Server-Lizenzbedingungen](../../../2014/getting-started/about-the-sql-server-license-terms.md)  
  
  
