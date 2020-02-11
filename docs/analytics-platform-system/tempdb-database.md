---
title: Tempdb-Datenbank
description: Die tempdb-Datenbank ist parallel Data Warehouse.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 3772e2b4cabac84c00854eba85f7a0c2a33d48bc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400138"
---
# <a name="tempdb-database-in-parallel-data-warehouse"></a>tempdb-Datenbank parallel Data Warehouse
bei **tempdb** handelt es sich um eine SQL Server PDW Systemdatenbank, in der lokale temporäre Tabellen für Benutzer Datenbanken gespeichert werden. Temporäre Tabellen werden häufig verwendet, um die Abfrageleistung zu verbessern. Beispielsweise können Sie eine temporäre Tabelle zum Modularisieren eines Skripts verwenden und berechnete Daten wieder verwenden.  
  
Weitere Informationen zu System Datenbanken finden Sie unter [System Datenbanken](system-databases.md).  
  
## <a name="Basics"></a>Wichtige Begriffe und Konzepte  
*lokale temporäre Tabelle*  
Eine *lokale temporäre Tabelle* verwendet das Präfix # vor dem Tabellennamen und ist eine temporäre Tabelle, die von einer lokalen Benutzersitzung erstellt wird. Jede Sitzung kann nur für eine eigene Sitzung auf die Daten in lokalen temporären Tabellen zugreifen.  
  
Jede Sitzung kann die Metadaten für lokale temporäre Tabellen in allen Sitzungen anzeigen. Beispielsweise können alle Sitzungen die Metadaten für alle lokalen temporären Tabellen mit der `SELECT * FROM tempdb.sys.tables` Abfrage anzeigen.  
  
globale temporäre Tabelle  
*Globale temporäre Tabellen*, die in SQL Server mit der # #-Syntax unterstützt werden, werden in dieser Version von SQL Server PDW nicht unterstützt.  
  
pdwtempdb  
**pdwtempdb** ist die Datenbank, in der lokale temporäre Tabellen gespeichert werden.  
  
PDW implementiert keine temporären Tabellen mithilfe der SQL Server**tempdb** -Datenbank. Stattdessen speichert PDW Sie in einer Datenbank mit dem Namen pdwtempdb. Diese Datenbank ist auf jedem Computeknoten vorhanden und für den Benutzer über die PDW-Schnittstellen nicht sichtbar. In der Verwaltungskonsole auf der Seite Speicher werden diese in einer PDW-Systemdatenbank namens **tempdb-SQL**berücksichtigt.  
  
tempdb  
**tempdb** ist die SQL Server tempdb-Datenbank. Es verwendet minimale Protokollierung. SQL Server verwendet tempdb auf den Computeknoten, um temporäre Tabellen zu speichern, die im Rahmen der Durchführung von SQL Server Vorgängen benötigt werden.  
  
SQL Server PDW löscht Tabellen aus **tempdb** , wenn:  
  
-   Die DROP TABLE-Anweisung wird ausgeführt.  
  
-   Eine Sitzung wird getrennt. Es werden nur temporäre Tabellen für die Sitzung gelöscht.  
  
-   Das Gerät wird heruntergefahren.  
  
-   Der Steuerungs Knoten verfügt über ein Cluster Failover.  
  
## <a name="general-remarks"></a>Allgemeine Hinweise  
SQL Server PDW führt die gleichen Vorgänge für temporäre Tabellen und permanente Tabellen aus, sofern nicht ausdrücklich anders angegeben. Beispielsweise werden die Daten in lokalen temporären Tabellen, genauso wie permanente Tabellen, entweder auf den Computeknoten verteilt oder repliziert.  
  
## <a name="LimitationsRestrictions"></a>Einschränkungen  
Einschränkungen für die SQL Server PDW**tempdb** -Datenbank. Folgendes ist *nicht möglich:*  
  
-   Erstellen Sie eine globale temporäre Tabelle, die mit # # beginnt.  
  
-   Führen Sie eine Sicherung oder Wiederherstellung von **tempdb**aus.  
  
-   Ändern Sie die Berechtigungen für **tempdb** mit den Anweisungen **Grant**, **Deny**oder **Widerruf** .  
  
-   Führen Sie **DBCC shrinklog** für **tempdb**tempdb aus.  
  
-   Ausführen von DDL-Vorgängen für **tempdb**. Hierfür gibt es einige Ausnahmen. Weitere Informationen finden Sie in der folgenden Liste mit Einschränkungen für lokale temporäre Tabellen.  
  
Einschränkungen für lokale temporäre Tabellen. Folgendes ist *nicht möglich:*  
  
-   Umbenennen einer temporären Tabelle  
  
-   Erstellen Sie Partitionen, Sichten oder nicht gruppierte Indizes für eine temporäre Tabelle. **Alter Index** kann verwendet werden, um einen gruppierten Index für eine Tabelle neu zu erstellen, die mit einem Index erstellt wurde.  
  
-   Ändern Sie die Berechtigungen für temporäre Tabellen mit den Anweisungen GRANT, Deny oder Widerruf.  
  
-   Ausführen von Daten Bank Konsolen Befehlen für temporäre Tabellen.  
  
-   Verwenden Sie den gleichen Namen für zwei oder mehr temporäre Tabellen innerhalb desselben Batches. Wenn in einem Batch mehrere lokale temporäre Tabellen verwendet werden, muss jede einen eindeutigen Namen aufweisen. Wenn mehrere Sitzungen denselben Batch ausführen und dieselbe lokale temporäre Tabelle erstellt, fügt SQL Server PDW intern ein numerisches Suffix an den lokalen temporären Tabellennamen an, um einen eindeutigen Namen für jede lokale temporäre Tabelle zu erhalten.  
  
> [!NOTE]  
> Sie *können* Statistiken für eine temporäre Tabelle erstellen und aktualisieren. **Alter Index** kann verwendet werden, um einen gruppierten Index neu zu erstellen.  
  
## <a name="permissions"></a>Berechtigungen  
Jeder Benutzer ist berechtigt, temporäre Objekte in tempdb zu erstellen. Benutzer haben nur Zugriff auf ihre eigenen Objekte, es sei denn, ihnen wurden zusätzliche Berechtigungen zugewiesen. Die CONNECT-Berechtigung für tempdb kann widerrufen werden, um Benutzer daran zu hindern, die tempdb-Datenbank zu verwenden. Von diesem Schritt wird jedoch abgeraten, da einige Routinevorgänge auf die Verwendung von tempdb angewiesen sind.  
  
## <a name="RelatedTasks"></a>Verwandte Aufgaben  
  
|Aufgaben|BESCHREIBUNG|  
|---------|---------------|  
|Erstellen Sie eine Tabelle in **tempdb**.|Sie können eine temporäre Benutzertabelle mit den CREATE TABLE und CREATE TABLE als SELECT-Anweisungen erstellen. Weitere Informationen finden Sie unter [CREATE TABLE](../t-sql/statements/create-table-azure-sql-data-warehouse.md) und [Create Table As Select](../t-sql/statements/create-table-as-select-azure-sql-data-warehouse.md).|  
|Anzeigen einer Liste vorhandener Tabellen in **tempdb**.|`SELECT * FROM tempdb.sys.tables;`|  
|Anzeigen einer Liste vorhandener Spalten in **tempdb**.|`SELECT * FROM tempdb.sys.columns;`|  
|Anzeigen einer Liste vorhandener Objekte in **tempdb**.|`SELECT * FROM tempdb.sys.objects;`|  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
