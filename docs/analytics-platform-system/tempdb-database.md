---
title: Tempdb-Datenbank – Parallel Data Warehouse | Microsoft-Dokumentation
description: Tempdb-Datenbank in Parallel Data Warehouse.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7e11f4eff980358f4b4906f8a100cfc509d19dd5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "63156962"
---
# <a name="tempdb-database-in-parallel-data-warehouse"></a>Tempdb-Datenbank in Parallel Data Warehouse
**Tempdb** ist eine SQL Server-PDW-Systemdatenbank, in der lokale temporäre Tabellen für die Benutzerdatenbanken gespeichert. Temporäre Tabellen werden häufig verwendet, um die abfrageleistung zu verbessern. Sie können beispielsweise eine temporäre Tabelle verwenden, um ein Skript zu modularisieren und berechnete Daten wiederverwenden.  
  
Weitere Informationen zu den Systemdatenbanken, finden Sie unter [Systemdatenbanken](system-databases.md).  
  
## <a name="Basics"></a>Hauptbegriffe und-Konzepte  
*lokale temporäre Tabelle*  
Ein *lokale temporäre Tabelle* verwendet das Präfix "#" vor dem Tabellennamen und eine temporäre Tabelle, die von einer Sitzung des lokalen Benutzers erstellt wird. Jede Sitzung kann nur die Daten im lokalen temporären Tabellen für ihre eigene Sitzung zugreifen.  
  
Jede Sitzung kann die Metadaten für lokale temporäre Tabellen in allen Sitzungen anzeigen. Beispielsweise können alle Sitzungen anzeigen die Metadaten für alle lokalen temporären Tabellen mit den `SELECT * FROM tempdb.sys.tables` Abfrage.  
  
Globale temporäre Tabelle  
*Globale temporäre Tabellen*, unterstützte in SQL Server mit der ## Syntax werden in dieser Version von SQL Server PDW nicht unterstützt.  
  
pdwtempdb  
**Pdwtempdb** ist die Datenbank, in der lokale temporäre Tabellen gespeichert.  
  
PDW temporäre Tabellen nicht über den SQL Server implementiert**Tempdb** Datenbank. Stattdessen speichert PDW sie in eine Datenbank namens Pdwtempdb. Diese Datenbank auf jedem Computeknoten vorhanden ist und für den Benutzer über die PDW-Schnittstellen nicht sichtbar ist. In der Verwaltungskonsole auf der Seite "Speicher" sehen Sie diese ausgewiesenen für in einer PDW-Systemdatenbank, die Namen **Tempdb-Sql-** .  
  
tempdb  
**Tempdb** ist die SQL Server-Tempdb-Datenbank. Die minimale Protokollierung verwendet. SQL Server verwendet Tempdb auf den Computeknoten zum Speichern von temporärer Tabellen, die beim Ausführen von SQL Server-Vorgängen werden muss.  
  
SQL Server PDW löscht die Tabellen aus **Tempdb** bei:  
  
-   Die DROP TABLE-Anweisung wird ausgeführt.  
  
-   Eine Sitzung wird getrennt. Es werden nur temporäre Tabellen für die Sitzung gelöscht.  
  
-   Das Gerät wird heruntergefahren.  
  
-   Der steuerknoten wurde ein Clusterfailover.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
SQL Server PDW führt die gleichen Vorgänge für temporäre Tabellen und dauerhaften Tabellen auf, wenn nicht ausdrücklich anders angegeben. Z. B. werden die Daten im lokalen temporären Tabellen wie bei dauerhaften Tabellen verteilt oder über den Compute-Knoten repliziert.  
  
## <a name="LimitationsRestrictions"></a>Einschränkungen  
Begrenzungen und Einschränkungen für die SQL Server PDW**Tempdb** Datenbank. Sie *nicht möglich:*  
  
-   Erstellen eine globale temporäre Tabelle, die mit ##.  
  
-   Führen Sie eine Sicherung oder Wiederherstellung des **Tempdb**.  
  
-   Ändern von Berechtigungen für **Tempdb** mit der **GRANT**, **Verweigern**, oder **widerrufen** Anweisungen.  
  
-   Führen Sie **DBCC SHRINKLOG** für **Tempdb**Tempdb.  
  
-   Führen Sie die DDL-Vorgänge auf **Tempdb**. Es gibt einige Ausnahmen. Weitere Informationen finden Sie unter der folgenden Liste der Einschränkungen für lokale temporäre Tabellen.  
  
Einschränkungen und Einschränkungen für die lokale temporäre Tabellen. Sie *nicht möglich:*  
  
-   Benennen Sie eine temporäre Tabelle  
  
-   Erstellen Sie Partitionen, Sichten oder nicht gruppierte Indizes für eine temporäre Tabelle ein. **ALTER INDEX** kann verwendet werden, um einen gruppierten Index für eine Tabelle erstellt, die mit einem neu zu erstellen.  
  
-   Ändern von Berechtigungen für temporäre Tabellen mit der GRANT, DENY oder REVOKE-Anweisungen.  
  
-   Führen Sie Datenbank-Konsolenbefehle auf temporäre Tabellen ein.  
  
-   Verwenden Sie den gleichen Namen für zwei oder mehr temporäre Tabellen innerhalb desselben Batches. Wenn in einem Batch mehrere lokale temporäre Tabellen verwendet werden, muss jede einen eindeutigen Namen aufweisen. Wenn mehrere Sitzungen sind die gleichen Batch ausgeführt und die gleiche lokale temporäre Tabelle erstellen, fügt SQL Server PDW intern ein numerisches Suffix an den Namen lokaler temporärer Tabellen einen eindeutigen Namen für jede lokale temporäre Tabelle zu verwalten.  
  
> [!NOTE]  
> Sie *können* erstellen und Aktualisieren von Statistiken für eine temporäre Tabelle. **ALTER INDEX** können verwendet werden, um einen gruppierten Index neu erstellen.  
  
## <a name="permissions"></a>Berechtigungen  
Jeder Benutzer ist berechtigt, temporäre Objekte in tempdb zu erstellen. Benutzer haben nur Zugriff auf ihre eigenen Objekte, es sei denn, ihnen wurden zusätzliche Berechtigungen zugewiesen. Die CONNECT-Berechtigung für tempdb kann widerrufen werden, um Benutzer daran zu hindern, die tempdb-Datenbank zu verwenden. Von diesem Schritt wird jedoch abgeraten, da einige Routinevorgänge auf die Verwendung von tempdb angewiesen sind.  
  
## <a name="RelatedTasks"></a>Verwandte Aufgaben  
  
|Richtlinienübersicht|Description|  
|---------|---------------|  
|Erstellen Sie eine Tabelle in **Tempdb**.|Sie können eine temporäre Tabelle für Benutzer mit der CREATE TABLE- und CREATE TABLE AS SELECT-Anweisungen erstellen. Weitere Informationen finden Sie unter [CREATE TABLE](../t-sql/statements/create-table-azure-sql-data-warehouse.md) und [CREATE TABLE AS SELECT](../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md).|  
|Anzeigen einer Liste vorhandener Tabellen in **Tempdb**.|`SELECT * FROM tempdb.sys.tables;`|  
|Anzeigen einer Liste von vorhandenen Spalten in **Tempdb**.|`SELECT * FROM tempdb.sys.columns;`|  
|Anzeigen einer Liste von vorhandenen Objekten im **Tempdb**.|`SELECT * FROM tempdb.sys.objects;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
