---
title: Always On-Verfügbarkeitsgruppen für SQLServer unter Linux | Microsoft-Dokumentation
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 11/27/2017
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: e37742d4-541c-4d43-9ec7-a5f9b2c0e5d1
ms.openlocfilehash: 892b13610d1a6acd9576ba79499fc4b89cca0cd0
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082982"
---
# <a name="always-on-availability-groups-on-linux"></a>Always On-Verfügbarkeitsgruppen unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel beschreibt die Merkmale des Always On Availability Groups (Verfügbarkeitsgruppen) unter Linux-basierten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Installationen. Darüber hinaus werden die Unterschiede zwischen Linux und Windows Server-Failovercluster (WSFC)-Basis-Verfügbarkeitsgruppen. Finden Sie unter den [Dokumentation zu Windows-basierten](../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) für die Grundlagen der Verfügbarkeitsgruppen, wenn sie die gleichen unter Windows und Linux mit Ausnahme von der WSFC arbeiten.

Vom Standpunkt auf hoher Ebene Verfügbarkeitsgruppen unter [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] unter Linux sind dieselben wie die WSFC-basierte Implementierungen werden. Das bedeutet, dass alle Einschränkungen und Funktionen identisch, abgesehen von einigen Ausnahmen sind. Die Hauptunterschiede sind:

-   Wird unter Linux in Microsoft Distributed Transaction Coordinator (DTC) unterstützt [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. Wenn Ihre Anwendungen die Verwendung von verteilten Transaktionen erfordern, benötigen eine Verfügbarkeitsgruppe bereitstellen [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] auf Windows.
-   Linux-basierten Bereitstellungen verwenden Pacemaker anstelle von einem WSFC.
-   Im Gegensatz zu den meisten Konfigurationen für Verfügbarkeitsgruppen in Windows mit Ausnahme des Workgroupcluster-Szenarios erfordert Pacemaker nie Active Directory Domain Services (AD DS).
-   Wie Sie eine Verfügbarkeitsgruppe von einem Knoten auf einen anderen durchführen, unterscheidet sich zwischen Linux und Windows.
-   Bestimmte Einstellungen wie z. B. `required_synchronized_secondaries_to_commit` kann nur über Pacemaker unter Linux, geändert werden, während eine WSFC-basierte Installation Transact-SQL verwendet.

## <a name="number-of-replicas-and-cluster-nodes"></a>Anzahl der Replikate und Clusterknoten

Eine Verfügbarkeitsgruppe in der [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)] haben zwei Replikate: ein primäres und ein sekundäres Replikat, das nur aus Gründen der Verfügbarkeit verwendet werden kann. Es kann nicht für nichts anderes, z. B. lesbare Abfragen verwendet werden. Eine Verfügbarkeitsgruppe in der [!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)] können bis zu neun Replikate aufweisen: einen primären und bis zu acht sekundäre Datenbanken, von denen bis zu drei (einschließlich des primären Replikats) synchron sein kann. Wenn einen zugrunde liegender Cluster verwenden, kann es sein bis zu 16 Knoten insgesamt, wenn Corosync beteiligt ist. Eine verfügbarkeitsgruppe kann höchstens neun von 16 Knoten mit umfassen [!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)], und zwei mit [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)].

Eine zwei Replikaten-Konfiguration, erfordert die Möglichkeit, automatisch ein Failover auf ein anderes Replikat ausgeführt, erfordert die Verwendung eines Replikats nur die Konfiguration aus, wie in beschrieben [reine konfigurationsreplikat und Quorum](#configuration-only-replica-and-quorum). Reines konfigurationsreplikat Replikate wurden in eingeführt [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] kumulative Update 1 (CU1) damit, die die mindestens erforderliche Version für diese Konfiguration bereitgestellt werden soll.

Wenn Pacemaker verwendet wird, muss er ordnungsgemäß konfiguriert werden, damit er betriebsbereit bleibt. Dies bedeutet, dass das Quorum und STONITH hinsichtlich der Pacemaker zusätzlich zu ordnungsgemäß implementiert werden müssen [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] Anforderungen wie z. B. ein reines konfigurationsreplikat Replikat.

Lesbare sekundäre Replikate werden nur unterstützt, mit [!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)].

## <a name="cluster-type-and-failover-mode"></a>Cluster-Typ und Failover-Modus

Neu bei [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] ist die Einführung eines clustertyps für Verfügbarkeitsgruppen. Für Linux gibt es zwei gültige Werte sind: externe und keine. Ein clustertyps externer bedeutet, dass Pacemaker unter der Verfügbarkeitsgruppe verwendet wird. Verwenden von externen für Clustertyp erfordert, dass der Failover-Modus als auch externe festgelegt werden (ebenfalls neu in [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]). Automatisches Failover wird unterstützt, aber im Gegensatz zu einem WSFC ist Failovermodus mit externen, nicht automatisch festgelegt, wenn Pacemaker verwendet wird. Im Gegensatz zu einem WSFC wird der Pacemaker-Teil der Verfügbarkeitsgruppe erstellt, nachdem die Verfügbarkeitsgruppe konfiguriert wurde.

Ein Clustertyp ' None ' bedeutet, dass keine Notwendigkeit für besteht, und die Verfügbarkeitsgruppe verwendet wird, Pacemaker. Auch auf Servern, die pacemaker konfiguriert wurde, ist eine Verfügbarkeitsgruppe so konfiguriert, mit dem Clustertyp None, Pacemaker nicht sehen oder verwalten diese Verfügbarkeitsgruppe. Ein Clustertyp ' None ' unterstützt nur Manuelles Failover von einem primären zu einem sekundären Replikat. Eine Verfügbarkeitsgruppe erstellt haben, mit dem keine ist in erster Linie für die schreibgeschützte horizontale Skalierung, Szenario sowie Upgrades vorgesehen. Während es in Szenarien wie die Wiederherstellung im Notfall oder lokalen verfügbarkeitsgruppe arbeiten kann, in denen kein automatisches Failover erforderlich ist, wird nicht empfohlen. Die Listener-Geschichte ist auch eine komplexere ohne Pacemaker.

Clustertyp befindet sich in der [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] dynamische verwaltungssicht (DMV) `sys.availability_groups`, in den Spalten `cluster_type` und `cluster_type_desc`.

## <a name="requiredsynchronizedsecondariestocommit"></a>erforderliche\_synchronisiert\_sekundäre Replikate\_zu\_Commit

Neu bei [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] ist eine Einstellung, mit dem Verfügbarkeitsgruppen-wird aufgerufen, `required_synchronized_secondaries_to_commit`. Dadurch wird der Verfügbarkeitsgruppe auf die Anzahl der sekundären Replikate, die im Gleichschritt mit der primären sein müssen. Dies ermöglicht Dinge wie automatische Failover (nur bei Pacemaker mit dem Clustertyp External integriert) und das Verhalten der Dinge wie die Verfügbarkeit der primären Datenbank steuert, ob die richtige Anzahl von sekundären Replikaten entweder online oder offline ist. Weitere Informationen hierzu finden Sie unter [hohe Verfügbarkeit und Datenschutz für verfügbarkeitsgruppenkonfigurationen](sql-server-linux-availability-group-ha.md). Die `required_synchronized_secondaries_to_commit` Wert ist standardmäßig festgelegt und von Pacemaker verwaltet /[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Sie können diesen Wert manuell überschreiben.

Die Kombination von `required_synchronized_secondaries_to_commit` und die neue Sequenznummer (befindet sich in `sys.availability_groups`) informiert Sie Pacemaker und [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] , z. B. Automatisches Failover auftreten kann. In diesem Fall müsste ein sekundäres Replikat gleichen Sequenznummer wie die primäre Datenbank, was bedeutet, dass es mit der aktuellen Konfigurationsinformationen auf dem neuesten Stand ist.

Es gibt drei Werte, die für die festgelegt werden, können `required_synchronized_secondaries_to_commit`: 0, 1 oder 2. Sie steuern das Verhalten von Was geschieht, wenn ein Replikat nicht mehr verfügbar ist. Die Zahlen entsprechen der Anzahl von sekundären Replikaten, die mit dem primären Replikat synchronisiert werden müssen. Das Verhalten ist wie folgt unter Linux:

-   0 – ist kein automatisches Failover möglich, da kein sekundäres Replikat synchronisiert werden muss. Die primäre Datenbank ist immer verfügbar.
-   1 – ein sekundäres Replikat muss in einem synchronisierten Zustand befindet, mit dem primären Replikat liegen. Automatisches Failover ist möglich. Die primäre Datenbank ist nicht verfügbar, bis ein sekundäres synchronisiertes Replikat verfügbar ist.
-   2 – beide sekundären Replikate in einer drei oder mehr Knoten AG-Konfiguration müssen mit dem primären Replikat synchronisiert werden; Automatisches Failover ist möglich.

`required_synchronized_secondaries_to_commit` Steuert, nicht nur das Verhalten der Failover mit synchronen Replikaten, aber Daten verloren gehen. Mit einem Wert von 1 oder 2 muss ein sekundäres Replikat immer synchronisiert werden, also wird immer die Datenredundanz. Das bedeutet keine Daten verloren gehen.

So ändern Sie den Wert der `required_synchronized_secondaries_to_commit`, verwenden Sie die folgende Syntax:

>[!NOTE]
>Ändern des Werts führt dazu, dass die Ressource neu zu starten, einen kurzen Ausfall bedeutet. Die einzige Möglichkeit, dies zu vermeiden ist, legen Sie die Ressource, die nicht vom Cluster verwaltet wird, vorübergehend sein.

**Red Hat Enterprise Linux (RHEL) und Ubuntu**

```bash
sudo pcs resource update <AGResourceName> required_synchronized_secondaries_to_commit=<Value>
```

**SUSE Linux Enterprise Server (SLES)**

```bash
sudo crm resource param ms-<AGResourceName> set required_synchronized_secondaries_to_commit <value>
```

wo *AGResourceName* ist der Name der Ressource für die Verfügbarkeitsgruppe, konfiguriert und *Wert* ist 0, 1 oder 2. Um es wieder auf den Standardwert von Pacemaker verwalten den Parameter festzulegen, führen Sie der gleichen Anweisung ohne Wert.

Automatisches Failover einer Verfügbarkeitsgruppe ist möglich, wenn die folgenden Bedingungen erfüllt sind:

-   Die primäre und das sekundäre Replikat werden zur synchronen datenverschiebung festgelegt.
-   Die sekundäre Datenbank dem Status synchronisiert (nicht synchronisiert), was bedeutet, dass derselbe Zeitpunkt Daten handelt es sich um.
-   Der Typ des Clusters ist auf External festgelegt. Automatisches Failover ist nicht möglich, mit dem Clustertyp None.
-   Die `sequence_number` des sekundären Replikats zu der Primärschlüssel verfügt die höchste Sequenznummer – das heißt, des sekundären Replikats des `sequence_number` entspricht, die über das ursprüngliche primäre Replikat.

Wenn diese Bedingungen erfüllt sind, und der Server, die das primäre Replikat hostet, ein Fehler auftritt, wird in die Verfügbarkeitsgruppe auf ein synchrones Replikat Besitz geändert werden. Das Verhalten für synchronen Replikaten (der es drei stehen gesamt: ein primäres und zwei sekundäre Replikate) können von weiteren gesteuert werden `required_synchronized_secondaries_to_commit`. Dies funktioniert mit Verfügbarkeitsgruppen unter Windows und Linux, aber es ist vollkommen unterschiedlich konfiguriert. Unter Linux wird der Wert automatisch vom Cluster für die AG-Ressource selbst konfiguriert werden.

## <a name="configuration-only-replica-and-quorum"></a>Reine konfigurationsreplikat und quorum

Ebenfalls neu in [!INCLUDE[sssql17-md](../includes/sssql17-md.md)] ab CU1 ist ein reines konfigurationsreplikat Replikat. Da Pacemaker eines WSFC unterscheidet, insbesondere, wenn es um das Quorum und erfordern von STONITH, geht funktioniert mit nur einer Konfiguration mit zwei Knoten nicht bei einer Verfügbarkeitsgruppe. Für eine FCI können die Quorum-Mechanismen von Pacemaker in Ordnung, sein, da alle Vermittlung der FCI-Failover auf den Cluster-Ebene erfolgt. Für eine Verfügbarkeitsgruppe, erfolgt die Vermittlung unter Linux in [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], wobei alle Metadaten gespeichert werden. Dies ist das reine konfigurationsreplikat kommt ins Spiel.

Ohne etwas anderes wäre einem dritten Knoten und mindestens ein synchronisiertes Replikat erforderlich. Dies funktionierte nicht für [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)], da es nur zwei Replikate, die Teil einer Verfügbarkeitsgruppe enthalten kann. Das reine konfigurationsreplikat speichert die Konfiguration der Verfügbarkeitsgruppe, in der master-Datenbank identisch mit den anderen Replikaten in der Konfiguration der Verfügbarkeitsgruppe. Das reine konfigurationsreplikat muss nicht die Benutzerdatenbanken, die in der Verfügbarkeitsgruppe teilnehmen. Die Konfigurationsdaten werden von der primären Datenbank synchron gesendet. Diese Konfigurationsdaten werden, ob sie automatische oder manuelle sind während eines Failovers verwendet.

Für eine Verfügbarkeitsgruppe Quorum beibehalten und automatische Failover mit einem externen Cluster aktivieren müssen sie entweder:

-   Haben Sie drei synchrone Replikaten ([!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)] nur); oder
-   Haben Sie zwei Replikate (Primär und sekundär) als auch in einer reinen konfigurationsreplikat.

Ein manuelles Failover möglich, unabhängig davon, ob extern oder keine Clustertypen für AG-Konfigurationen. Obwohl ein reines konfigurationsreplikat Replikat einer Verfügbarkeitsgruppe konfiguriert werden kann, der einen vom Clustertyp ' None ', ist es nicht empfohlen, da es erschwert, dass die Bereitstellung. Bei Konfigurationen, ändern Sie manuell `required_synchronized_secondaries_to_commit` Wert von mindestens 1 haben, sodass mindestens ein synchronisiertes Replikat vorhanden ist.

Eine reine konfigurationsreplikat kann auf eine beliebige Edition von gehostet werden [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], einschließlich [!INCLUDE[ssexpress-md](../includes/ssexpress-md.md)]. Dies wird minimiert, Lizenzierungskosten und stellt sicher, es funktioniert mit Verfügbarkeitsgruppen in [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)]. Dies bedeutet, dass die dritte erforderliche Server lediglich zum Erfüllen der Mindestanforderungen für [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)], da es keine Transaktion von Benutzerdatenverkehr für die Verfügbarkeitsgruppe empfängt.

Wenn ein reines konfigurationsreplikat Replikat verwendet wird, ist es das folgende Verhalten:

-   In der Standardeinstellung `required_synchronized_secondaries_to_commit` auf 0 festgelegt ist. Dies kann manuell auf 1 geändert werden, falls gewünscht.
-   Wenn die primäre Datenbank ausfällt und `required_synchronized_secondaries_to_commit` gleich 0 ist, das sekundäre Replikat wird zu der neuen primären Datenbank und für Lese- und Schreibvorgänge verfügbar. Wenn der Wert 1 ist, automatisches Failover ausgeführt wird, sondern akzeptiert keine neue Transaktionen aus, bis das andere Replikat online ist.
-   Wenn ein sekundäres Replikat ausfällt und `required_synchronized_secondaries_to_commit` ist 0, das primäre Replikat wird weiterhin Transaktionen akzeptiert, aber wenn die primäre an diesem Punkt fehlschlägt, besteht kein Schutz der Daten noch Failover möglich (manuell oder automatisch), da ein sekundäres Replikat nicht verfügbar ist.
-   Wenn die Replikate nur die Konfiguration ein Fehler auftritt, wird ein ordnungsgemäß für die Verfügbarkeitsgruppe, aber kein automatisches Failover ist möglich.
-   Wenn sowohl ein synchrones sekundäres Replikat als auch das reine konfigurationsreplikat Fehler auftreten, die primäre kann nicht akzeptiert Transaktionen werden und es an keiner Stelle für die primäre auf.

In CU1 besteht ein bekanntes Problem in der Protokollierung in der corosync.log-Datei, die generiert wird, über `mssql-server-ha`. Wenn ein sekundäres Replikat nicht können primären aufgrund der Anzahl der erforderlichen Replikate verfügbar ist, meldet, dass die aktuelle Nachricht "1 Sequenznummern zu empfangen erwartet aber nur 2 empfangen. Nicht genügend Replikate sind online auf sichere Weise das lokale Replikat höher stufen." Die Zahlen sollten rückgängig gemacht werden soll, und es müsste "erwartet 2 Sequenznummern zu empfangen, aber nur 1 empfangen. Nicht genügend Replikate sind online auf sichere Weise das lokale Replikat höher stufen." 

## <a name="multiple-availability-groups"></a>Mehrere Verfügbarkeitsgruppen 

Pro Pacemaker-Clusters oder einer Gruppe von Servern kann mehr als eine Verfügbarkeitsgruppe erstellt werden. Die einzige Einschränkung besteht darin, Systemressourcen beansprucht wird. AG-Besitz wird vom Master angezeigt. Unterschiedliche Verfügbarkeitsgruppen können von verschiedenen Knoten im Besitz sein. Sie müssen nicht alle auf demselben Knoten ausgeführt werden.

## <a name="drive-and-folder-location-for-databases"></a>Laufwerks- und Speicherort für Datenbanken

Die Struktur Laufwerk- und Ordnerpfad für die Benutzerdatenbanken in einer Verfügbarkeitsgruppe teilnehmen sollten identisch sein, wie auf Windows-basierte Verfügbarkeitsgruppen. Wenn die Benutzerdatenbanken in sind z. B. `/var/opt/mssql/userdata` auf Server A, sollte dieser Ordner auf Server b vorhanden sein Die einzige Ausnahme hierbei finden Sie im Abschnitt [Interoperabilität mit Windows-basierte Verfügbarkeitsgruppen und Replikaten](#interoperability-with-windows-based-availability-groups-and-replicas).

## <a name="the-listener-under-linux"></a>Der Listener unter Linux

Der Listener ist die optionale Funktionen für eine Verfügbarkeitsgruppe. Er bietet nur einen Eintrag für alle Verbindungen (Lesen/Schreiben, um das primäre Replikat und/oder schreibgeschützte sekundäre Replikate), damit Anwendungen und Endbenutzern nicht müssen wissen, welcher Server die Daten gehostet wird. In einem WSFC ist dies die Kombination von einer Netzwerknamenressource und einer IP-Adressressource, die dann in AD DS (falls erforderlich) registriert ist und DNS an. In Kombination mit der AG-Ressource selbst wird diese Abstraktion. Weitere Informationen über einen Listener, finden Sie unter [Listener, Clientkonnektivität und Anwendungsfailover](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md).

Der Listener unter Linux ist anders konfiguriert, aber die Funktionalität ist identisch. Es ist kein Konzept für eine Netzwerknamenressource in Pacemaker, noch wird ein Objekt in AD DS erstellt; Es gibt nur eine IP-Adressressource erstellt in Pacemaker, die auf einem Knoten ausgeführt werden kann. Ein Eintrag der IP-Ressource zugeordnet sind, für den Listener in DNS mit dem "Anzeigenamen" muss erstellt werden. Die IP-Adressressource für den Listener werden nur auf dem Server, die das primäre Replikat für diese verfügbarkeitsgruppe hostet.

Wenn Pacemaker verwendet wird, und eine IP-Adressressource wird erstellt, die mit dem Listener verbunden ist, werden ein kurzen Ausfall die IP-Adresse wird auf den Server beendet und gestartet wird, auf dem anderen, ob sie die automatische oder manuelle Failover ist. Während dieser Abstraktion über die Kombination aus einem einzelnen Namen und die IP-Adresse bereitgestellt werden, wird es der Ausfall nicht maskiert. Eine Anwendung muss so behandeln Sie die Trennung der Verbindung müssen eine Art von Funktionalität zu erkennen und erneut eine Verbindung herstellen können.

Allerdings ist die Kombination des DNS-Namen und IP-Adresse noch nicht genug, um die gesamte Funktionalität zu gewährleisten, die ein Listener auf einem WSFC bereitstellt, wie z. B. das schreibgeschützte routing für sekundäre Replikate. Wenn Sie eine Verfügbarkeitsgruppe zu konfigurieren, wird ein "Listener" noch konfiguriert werden muss [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]. Dies kann im Assistenten als auch die Transact-SQL-Syntax angezeigt werden. Es gibt zwei Möglichkeiten, dieses konfiguriert werden kann, wie unter Windows funktioniert:

-   Für eine Verfügbarkeitsgruppe mit dem Clustertyp External, die IP-Adresse verknüpft ist, mit der "Listener" im erstellten [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] sollte die IP-Adresse der Ressource in Pacemaker erstellt werden.
-   Verwenden Sie für eine Verfügbarkeitsgruppe mit dem Clustertyp None erstellt wurde die IP-Adresse, die mit dem primären Replikat verknüpft ist.

Die Instanz, die die angegebene IP-Adresse zugeordnet sind, dann wird der Koordinator für Aufgaben wie das schreibgeschützte routing Anforderungen von Anwendungen.

## <a name="interoperability-with-windows-based-availability-groups-and-replicas"></a>Interoperabilität mit Windows-basierte Verfügbarkeitsgruppen und Replikaten 

Eine Verfügbarkeitsgruppe, die den Clustertyp External oder einem WSFC sind keine Plattformen plattformübergreifende Replikate. Dies ist "true" gibt an, ob die Verfügbarkeitsgruppe [!INCLUDE[ssstandard-md](../includes/ssstandard-md.md)] oder [!INCLUDE[ssenterprise-md](../includes/ssenterprise-md.md)]. Dies bedeutet, dass in einer herkömmlichen verfügbarkeitsgruppenkonfiguration mit einem zugrunde liegenden Cluster, nicht möglich ein Replikat auf einem WSFC und der andere auf Linux mit Pacemaker.

Eine Verfügbarkeitsgruppe mit dem Clustertyp None haben ihre Replikate OS-Grenzen überschreiten, es könnte also sowohl Linux- und Windows-basierte Replikaten in derselben Verfügbarkeitsgruppe. Ein Beispiel ist hier dargestellt, in dem das primäre Replikat ist Windows-basiert, während die sekundäre Datenbank auf einem der Linux-Distributionen ist.

![Hybride keine](./media/sql-server-linux-availability-group-overview/image1.png)

Eine verteilte Verfügbarkeitsgruppe kann auch OS-Grenzen überschreiten. Die zugrunde liegende Verfügbarkeitsgruppen anhand der Regeln gebunden sind, für deren, z. B. eine, bei denen externe Konfiguration nur-Linux-, aber die Verfügbarkeitsgruppe, die sie hinzugefügt wurde mit einem WSFC konfiguriert werden konnte. Betrachten Sie das folgende Beispiel:

![Hybrid-Dist-Verfügbarkeitsgruppe](./media/sql-server-linux-availability-group-overview/image2.png)

<!-- Distributed AGs are also supported for upgrades from [!INCLUDE[sssql15-md](../includes/sssql15-md.md)] to [!INCLUDE[sssql17-md](../includes/sssql17-md.md)]. For more information on how to achieve this, see [the article “x”].

If using automatic seeding with a distributed availability group that crosses OSes, it can handle the differences in folder structure. How this works is described in [the documentation for automatic seeding].
-->
 
## <a name="next-steps"></a>Nächste Schritte
[Konfigurieren von Verfügbarkeitsgruppen für SQL Server unter Linux](sql-server-linux-availability-group-configure-ha.md)

[Konfigurieren von schreibgeschützten Verfügbarkeitsgruppen für SQL Server unter Linux](sql-server-linux-availability-group-configure-rs.md)

[Fügen Sie der verfügbarkeitsgruppe Clusterressource unter RHEL](sql-server-linux-availability-group-cluster-rhel.md)

[Verfügbarkeitsgruppe-Clusterressource auf SLES hinzufügen](sql-server-linux-availability-group-cluster-sles.md)

[Hinzufügen der verfügbarkeitsgruppe Clusterressource unter Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

[Konfigurieren einer plattformübergreifenden verfügbarkeitsgruppe](sql-server-linux-availability-group-cross-platform.md)

