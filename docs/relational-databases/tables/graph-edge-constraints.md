---
title: Graph-Edgeeinschränkungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- edge constraints [SQL Server]
- CONNECTION constraints
- edge constraints [Azure SQL Database]
- graph edge constraints
- SQL Graph
author: shkale-msft
ms.author: shkale
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current||=azuresqldb-current'
ms.openlocfilehash: aa73858e6df29c814821ee9e24923cbfc0fbd4a2
ms.sourcegitcommit: 630f7cacdc16368735ec1d955b76d6d030091097
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2019
ms.locfileid: "67343886"
---
# <a name="edge-constraints"></a>Edgeeinschränkungen

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Edgeeinschränkungen können verwendet werden, um die Datenintegrität und eine spezifische Semantik in den Edgetabellen in einer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Graph-Datenbank zu erzwingen.

##  <a name="Connection"></a> Edgeeinschränkungen
 Im ersten Release der Graph-Features wurde für die Endpunkt des Edge durch die Edgetabellen nichts erzwungen. Anders gesagt: Ein Edge in einer Graph-Datenbank konnte unabhängig vom Knotentyp eine Verbindung von jedem Knoten mit jedem Knoten herstellen. 

 In diesem Release werden Edgeeinschränkungen eingeführt, mit denen Benutzer Einschränkungen zu ihren Edgetabellen hinzufügen und damit eine bestimmte Semantik erzwingen und die Datenintegrität sicherstellen können. Wenn einer Edgetabelle mit Edgeeinschränkungen ein neues Edge hinzugefügt wird, erzwingt die [!INCLUDE[ssDE](../../includes/ssde-md.md)], dass die Knoten, mit denen das Edge eine Verbindung herstellen möchte, in den richtigen Knotentabellen vorhanden sein müssen. Es wird ebenfalls sichergestellt, dass ein Knoten nicht gelöscht werden kann, wenn noch von einem Edge auf ihn verwiesen wird. 

 ### <a name="edge-constraint-clauses"></a>Edgeeinschränkungsklauseln
 Jede Edgeeinschränkung besteht aus mindestens einer Edgeeinschränkungsklausel. Eine Edgeeinschränkungsklausel ist ein Paar aus FROM- und TO-Knoten, das vom angegebenen Edge verbunden werden kann. 

 Ein Beispiel: Sie haben die Knoten `Product` und `Customer` in Ihrem Graph und verwenden ein `Bought`-Edge, um diese Knoten zu verbinden. Die Edgeeinschränkungsklausel gibt das FROM- und TO-Knotenpaar und die Richtung des Edge an. In diesem Fall lautet die Edgeeinschränkungsklausel „`Customer` TO `Product`“. Das bedeutet Folgendes: Das Einfügen eines `Bought`-Edge von `Customer` zu `Product` ist zulässig. Es ist aber nicht möglich, ein Edge von `Product` zu `Customer` einzufügen. 
  
- Eine Edgeeinschränkungsklausel enthält ein Paar aus FROM- und TO-Knotentabellen, in denen die Edgeeinschränkung erzwungen wird. 
  
- Benutzer können für jede Edgeeinschränkung mehrere Edgeeinschränkungsklauseln angeben, die als Disjunktion angewendet werden.

- Wenn in einer einzelnen Edgetabelle mehrere Edgeeinschränkungen erstellt werden, müssen Edges ALLE Einschränkungen zulassen.
  
### <a name="indexes-on-edge-constraints"></a>Indizes in Edgeeinschränkungen
 Durch Erstellen einer Edgeeinschränkung wird nicht automatisch ein entsprechender Index in den `$from_id`- und `$to_id`-Spalten der Edgetabelle erstellt. Es empfiehlt sich, manuell einen Index in einem `$from_id`,`$to_id`-Spaltenpaar zu erstellen, wenn Sie Punktsuchabfragen oder OLTP-Workloads verarbeiten. 

##  <a name="Tasks"></a> Verwandte Aufgaben  
 In der folgenden Tabelle sind die gängigen Aufgaben im Zusammenhang mit Edgeeinschränkungen aufgeführt.  
  
|Task|Artikel|  
|----------|-----------|  
|Beschreibt, wie Edgeeinschränkungen erstellt werden.|[Erstellen von Edgeeinschränkungen](../../relational-databases/tables/create-edge-constraints.md)|  
|Beschreibt, wie eine Edgeeinschränkung gelöscht wird.|[Löschen einer Edgeeinschränkung](../../relational-databases/tables/delete-edge-constraint.md)|  
|Beschreibt, wie eine Edgeeinschränkung geändert wird.|[Ändern einer Edgeeinschränkung](../../relational-databases/tables/modify-edge-constraint.md)|  
|Beschreibt, wie die Eigenschaften von Edgeeinschränkungen angezeigt werden.|[Anzeigen der Eigenschaften von Edgeeinschränkungen](../../relational-databases/tables/view-edge-constraint-properties.md)|  
| Übersicht über die Graph-Technologie in SQL Server | [Graph-Verarbeitung mit SQL Server und Azure SQL-Datenbank](../graphs/sql-graph-overview.md) |
| &nbsp; | &nbsp; |
