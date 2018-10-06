---
title: SQL Server Always On Availability Group Kubernetes Operator globale Anforderungen
description: In diesem Artikel werden die Parameter für die SQL Server Kubernetes Always On Availability Group-Operator globale Anforderungen erläutert.
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 187517c79f14ddcbf08ffa644e65558fa0a85b38
ms.sourcegitcommit: 4832ae7557a142f361fbf0a4e2d85945dbf8fff6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/03/2018
ms.locfileid: "48251998"
---
# <a name="sql-server-always-on-availability-group-kubernetes-operator-parameters"></a>SQL Server Always On Availability Group Kubernetes Operator Parameter

Eine Always On-verfügbarkeitsgruppe auf Kubernetes ist erforderlich, einen Operator. Ein Manifest beschreibt den Operator. Das Manifest ist eine `.yaml` Datei. Ein Beispiel der Spezifikation im [Always On-Verfügbarkeitsgruppen für SQL Server-Containern](sql-server-ag-kubernetes.md).

Dieser Artikel beschreibt die globalen Umgebungsvariablen Operator.

## <a name="example"></a>Beispiel

Das folgende Beispiel beschreibt eine Bereitstellung für die `mssql-operator`.

## <a name="global-environment-variables"></a>Globale Umgebungsvariablen

* `MSSQL_K8S_POD_NAMESPACE` 
  * Required
  * **Beschreibung**: die Kubernetes-Namespace des Operators.

* `MSSQL_K8S_SQL_WRITE_LEASE_PERIOD_SECONDS`
  * Optional
  * **Beschreibung**: die Dauer der Schreibzugriff für die Sql Server-Lease. Zum Beibehalten der Sql Servers beschreibbaren und Split-Brain-Szenarien zu verhindern, dass verwendet. Sekundäre Replikate warten Sie auf diese Anzahl von Sekunden, nachdem Sie eine neue übergeordnete Instanz ausgewählt haben.

* `MSSQL_K8S_MONITOR_PERIOD_SECONDS`
  * Optional
  * **Beschreibung**: der Zeitraum zum Überwachen des Status der verfügbarkeitsgruppe. Bestimmt, wie schnell Replikate hinzugefügt und gelöscht werden. Muss kleiner als `MSSQL_K8S_SQL_WRITE_LEASE_PERIOD_SECONDS`.
  * **Standard**: 1

* `MSSQL_K8S_LEASE_DURATION_SECONDS`
  * Optional
  * **Beschreibung**: Dauer der Availability Group Leader Lease. Bestimmt, wie lange die sekundären Replikate gewartet wird, bevor Sie erneut auf die Wahl, wenn das primäre Replikat ist abgestürzt. Dies ist anders als schreiblease für SQL Server. 
  * **Standard**: 10
  
  >[!NOTE]
  >Andere Einstellungen automatisch berechnet, basierend auf `MSSQL_K8S_LEASE_DURATION_SECONDS`.

* `MSSQL_K8S_RENEW_DEADLINE_SECONDS`
  * Optional
  * **Beschreibung**: Dauer, die das primäre Replikat fungiert aktualisiert Leadership wiederholt, bevor aufgegeben wird. Muss kleiner als `MSSQL_K8S_LEASE_DURATION_SECONDS`.
  * **Standard**:  `MSSQL_K8S_LEASE_DURATION_SECONDS` /2

* `MSSQL_K8S_RETRY_PERIOD_SECONDS`
  * Optional
  * **Beschreibung**: Dauer der agierende [master](http://kubernetes.io/docs/concepts/architecture/master-node-communication/) wartet, bevor die übergeordnete Instanz Lease erneuern. Muss kleiner als `MSSQL_K8S_LEASE_DURATION_SECONDS`.
  * **Standard**:  `MSSQL_K8S_RENEW_DEADLINE_SECONDS` /2

* `MSSQL_K8S_ACQUIRE_PERIOD_SECONDS` 
  * Optional
  * **Beschreibung**: Zeitraum, in dem sekundäre Replikate abrufen, wenn die übergeordnete Instanz Lease abgelaufen ist. 
  * **Standard**: 1


  ## <a name="next-steps"></a>Nächste Schritte

[SQL Server-verfügbarkeitsgruppe in Kubernetes-cluster](sql-server-ag-kubernetes.md)
