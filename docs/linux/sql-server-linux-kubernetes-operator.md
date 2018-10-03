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
ms.openlocfilehash: f8667c74843ab26b251c5a23a1e93f7f26e72fef
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759358"
---
# <a name="sql-server-always-on-availability-group-kubernetes-operator-parameters"></a>SQL Server Always On Availability Group Kubernetes Operator Parameter

Eine Always On-verfügbarkeitsgruppe auf Kubernetes ist erforderlich, einen Operator. Der Operator wird in einer yaml-Datei beschrieben.  Ein Beispiel der Spezifikation im [in diesem Tutorial](tutorial-sql-server-ag-kubernetes.md).

Dieser Artikel beschreibt die globalen Umgebungsvariablen Operator.

## <a name="example"></a>Beispiel

Das folgende Beispiel beschreibt eine Bereitstellung für die `mssql-operator`.

## <a name="global-environment-variables"></a>Globale Umgebungsvariablen

* `MSSQL_K8S_POD_NAMESPACE` 
  * Required
  * **Beschreibung**: die Kubernetes-Namespace des Operators.

* `MSSQL_K8S_SQL_WRITE_LEASE_PERIOD_SECONDS`
  * Optional
  * **Beschreibung**: die Dauer des externen SQLServer-Lease behalten die SQLServer beschreibbaren und Split-Brain-Szenarien zu verhindern, dass zu schreiben. Sekundäre Replikate ist von dieser Ablauf nach Wahl eine neue übergeordnete Instanz warten.

* `MSSQL_K8S_MONITOR_PERIOD_SECONDS`
  * Optional
  * **Beschreibung**: der Zeitraum zum Überwachen der Status der verfügbarkeitsgruppe. Bestimmt, wie schnell Replikate hinzugefügt und gelöscht werden. Muss kleiner als `MSSQL_K8S_SQL_WRITE_LEASE_PERIOD_SECONDS`.
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
