---
title: Filtern veröffentlichter Daten für die Mergereplikation| Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication [SQL Server replication], filtering published data
- replication [SQL Server], filtering published data
ms.assetid: 46c5023d-7a3b-4455-becc-e159fcb5d6c4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 60fe7e6fd2b818c653c3f5fd713de5b1945fb714
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48219580"
---
# <a name="filter-published-data-for-merge-replication"></a>Filtern veröffentlichter Daten für die Mergereplikation
  Abgesehen von den statischen Zeilenfiltern und Spaltenfiltern, die Sie auch bei anderen Replikationstypen definieren können, ermöglicht die Mergereplikation die Verwendung von parametrisierten Zeilenfiltern und Joinfiltern. Weitere Informationen zu statischen Zeilenfiltern und Spaltenfiltern finden Sie unter [Filtern von veröffentlichten Daten](../publish/filter-published-data.md).  
  
 Die Mergereplikation wird in vielen Anwendungen zur Unterstützung mobiler Benutzer verwendet. Bei diesem Anwendungen gibt es meist eine große Zahl Abonnements, wobei jedes Abonnement ein eindeutiges Dataset empfängt. Parametrisierte Filter in Kombination mit Joinfiltern ermöglichen es einem Administrator, eine Veröffentlichung einzurichten (oder maximal eine kleine Zahl von Veröffentlichungen) und dabei verschiede Datasets bereitzustellen. Dadurch wird der Verwaltungsaufwand reduziert, der durch das Erstellen mehrerer Veröffentlichungen entsteht.  
  
-   Mit parametrisierten Filtern können verschiedene Partitionen von Daten an verschiedene Abonnenten gesendet werden, ohne dass mehrere Veröffentlichungen erstellt werden müssen. Eine Tabelle kann z. B. so gefiltert werden, dass Daten für einen bestimmten Vertriebsmitarbeiter tatsächlich nur für diesen Vertriebsmitarbeiter repliziert werden. Parametrisierte Filter bieten eine Vielzahl von Optionen, mit deren Hilfe Sie Filter zur Optimierung der Leistung und Ihren Daten- und Anwendungsanforderungen entsprechend perfekt anpassen können. Weitere Informationen zu parametrisierten Zeilenfiltern finden Sie unter [Parametrisierte Zeilenfilter](parameterized-filters-parameterized-row-filters.md).  
  
-   Joinfilter werden in der Regel in Verbindung mit parametrisierten Filtern verwendet, um die Filterung auf verknüpfte Tabellen auszuweiten (sie können auch zusammen mit statischen Filtern verwendet werden). Der Vertriebsmitarbeiter benötigt z. B. meist auch Daten aus anderen Tabellen (z. B. Kunden oder Aufträge). Diese Daten können so gefiltert werden, dass der Vertriebsmitarbeiter nur die Daten zu seinen Kunden und Kundenaufträgen erhält. Weitere Informationen finden Sie unter [Join Filters](join-filters.md).  
  
 Ein Filter muss die von der Replikation verwendete `rowguidcol` nicht einschließen, um Zeilen zu identifizieren. Standardmäßig ist dies die Spalte, die zum Zeitpunkt hinzugefügt wurde, als Sie die Mergereplikation eingerichtet haben, und sie heißt **rowguid**.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von Daten und Datenbankobjekten](../publish/publish-data-and-database-objects.md)  
  
  
