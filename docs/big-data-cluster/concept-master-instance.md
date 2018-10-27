---
title: Was ist, dass die SQL Server-big Data-Cluster master-Instanz? | Microsoft-Dokumentation
description: Dieser Artikel beschreibt die Masterinstanz in einer SQL Server-2019 big Data-Cluster.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 7c58d925e9d52ee4496f8a324eab91bbfa7ccaad
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50051062"
---
# <a name="what-is-the-sql-server-big-data-cluster-master-instance"></a>Was ist, dass großen SQL Server-Daten cluster Masterinstanz?

Dieser Artikel beschreibt die Rolle der *SQL Server-Masterinstanz* in einem SQL Server-2019 big Ata-Cluster. Die master-Instanz ist eine SQL Server-Instanz, die in einer SQL Server-big Data-Cluster ausgeführt [Steuerungsebene](big-data-cluster-overview.md#controlplane).

Die SQL Server-Masterinstanz bietet die folgenden Funktionen:

## <a name="connectivity"></a>Connectivity

Master SQL Server-Instanz wird ein extern zugänglichen TDS-Endpunkt für den Cluster. Sie können Anwendungen oder SQL Server-Tools wie Azure Data Studio verbinden, oder SQL Server Management Studio an diesen Endpunkt wie würden jede andere SQL Server-Instanz.

## <a name="scale-out-query-management"></a>Verwaltung von hochskalierungsabfragen

Master SQL Server-Instanz enthält, die horizontale Skalierung-Abfrage-Engine, die verwendet wird, um Abfragen zu SQL Server-Instanzen auf Knoten im Verteilen der [compute Pool](concept-compute-pool.md). Die horizontale Skalierung-Abfrage-Engine bietet auch Zugriff über Transact-SQL auf alle Hive-Tabellen im Cluster ohne zusätzliche Konfiguration. (Unterstützung für Hive-Tabellen ist nicht in CTP 2.0)

## <a name="metadata-and-user-databases"></a>Metadaten und Benutzerdatenbanken

Zusätzlich zu den standardmäßigen SQL Server-Systemdatenbanken enthält die master-SQL-Instanz auch Folgendes:

- Eine metadatendatenbank, die HDFS-Tabellenmetadaten enthält.
- Eine Ebene-Shard-Zuordnung
- Details der externen Tabellen, die Zugriff auf die Datenebene für den Cluster bereitstellen.
- PolyBase, externe Datenquellen und externe Tabellen, die in den Benutzerdatenbanken definiert.

Sie können auch Ihre eigenen Benutzerdatenbanken master SQL Server-Instanz hinzufügen.

## <a name="machine-learning-services"></a>Machine Learning-Dienste

SQL Server-Machine learning-Dienste ist ein Add-On-Feature der Datenbank-Engine, die zum Ausführen von Java, R und Python-Code in SQL Server verwendet. Dieses Feature basiert auf dem SQL Server Extensibility Framework, die isoliert von externer Prozessen von der Kern-Engine-Prozesse, aber die vollständige Integration mit relationalen Daten als gespeicherte Prozeduren, wie T-SQL-Skript, R oder Python-Anweisungen enthält, oder als Java, R oder T-SQL mit Python-Code.

Als Teil einer SQL Server-big Data-Cluster stehen Machine Learning-Dienste für die master Serevr für SQL-Instanz in der Standardeinstellung. Dies bedeutet, dass nach der Ausführung des externen Skripts für die master SQL Server-Instanz aktiviert ist, es ist möglich, Java, R- und Python-Skripts, die mithilfe von Sp_execute_external_script auszuführen ist.

### <a name="advantages-of-machine-learning-services-in-a-big-data-cluster"></a>Vorteile von Machine Learning-Dienste in einer big Data-cluster

SQL Server-2019 erleichtert für big Data mit verknüpft die Dimensionsdaten in der Regel in der Enterprise-Datenbank gespeichert werden. Der Wert der big Data wird erheblich erhöht, ist nicht nur in den Händen von Teilen einer Organisation, jedoch ist auch in Berichten, Dashboards und -Anwendungen enthalten. Datenanalysten können weiterhin zur gleichen Zeit, zu verwenden, die Spark/HDFS-ökosystemtools einfach und Real-Time-Zugriff auf die Daten in der master-SQL Server-Instanz und in externen Datenquellen zugegriffen werden kann _über_ der SQL Server-Master -Instanz.

SQL Server-2019 big Data-Cluster können Sie mehr erreichen mit Ihrem Enterprise Data Lakes. SQL Server-Entwickler und Wirtschaftsanalytiker können Aktionen ausführen:

* Erstellen Sie Anwendungen, die Nutzung von Daten aus Enterprise Data Lakes.
* Der Grund für alle Daten mit Transact-SQL-Abfragen.
* Verwenden Sie die vorhandene Ökosystem aus SQL Server-Tools und Anwendungen aufrufen und Analysieren von Daten des Unternehmens ein.
* Reduzieren Sie den Bedarf für die datenverschiebung durch Virtualisieren und Datamarts.
* Verwenden von Spark für big Data-Szenarien weiterhin.
* Erstellen Sie intelligenter Anwendungen, die mithilfe von Spark oder SQL Server zum Trainieren von Modellen über Data Lakes.
* Operationalisieren von Modellen in den Produktionsdatenbanken für eine optimale Leistung.
* Stream-Daten direkt in der Enterprise Datamarts für die Analyse in Echtzeit.
* Untersuchen Sie Daten visuell mit interaktive Analyse und BI-Tools.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den SQL Server-big Data-Clustern finden Sie unter der Übersicht über die folgenden:

- [Was sind SQL Server-2019 big Data-Cluster?](big-data-cluster-overview.md)
