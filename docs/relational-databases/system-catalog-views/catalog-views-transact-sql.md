---
title: Katalog Sichten (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 05/02/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sql13.SysViewExpandPortal.f1
dev_langs:
- TSQL
helpviewer_keywords:
- catalog metadata [SQL Server]
- system views [SQL Server], catalog
- metadata [SQL Server], views
- catalogs [SQL Server], metadata
- catalog views [SQL Server]
- Database Engine [SQL Server], metadata
- catalog views [SQL Server], about catalog views
ms.assetid: 13bccc2f-ed3c-4b58-abd0-ca8bf34a66b8
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9532ee19ec8489caa51d090feaff464e030a0da0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68670556"
---
# <a name="system-catalog-views-transact-sql"></a>System Katalog Sichten (Transact-SQL)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Katalogsichten geben Informationen zurück, die von [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] verwendet werden. Sie sollten Katalogsichten verwenden, da sie die allgemeinste Schnittstelle zu den Katalogmetadaten darstellen und die effizienteste Methode zum Abrufen, Transformieren und Präsentieren dieser Informationen in benutzerdefinierter Form bereitstellen. Alle für Benutzer verfügbaren Katalogmetadaten werden über Katalogsichten verfügbar gemacht.

> [!NOTE]
> Katalogsichten enthalten keine Informationen zu Replikation, Sicherung, Datenbank-Wartungsplan oder Katalogdaten zum [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Agent.

 Einige Katalogsichten erben Zeilen von anderen Katalogsichten. Die [sys. Tables](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md) -Katalog Sicht erbt z. b. von der [sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) -Katalog Sicht. Die sys.objects-Katalogsicht wird als Basissicht bezeichnet, und die sys.tables-Sicht wird abgeleitete Sicht genannt. Die sys.tables-Katalogsicht gibt die Spalten zurück, die für Tabellen spezifisch sind, sowie alle Spalten, die die sys.objects-Katalogsicht zurückgibt. Die sys.objects-Katalogsicht gibt Zeilen für Objekte zurück, bei denen es sich nicht um Tabellen handelt, z. B. gespeicherte Prozeduren und Sichten. Nachdem eine Tabelle erstellt wurde, werden die Metadaten für die Tabelle in beiden Sichten zurückgegeben. Die beiden Katalogsichten geben zwar unterschiedliche Ebenen von Informationen zur Tabelle zurück, es gibt jedoch nur einen Metadateneintrag für diese Tabelle mit einem Namen und einem object_id-Wert. Dies kann wie folgt zusammengefasst werden:

- Die Basissicht enthält eine Teilmenge der Spalten und eine Obermenge der Zeilen.
- Die abgeleitete Sicht enthält eine Obermenge der Spalten und eine Teilmenge der Zeilen.

> [!IMPORTANT]
> In zukünftigen Versionen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird die Definition der Systemkatalogsichten von [!INCLUDE[msCoName](../../includes/msconame-md.md)] möglicherweise erweitert, indem am Ende der Spaltenliste Spalten hinzugefügt werden. Es wird empfohlen, die Syntax SELECT \* from *sys. catalog_view_name* im Produktionscode zu verwenden, da sich die Anzahl der zurückgegebenen Spalten möglicherweise ändert und Ihre Anwendung unterbricht.

Die Katalogsichten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wurden in den folgenden Kategorien organisiert:

|||
|-|-|
|[Katalogsichten Always On-Verfügbarkeitsgruppen &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)|[Nachrichten &#40;für Fehler&#41; Katalog Sichten &#40;Transact-SQL-&#41;](../system-catalog-views/messages-for-errors-catalog-views-sys-messages.md))|
|[Azure SQL-Datenbank-Katalogsichten](../../relational-databases/system-catalog-views/azure-sql-database-catalog-views.md)|[Objektkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)|
|[Änderungsnachverfolgung Katalog Sichten &#40;Transact-SQL-&#41;](../system-catalog-views/change-tracking-catalog-views-sys-change-tracking-databases.md)|[Katalog Sichten für Partitions Funktionen &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/partition-function-catalog-views-transact-sql.md)|
|[CLR-assemblykatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/clr-assembly-catalog-views-transact-sql.md)|[Sichten der Richtlinien basierten Verwaltung &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)|
|[Datensammler Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/data-collector-views-transact-sql.md)|[Resource Governor Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)|
|[Datenbereiche &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)|[Katalogsichten des Abfragespeichers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/query-store-catalog-views-transact-sql.md)|
|[Datenbank-E-Mail Ansichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/database-mail-views-transact-sql.md)|[Skalare Typenkatalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/scalar-types-catalog-views-transact-sql.md)|
|[Katalog Sichten für die Datenbank-Spiegelungs Zeugen &#40;Transact-SQL-&#41;](../system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)|[Schemas-Katalog Sichten &#40;Transact-SQL-&#41;](../system-catalog-views/schemas-catalog-views-sys-schemas.md)|
|[Katalog Sichten für Datenbanken und Dateien &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)|[Sicherheitskatalogsichten &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)|
|[Endpoints Catalog Views &#40;Transact-SQL&#41; (Katalogsichten für Endpunkte &#40;Transact-SQL&#41;)](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)|[Service Broker Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql.md)|
|[Katalogsichten für erweiterte Ereignisse &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)|[Server weite Konfigurations Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/server-wide-configuration-catalog-views-transact-sql.md)|
|[Katalogsichten für erweiterte Eigenschaften &#40;Transact-SQL&#41;](../system-catalog-views/extended-properties-catalog-views-sys-extended-properties.md)|[Katalogsichten für räumliche Daten](../../relational-databases/system-catalog-views/spatial-data-catalog-views.md)|
|[Externe Vorgangs Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/external-operations-catalog-views-transact-sql.md)|[SQL Data Warehouse und parallele Data Warehouse Katalog Sichten](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)|
|[FILESTREAM-und FILETABLE-Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)|[Stretch Database Katalog Sichten &#40;Transact-SQL-&#41;](../system-catalog-views/stretch-database-catalog-views-sys-remote-data-archive-databases.md)|
|[Katalog Sichten für die voll Text Suche und die semantische Suche &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/full-text-search-and-semantic-search-catalog-views-transact-sql.md)|[XML-Schemas &#40;XML-Typsystem&#41; Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)|
|[Verknüpfte Server-Katalog Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)||

## <a name="see-also"></a>Weitere Informationen

- [Informations Schema Sichten &#40;Transact-SQL-&#41;](../../relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)
- [Systemtabellen &#40;Transact-SQL&#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)
- [FAQ: Abfragen des SQL Server-Systemkatalogs](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)
