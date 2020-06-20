---
title: 'Vorgehensweise: Installieren des Upgrade Advisors | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, installing
- Upgrade Advisor [SQL Server], installing
ms.assetid: 481b0704-ce79-4543-b141-67306128aa2b
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: ac1488cd9a42a8f7e212fe533615dbb131fe7290
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059306"
---
# <a name="how-to-install-upgrade-advisor"></a>Gewusst wie: Installieren des Upgrade Advisors
  Upgrade Advisor unterstützt die Remoteanalyse aller unterstützten Komponenten mit Ausnahme von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Wenn Sie keine Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scannen, können Sie den Upgrade Advisor auf einem beliebigen Computer installieren, der eine Verbindung mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] herstellen kann. Der Computer muss zudem die Voraussetzungen für den Upgrade Advisor erfüllen. Wenn Sie Instanzen von [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scannen, müssen Sie den Upgrade Advisor auf dem Berichtsserver installieren.  
  
 Weitere Informationen finden Sie unter [Installieren des Upgrade Advisors](../../../2014/sql-server/install/installing-upgrade-advisor.md).  
  
### <a name="to-install-upgrade-advisor"></a>So installieren Sie den Upgrade Advisor  
  
1.  Starten Sie die Installation mithilfe einer der folgenden Methoden:  
  
    -   Wenn Sie von der Website installieren [!INCLUDE[msCoName](../../includes/msconame-md.md)] , klicken Sie auf den Link **Download** , und klicken Sie dann auf die Schaltfläche **Ausführen** , um die Installation zu starten.  
  
    -   Wenn Sie von einem Produkt Medium installieren, öffnen Sie den Ordner **Redist** , öffnen Sie den Ordner **Upgrade Advisor** , und doppelklicken Sie dann auf **SQLUA.msi**.  
  
    > [!NOTE]  
    >  Für Upgrade Advisor ist [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 4 erforderlich. Wenn die Anwendung nicht installiert ist oder Sie eine Vorabversion verwenden, wird eine Fehlermeldung angezeigt. Deinstallieren Sie frühere Versionen von [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], und installieren Sie dann die aktuelle Version von .NET Framework 4.  
    >   
    >  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom ist eine Voraussetzung für die Installation [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] von Upgrade Advisor und wird vom Upgrade Advisor-Setup nicht installiert. Das Setup erfordert, dass Sie das [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom aus dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack herunterladen und installieren.  
  
2.  Klicken Sie auf der Seite **Willkommen [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ** auf **weiter**.  
  
3.  Lesen Sie auf der Seite **Lizenzvertrag** den Lizenzvertrag. Wenn Sie zustimmen, wählen Sie **Ich akzeptiere die Lizenzvereinbarung** aus, und klicken Sie dann auf **weiter**.  
  
4.  Geben Sie auf der Seite **Registrierungsinformationen** ihren Namen und Ihr Unternehmen ein.  
  
5.  Überprüfen Sie auf der Seite **Funktionsauswahl** den Wert für den **Installationspfad** . Verwenden Sie ggf. die Schaltfläche **Durchsuchen** , um den Speicherort zu ändern. Klicken Sie auf **Weiter**.  
  
6.  Klicken Sie auf der Seite **bereit zum Installieren des Programms** auf **Installieren** , um den Upgrade Advisor zu installieren.  
  
7.  Klicken Sie auf **Fertig stellen**, um den Assistenten zu beenden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Voraussetzungen für den Upgrade Advisor](../../../2014/sql-server/install/upgrade-advisor-prerequisites.md)  
  
  
