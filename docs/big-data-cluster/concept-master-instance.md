---
title: Was ist die Masterinstanz?
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird die SQL Server-Masterinstanz in einem Big Data-Cluster für SQL Server 2019 (Vorschau) beschrieben.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d62b1fe82698ff8722786b42f534afe83cd6c481
ms.sourcegitcommit: 2604e13627fbc9f3bda3926b67045fceb7b04e37
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822694"
---
# <a name="what-is-the-master-instance-in-a-sql-server-big-data-cluster"></a>Was ist die Masterinstanz in einem SQL Server-Big Data Cluster?

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird die Rolle der *SQL Server Master Instanz* in einem Big Data Cluster für SQL Server 2019 beschrieben. Die Master Instanz ist eine SQL Server-Instanz, die in einem Big Data Cluster ausgeführt wird, um Konnektivität, horizontal hochskalierbare Abfragen, Metadaten und Benutzer Datenbanken sowie Machine Learning-Dienste zu verwalten.

Die SQL Server-Masterinstanz bietet folgende Funktionen:

## <a name="connectivity"></a>Connectivity

Die SQL Server-Masterinstanz stellt einen extern erreichbaren TDS-Endpunkt für den Cluster bereit. Sie können Anwendungen oder SQL Server-Tools wie Azure Data Studio oder SQL Server Management Studio mit diesem Endpunkt verbinden, genauso wie mit jeder anderen SQL Server-Instanz.

## <a name="scale-out-query-management"></a>Horizontale Skalierung der Abfrageverwaltung

Die SQL Server-Masterinstanz enthält die Abfrage-Engine für die horizontale Skalierung, mit der Abfragen auf SQL Server-Instanzen auf Knoten im [Computepool](concept-compute-pool.md) verteilt werden. Die Abfrage-Engine für die horizontale Skalierung bietet über Transact-SQL auch Zugriff auf alle Hive-Tabellen im Cluster, ohne dass zusätzliche Konfiguration erforderlich ist.

## <a name="metadata-and-user-databases"></a>Metadaten und Benutzerdatenbanken

Zusätzlich zu den standardmäßigen SQL Server-Systemdatenbanken enthält die SQL Server-Masterinstanz Folgendes:

- Eine Metadaten-Datenbank für HDFS-Tabellenmetadaten
- Eine Zuordnung der Datenebenenshards
- Details aus externen Tabellen, die Zugriff auf die Clusterdatenebene bieten.
- In Benutzerdatenbanken definierte externe PolyBase-Datenquellen und externe Tabellen.

Sie können der SQL Server-Masterdatenbank auch Ihre eigenen Benutzerdatenbanken hinzufügen.

## <a name="machine-learning-services"></a>Dienste für maschinelles Lernen

Die SQL Server-Dienste für maschinelles Lernen stehen als Add-On für die Datenbank-Engine zur Verfügung und werden für die Ausführung von Java-, R- und Python-Code in SQL Server verwendet. Dieses Feature basiert auf dem SQL Server-Erweiterbarkeitsframework, das externe Prozesse von den Engine-Kernprozessen isoliert, aber in Form von gespeicherten Prozeduren, T-SQL-Skript mit R- oder Python-Anweisungen oder Java-, R- oder Python-Code mit T-SQL vollständig in die relationalen Daten integriert ist.

Als Teil eines SQL Server-Big Data-Clusters sind die Dienste für maschinelles Lernen standardmäßig in der SQL Server-Masterinstanz verfügbar. Das bedeutet, dass Sie mit „sp_execute_external_script“ Java-, R- und Python-Skripts ausführen können, sobald die externe Skriptausführung in der SQL Server-Masterinstanz aktiviert ist.

### <a name="advantages-of-machine-learning-services-in-a-big-data-cluster"></a>Vorteile der Dienste für maschinelles Lernen in einem Big Data-Cluster

In SQL Server 2019 lassen sich Big Data ganz einfach mit den Dimensionsdaten verknüpfen, die typischerweise in einer Unternehmensdatenbank gespeichert sind. Der Wert der Big Data vervielfacht sich, wenn diese nicht nur einem Teil der Organisation zur Verfügung stehen, sondern auch in Berichte, Dashboards und Anwendungen eingebunden werden können. Gleichzeitig können Data Scientists weiter die Tools des Spark/HDFS-Ökosystems nutzen und von einfachem Echtzeitzugriff auf die Daten in der SQL Server-Masterinstanz und in den externe Datenquellen profitieren, auf die _über_ die Masterinstanz zugegriffen werden kann.

Mit Big Data-Clustern für SQL Server 2019 können Sie einen noch größeren Mehrwert aus den Data Lakes Ihres Unternehmens erzielen. SQL Server-Entwickler und Analysten stehen folgende Möglichkeiten offen:

* Sie können Anwendungen erstellen, die Daten aus den Data Lakes des Unternehmens verwenden.
* Sie können mithilfe von Transact-SQL-Abfragen Schlussfolgerungen aus allen Daten ziehen.
* Sie können das vorhandene Ökosystem mit SQL Server-Tools und -Anwendungen verwenden, um auf Unternehmensdaten zuzugreifen und diese zu analysieren.
* Sie können mithilfe von Datenvirtualisierung und Data Marts die Anzahl von Datenverschiebungen reduzieren.
* Sie können weiterhin Spark für Big Data-Szenarien verwenden.
* Sie können mit Spark oder SQL Server intelligente Unternehmensanwendungen erstellen, um Modelle mit Data Lakes zu trainieren.
* Sie können Modelle in Produktionsdatenbanken operationalisieren, um eine optimale Leistung zu erzielen.
* Sie können Daten direkt in Unternehmens-Data Marts streamen, um Echtzeitanalysen durchzuführen.
* Sie können Daten mithilfe von interaktiven Analyse- und BI-Tools visuell erkunden.

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Artikeln finden Sie weitere Informationen zu den Big-Data-Clustern für SQL Server:

- [Was sind Big Data-Cluster für SQL Server 2019?](big-data-cluster-overview.md)
- [Workshop: Microsoft SQL Server big data clusters Architecture](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters) (Workshop: Big Data-Cluster für SQL Server – Architektur)
