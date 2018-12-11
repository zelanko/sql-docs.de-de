---
title: Konfigurieren Sie die RHEL-Cluster für SQL Server-Verfügbarkeitsgruppe | Microsoft-Dokumentation
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 06/14/2017
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: b7102919-878b-4c08-a8c3-8500b7b42397
ms.openlocfilehash: ec5ed0ce61c1b1f48ecc148326b9a1906ff95122
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51670819"
---
# <a name="configure-rhel-cluster-for-sql-server-availability-group"></a>Konfigurieren Sie die RHEL-Cluster für SQL Server-Verfügbarkeitsgruppe

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieses Dokument erläutert, wie Sie einen Gruppe-Cluster mit drei Knoten Verfügbarkeit für SQL Server unter Red Hat Enterprise Linux zu erstellen. Für hohe Verfügbarkeit, eine verfügbarkeitsgruppe für Linux erfordert drei Knoten – Siehe [hohe Verfügbarkeit und Datenschutz für verfügbarkeitsgruppenkonfigurationen](sql-server-linux-availability-group-ha.md). Die clustering-Ebene basiert auf Red Hat Enterprise Linux (RHEL) [HA-Add-On](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf) baut auf [Pacemaker](https://clusterlabs.org/). 

> [!NOTE] 
> Zugriff auf die vollständige Dokumentation für Red Hat muss es sich um ein gültiges Abonnement. 

Weitere Informationen zu Clusterkonfiguration, Optionen für Agents und Management finden Sie unter [RHEL-Referenzdokumentation](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html).

> [!NOTE] 
> SQL Server ist mit Pacemaker unter Linux nicht so stark integriert, wie mit Windows Server-Failoverclustering. SQL Server-Instanz ist nicht über den Cluster. Pacemaker ermöglicht eine Cluster-Resource-Orchestrierung. Darüber hinaus Name des virtuellen Netzwerks bezieht sich auf Windows Server Failover-Clusterunterstützung – es gibt keine Entsprechung in Pacemaker. Verfügbarkeit Gruppe dynamische Verwaltungssichten (DMVs), die Clusterinformationen Abfragen geben eine leere Zeilen auf Pacemaker-Cluster zurück. Zum Erstellen eines Listeners für das transparente erneute Verbindung nach einem Failover manuell registrieren der verfügbarkeitsgruppenlistener-Namen im DNS mit der IP-Adresse verwendet, um die virtuelle IP-Ressource zu erstellen. 

Die folgenden Abschnitte führen die Schritte zum Einrichten eines Pacemaker-Clusters ein, und fügen einer verfügbarkeitsgruppe als Ressource im Cluster für hohe Verfügbarkeit.

## <a name="roadmap"></a>Roadmap für die

Die Schritte zum Erstellen einer verfügbarkeitsgruppe auf Linux-Servern für hochverfügbarkeit unterscheiden sich von den Schritten in einem Windows Server-Failovercluster. Die folgende Liste beschreibt die allgemeinen Schritte: 

1. [Konfigurieren von SQL Server auf den Clusterknoten](sql-server-linux-setup.md).

2. [Erstellen der verfügbarkeitsgruppe](sql-server-linux-availability-group-configure-ha.md). 

3. Konfigurieren Sie eine Clusterressourcen-Manager, z.B. Pacemaker. Diese Anweisungen sind in diesem Dokument.
   
   Die Möglichkeit, einen Cluster-Ressourcen-Manager zu konfigurieren, hängt von der jeweilige Linux-Distribution. 

   >[!IMPORTANT]
   >Produktionsumgebungen sind erforderlich, einen umgrenzungs-Agent, wie STONITH für hohe Verfügbarkeit. Die Demos in dieser Dokumentation verwenden keine Umgrenzung-Agents. Die Demos sind für Tests und Überprüfung nur auf. 
   
   >Ein Linux-Cluster verwendet Umgrenzung, um den Cluster in einen bekannten Zustand zurückzugeben. Die Möglichkeit zum Konfigurieren der Umgrenzung hängt davon ab, die Verteilung und der Umgebung. Umgrenzung ist derzeit nicht in eine Cloud-Umgebungen verfügbar. Weitere Informationen finden Sie unter [Supportrichtlinien für RHEL High Availability Cluster - Virtualisierungsplattformen](https://access.redhat.com/articles/29440).

5. [Fügen Sie die verfügbarkeitsgruppe als Ressource im Cluster](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource).  

## <a name="configure-high-availability-for-rhel"></a>Konfigurieren von hochverfügbarkeit für RHEL

Um hochverfügbarkeit für RHEL konfigurieren möchten, aktivieren Sie das Abonnement für die hohe Verfügbarkeit, und konfigurieren Sie Pacemaker.

### <a name="enable-the-high-availability-subscription-for-rhel"></a>Aktivieren Sie die hohe Verfügbarkeit-Abonnement für RHEL

Jeder Knoten im Cluster muss ein entsprechendes Abonnement für RHEL und hoher Verfügbarkeit hinzufügen verfügen. Überprüfen Sie die Anforderungen an [zum Installieren von clusterpakete für hohe Verfügbarkeit in Red Hat Enterprise Linux](https://access.redhat.com/solutions/45930). Um das Abonnement und Repositorys zu konfigurieren, gehen Sie wie folgt vor:

1. Registrieren Sie das System an.

   ```bash
   sudo subscription-manager register
   ```

   Geben Sie Ihren Benutzernamen und Ihr Kennwort ein.   

1. Listet die verfügbare Pools für die Registrierung.

   ```bash
   sudo subscription-manager list --available
   ```

   Beachten Sie die Pool-ID für das Abonnement für die hohe Verfügbarkeit, aus der Liste der verfügbaren Pools.

1. Aktualisieren Sie das folgende Skript ein. Ersetzen Sie dies `<pool id>` mit die Pool-ID für hohe Verfügbarkeit aus dem vorherigen Schritt. Führen Sie das Skript, um das Abonnement anfügen.

   ```bash
   sudo subscription-manager attach --pool=<pool id>
   ```

1. Aktivieren Sie das Repository ein.

   ```bash
   sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
   ```

Weitere Informationen finden Sie unter [Pacemaker – die Open-Source-Cluster mit hoher Verfügbarkeit](https://www.opensourcerers.org/pacemaker-the-open-source-high-availability-cluster/). 

Nachdem Sie das Abonnement konfiguriert haben, führen Sie die folgenden Schritte aus, um Pacemaker zu konfigurieren:

### <a name="configure-pacemaker"></a>Konfigurieren von Pacemaker

Nachdem Sie das Abonnement registriert haben, führen Sie die folgenden Schritte aus, um Pacemaker zu konfigurieren:
   
[!INCLUDE [RHEL-Configure-Pacemaker](../includes/ss-linux-cluster-pacemaker-configure-rhel.md)]

Verwenden Sie nach der Konfiguration Pacemaker `pcs` , mit dem Cluster interagieren. Führen Sie alle Befehle auf einem Knoten aus dem Cluster. 

## <a name="configure-fencing-stonith"></a>Konfigurieren von Umgrenzung (STONITH)

Pacemaker-Clusters Anbieter erfordern STONITH aktiviert werden und ein umgrenzungs-Gerät, das für einen unterstützten Cluster-Setup konfiguriert. STONITH steht für "den anderen Knoten dafür im Kopf". Wenn der Clusterressourcen-Manager den Status eines Knotens oder einer Ressource auf einem Knoten nicht ermitteln kann, bringt jedoch Umgrenzung den Cluster in einen bekannten Zustand wieder.

Ressource Ebene Umgrenzung wird sichergestellt, dass keine datenbeschädigung bei einem Ausfall durch Konfigurieren einer Ressource. Beispielsweise können Sie Ressourcen auf Umgrenzung, markieren Sie den Datenträger auf einem Knoten als veraltete bei die kommunikationsverbindung ausfällt. 

Ebene Umgrenzung Knoten wird sichergestellt, dass alle Ressourcen von ein Knoten nicht ausgeführt werden kann. Dies erfolgt durch das Zurücksetzen des Knotens. Pacemaker unterstützt eine Vielzahl von Geräten für das umgrenzen. Beispiele hierfür sind eine unterbrechungsfreie bereitstellen oder die Verwaltung Netzwerkschnittstellenkarten für Server.

Informationen zu STONITH und Umgrenzung finden Sie unter den folgenden Artikeln:

* [Pacemaker-Cluster von Grund auf neu](https://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html)
* [Umgrenzung und STONITH](https://clusterlabs.org/doc/crm_fencing.html)
* [Red Hat Hochverfügbarkeit-Add-On mit Pacemaker: für das Umgrenzen der](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/ch-fencing-HAAR.html)

Da die Ebene des Knotens für das umgrenzen der Konfiguration in Ihrer Umgebung stark abhängig ist, deaktivieren Sie ihn für dieses Tutorial (sie kann später konfiguriert werden). Das folgende Skript wird die Ebene Umgrenzung Knoten deaktiviert:

```bash
sudo pcs property set stonith-enabled=false
```
  
>[!IMPORTANT]
>Deaktivieren die STONITH ist nur für Testzwecke verwenden. Wenn Sie Pacemaker in einer produktionsumgebung verwenden möchten, sollten Sie eine STONITH-Implementierung planen, je nach Umgebung und behalten sie die Einstellung aktiviert. RHEL bietet keine Umgrenzung-Agents für alle Cloud-Umgebungen (einschließlich Azure) oder Hyper-V. Nichts enthält, bietet der Hersteller der Cluster keine Unterstützung für Produktionscluster in diesen Umgebungen ausgeführt. Wir arbeiten an einer Lösung für diese Lücke zu schließen, die in zukünftigen Versionen zur Verfügung stehen.

## <a name="set-cluster-property-cluster-recheck-interval"></a>Legen Sie die Cluster-Cluster-erneute zugriffsprüfung während-Interval-Eigenschaft

`cluster-recheck-interval` Gibt an, das Abrufintervall auf Änderungen in der Ressourcenparameter, Einschränkungen oder andere Clusteroptionen an dem der Cluster überprüft. Wenn ein Replikat ausfällt, versucht der Cluster, das Replikat in einem Intervall neu zu starten, die gebunden wird, indem die `failure-timeout` Wert und die `cluster-recheck-interval` Wert. Z. B. wenn `failure-timeout` auf 60 Sekunden festgelegt ist und `cluster-recheck-interval` festgelegt ist auf 120 Sekunden, wird versucht, der Neustart in einem Intervall, das mehr als 60 Sekunden, jedoch weniger als 120 Sekunden ist. Es wird empfohlen, dass Sie die Fehler-Timeout 60er-Bereich und die Cluster-erneute zugriffsprüfung während--Intervall auf einen Wert, der größer als 60 Sekunden festlegen. Cluster-erneute zugriffsprüfung während-Intervall auf einen niedrigen Wert festlegen, wird nicht empfohlen.

Aktualisieren Sie den Eigenschaftswert an `2 minutes` ausführen:

```bash
sudo pcs property set cluster-recheck-interval=2min
```

> [!IMPORTANT] 
> Alle Verteilungen (einschließlich RHEL 7.3 und 7.4), mit denen die neuesten verfügbaren Pacemaker Paket 1.1.18-11.el7 führen eine verhaltensänderung für die Start-Fehler-ist--Schwerwiegender Cluster-Einstellung, wenn der Wert "false" ist. Diese Änderung wirkt sich auf die testfailover-Workflow. Wenn ein primäres Replikat ein Ausfall auftritt, wird der Cluster für ein Failover auf eines der sekundären Replikate verfügbar erwartet. Stattdessen sehen Benutzer, dass der Cluster immer wieder versucht, das fehlerhafte primäre Replikat zu starten. Wenn dieser primären (aufgrund von einem dauerhaften Ausfall) nicht online ist, ein Failover des Clusters nicht an ein anderes verfügbares sekundäres Replikat. Aufgrund dieser Änderung eine zuvor empfohlene Konfiguration festzulegende Start Fehler-ist-schwerwiegender ist nicht mehr gültig und die Einstellung muss auf den Standardwert zurückgesetzt werden `true`. Darüber hinaus muss die AG-Ressource aktualisiert werden, enthält die `failover-timeout` Eigenschaft. 

Aktualisieren Sie den Eigenschaftswert an `true` ausführen:

```bash
sudo pcs property set start-failure-is-fatal=true
```

Beim Aktualisieren der `ag1` Ressourceneigenschaft `failure-timeout` zu `60s` ausführen:

```bash
pcs resource update ag1 meta failure-timeout=60s
```


Weitere Informationen zu den Eigenschaften der Pacemaker-Cluster finden Sie unter [Pacemaker-Cluster Eigenschaften](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-clusteropts-HAAR.html).

## <a name="create-a-sql-server-login-for-pacemaker"></a>Erstellen Sie eine SQL Server-Anmeldung für Pacemaker

[!INCLUDE [SQL-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="create-availability-group-resource"></a>Verfügbarkeitsgruppen-Ressource erstellen

Verwenden Sie zum Erstellen der verfügbarkeitsgruppenressource `pcs resource create` -Befehl aus, und legen Sie die Ressourceneigenschaften. Der folgende Befehl erstellt eine `ocf:mssql:ag` Typressource für die verfügbarkeitsgruppe mit dem Namen, Primär-/Sekundärgerät `ag1`.

```bash
sudo pcs resource create ag_cluster ocf:mssql:ag ag_name=ag1 meta failure-timeout=30s master notify=true
``` 

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

<a name="createIP"></a>

## <a name="create-virtual-ip-resource"></a>Erstellen Sie virtuelle IP-Ressource

Um die virtuelle IP-Adressressource zu erstellen, führen Sie den folgenden Befehl auf einem Knoten ein. Verwenden Sie eine verfügbare statische IP-Adresse aus dem Netzwerk. Ersetzen Sie die IP-Adresse zwischen `<10.128.16.240>` mit einer gültigen IP-Adresse.

```bash
sudo pcs resource create virtualip ocf:heartbeat:IPaddr2 ip=<10.128.16.240>
```

Es gibt keinen virtuellen Server-Namen Pacemaker entspricht. Um eine Verbindungszeichenfolge zu verwenden, die auf eine Zeichenfolge den Servernamen anstelle einer IP-Adresse verweist, registrieren Sie die virtuelle IP-Ressource-Adresse und den Namen des gewünschten virtuellen Servers in DNS. Registrieren Sie für DR-Konfigurationen den gewünschten virtuellen Servernamen und die IP-Adresse mit dem DNS-Servern auf primären und DR-Standort aus.

## <a name="add-colocation-constraint"></a>Zusammenstellung-Einschränkung hinzufügen

Fast jeder Entscheidung im eines Pacemaker-Clusters, z. B. auswählen, in dem eine Ressource ausgeführt werden soll, erfolgt durch Vergleichen der Ergebnisse. Ergebnisse werden pro Ressource berechnet. Der Clusterressourcen-Manager wählt den Knoten mit der höchsten Bewertung für eine bestimmte Ressource. Wenn ein Knoten ein negatives Ergebnis für eine Ressource verfügt, kann nicht der Ressource auf diesem Knoten ausgeführt werden.

Klicken Sie auf einen Pacemaker-Cluster können Sie die Entscheidungen des Clusters mit Einschränkungen ändern. Eine Bewertung eine Beschränkung vorliegt. Wenn eine Einschränkung eine Bewertung, die niedriger als verfügt `INFINITY`, Pacemaker betrachtet sie als Empfehlung. Eine Bewertung von `INFINITY` ist obligatorisch.

Definieren Sie eine Zusammenstellung-Einschränkung mit einer Bewertung von UNENDLICH, um sicherzustellen dass das primäre Replikat und die virtuelle IP-Ressourcen auf dem gleichen Host ausgeführt. Um die Zusammenstellung Einschränkung hinzuzufügen, führen Sie den folgenden Befehl auf einem Knoten ein.

```bash
sudo pcs constraint colocation add virtualip ag_cluster-master INFINITY with-rsc-role=Master
```

## <a name="add-ordering-constraint"></a>Sortieren-Einschränkung hinzufügen

Die Zusammenstellung-Einschränkung verfügt über eine implizite Sortierung Einschränkung. Die virtuelle IP-Adressressource verschoben wird, bevor sie die verfügbarkeitsgruppenressource verschoben. Standardmäßig ist die Abfolge der Ereignisse:

1. Benutzerproblemen `pcs resource move` auf dem primären verfügbarkeitsgruppenobjekt von Knoten1 auf Knoten2.
1. Die virtuelle IP-Adressressource, die auf Knoten 1 beendet werden.
1. Die virtuelle IP-Adressressource, die auf Knoten 2 wird gestartet.
  
   >[!NOTE]
   >An diesem Punkt die IP-Adresse temporär verweist auf Knoten 2 während Knoten 2 immer noch ein vor dem Failover ist sekundären. 
   
1. Die verfügbarkeitsgruppe, die auf Knoten 1 primären zum sekundären Standort tiefer gestuft wird.
1. Die auf Knoten 2 sekundären verfügbarkeitsgruppe wird zum primären Replikat höher gestuft. 

Um zu verhindern, dass die IP-Adresse vorübergehend auf den Knoten mit der vor dem Failover sekundären Datenbank verweist, fügen Sie eine Sortierung Einschränkung hinzu. 

Um eine Sortierung Einschränkung hinzuzufügen, führen Sie den folgenden Befehl auf einem Knoten ein:

```bash
sudo pcs constraint order promote ag_cluster-master then start virtualip
```

>[!IMPORTANT]
>Nachdem Sie den Cluster konfigurieren, und fügen Sie als Clusterressource der verfügbarkeitsgruppe hinzu, können Sie Transact-SQL keine für das Failover der verfügbarkeitsgruppenressourcen. Ressourcen für SQL Server-Clusters unter Linux sind nicht so eng mit dem Betriebssystem verknüpft, wie sie auf einem Windows Server Failover Cluster (WSFC) sind. SQL Server-Dienst ist nicht über das Vorhandensein des Clusters. Alle Orchestrierung erfolgt über die Verwaltungstools. In RHEL oder Ubuntu verwenden `pcs` und SLES `crm` Tools. 

Ausführen des manuellen Failovers der verfügbarkeitsgruppe mit `pcs`. Initiieren Sie Failover mit Transact-SQL nicht. Anweisungen hierzu finden Sie unter [Failover](sql-server-linux-availability-group-failover-ha.md#failover).

## <a name="next-steps"></a>Nächste Schritte

[Betreiben von HA-verfügbarkeitsgruppe](sql-server-linux-availability-group-failover-ha.md)
