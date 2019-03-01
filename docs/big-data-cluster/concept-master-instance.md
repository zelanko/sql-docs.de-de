---
title: Was ist der Masterinstanz?
titleSuffix: SQL Server 2019 big data clusters
description: Dieser Artikel beschreibt die SQL Server-Masterinstanz in einer SQL Server-2019 big Data-Cluster (Vorschau).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: 67109dc6af3c03960435116c79e9f92ae79f595c
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017796"
---
# <a name="what-is-the-master-instance-in-a-sql-server-2019-big-data-cluster"></a>Was ist die Masterinstanz in einer SQL Server-2019 big Data-Cluster?

Dieser Artikel beschreibt die Rolle der *SQL Server-Masterinstanz* in einer SQL Server-2019 big Data-Cluster. Die master-Instanz ist eine SQL Server-Instanz, die in einer SQL Server-big Data-Cluster ausgeführt [Steuerungsebene](big-data-cluster-overview.md#controlplane).

Die SQL Server-Masterinstanz bietet die folgenden Funktionen:

## <a name="connectivity"></a>Connectivity

Master SQL Server-Instanz wird ein extern zugänglichen TDS-Endpunkt für den Cluster. Sie können Anwendungen oder SQL Server-Tools wie Azure Data Studio verbinden, oder SQL Server Management Studio an diesen Endpunkt wie würden jede andere SQL Server-Instanz.

## <a name="scale-out-query-management"></a>Verwaltung von hochskalierungsabfragen

Master SQL Server-Instanz enthält, die horizontale Skalierung-Abfrage-Engine, die verwendet wird, um Abfragen zu SQL Server-Instanzen auf Knoten im Verteilen der [compute Pool](concept-compute-pool.md). Die horizontale Skalierung-Abfrage-Engine bietet auch Zugriff über Transact-SQL auf alle Hive-Tabellen im Cluster ohne zusätzliche Konfiguration. (Unterstützung für Hive-Tabellen ist nicht in CTP 2.3)

## <a name="metadata-and-user-databases"></a>Metadaten und Benutzerdatenbanken

Zusätzlich zu den standardmäßigen SQL Server-Systemdatenbanken enthält die master-SQL-Instanz auch Folgendes:

- Eine metadatendatenbank, die HDFS-Tabellenmetadaten enthält.
- Eine Ebene-Shard-Zuordnung
- Details der externen Tabellen, die Zugriff auf die Datenebene für den Cluster bereitstellen.
- PolyBase, externe Datenquellen und externe Tabellen, die in den Benutzerdatenbanken definiert.

Sie können auch Ihre eigenen Benutzerdatenbanken master SQL Server-Instanz hinzufügen.

## <a name="machine-learning-services"></a>Machine Learning-Dienste

SQL Server-Machine learning-Dienste ist ein Add-On-Feature der Datenbank-Engine, die zum Ausführen von Java, R und Python-Code in SQL Server verwendet. Dieses Feature basiert auf dem SQL Server Extensibility Framework, die isoliert von externer Prozessen von der Kern-Engine-Prozesse, aber die vollständige Integration mit relationalen Daten als gespeicherte Prozeduren, wie T-SQL-Skript, R oder Python-Anweisungen enthält, oder als Java, R oder T-SQL mit Python-Code.

Als Teil einer SQL Server-big Data-Cluster stehen Machine Learning-Dienste für die master SQL Server-Instanz in der Standardeinstellung. Dies bedeutet, dass nach der Ausführung des externen Skripts für die master SQL Server-Instanz aktiviert ist, es ist möglich, Java, R- und Python-Skripts, die mithilfe von Sp_execute_external_script auszuführen ist.

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
