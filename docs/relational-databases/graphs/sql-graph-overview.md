---
title: Graph-Verarbeitung mit SQL Server und Azure SQL-Datenbank | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, overview
ms.assetid: ''
author: shkale-msft
ms.author: shkale
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 010d985245052949451a0b519ee4d7b312a97f4a
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2019
ms.locfileid: "67413075"
---
# <a name="graph-processing-with-sql-server-and-azure-sql-database"></a>Graph-Verarbeitung mit SQL Server und Azure SQL-Datenbank
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bietet graphdatenbank-Funktionen zum Modellieren von m: n Beziehungen. Die Graph-Beziehungen sind in integriert [!INCLUDE[tsql-md](../../includes/tsql-md.md)] und erhalten die Vorteile der Verwendung [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] als grundlegende Database Managementsystem.


## <a name="what-is-a-graph-database"></a>Was ist eine Graphdatenbank?  
Eine Diagrammdatenbank ist eine Sammlung von Knoten (oder Vertices) und Edges (oder Beziehungen). Ein Knoten stellt eine Entität (z.B. eine Person oder Organisation) dar, und ein Edge repräsentiert eine Beziehung zwischen den beiden Knoten, die durch den Edge verbunden werden (z.B. Likes oder Freunde). Sowohl Knoten und Edges können Eigenschaften zugeordnet haben. Hier sind einige Funktionen, die eine graphdatenbank eindeutig zu machen:  
-   Ränder oder Beziehungen sind erstklassige Entitäten in einer Diagrammdatenbank und können haben Attribute oder Eigenschaften zugeordnet. 
-   Eine einzelne Kante kann flexibel auf mehrere Knoten in einer Diagrammdatenbank verbinden.
-   Sie können Musterabgleich und Multi-Hop-Navigation-Abfragen problemlos Ausdrücken.
-   Sie können transitiver und polymorphe Abfragen problemlos Ausdrücken.

## <a name="when-to-use-a-graph-database"></a>Wann wird eine Graphdatenbank verwendet?

Es gibt nichts, was eine Diagrammdatenbank erreichen kann, die Verwendung einer relationalen Datenbank erreicht werden kann. Allerdings kann eine Diagrammdatenbank express bestimmte Art von Abfragen erleichtern. Darüber hinaus können mit bestimmten Optimierungen, bestimmte Abfragen eine bessere Leistung. Basiert die Entscheidung, wann auswählen kann auf folgenden Faktoren:  
-   Ihre Anwendung verfügt über hierarchische Daten. Der HierarchyID-Datentyp kann verwendet werden, um Hierarchien zu implementieren, aber es gelten einige Einschränkungen. Beispielsweise können dabei nicht mehrere übergeordnete Elemente für einen Knoten zu speichern.
-   Ihre Anwendung verfügt über komplexe m: n Beziehungen; Anwendung weiterentwickelt, werden neue Beziehungen hinzugefügt.
-   Sie müssen miteinander verbundener Daten und Beziehungen zu analysieren.

## <a name="graph-features-introduced-in-includesssqlv14includessssqlv14-mdmd"></a>Graph-Funktionen in [!INCLUDE[sssqlv14](../../includes/sssqlv14-md.md)] 
Wir beginnen damit, Hinzufügen von Graph-Erweiterungen mit SQL Server, um das Speichern und Abfragen von Diagrammdaten zu erleichtern. Folgende Features werden in der ersten Version eingeführt. 


### <a name="create-graph-objects"></a>Erstellen von Graph-Objekten
[!INCLUDE[tsql-md](../../includes/tsql-md.md)] Erweiterungen können Benutzer Knoten-oder edgetabellen zu erstellen. Sowohl Knoten und Edges können Eigenschaften, die ihnen zugewiesene verfügen. Da Knoten und Kanten werden als Tabellen gespeichert, alle Vorgänge, die auf relationalen Tabellen unterstützt werden, werden auf Knoten-oder edgetabelle unterstützt. Beispiel:  

```   
CREATE TABLE Person (ID INTEGER PRIMARY KEY, Name VARCHAR(100), Age INT) AS NODE;
CREATE TABLE friends (StartDate date) AS EDGE;
```   

![Person-Freunde-Tables](../../relational-databases/graphs/media/person-friends-tables.png "Person-Knoten und Freunde edge-Tabellen")  
Knoten und Kanten werden als Tabellen gespeichert.  

### <a name="query-language-extensions"></a>Abfrage-spracherweiterungen  
Neue `MATCH` Klausel eingeführt, um die Unterstützung von Musterabgleich und Multi-Hop-Navigation durch das Diagramm. Die `MATCH` Funktion verwendet die Syntax im ASCII-Grafik Format für den Musterabgleich. Zum Beispiel:  

```   
-- Find friends of John
SELECT Person2.Name 
FROM Person Person1, Friends, Person Person2
WHERE MATCH(Person1-(Friends)->Person2)
AND Person1.Name = 'John';
```   
 
### <a name="fully-integrated-in-includessnoversionincludesssnoversion-mdmd-engine"></a>Vollständig integrierte in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Engine 
Graph-Erweiterungen sind vollständig integriert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Engine. Verwenden Sie den gleichen Speicher-Engine, Metadaten, Abfrageprozessor usw., speichern und Abfragen von Diagrammdaten. Die Abfrage Graph und relationalen Daten in einer einzelnen Abfrage. Graph-Funktionen mit anderen kombiniert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Technologien wie Columnstore, hohe Verfügbarkeit, R Services usw. SQL-Graph-Datenbank unterstützt auch alle Sicherheits- und Complianceanforderungen Funktionen mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
 
### <a name="tooling-and-ecosystem"></a>Tools und das Ökosystem

Vorhandene Tools und das Ökosystem profitieren, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] bietet. Tools wie Sichern und wiederherstellen, importieren und exportieren, BCP praktisch von selbst standardmäßig. Andere Tools und Dienste wie SSIS, SSRS oder Power BI funktioniert mit der Graph-Tabellen, nur die Möglichkeit, die sie mit relationalen Tabellen arbeiten.

## <a name="edge-constraints"></a>Edgeeinschränkungen
Eine Edge-Einschränkung für eine Graph-Edge-Tabelle definiert ist, und es besteht aus einem Paar von Knoten-Tabellen, die ein bestimmten Edge-Typ, eine Verbindung herstellen kann. So erhalten Benutzer eine bessere Kontrolle über die Graph-Schema. Mithilfe des edgeeinschränkungen können Benutzer den Typ der Knoten beschränken, die eine bestimmte Kante eine Verbindung herstellen darf. 

Erfahren mehr über das Erstellen und Verwenden von edgeeinschränkungen, finden Sie unter [Edgeeinschränkungen](../../relational-databases/tables/graph-edge-constraints.md)

## <a name="merge-dml"></a>Zusammenführen von DML 
Die [MERGE](../../t-sql/statements/merge-transact-sql.md) Anweisung führt einfügen, aktualisieren oder delete-Vorgänge in eine Zieltabelle, die auf der Grundlage der Ergebnisse eines Joins mit einer Quelltabelle. Sie können z. B. zwei Tabellen synchronisieren, indem einfügen, aktualisieren oder Löschen von Zeilen in eine Zieltabelle basierend auf den Unterschieden zwischen der Zieltabelle und der Quelltabelle. Mithilfe von MATCH-Prädikate in einer MERGE-Anweisung wird jetzt auf Azure SQL-Datenbank und SQL Server vNext unterstützt. Also ist es jetzt möglich, Ihre aktuellen Diagrammdaten (Knoten- oder edgetabelle Tabellen) mit neuen Daten, die mithilfe der MATCH-Prädikate zur Angabe der Graph-Beziehungen in einer einzigen Anweisung anstelle von separaten INSERT/UPDATE/DELETE-Anweisungen zusammenführen.

Erfahren mehr über die wie Übereinstimmung in DML-Zusammenführung verwendet werden kann, finden Sie unter [MERGE-Anweisung](../../t-sql/statements/merge-transact-sql.md)

## <a name="shortest-path"></a>Kürzeste Pfad
Die [SHORTEST_PATH](./sql-graph-shortest-path.md) Funktion findet den kürzesten Pfad zwischen 2 Knoten in einem Diagramm oder ab einem bestimmten Knoten zu den anderen Knoten im Diagramm. Kürzeste Pfad kann auch verwendet werden, finden Sie ein transitiver oder beliebiger Länge traversierungen im Diagramm. 

 ## <a name="next-steps"></a>Nächste Schritte  
Lesen der [SQL-Graph-Datenbank – Architektur](./sql-graph-architecture.md)
   

