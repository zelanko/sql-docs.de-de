---
title: Aktualisieren einer SQL Server-Failoverclusterinstanz (Setup) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading clusters
- clusters [SQL Server], upgrading
- failover clustering [SQL Server], creating clusters
- clusters [SQL Server], creating
- failover clustering [SQL Server], upgrading
ms.assetid: ea8b7d66-e5a1-402f-9928-8f7310e84f5c
caps.latest.revision: 59
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 09cddbea72c375cb369f7bf4e795ae555099652e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36048895"
---
# <a name="upgrade-a-sql-server-failover-cluster-instance-setup"></a>Aktualisieren einer SQL Server-Failoverclusterinstanz (Setup)
  Sie können einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Failovercluster mithilfe des Installations-Assistenten für [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] oder mithilfe einer Eingabeaufforderung auf einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Failovercluster aktualisieren.  
  
 Während des Failoverclusterupgrades wird die Ausfallzeit auf die Failoverzeit und auf die Ausführungszeit der Upgradeskripts begrenzt. Wenn Sie den parallelen Updatevorgang des Failoverclusters ausführen, erzielen Sie minimale Ausfallzeiten. Wenn jedoch alle erforderlichen Komponenten nicht bereits im Failoverclusterknoten installiert sind, müssen Sie zusätzliche Ausfallzeit für die Installation dieser Komponenten einkalkulieren. Weitere Informationen dazu, wie Sie die Ausfallzeit minimieren, während des Upgrades finden Sie unter der [bewährte Methoden vor dem Upgrade eines Failoverclusters](#BestPractices) Abschnitt auf dieser Seite.  
  
 Weitere Informationen zum upgrade finden Sie unter [Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md) und [aktualisieren auf SQL Server 2014](../../../database-engine/install-windows/upgrade-sql-server.md).  
  
 Weitere Informationen zur Beispielsyntax für die Verwendung der Eingabeaufforderung finden Sie unter [Installieren von SQL Server 2014 von der Befehlszeile aus](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Lesen Sie die folgenden wichtigen Informationen, bevor Sie beginnen:  
  
-   [Vor dem Installieren des Failoverclusterings](../install/before-installing-failover-clustering.md)  
  
-   [Verwenden von Upgrade Advisor zur Vorbereitung auf Upgrades](../../install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
-   
  [Aktualisieren der Datenbank-Engine](../../../database-engine/install-windows/upgrade-database-engine.md)  
  
-   In einem Clusterbetriebssystem wird .NET Framework 4.0 von Setup installiert. Um mögliche Ausfallzeiten zu minimieren, wird empfohlen, .NET Framework 4 zu installieren, bevor Sie Setup ausführen.  
  
-   Um sicherzustellen, dass die Visual Studio-Komponente ordnungsgemäß installiert werden kann [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] erfordert, dass Sie ein Update zu installieren. Das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Setup überprüft, ob dieses Update vorhanden ist, und fordert Sie zum Herunterladen und Installieren des Updates auf, bevor Sie die Installation von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fortsetzen. Vermeiden Sie die Unterbrechung beim [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup können Sie herunterladen und Installieren des Updates vor der Ausführung [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup wie unten beschrieben (oder installieren Sie alle Updates für .NET 3.5 SP1 über Windows Update verfügbar):  
  
     Bei der Installation [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] auf einem Computer mit dem Betriebssystem Windows Server 2008 SP2, erhalten Sie das erforderliche Update [hier](http://go.microsoft.com/fwlink/?LinkId=198093)  
  
     Wenn Sie [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] auf einem Computer mit dem Betriebssystem [!INCLUDE[win7](../../../includes/win7-md.md)] SP1 oder [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] SP1 installieren, ist dieses Update bereits enthalten.  
  
-   .NET Framework 3.5 SP1 wird vom [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Setup nicht mehr installiert; diese Version kann jedoch für die Installation von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] unter [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] erforderlich sein. Weitere Informationen finden Sie in den [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)][Versionshinweise](http://go.microsoft.com/fwlink/?LinkId=296445).  
  
-   Bei lokalen Installationen müssen Sie das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Setup als Administrator ausführen. Wenn Sie [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] von einer Remotefreigabe installieren, müssen Sie auf der Remotefreigabe ein Domänenkonto mit Leseberechtigungen verwenden.  
  
-   Zum Aktualisieren einer Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] zu einem [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Failovercluster, der zu aktualisierenden Instanz muss einem Failovercluster sein.  
  
     Um eine eigenständige Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] auf einen [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]-Failovercluster zu verschieben, müssen Sie einen neuen [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]-Failovercluster installieren und die Benutzerdatenbanken dann mithilfe des Assistenten zum Kopieren von Datenbanken von der eigenständigen Instanz migrieren. Weitere Informationen finden Sie unter [Use the Copy Database Wizard](../../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="rolling-upgrades"></a>Parallele Upgrades  
 Um einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Failovercluster auf [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] zu aktualisieren, müssen Sie Setup mit der Upgradeaktion für jeden Failoverclusterknoten ausführen, mit den passiven Knoten beginnend. Beim Aktualisieren der einzelnen Knoten wird der jeweilige Knoten nicht als möglicher Besitzer des Failoverclusters angezeigt. Im Fall eines unerwarteten Failovers können die aktualisierten Knoten erst im Failover verwendet werden, wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Setup den Gruppenbesitz von Clusterressourcen zu einem aktualisierten Knoten verschiebt.  
  
 In der Standardeinstellung wird vom Setup automatisch festgelegt, wann ein Failover zu einem aktualisierten Knoten auszuführen ist. Dies ist von der Gesamtanzahl der Knoten in der Failoverclusterinstanz und der Anzahl der bereits aktualisierten Knoten abhängig. Wenn bereits mindestens die Hälfte der Knoten aktualisiert wurde, führt Setup einen Failover zu einem aktualisierten Knoten aus, wenn Sie im nächsten Knoten eine Aktualisierung ausführen. Nach dem Failover zu einem aktualisierten Knoten wird die Clustergruppe in einen aktualisierten Knoten verschoben. Alle aktualisierten Knoten werden in die Liste möglicher Besitzer eingefügt. Alle Knoten, die noch nicht aktualisiert wurden, werden aus der Liste möglicher Besitzer entfernt. Jeder verbleibende Knoten, den Sie aktualisieren, wird der Liste möglicher Besitzer des Failoverclusters hinzugefügt.  
  
 Durch diesen Vorgang wird die Ausfallzeit während der gesamten Failoverclusteraktualisierung auf eine Failoverzeit und die Ausführungszeit für Aktualisierungsskripts begrenzt.  
  
 Führen Sie zum Steuern des Failoververhaltens von Clusterknoten während des Upgradevorgangs den Upgradevorgang über die Eingabeaufforderung aus, und verwenden Sie dabei den /FAILOVERCLUSTERROLLOWNERSHIP-Parameter. Weitere Informationen finden Sie unter [Installieren von SQL Server 2014 über die Eingabeaufforderung](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md).  
  
 **Hinweis** Wenn es ein Einzelknoten-Failovercluster ist [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Ressourcengruppe der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Ressourcengruppe offline.  
  
## <a name="considerations-when-upgrading-from-includessversion2005includesssversion2005-mdmd"></a>Überlegungen zum Aktualisieren von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]  
 Wenn Sie Domänengruppen für die Sicherheitsrichtlinie für Cluster angegeben haben, können Sie keine Dienst-SID für [!INCLUDE[nextref_longhorn](../../../includes/nextref-longhorn-md.md)] angeben. Wenn Sie die Dienst-SID verwenden möchten, müssen Sie ein paralleles Upgrade durchführen.  
  
 Wenn Sie [!INCLUDE[ssDE](../../../includes/ssde-md.md)] für das Upgrade auswählen, ist die Volltextsuche im Setup enthalten, unabhängig davon, ob sie unter [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] installiert war.  
  
 Wenn die Volltextsuche in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] aktiviert war, erstellt Setup den Volltextsuchkatalog unabhängig von den für Sie verfügbaren Optionen neu.  
  
## <a name="upgrading-to-a-includesssql14includessssql14-mdmd-multi-subnet-failover-cluster"></a>Aktualisieren auf einen [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]-Multisubnetz-Failovercluster  
 Es gibt zwei mögliche Szenarien für Upgrades:  
  
1.  Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Failovercluster ist derzeit für ein einziges Subnetz konfiguriert: Sie müssen zuerst den vorhandenen Cluster auf [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] aktualisieren, indem Sie Setup starten und die erforderlichen Upgradeschritte ausführen. Fügen Sie nach Abschluss des Upgradeprozesses für den vorhandenen Failovercluster mithilfe der AddNode-Funktion einen Knoten hinzu, der sich in einem anderen Subnetz befindet. Bestätigen Sie auf der Konfigurationsseite des Clusternetzwerks die Änderung der IP-Adressabhängigkeit in OR. Sie verfügen jetzt über einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Multisubnetz-Failovercluster.  
  
2.  Der [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Failovercluster ist derzeit unter Verwendung von Stretch-V-LAN-Technologie für mehrere Subnetze konfiguriert: Sie müssen zuerst den vorhandenen Cluster auf [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] aktualisieren. Da mit der Stretch-V-LAN-Technologie ein einzelnes Subnetz konfiguriert wird, muss die Netzwerkkonfiguration in mehrere Subnetze geändert werden, und die Abhängigkeit der IP-Adressressource muss mithilfe des Failovercluster-Manager von Windows in OR geändert werden.  
  
###  <a name="BestPractices"></a> Bewährte Methoden vor dem Upgrade eine [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Failovercluster  
 Um unerwartete Ausfallzeiten aufgrund eines Neustarts auszuschließen, installieren Sie vor dem Aktualisieren der Clusterknoten das Updatepaket (kein Neustart erforderlich) für .NET Framework 4.0 in allen Failoverclusterknoten. Für die Vorinstallation der erforderlichen Komponenten werden folgende Schritte empfohlen:  
  
-   Installieren Sie das Updatepaket (kein Neustart erforderlich) für .NET Framework 4, und aktualisieren Sie, beginnend mit den passiven Knoten, nur die freigegebenen Komponenten. Auf diese Weise werden die Unterstützungsdateien für [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 4.0, Windows Installer 4.5 und [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installiert.  
  
-   Führen Sie einen oder ggf. mehrere Neustarts aus.  
  
-   Führen Sie ein Failover zu einem aktualisierten Knoten aus.  
  
-   Aktualisieren Sie die freigegebenen Komponenten im letzten verbleibenden Knoten.  
  
 Starten Sie die Failoverclusteraktualisierung, nachdem alle freigegebenen Komponenten aktualisiert und die erforderlichen Komponenten installiert wurden. Die Aktualisierung muss in jedem Failoverclusterknoten ausgeführt werden, beginnend mit den passiven Knoten bis zu dem Knoten, der als Besitzer der Clusterressourcengruppe fungiert.  
  
-   Einem vorhandenen Failovercluster können Sie keine Funktionen hinzufügen.  
  
-   Änderungen der Edition des Failoverclusters sind auf bestimmte Szenarien beschränkt. Weitere Informationen finden Sie unter [Unterstützte Versions- und Editionsupgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
##  <a name="UpgradeSteps"></a> So aktualisieren Sie einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster  
  
#### <a name="to-upgrade-a-includessnoversionincludesssnoversion-mdmd-failover-cluster"></a>So aktualisieren Sie einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Failovercluster  
  
1.  Legen Sie das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Installationsmedium ein, und doppelklicken Sie im Stammordner auf Setup.exe. Wenn Sie eine Installation über eine Netzwerkfreigabe ausführen möchten, wechseln Sie in der Freigabe zum Stammordner, und doppelklicken Sie auf Setup.exe. Möglicherweise werden Sie aufgefordert, die erforderlichen Komponenten zu installieren, falls sie nicht bereits installiert wurden.  
  
2.  > [!IMPORTANT]  
    >  Weitere Informationen zu den Schritten 3 und 4 finden Sie unter der [bewährte Methoden vor dem Upgrade eines Failoverclusters](#BestPractices) Abschnitt.  
  
3.  Nachdem die erforderlichen Komponenten installiert wurden, startet der Installations-Assistent das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Installationscenter. So aktualisieren Sie eine vorhandene Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], klicken Sie auf **Aktualisieren von [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)], oder [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].**  
  
4.  Wenn Setup-Unterstützungsdateien erforderlich sind, werden diese durch das [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Setup installiert. Wenn Sie zum Neustarten des Computers aufgefordert werden, führen Sie einen Neustart durch, bevor Sie den Vorgang fortsetzen.  
  
5.  Die Systemkonfigurationsprüfung führt einen Ermittlungsvorgang auf dem Computer aus. [!INCLUDE[clickOK](../../../includes/clickok-md.md)], um den Vorgang fortzusetzen.  
  
6.  Geben Sie auf der Seite Product Key den PID-Schlüssel für die neue Versionsedition ein, die der Edition der alten Produktversion entspricht. Wenn Sie z. B. einen Enterprise-Failovercluster aktualisieren möchten, müssen Sie einen PID-Schlüssel für [!INCLUDE[ssEnterprise](../../../includes/ssenterprise-md.md)]angeben. Klicken Sie auf **Weiter** , um den Vorgang fortzusetzen. Der für ein Failoverclusterupgrade verwendete PID-Schlüssel muss für alle Failoverclusterknoten einer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Instanz einheitlich sein. Weitere Informationen finden Sie unter [Editionen und Komponenten von SQL Server 2014](../../editions-and-components-of-sql-server-2016.md) und [Supported Version and Edition Upgrades](../../../database-engine/install-windows/supported-version-and-edition-upgrades.md).  
  
7.  Lesen Sie auf der Seite mit den Lizenzbedingungen den Lizenzvertrag, und aktivieren Sie dann das Kontrollkästchen, um den Lizenzbestimmungen zuzustimmen. Falls Sie zur Verbesserung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]beitragen möchten, können Sie auch die Option zur Funktionsverwendung aktivieren und Berichte an [!INCLUDE[msCoName](../../../includes/msconame-md.md)]senden. **Klicken Sie auf „Weiter“, um den Vorgang fortzusetzen**. Klicken Sie auf **Abbrechen**, wenn Sie den Setupvorgang beenden möchten.  
  
8.  Geben Sie auf der Seite Instanz auswählen die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] an, die auf [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]aktualisiert werden soll. **Klicken Sie auf „Weiter“, um den Vorgang fortzusetzen**.  
  
9. Auf der Seite Funktionsauswahl sind die zu aktualisierenden Funktionen bereits markiert. Nach Auswahl des Funktionsnamens wird im rechten Bereich eine Beschreibung für die einzelnen Komponentengruppen angezeigt. Sie können die zu aktualisierenden Funktionen nicht ändern und während des Aktualisierungsvorgangs keine Funktionen hinzufügen. Hinzufügen von Funktionen zu einer aktualisierten Instanz von [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] , nachdem der Upgradevorgang abgeschlossen ist, finden Sie unter [Hinzufügen von Funktionen zu einer Instanz von SQL Server 2014 &#40;Setup&#41;](../../../database-engine/install-windows/add-features-to-an-instance-of-sql-server-setup.md).  
  
     Die erforderlichen Komponenten für die ausgewählten Funktionen werden im rechten Bereich angezeigt. SQL Server-Setup installiert die erforderlichen Komponenten, die nicht bereits während des im weiteren Verlauf dieser Prozedur beschriebenen Installationsschritts installiert werden.  
  
10. Auf der Seite Instanzkonfiguration werden die Felder automatisch aus der alten Instanz aufgefüllt. Sie können optional auch den neuen InstanceID-Wert angeben.  
  
     **Instanz-ID** : Standardmäßig wird der Instanzname als Instanz-ID verwendet. Das Ziel ist dabei, Installationsverzeichnisse und Registrierungsschlüssel für die Instanz von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]zu identifizieren. Dies ist der Fall für Standardinstanzen und benannte Instanzen. Bei einer Standardinstanz lauten Instanzname und Instanz-ID MSSQLSERVER. Wenn Sie nicht die Standardinstanz-ID verwenden möchten, aktivieren Sie das Kontrollkästchen **Instanz-ID** , und geben Sie einen Wert ein. Wenn Sie den Standardwert überschreiben, müssen Sie die gleiche Instanz-ID für die Instanz angeben, die in allen Failoverclusterknoten aktualisiert wird. Die Instanz-ID für die aktualisierte Instanz muss in allen Knoten übereinstimmen.  
  
     **Ermittelte Instanzen und Funktionen** -Raster zeigt Instanzen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , sind auf dem Computer, auf dem Setup ausgeführt wird. **Klicken Sie auf „Weiter“, um den Vorgang fortzusetzen**.  
  
11. Auf der Seite Erforderlicher Speicherplatz wird der für die angegebenen Funktionen erforderliche Speicherplatz berechnet, und die Anforderungen werden mit dem Speicherplatz verglichen, der auf dem Computer verfügbar ist, auf dem Setup ausgeführt wird.  
  
12. Geben Sie auf der Seite Aktualisieren der Volltextsuche die Aktualisierungsoptionen für die Datenbanken an, die aktualisiert werden sollen. Weitere Informationen finden Sie unter [Upgradeoptionen für die Volltextsuche](../../install/full-text-search-upgrade-options.md).  
  
13. Geben Sie auf der Seite **Fehlerberichterstellung** die Informationen an, die Sie an [!INCLUDE[msCoName](../../../includes/msconame-md.md)] senden möchten, um zur Verbesserung von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]beizutragen. Die Option für Fehlerberichte ist standardmäßig aktiviert.  
  
14. Bei der Systemkonfigurationsprüfung wird eine weitere Reihe von Regeln ausgeführt, um die Konfiguration des Computers anhand der von Ihnen angegebenen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Funktionen zu überprüfen, bevor der Aktualisierungsvorgang beginnt.  
  
15. Auf der Seite Clusteraktualisierungsbericht werden die Liste mit den Knoten in der Failoverclusterinstanz und die Instanzversionsinformationen für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Komponenten in jedem Knoten angezeigt. Der Datenbankskriptstatus und der Replikationsskriptstatus werden angezeigt. Außerdem werden Informationsmeldungen zu den Vorgängen angezeigt, die ausgeführt werden, wenn Sie auf **Weiter**klicken. Abhängig von der Anzahl der Failoverclusterknoten, der bereits aktualisierten und den gesamten Anzahl von Knoten haben, zeigt Setup das Failoververhalten an, das ausgeführt wird, wenn Sie auf **Weiter**. Es werden auch Warnungen bei möglicher unnötiger Ausfallzeit angezeigt, wenn die erforderlichen Komponenten noch nicht installiert sind.  
  
16. Auf der Seite Das Upgrade kann jetzt ausgeführt werden wird eine Strukturansicht der Installationsoptionen angezeigt, die während des Setups angegeben wurden. Klicken Sie zum Fortsetzen des Vorgangs auf **Aktualisieren**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup installiert zuerst die erforderlichen Komponenten für die ausgewählten Funktionen und dann die Funktionen.  
  
17. Während des Upgrades wird auf der Seite Status der Status angezeigt, sodass Sie während des Setupvorgangs den Upgradefortschritt überwachen können.  
  
18. Nach der Aktualisierung des aktuellen Knotens werden auf der Seite Clusteraktualisierungsbericht Statusinformationen zur Aktualisierung der einzelnen Failoverclusterknoten sowie die Funktionen in jedem Failoverclusterknoten und ihre Versionsinformationen angezeigt. Bestätigen Sie die angezeigten Versionsinformationen, und fahren Sie mit der Aktualisierung der verbleibenden Knoten fort. Wenn das Failover zu aktualisierten Knoten aufgetreten ist, wird dies ebenfalls auf der Statusseite angezeigt. Sie können diese Informationen zur Bestätigung außerdem im Windows-Clusterverwaltungstool überprüfen.  
  
19. Nach der Aktualisierung werden auf der Seite Abgeschlossen ein Link zur zusammenfassenden Protokolldatei für die Installation sowie weitere wichtige Hinweise bereitgestellt. Klicken Sie auf **Schließen** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , um die Installation von abzuschließen.  
  
20. Starten Sie den Computer neu, falls Sie dazu aufgefordert werden. Wenn Sie den Setupvorgang abgeschlossen haben, sollten Sie unbedingt die vom Installations-Assistenten angezeigte Meldung lesen. Weitere Informationen zu Setupprotokolldateien finden Sie unter [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).  
  
21. Wiederholen Sie die Schritte 1 bis 21 in allen anderen Knoten des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Failoverclusters, um den Upgradevorgang abzuschließen.  
  
## <a name="to-upgrade-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster"></a>So aktualisieren Sie auf einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Multisubnetz-Failovercluster  
  
#### <a name="to-upgrade-to-a-includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster-existing-includessnoversionincludesssnoversion-mdmd-cluster-is-a-non-multi-subnet-cluster"></a>Aktualisieren auf einen [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Multisubnetz-Failovercluster (vorhandener [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] -Cluster ist kein Multisubnetzcluster)  
  
1.  Führen Sie die Schritte 1 bis 24 im die [so aktualisieren Sie einen SQL Server-Failovercluster](#UpgradeSteps) Abschnitt oben, um zum Aktualisieren des Clusters [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  
  
2.  Fügen Sie mit der Setupaktion AddNode einen Knoten in einem anderen Subnetz hinzu, und bestätigen Sie auf der Seite **Netzwerkkonfiguration für Cluster** die Änderung der IP-Adressabhängigkeit in OR. Weitere Informationen finden Sie unter [Hinzufügen oder Entfernen von Knoten in einem SQL Server-Failovercluster &#40;Setup&#41;](../install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
#### <a name="to-upgrade-a-multi-subnet-cluster-currently-using-stretch-v-lan"></a>So aktualisieren Sie einen Multisubnetzcluster mit Stretch-V-Lan  
  
1.  Führen Sie die Schritte 1 bis 24 im die [so aktualisieren Sie einen SQL Server-Failovercluster](#UpgradeSteps) Abschnitt oben, um zum Aktualisieren des Clusters [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].  
  
2.  Ändern Sie die Netzwerkeinstellungen, um den Remoteknoten in ein anderes Subnetz zu verschieben.  
  
3.  Fügen Sie mit dem Failovercluster-Manager von Windows eine neue IP-Adresse für das neue Subnetz hinzu, und legen Sie die IP-Adressabhängigkeit auf OR fest.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Führen Sie nach dem Aktualisieren auf [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]die folgenden Tasks aus:  
  
-   Registrieren der Server  
  
     Beim Aktualisieren werden die Registrierungseinstellungen für die vorherige [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz entfernt. Nach dem Aktualisieren müssen Sie die Server neu registrieren.  
  
-   Statistikaktualisierung  
  
     Um die Abfrageleistung zu optimieren, sollten Sie nach dem Update die Statistiken für alle Datenbanken aktualisieren. Statistiken in benutzerdefinierten Tabellen in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Datenbanken aktualisieren Sie mithilfe der gespeicherten Prozedur **sp_updatestats**.  
  
-   Konfigurieren Sie die neue [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Installation  
  
     Zum Reduzieren der Angriffsfläche eines Systems werden zentrale Dienste und Funktionen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] selektiv installiert und aktiviert. Weitere Informationen zur Oberflächenkonfiguration finden Sie in der Infodatei für diese Version.  
  
## <a name="see-also"></a>Siehe auch  
 [Installieren von SQLServer 2014 von der Befehlszeile aus](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Lesen und Anzeigen der Setupprotokolldateien von SQL Server](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  