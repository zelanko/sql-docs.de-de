---
title: Installieren von Distributed Replay von der Eingabeaufforderung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ea1171da-f50e-4f16-bedc-5e468a46477f
caps.latest.revision: 18
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1cc56f35b44636493fe022b7adbc2270bf121e55
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37310840"
---
# <a name="install-distributed-replay-from-the-command-prompt"></a>Installieren von Distributed Replay von der Eingabeaufforderung
  Wenn Sie eine neue Distributed Replay-Instanz mithilfe der Eingabeaufforderung installieren, können Sie angeben, welche Funktionen installiert und wie diese konfiguriert werden sollen. Die Installation an der Eingabeaufforderung unterstützt das Installieren, Reparieren, Aktualisieren und Deinstallieren der Distributed Replay Utility-Komponenten. Beim Installieren über die Eingabeaufforderung unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] mithilfe des /Q-Parameters den vollständigen stillen Modus.  
  
> [!NOTE]  
>  Bei lokalen Installationen müssen Sie das Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie ein Domänenkonto verwenden, das Lese- und Ausführungsberechtigungen auf der Remotefreigabe hat.  
  
## <a name="installation-parameters"></a>Installationsparameter  
 Die Liste der Funktionen höchster Ebene umfasst [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]und Tools. Mit der Funktion Tools werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Verwaltungstools, die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]und weitere freigegebene Komponenten installiert. Geben Sie für die Installation der Distributed Replay-Komponenten die folgenden Parameter an:  
  
|Komponente|Parameter|  
|---------------|---------------|  
|Distributed Replay Controller|**DREPLAY_CTLR**|  
|Distributed Replay Client|**DREPLAY_CLT**|  
|Verwaltungstool|**Tools**|  
  
> [!IMPORTANT]  
>  Nachdem Sie Distributed Replay installiert haben, müssen Sie auf dem Controller und den Clientcomputern Firewallregeln erstellen und jedem Clientcomputer Berechtigungen für den Zielserver gewähren. Weitere Informationen finden Sie unter [Ausführen der Schritte nach der Installation](complete-the-post-installation-steps.md).  
  
 Entwickeln Sie mit den in der folgenden Tabelle aufgeführten Parametern Befehlszeilenskripts für die Installation.  
  
|Parameter|Description|Unterstützte Werte|  
|---------------|-----------------|----------------------|  
|/CTLRSVCACCOUNT<br /><br /> **Optional**|Dienstkonto für den Distributed Replay Controller-Dienst.|Überprüft Konto und Kennwort.|  
|/CTLRSVCPASSWORD<br /><br /> **Optional**|Kennwort für das Distributed Replay Controller-Dienstkonto.|Überprüft Konto und Kennwort.|  
|/CTLRSTARTUPTYPE<br /><br /> **Optional**|Starttyp für den Distributed Replay Controller-Dienst.|Automatic<br /><br /> Disabled<br /><br /> Manuell|  
|/CTLRUSERS<br /><br /> **Optional**|Geben Sie an, welche Benutzer über Berechtigungen für den Distributed Replay Controller-Dienst verfügen.|Satz von Benutzerkontozeichenfolgen, mit " " (Leerzeichen) als Trennzeichen.<br /><br /> **Wichtig**: Wenn Sie den Distributed Replay Controller-Dienst konfigurieren, können Sie mindestens ein Benutzerkonto angeben, das zum Ausführen der Distributed Replay Client-Dienste verwendet wird. Die folgenden Kontotypen werden unterstützt:<br /><br /> Domänenbenutzerkonto<br /><br /> Vom Benutzer erstelltes lokales Benutzerkonto<br /><br /> Administrator<br /><br /> Virtuelles Konto und verwaltetes Dienstkonto (Managed Service Account, MSA)<br /><br /> Netzwerkdienste, lokale Dienste und System<br /><br /> <br /><br /> Gruppenkonten (lokales oder Domänenbenutzerkonto) und andere integrierte Konten (wie "Jeder") werden nicht akzeptiert.|  
|/CLTSVCACCOUNT<br /><br /> **Optional**|Dienstkonto für den Distributed Replay Client-Dienst.|Überprüft Konto und Kennwort.|  
|/CLTSVCPASSWORD<br /><br /> **Optional**|Kennwort für das Distributed Replay Client-Dienstkonto.|Überprüft Konto und Kennwort.|  
|/CLTSTARTUPTYPE<br /><br /> **Optional**|Starttyp für den Distributed Replay Client-Dienst.|Automatic<br /><br /> Disabled<br /><br /> Manuell|  
|/CLTCTLRNAME<br /><br /> **Optional**|Der Computername, mit dem der Client für den Distributed Replay Controller-Dienst kommuniziert.||  
|/CLTWORKINGDIR<br /><br /> **Optional**|Das Arbeitsverzeichnis für den Distributed Replay Client-Dienst.|Gültiger Pfad|  
|/CLTRESULTDIR<br /><br /> **Optional**|Das Ergebnisverzeichnis für den Distributed Replay Client-Dienst.|Gültiger Pfad|  
  
### <a name="sample-syntax"></a>Beispielsyntax:  
 **So installieren Sie die Distributed Replay Controller-Komponente**  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CTLR /IAcceptSQLServerLicenseTerms /CTLRUSERS="domain\user1" "domain\user2" /CTLRSVCACCOUNT="domain\svcuser" /CTLRSVCPASSWORD="password" /CTLRSTARTUPTYPE=Automatic  
```  
  
 **So installieren Sie die Distributed Replay Client-Komponente**  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CLT /IAcceptSQLServerLicenseTerms /CLTSVCACCOUNT="domain\svcuser" /CLTSVCPASSWORD="password" /CLTSTARTUPTYPE=Automatic /CLTCTLRNAME=ControllerMachineName /CLTWORKINGDIR="C:\WorkingDir" /CLTRESULTDIR="C:\ResultDir  
```  
  
  
