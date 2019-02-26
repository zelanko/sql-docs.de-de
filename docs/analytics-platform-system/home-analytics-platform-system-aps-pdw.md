---
title: Dokumentation zu Analytics Platform System | Microsoft-Dokumentation
description: Microsoft Analytics Platform System (APS) ist eine Datenplattform, die für Data Warehousing und Big Data-Analysen entwickelt wurde. Sie bietet nahtlose Datenintegration, schnelle Abfrageverarbeitung, hochgradig skalierbaren Speicher sowie eine unkomplizierte Wartung für End-to-End-Lösungen für Business Intelligence.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/18/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: bc8765d0bc8fe4b5b9ab3b4bcc98ce940f99400c
ms.sourcegitcommit: a13256f484eee2f52c812646cc989eb0ce6cf6aa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803465"
---
# <a name="microsoft-analytics-platform-system"></a>Microsoft Analytics Platform System

Microsoft Analytics Platform System (APS) ist eine Datenplattform, die für Data Warehousing und Big Data-Analysen entwickelt wurde. Sie bietet nahtlose Datenintegration, schnelle Abfrageverarbeitung, hochgradig skalierbaren Speicher sowie eine unkomplizierte Wartung für End-to-End-Lösungen für Business Intelligence.

![Appliancearchitektur](media/architecture-high-level.png "appliance architecture")

APS hostet SQL Server Parallel Data Warehouse (PDW). Dabei handelt es sich um eine Software, die ein MPP-Data Warehouse (Massively Parallel Processing) ausführt.

Die PolyBase-Technologie kombiniert relationale PDW-Daten mit Hadoop-Daten aus verschiedenen Quellen, unter anderem Hortonworks unter Windows Server, Hortonworks unter Linux, Cloudera unter Linux und Microsoft Azure Blob Storage von HDInsight. Durch diese erweiterten Datenintegrationsfunktionen und die nahtlose Integration in Business Intelligence-Tools kann Analytics Platform System integrierte Analysen zurückgeben, mit denen Entscheidungsträger Ihres Unternehmens bessere und informiertere Unternehmensentscheidungen treffen können.

Analytics Platform System wird als Appliance mit Hardware und vorinstallierter Software in Ihr Rechenzentrum geliefert, und ist so konfiguriert, dass es mehrere Workloads ausführen kann. Wenn Sie Analytics Platform System erwerben, kaufen Sie auch Computeknoten für PDW entsprechend Ihren Geschäftsanforderungen.

Analytics Platform System ist nicht nur schnell und skalierbar, sondern weist auch eine hohe Redundanz und Hochverfügbarkeit auf. Dies macht es zu einer zuverlässigen Plattform für Ihre unternehmenswichtigen Daten. Analytics Platform System ist auf Einfachheit getrimmt, sodass Sie schnell damit zurecht kommen und es leicht verwalten können. Die PolyBase-Technologie von Parallel Data Warehouse, die zur Analyse von Hadoop-Daten eingesetzt wird, und die nahtlose Integration in Business Intelligence-Tools machen Analytics Platform System zu einer umfangreichen Plattform zum Erstellen von End-to-End-Lösungen.

## <a name="parallel-data-warehouse-software-designed-for-massively-parallel-processing"></a>Parallel Data Warehouse: für MPP entwickelt

Verwenden Sie Parallel Data Warehouse als Hauptkomponente Ihrer Business Intelligence-End-to-End-Lösung für relationales Data Warehousing. Mit dem MPP-Design von PDW können Abfragen meist 50-mal schneller als traditionelle Data Warehouses abgeschlossen werden, die auf SMP-DBMS aufbauen (Datenbankverwaltungssysteme).

> [!NOTE]
> Dies bedeutet, dass Abfrage in wenigen Minuten oder wenigen Sekunden, und nicht nach mehreren Stunden oder Minuten abgeschlossen werden. Durch diese revolutionäre Leistung können Ihre Unternehmensanalysten schneller umfangreichere Ergebnisse liefern und ganz leicht Ad-hoc-Abfragen durchführen oder ausführlicher nachforschen. So kann Ihr Unternehmen schneller bessere Entscheidungen treffen.

PDW ermöglicht nicht nur eine noch nie da gewesene Abfrageleistung, sondern auch Folgendes:

- Erweitern Sie Ihr Datawarehouse an einem beliebigen Standort aus einige Terabytes auf mehr als 6 Petabytes von Daten in einer einzelnen Appliance durch Hinzufügen von "Skalierungseinheiten" können Sie Ihrem System.

- Vertrauen Sie, dass Ihre Daten vorhanden sein werden, wenn Sie aufgrund der integrierte hohe Redundanz und hochverfügbarkeit benötigt.

- Lösen Sie Probleme beim Laden und Konsolidieren von Daten.

- Integrieren Sie Hadoop-Daten mit relationalen Daten, die für die schnelle Analyse mithilfe der hochgradig parallelisierten PolyBase-Technologie von PDW.

- Sie können umfangreiche End-to-End-Lösungen mit Business Intelligence-Tools entwickeln.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu den Vorteilen von Parallel Data Warehouse finden Sie im Whitepaper [A Breakthrough Platform for Next-Generation Data Warehousing and Big Data Solutions (Eine revolutionäre Plattform für Data Warehousing und Big Data-Lösungen der nächsten Generation)](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/dn520808%28v=msdn.10%29) auf MSDN.
