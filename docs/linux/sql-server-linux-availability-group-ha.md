---
title: SQL Server Always On Availability Group-Bereitstellungsmuster | Microsoft-Dokumentation
ms.custom: sql-linux
ms.date: 10/16/2017
ms.prod: sql
ms.component: ''
ms.reviewer: ''
ms.suite: sql
ms.technology: linux
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: edd75f68-dc62-4479-a596-57ce8ad632e5
caps.latest.revision: 34
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c37cba83ebea7fbced662c3e909ee4007f57225f
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39084662"
---
# <a name="high-availability-and-data-protection-for-availability-group-configurations"></a>Hohe Verfügbarkeit und Datenschutz für die Konfigurationen von Verfügbarkeitsgruppen

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Dieser Artikel stellt unterstützte Bereitstellungskonfigurationen für SQL Server Always On-Verfügbarkeitsgruppen auf Linux-Servern. Eine verfügbarkeitsgruppe unterstützt hohe Verfügbarkeit und Schutz von Daten. Bieten hochverfügbarkeit, automatische fehlererkennung, automatisches Failover und transparente verbindungswiederherstellung nach dem Failover. Synchronisierte Replikate Geben Sie den Schutz von Daten. 

Auf einem Windows Server Failover Cluster (WSFC) verwendet eine gemeinsame Konfiguration für hohe Verfügbarkeit, zwei synchronen Replikaten und einen dritten Server oder eine Dateifreigabe wird, um Quorum bereitzustellen. Den Dateifreigabenzeugen überprüft die Konfiguration der verfügbarkeitsgruppe – Status der Synchronisierung und die Rolle des Replikats, zum Beispiel. Diese Konfiguration wird sichergestellt, dass das sekundäre Replikat als Ziel für das Failover die neuesten Daten und Änderungen an der Konfiguration von Verfügbarkeitsgruppen-Gruppe wurde ausgewählt. 

Der WSFC synchronisiert die Konfigurationsmetadaten für Failover-Vermittlung zwischen die Replikate der verfügbarkeitsgruppe und den Dateifreigabenzeugen. Wenn eine verfügbarkeitsgruppe nicht auf einem WSFC ist, speichern SQL Server-Instanzen Konfigurationsmetadaten in der master-Datenbank.

Eine verfügbarkeitsgruppe auf einem Linux-Cluster enthält beispielsweise `CLUSTER_TYPE = EXTERNAL`. Es gibt keine WSFC Failover vermitteln konnte. In diesem Fall wird die Konfigurationsmetadaten verwaltet und von SQL Server-Instanz verwaltet wird. Da in diesem Cluster keine Dateifreigabenzeugen-Server vorhanden ist, muss eine dritte SQL Server-Instanz zum Konfigurationsmetadaten-Zustand zu speichern. Alle drei SQL Server-Instanzen bieten zusammen verteilte Metadatenspeicher für den Cluster. 

Der Cluster-Manager können Sie Abfragen von SQL Server-Instanzen in der verfügbarkeitsgruppe und orchestriert Failover aus, um hochverfügbarkeit zu gewährleisten. In einem Linux-Cluster ist Pacemaker der Clustermanager. 

SQL Server 2017 CU 1 ermöglicht hohen Verfügbarkeit für eine verfügbarkeitsgruppe mit `CLUSTER_TYPE = EXTERNAL` für zwei synchronen Replikaten sowie einen reinen konfigurationsreplikat. Die reinen konfigurationsreplikat kann auf einer beliebigen Edition von SQL Server 2017 CU1 oder höher – einschließlich SQL Server Express Edition gehostet werden. Die reinen konfigurationsreplikat enthält verwaltet die Konfigurationsinformationen für die verfügbarkeitsgruppe in der master-Datenbank jedoch keine Benutzerdatenbanken in der verfügbarkeitsgruppe. 

## <a name="how-the-configuration-affects-default-resource-settings"></a>Auswirkungen von Standardeinstellungen für die Ressource in die Konfiguration

SQL Server 2017 führt die `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` clusterressourceneinstellung ist. Diese Einstellung garantiert der angegebene Anzahl der sekundären Replikate die Transaktionsdaten anmelden, bevor das primäre Replikat jeder Transaktion ein Commit ausgeführt. Wenn Sie einen externen Cluster-Manager verwenden, wirkt sich diese Einstellung auf hohe Verfügbarkeit und Schutz von Daten aus. Der Standardwert für die Einstellung hängt von der Architektur zu dem Zeitpunkt, der die Clusterressource erstellt wurde. Bei der Installation der SQL Server-Ressourcen-Agent - `mssql-server-ha` - und eine Clusterressource für die verfügbarkeitsgruppe erstellen, wird der Clustermanager erkennt die Verfügbarkeit gruppieren, Konfiguration und legt `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` entsprechend. 

Wenn von der Konfiguration der Ressourcen-Agent-Parameter unterstützt `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` festgelegt ist, auf den Wert an, die hohe Verfügbarkeit und Datenschutz bietet. Weitere Informationen finden Sie unter [verstehen von SQL Server-Ressourcen-Agent für Pacemaker](#pacemakerNotify).

In den folgenden Abschnitten wird erläutert, das Standardverhalten für die Clusterressource. 

Wählen Sie ein Entwurfs von Verfügbarkeit auf bestimmte unternehmensanforderungen für hohe Verfügbarkeit, den Schutz von Daten und für die leseskalierung.

Die folgenden Konfigurationen werden die Availability Group-Entwurfsmuster und die Funktionen der einzelnen Muster beschrieben. Diese Muster gelten für Verfügbarkeitsgruppen mit `CLUSTER_TYPE = EXTERNAL` für Lösungen mit hoher Verfügbarkeit. 

- **Drei synchroner Replikate**
- **Zwei synchrone Replikate**
- **Zwei synchronen Replikaten und einer reinen konfigurationsreplikat**

<a name="threeSynch"></a>

## <a name="three-synchronous-replicas"></a>Drei synchronen Replikaten

Diese Konfiguration besteht aus drei synchronen Replikaten. Standardmäßig wird eine hohe Verfügbarkeit und Datenschutz. Sie können auch schreibgeschützte horizontale Skalierung bereitstellen.

![Drei Replikate][3]

Eine verfügbarkeitsgruppe mit drei synchrone Replikate kann schreibgeschützte horizontale Skalierung, hohe Verfügbarkeit und Schutz von Daten bereitstellen. In der folgende Tabelle wird die Verfügbarkeit Verhalten beschrieben. 

| |schreibgeschützte horizontale Skalierung|Hohe Verfügbarkeit & </br> Datenschutz | Schutz von Daten
|:---|---|---|---
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 |1<sup>*</sup>|2
|Ausfall des primären Replikats | Manuelles Failover. Möglicherweise kommt es zu Datenverlusten. Neues primäres Replikat ist R / w. |Automatisches Failover. Neues primäres Replikat ist R / w. |Automatisches Failover. Neue primäre Replikat ist nicht verfügbar für Transaktionen, bis die vorherigen primären wiederhergestellt und verknüpft die verfügbarkeitsgruppe als sekundär. 
|Ausfall eines sekundären Replikats  | Primäre ist R / w. Kein automatisches Failover, wenn die primäre Datenbank ausfällt. |Primäre ist R / w. Kein automatisches Failover, wenn das primäre schlägt auch fehl. | Primäre ist nicht verfügbar, für Transaktionen. 
<sup>*</sup> Standardwert

<a name="twoSynch"></a>

## <a name="two-synchronous-replicas"></a>Zwei synchrone Replikate

Diese Konfiguration ermöglicht den Schutz von Daten. Wie die anderen Konfigurationen von Verfügbarkeitsgruppen können sie schreibgeschützte horizontale Skalierung aktivieren. Die Konfiguration von zwei synchronen Replikaten bietet keine automatische hochverfügbarkeit. 

![Zwei synchrone Replikate][1]

Eine verfügbarkeitsgruppe mit zwei synchronen Replikaten enthält die schreibgeschützte horizontale Skalierung und den Datenschutz. In der folgende Tabelle wird die Verfügbarkeit Verhalten beschrieben. 

| |schreibgeschützte horizontale Skalierung |Schutz von Daten
|:---|---|---
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 <sup>*</sup>|1
|Ausfall des primären Replikats | Manuelles Failover. Möglicherweise kommt es zu Datenverlusten. Neues primäres Replikat ist R / w.| Automatisches Failover. Neue primäre Replikat ist nicht verfügbar für Transaktionen, bis die vorherigen primären wiederhergestellt und verknüpft die verfügbarkeitsgruppe als sekundär.
|Ausfall eines sekundären Replikats  |Die primäre ist R/W, mit Gefahr von Datenverlusten. |Primäre steht nicht für Transaktionen bis das sekundäre wiederhergestellt.
<sup>*</sup> Standardwert

>[!NOTE]
>Das oben beschriebene Szenario ist das Verhalten vor SQL Server 2017 CU 1. 

<a name = "configOnly"></a>

## <a name="two-synchronous-replicas-and-a-configuration-only-replica"></a>Zwei synchronen Replikaten und einer reinen konfigurationsreplikat

Eine verfügbarkeitsgruppe mit zwei (oder mehr) einen synchronen Replikaten und einer reinen konfigurationsreplikat Datenschutz bietet und möglicherweise auch hohen Verfügbarkeit. Im folgenden Diagramm dargestellt, diese Architektur:

![Konfiguration nur der verfügbarkeitsgruppe][2]

1. Synchrone Replikation von Daten des Benutzers an das sekundäre Replikat. Darüber hinaus Konfigurationsmetadaten von Verfügbarkeitsgruppen.
2. Synchrone Replikation von Konfigurationsmetadaten von Verfügbarkeitsgruppen. Er umfasst keine Benutzerdaten.

Im Diagramm Gruppe Verfügbarkeit überträgt ein primäres Replikat Konfigurationsdaten auf dem reinen konfigurationsreplikat und das sekundäre Replikat. Das sekundäre Replikat empfängt auch die Daten des Benutzers. Die reinen konfigurationsreplikat erhält keine Benutzerdaten. Das sekundäre Replikat ist im Verfügbarkeitsmodus für synchrone. Die reinen konfigurationsreplikat enthält keine Datenbanken in der verfügbarkeitsgruppe – nur die Metadaten zur verfügbarkeitsgruppe. Konfigurationsdaten auf dem reinen konfigurationsreplikat ist synchron ein Commit ausgeführt.

>[!NOTE]
>Eine Availabilility-Gruppe mit reinen konfigurationsreplikat ist neu in SQL Server 2017 CU1. Alle Instanzen von SQL Server in der verfügbarkeitsgruppe muss SQL Server 2017 CU1 oder höher. 

Der Standardwert für `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` ist 0. In der folgende Tabelle wird die Verfügbarkeit Verhalten beschrieben. 

| |Hohe Verfügbarkeit & </br> Datenschutz | Schutz von Daten
|:---|---|---
|`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT=`|0 <sup>*</sup>|1
|Ausfall des primären Replikats | Automatisches Failover. Neues primäres Replikat ist R / w. | Automatisches Failover. Neue primäre Replikat ist nicht verfügbar, für Transaktionen. 
|Ausfall des sekundären Replikats | Primäre Replikat ist R/W, mit Gefahr von Datenverlust (wenn primäre schlägt fehl und kann nicht wiederhergestellt werden). Kein automatisches Failover, wenn das primäre schlägt auch fehl. | Primäre ist nicht verfügbar, für Transaktionen. Kein für den Failover zu durchführen, wenn das primäre Replikat schlägt auch fehl. 
|Konfiguration nur Replikat Ausfall | Primäre ist R / w. Kein automatisches Failover, wenn das primäre schlägt auch fehl. | Primäre ist R / w. Kein automatisches Failover, wenn das primäre schlägt auch fehl. 
|Synchronen sekundären Replikat + -Konfiguration nur Replikat Ausfall| Primäre ist nicht verfügbar, für Transaktionen. Kein automatisches Failover. | Primäre ist nicht verfügbar, für Transaktionen. Kein Replikat für ein Failover auf, wenn auch die primären fehlschlägt. 
<sup>*</sup> Standardwert

>[!NOTE]
>Die Instanz von SQL Server, dem reinen konfigurationsreplikat hostet, kann auch andere Datenbanken hosten. Sie können auch als eine einzige Konfigurationsdatenbank für mehr als eine verfügbarkeitsgruppe teilnehmen. 

## <a name="requirements"></a>Anforderungen

* Alle Replikate in einer verfügbarkeitsgruppe mit einer reinen konfigurationsreplikat müssen SQL Server 2017 CU 1 oder höher sein.
* Eine beliebige Edition von SQL Server kann es sich um einen reinen konfigurationsreplikat, einschließlich SQL Server Express hosten. 
* Die verfügbarkeitsgruppe benötigt mindestens ein sekundäres Replikat – zusätzlich zu das primäre Replikat.
* Konfiguration nur Replikate werden für die maximale Anzahl von Replikaten pro Instanz von SQL Server nicht berücksichtigt. SQL Server standard Edition kann bis zu drei Replikate, SQL Server Enterprise Edition können bis zu 9.

## <a name="considerations"></a>Weitere Überlegungen

* Nicht mehr als einen reinen konfigurationsreplikat pro verfügbarkeitsgruppe. 
* Einen reinen konfigurationsreplikat darf nicht über ein primäres Replikat sein.
* Den Verfügbarkeitsmodus des reinen konfigurationsreplikat kann nicht geändert werden. Um von einem reinen konfigurationsreplikat an ein sekundäres Replikat für synchrone oder asynchrone ändern möchten, entfernen Sie die reinen konfigurationsreplikat und Hinzufügen eines sekundären Replikats mit den erforderlichen Verfügbarkeitsmodus. 
* Einen reinen konfigurationsreplikat ist synchron Metadaten der verfügbarkeitsgruppe. Es sind keine Benutzerdaten. 
* Eine verfügbarkeitsgruppe mit einem primären Replikat und einem reinen konfigurationsreplikat, aber kein sekundäres Replikat ist ungültig. 
* Das Erstellen einer verfügbarkeitsgruppe auf einer Instanz von SQL Server Express Edition ist nicht möglich. 

<a name="pacemakerNotify"></a>

## <a name="understand-sql-server-resource-agent-for-pacemaker"></a>Verstehen von SQL Server-Ressourcen-Agent für pacemaker

SQL Server 2017 CTP 1.4 hinzugefügt `sequence_number` zu `sys.availability_groups` Pacemaker wie aktuell sekundäre identifizieren können Replikate, die mit dem primären Replikat sind. `sequence_number` ist ein monoton ansteigender bigint-DATENTYP, der wie aktuell das lokale verfügbarkeitsgruppenreplikat darstellt. Pacemaker-Updates der `sequence_number` mit jeder konfigurationsänderung des Availability-Gruppe. Beispiele für Änderungen an der Konfiguration sind Failover, Replikat hinzufügen oder entfernen. Die Zahl wird auf dem primären Replikat aktualisiert, anschließend an sekundäre Replikate repliziert. Daher muss ein sekundäres Replikat, das der aktuellen Konfiguration hat die gleiche Sequenznummer wie die primäre Datenbank. 

Wenn Pacemaker entscheidet, ein Replikat zum primären heraufzustufen, sendet er zuerst eine *heraufstufen* Benachrichtigung an alle Replikate. Die Replikate zurück, die Sequenznummer. Als Nächstes beim Pacemaker tatsächlich versucht, ein Replikat zum primären heraufzustufen, stuft das Replikat nur selbst wenn seine Sequenznummer die höchste die Sequenznummern ist. Wenn Sie eine eigene Sequenznummer die höchste Sequenznummer nicht übereinstimmt, lehnt das Replikat die heraufstufung ab. Auf diese Weise kann nur das Replikat mit der höchsten Sequenznummer zu einem primären heraufgestuft werden, sodass es nicht zu Datenverlust kommt. 

Dieser Prozess erfordert mindestens ein Replikat verfügbar, für die heraufstufung mit der gleichen Sequenznummer wie das bisherige primäre. Die Pacemaker-Agent-Ressourcensätzen `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` so, dass mindestens ein sekundäres Replikat ist, auf dem neuesten Stand und das Ziel in der Standardeinstellung ein automatisches Failover zur Verfügung. Mit jeder Überwachungsaktion wird der Wert des `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` berechnet (und aktualisiert werden, falls erforderlich). Die `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` Wert ist "Anzahl der synchronen Replikate" geteilt durch 2. Zeitpunkt des Failovers erfordert der Ressourcen-Agent (`total number of replicas`  -  `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` Replikate), reagiert die Vorabbenachrichtigung. Das Replikat mit der höchsten `sequence_number` zum primären heraufgestuft wird. 

Z. B. eine verfügbarkeitsgruppe mit drei synchronen Replikaten: ein primäres Replikat und zwei synchrone sekundäre Replikate.

- `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` ist 1. (3 / 2-1 >).

- Die erforderliche Anzahl von Replikaten auf berührungen reagieren Vorabbenachrichtigung ist 2. (3 – 1 = 2). 

In diesem Szenario haben zwei Replikate für das Failover ausgelöst werden zu reagieren. Für eine erfolgreiche automatische testfailover nach einem Ausfall des primären Replikats, beide sekundären Replikate müssen auf dem neuesten Stand und reagieren auf die Vorabbenachrichtigung. Wenn sie online und synchron sind, haben sie die gleiche Sequenznummer. Die verfügbarkeitsgruppe wird eine davon. Wenn nur einer der sekundären Replikate, reagiert das Heraufstufen, der Ressourcen-Agent kann nicht garantieren, dass das sekundäre Replikat, das geantwortet die höchste Sequence_number hat, und ein Failover wird nicht ausgelöst.

>[!IMPORTANT]
>Wenn `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` 0 (null) entspricht, besteht das Risiko von Datenverlust. Bei einem Ausfall des primären Replikats ist der Ressourcen-Agent nicht automatisch ein Failover auslösen. Sie können entweder warten, bis vom primären zum Wiederherstellen oder Ausführen des manuellen Failovers mit `FORCE_FAILOVER_ALLOW_DATA_LOSS`.

Sie können das Standardverhalten außer Kraft setzen und verhindern, dass die verfügbarkeitsgruppenressource Einstellung `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` automatisch.

Das folgende Skript legt `REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` auf 0 für eine verfügbarkeitsgruppe mit dem Namen `<**ag1**>`. Ersetzen Sie `<**ag1**>` vor der Ausführung durch den Namen der Verfügbarkeitsgruppe.

```bash
sudo pcs resource update <**ag1**> required_synchronized_secondaries_to_commit=0
```

Wieder in den Standardwert, basierend auf der Konfiguration der verfügbarkeitsgruppe ausführen:

```bash
sudo pcs resource update <**ag1**> required_synchronized_secondaries_to_commit=
```

>[!NOTE]
>Wenn Sie die vorherigen Befehle ausführen, wird das primäre vorübergehend zum sekundären Standort, herabgestuft, klicken Sie dann erneut heraufgestuft. Das Update der Ressource bewirkt, dass alle Replikate beendet und neu gestartet wird. Der neue Wert für`REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT` wird nur festgelegt werden, sobald die Replikate neu gestartet werden, nicht sofort.

## <a name="see-also"></a>Siehe auch

[Verfügbarkeitsgruppen unter Linux](sql-server-linux-availability-group-overview.md)

<!--Image references-->
[1]: ./media/sql-server-linux-availability-group-ha/1-read-scale-out.png
[2]: ./media/sql-server-linux-availability-group-ha/2-configuration-only.png
[3]: ./media/sql-server-linux-availability-group-ha/3-three-replica.png
[4]: ./media/sql-server-linux-availability-group-ha/configuration-only-example.png
