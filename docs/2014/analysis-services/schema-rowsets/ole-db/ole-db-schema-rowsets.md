---
title: OLE DB-Schemarowsets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
- apinav
helpviewer_keywords:
- schema rowsets [OLE DB]
- schema rowsets [Analysis Services], OLE DB
- OLE DB schema rowsets
- rowsets [Analysis Services], OLE DB
ms.assetid: ca2ee87a-ba04-4501-9125-33934c58ab31
caps.latest.revision: 37
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3a1d03d6fd8d527d48a9a4051f201368ff870882
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161191"
---
# <a name="ole-db-schema-rowsets"></a>OLE DB-Schemarowsets
  Die folgenden OLE DB-Schemarowsets werden vom [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis-Anbieter (XMLA) unterstützt. Verwenden der `DISCOVER_ENUMERATORS` Rowset mit der [Discover](../../xmla/xml-elements-methods-discover.md) -Methode überprüft, ob ein bestimmter Datenquellenanbieter ein Rowset unterstützt.  
  
 Weitere Informationen über diese Rowsets finden Sie im Thema "Schema Rowsets" im Abschnitt "OLE DB Programmer's Reference" der MSDN® Library auf der [!INCLUDE[msCoName](../../../includes/msconame-md.md)]-Website.  
  
 In der folgenden Tabelle werden diese Schemarowsets beschrieben.  
  
|Rowset|Description|  
|------------|-----------------|  
|`DBSCHEMA_ASSERTIONS`|Gibt die im Katalog definierten Assertionen an, deren Eigentümer ein angegebener Benutzer ist.|  
|[DBSCHEMA_CATALOGS-Rowset](dbschema-catalogs-rowset.md) <sup>1</sup>|Gibt die physischen Attribute zugeordneten Kataloge, die von der Datenbank-Managementsystem (DBMS) zugegriffen werden kann. Für einige Systeme, beispielsweise [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Access, ist möglicherweise nur ein Katalog verfügbar. Für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] listet dieses Rowset alle in der Systemdatenbank definierten Kataloge (Datenbanken) auf.|  
|`DBSCHEMA_CHARACTER_SETS`|Gibt die im Katalog definierten Zeichensätze an, auf die ein angegebener Benutzer zugreifen kann.|  
|`DBSCHEMA_CHECK_CONSTRAINTS`|Gibt die CHECK-Einschränkungen an, die in dem Katalog definierten sind, dessen Eigentümer ein angegebener Benutzer ist.|  
|`DBSCHEMA_CHECK_CONSTRAINTS_BY_TABLE`|Gibt die CHECK-Einschränkungen für eine bestimmte Tabelle an, die in einem Katalog definiert sind, dessen Eigentümer ein angegebener Benutzer ist.|  
|`DBSCHEMA_COLLATIONS`|Gibt die im Katalog definierten Sortierungen an, auf die ein angegebener Benutzer zugreifen kann.|  
|`DBSCHEMA_COLUMN_DOMAIN_USAGE`|Gibt die im Katalog definierten Spalten an, die von einer im Katalog definierten Domäne abhängig sind und deren Eigentümer ein angegebener Benutzer ist.|  
|`DBSCHEMA_COLUMN_PRIVILEGES`|Gibt die im Katalog definierten Berechtigungen für Tabellenspalten an, die für einen angegebenen Benutzer verfügbar sind oder von diesem erteilt wurden.|  
|[DBSCHEMA_COLUMNS-Rowset](dbschema-columns-rowset.md) <sup>1</sup>|Stellt Spalteninformationen für alle Spalten bereit, die den bereitgestellten Einschränkungskriterien entsprechen.|  
|`DBSCHEMA_CONSTRAINT_COLUMN_USAGE`|Gibt die im Katalog definierten Spalten an, die von referenziellen Einschränkungen, UNIQUE-Einschränkungen, CHECK-Einschränkungen und Assertionen verwendet werden und deren Eigentümer ein angegebener Benutzer ist.|  
|`DBSCHEMA_CONSTRAINT_TABLE_USAGE`|Gibt die im Katalog definierten Tabellen an, die von referenziellen Einschränkungen, UNIQUE-Einschränkungen, CHECK-Einschränkungen und Assertionen verwendet werden und deren Eigentümer ein angegebener Benutzer ist.|  
|`DBSCHEMA_FOREIGN_KEYS`|Gibt die im Katalog von einem angegebenen Benutzer definierten Fremdschlüsselspalten an. Dieses Schemarowset wird auf der Grundlage mehrerer ISO-Schemasichten zur Erleichterung von Nicht-SQL-Programmierern erstellt Wenn es unterstützt wird, muss dieses Schemarowset mit den zugehörigen ISO-Sichten synchronisiert werden (`REFERENTIAL_CONSTRAINTS` und `CONSTRAINT_COLUMN_USAGE`).|  
|`DBSCHEMA_INDEXES`|Gibt die im Katalog definierten Indizes an, deren Eigentümer ein angegebener Benutzer ist.|  
|`DBSCHEMA_KEY_COLUMN_USAGE`|Gibt die Spalten an, die im Katalog definiert sind und von einem bestimmten Benutzer als Schlüssel eingeschränkt wurden.|  
|`DBSCHEMA_PRIMARY_KEYS`|Gibt die im Katalog von einem angegebenen Benutzer definierten Primärschlüsselspalten an. Dieses Schemarowset wird auf der Grundlage einer ISO-Schemasicht zur Erleichterung von Nicht-SQL-Programmierern erstellt. Wenn es unterstützt wird, muss dieses Schemarowset mit der zugehörigen ISO-Sicht synchronisiert werden (`CONSTRAINT_COLUMN_USAGE`).|  
|`DBSCHEMA_PROCEDURE_COLUMNS`|Gibt Informationen zu den Spalten von Rowsets zurück, die von Prozeduren zurückgegeben werden.|  
|`DBSCHEMA_PROCEDURE_PARAMETERS`|Gibt Informationen zu den Parametern und Rückgabecodes von Prozeduren zurück.|  
|`DBSCHEMA_PROCEDURES`|Gibt die im Katalog definierten Prozeduren an, deren Eigentümer ein angegebener Benutzer ist. Dies ist eine Erweiterung von OLE DB.|  
|[DBSCHEMA_PROVIDER_TYPES-Rowset](dbschema-provider-types-rowset.md) <sup>1</sup>|Gibt die von dem Datenanbieter unterstützten (Basis-)Datentypen an.|  
|`DBSCHEMA_REFERENTIAL_CONSTRAINTS`|Gibt die referenziellen Einschränkungen an, die in dem Katalog definiert sind, dessen Eigentümer ein angegebener Benutzer ist.|  
|`DBSCHEMA_SCHEMATA`|Gibt die Schemas an, dessen Eigentümer ein angegebener Benutzer ist.|  
|`DBSCHEMA_SQL_LANGUAGES`|Gibt die definierten Übereinstimmungsebenen, Optionen und Dialekte an, die von der SQL-Implementierung unterstützt werden, die die im Katalog definierten Daten verarbeitet.|  
|`DBSCHEMA_STATISTICS`|Gibt die im Katalog definierten Statistiken an, deren Eigentümer ein angegebener Benutzer ist.<br /><br /> Diese Tabelle gehört nicht zum `TABLE_STATISTICS`-Rowset.|  
|`DBSCHEMA_TABLE_CONSTRAINTS`|Gibt die Tabelleneinschränkungen an, die in dem Katalog definiert sind, dessen Eigentümer ein angegebener Benutzer ist.|  
|`DBSCHEMA_TABLE_PRIVILEGES`|Gibt die im Katalog definierten Berechtigungen für Tabellen an, die für einen angegebenen Benutzer verfügbar sind oder von diesem erteilt wurden.|  
|`DBSCHEMA_TABLE_STATISTICS`|Beschreibt den beim Anbieter verfügbaren Satz von Statistiken für Tabellen.<br /><br /> Dieses Rowset gehört nicht zum `STATISTICS`-Rowset.|  
|[DBSCHEMA_TABLES-Rowset](dbschema-tables-rowset.md) <sup>1</sup>|Gibt die Measuregruppen und Dimensionen, die verfügbar gemacht werden, als Tabellen in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|`DBSCHEMA_TABLES_INFO` <sup>1</sup>|Gibt die im Katalog definierten Tabellen (einschließlich Sichten) an, auf die ein angegebener Benutzer zugreifen kann.|  
|`DBSCHEMA_TRANSLATIONS`|Gibt die im Katalog definierten Übersetzungen an, auf die ein angegebener Benutzer zugreifen kann.|  
|`DBSCHEMA_TRUSTEE`|Listet die Vertrauensnehmer einer Datenquelle auf.|  
|`DBSCHEMA_USAGE_PRIVILEGES`|Gibt die im Katalog definierten `USAGE`-Berechtigungen für Objekte an, die für einen angegebenen Benutzer verfügbar sind oder von diesem erteilt wurden.|  
|`DBSCHEMA_VIEW_COLUMN_USAGE`|Gibt die im Katalog definierten Sichten an, auf die ein angegebener Benutzer zugreifen kann.|  
|`DBSCHEMA_VIEW_TABLE_USAGE`|Gibt die Tabellen an, von denen im Katalog definierte Tabellen in Sichten, deren Eigentümer ein angegebener Benutzer ist, abhängig sind.|  
|`DBSCHEMA_VIEWS`|Gibt die im Katalog definierten Sichten an, auf die ein angegebener Benutzer zugreifen kann.|  
  
 <sup>1</sup> gibt Schemarowsets unterstützt, indem Sie die MSOLAP-Datenquellenanbieter für den [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XMLA-Anbieter.  
  
## <a name="see-also"></a>Siehe auch  
 [DISCOVER_ENUMERATORS-Rowset](../xml/discover-enumerators-rowset.md)   
 [Analysis Services-Schemarowsets](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  
