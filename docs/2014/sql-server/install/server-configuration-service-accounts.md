---
title: Server Konfiguration-Dienst Konten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- service account configuration, SQL Server
ms.assetid: c283702d-ab20-4bfa-9272-f0c53c31cb9f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: a894475f9dbdc95396f27b32f25f56bc409f0348
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85036721"
---
# <a name="server-configuration---service-accounts"></a>Serverkonfiguration – Dienstkonten
  Auf der Seite Serverkonfiguration des Installations-Assistenten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] können Sie den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Diensten Anmeldekonten zuweisen. Welche Dienste tatsächlich auf dieser Seite konfiguriert sind, ist von den Funktionen abhängig, die Sie für die Installation ausgewählt haben.  
  
Start Konten, die zum Starten und Ausführen von verwendet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] werden, können Domänen Benutzerkonten, lokale Benutzerkonten, verwaltete Dienst Konten, virtuelle Konten oder integrierte Systemkonten sein.  
  
## <a name="options"></a>Optionen  
 Sie können allen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Diensten dasselbe Anmeldekonto zuweisen, oder Sie können jedes Dienstkonto einzeln konfigurieren. Außerdem können Sie angeben, ob Dienste automatisch starten sollen, manuell gestartet werden oder deaktiviert sind. Das Standardkonto wird für die meisten Installationen empfohlen.  
  
 Unter Windows 7 und [!INCLUDE[nextref_longhorn](../../includes/nextref-longhorn-md.md)] R2 werden die meisten Konten standardmäßig als virtuelles Konto eingerichtet.  
  
 Wenn Sie Dienste für die Verwendung von Domänenkonten konfigurieren, empfiehlt [!INCLUDE[msCoName](../../includes/msconame-md.md)] , die Dienstkonten einzeln zu konfigurieren, um möglichst geringe Rechte für jeden Dienst bereitzustellen. Dabei erhalten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste die Berechtigungen, die mindestens erforderlich ist, um ihre Tasks auszuführen. Weitere Informationen einschließlich Beschreibungen der Kontotypen finden Sie unter [Konfigurieren von Windows-Dienstkonten und -Berechtigungen](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).  
  
 **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Dienst Konten einzeln konfigurieren (empfohlen)**  
 Stellen Sie mithilfe des Rasters die einzelnen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste mit Benutzername und Kennwort bereit, und legen Sie den Starttyp für jeden Dienst fest. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienste können mit integrierten Systemkonten, lokalen Konten, lokalen Gruppen, Domänengruppen oder Domänenbenutzerkonten verwendet werden.  
  
 Wählen Sie einen der folgenden Dienste aus, um die Einstellungen anzupassen.  
  
|Diesen Dienst auswählen|Zum Konfigurieren der Authentifizierungseinstellungen für|  
|-------------------------|----------------------------------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Agent|Dienst, der Aufträge ausführt, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]überwacht und die Automatisierung administrativer Tasks ermöglicht.<br /><br /> Dieser Dienst verfügt nicht über ein Standardanmeldekonto.<br /><br /> Der Standardstarttyp ist Manuell.|  
|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|Der Standardstarttyp ist Automatisch.|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|Der Standardstarttyp ist Automatisch.<br /><br /> Für den integrierten SharePoint-Modus müssen Sie ein Windows-Domänenbenutzerkonto angeben. Das von Ihnen angegebene Konto wird für den [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Dienst verwendet. Das Konto, das Sie für die aktuelle Instanz angeben, muss auch für alle zusätzlichen [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] -Instanzen verwendet werden, die der gleichen Farm anschließend hinzugefügt werden.|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|Dienstkonten werden verwendet, um eine Verbindung mit der Berichtsserver-Datenbank zu konfigurieren. Wählen Sie den integrierten Netzwerkdienst aus, wenn Sie Standardauthentifizierungseinstellungen verwenden möchten. Wenn Sie ein Domänenbenutzerkonto angeben und auf dem Berichtsserver die Windows-Authentifizierung verwenden, müssen Sie dafür einen Dienstprinzipalnamen (Service Principal Name, SPN) registrieren. Weitere Informationen finden Sie unter [Konfigurieren der Windows-Authentifizierung auf dem Berichtsserver](../../reporting-services/security/configure-windows-authentication-on-the-report-server.md).<br /><br /> Der Standardstarttyp ist Automatisch.|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stellt eine Gruppe grafischer Tools und programmierbarer Objekte zum Verschieben, Kopieren und Transformieren von Daten bereit.<br /><br /> Der Standardstarttyp ist Automatisch.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client|Dienstkonto für den Distributed Replay Client-Dienst.<br /><br /> Stellen Sie ein Konto bereit, unter dem der Distributed Replay Client-Dienst ausgeführt werden soll. Dieses Konto sollte nicht mit dem Konto identisch sein, das Sie für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst verwenden.<br /><br /> Der Standardstarttyp ist Manuell.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Controller|Dienstkonto für den Distributed Replay Controller-Dienst.<br /><br /> Stellen Sie ein Konto bereit, unter dem der Distributed Replay Controller-Dienst ausgeführt werden soll. Dieses Konto sollte nicht mit dem Konto identisch sein, das Sie für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst verwenden.<br /><br /> Der Standardstarttyp ist Manuell.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Volltextfilterdaemon-Startprogramm|Der Dienst, der die fdhost.exe-Prozesse erstellt. Dieser wird zum Hosten der Wörtertrennungen und Filter benötigt, mit denen Textdaten für die Volltextindizierung verarbeitet werden.<br /><br /> Wenn Sie ein Domänenkonto angeben, unter dem der FDHOST-Startprogrammdienst ausgeführt wird, wird dringend empfohlen, ein Konto mit eingeschränkten Berechtigungen zu verwenden. Dieses Konto sollte nicht mit dem Konto identisch sein, das Sie für den [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Dienst verwenden.|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Browser ist der Namensauflösungsdienst, der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Verbindungsinformationen für Clientcomputer bereitstellt. Dieser Dienst wird für mehrere Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] freigegeben. Das Standardanmeldekonto ist NT-Autorität\Lokaler Dienst und kann während des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Setups nicht geändert werden. Sie können das Konto ändern, nachdem Setup abgeschlossen wurde. Wird der Starttyp beim Setup nicht angegeben, wird er wie folgt bestimmt:<br /><br /> Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Browser wird auf Automatisch festgelegt und in den unten beschriebenen Installationsszenarien ausgeführt:<br />-<br />                            [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Failoverclusterinstanz<br />-<br />                            Benannte Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], wobei TCP oder NP aktiviert ist<br />-<br />                            Benannte Instanz von Analysis-Server und keine Gruppierung<br /><br /> Wenn keines dieser Szenarien zutrifft und der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browser bereits installiert ist, wird der aktuelle Status des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Browsers beibehalten.<br /><br /> Der Starttyp wird auf Deaktiviert festgelegt und beendet, wenn vor der Installation keine Instanz einer älteren Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vorhanden ist.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Überlegungen zur Sicherheit bei SQL Server-Installationen](../../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
