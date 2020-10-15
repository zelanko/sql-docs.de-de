---
description: Optionen (SQL Server-Objekt-Explorer – Seite „Skripterstellung“)
title: Optionen (SQL Server-Objekt-Explorer – Seite „Skripterstellung“)
ms.custom: seo-lt-2019
ms.date: 08/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.ObjectExplorerScripting
- VS.ToolsOptionsPages.Sql_Server_Object_Explorer.ObjectExplorerScripting
ms.assetid: 6105aec9-1b72-4cb2-bd24-fc35f6d95240
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 35a255bb4df3779897ec40da29da9cc15f62ba1f
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "92037627"
---
# <a name="options-sql-server-object-explorer---scripting-page"></a>Optionen (SQL Server-Objekt-Explorer – Seite „Skripterstellung“)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
 Auf dieser Seite können Sie Skripterstellungsoptionen festlegen, die auf die folgenden Befehle in Objektkontextmenüs im **Objekt-Explorer** angewendet werden:  
  
-   **Bearbeiten**-Befehle für Benutzertabellen und Sichten.  
  
-   **Skript für <object> erstellen als**-Befehle für vom Benutzer erstellte Objekte.  
  
-   Befehl **Ändern** für vom Benutzer erstellte Objekte.  
  
-   Auf dieser Seite werden zudem die Standardwerte der Skripterstellungsoptionen für den **Assistenten zum Generieren von SQL Server-Skripts**festgelegt.  
  
## <a name="remarks"></a>Bemerkungen  
Die Befehle **Bearbeiten** und **Ändern** führen möglicherweise zu Ergebnissen, die sich vom Befehl **Skript für <object> erstellen als** für die gleiche Optionseinstellung unterscheiden. Die Befehle **Bearbeiten** und **Ändern** sind für das Ändern von Objekten in der aktuellen Datenbank während einer Abfrage-Editor-Sitzung vorgesehen. Der Befehl **Skript für <object> erstellen als** ist zum Generieren eines Skripts vorgesehen, sodass es später zum Erstellen von Objekten verwendet werden kann.  
  
## <a name="options"></a>Optionen  
Geben Sie Skriptoptionen an, indem Sie eine Auswahl aus den verfügbaren Einstellungen in der Liste rechts neben den einzelnen Optionen treffen.

> [!NOTE]
> Die aufgeführten Standardeinstellungen gelten nur für die Option **Skripterstellung für gesamte Datenbank und alle Datenbankobjekte** und können bei Verwendung der Option **Bestimmte Datenbankobjekte auswählen** variieren.
  
### <a name="general-scripting-options"></a>Allgemeine Skripterstellungsoptionen  
**Einzelne Anweisungen begrenzen**  
Trennt die einzelnen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen mithilfe eines Batchtrennzeichens voneinander ab. Wenn Sie das Standardbatchtrennzeichen für **Abfrage-Editor**ändern möchten, wählen Sie **Extras**/**Optionen**/**Abfrageausführung**/**SQL Server**/**Allgemein**/**Batchtrennzeichen**aus. Der Standardwert lautet False. Weitere Informationen finden Sie unter [GO (Transact-SQL)](../../t-sql/language-elements/sql-server-utilities-statements-go.md).  
  
**Beschreibende Header einschließen**  
Fügt dem Skript beschreibende Kommentare hinzu, indem das Skript in Abschnitte für die einzelnen Objekte aufgeteilt wird. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [/ *...* / (Kommentar) (Transact-SQL)](../../t-sql/language-elements/slash-star-comment-transact-sql.md).  
  
**Einschließen der Aktivierung von Vardecimal-Komprimierung**  
Schließt die vardecimal-Speicheroptionen ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [sp_db_vardecimal_storage_format (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md).  
  
**Skript für Änderungsnachverfolgung erstellen**  
Schließt Nachverfolgungsinformationen für Änderungen im Skript ein.  
  
**Skripterstellung für Volltextkataloge**  
Schließt ein Skript für Volltextkataloge ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE FULLTEXT CATALOG (Transact-SQL)](../../t-sql/statements/create-fulltext-catalog-transact-sql.md).  
  
**Skripterstellung für USE <database>**  
Fügt die USE DATABASE-Anweisung dem Skript hinzu, mit dem Datenbankobjekte im Kontext der aktuellen **Objekt-Explorer** -Datenbank erstellt werden. Wenn das Skript für die Verwendung in einer anderen Datenbank vorgesehen ist, wählen Sie False aus, um dies auszulassen. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [USE (Transact-SQL)](../../t-sql/language-elements/use-transact-sql.md).  
  
### <a name="object-scripting-options"></a>Skripterstellungsoptionen für Objekte  

**Vorhandensein von Objekten überprüfen** Überprüfen Sie vor dem Löschen oder Ändern, ob ein Objekt mit dem angegebenen Namen vorhanden ist, bzw. vor dem Erstellen, ob noch kein Objekt mit dem angegebenen Namen vorhanden ist. Weitere Informationen finden Sie unter [IF... ELSE (Transact-SQL)](../../t-sql/language-elements/if-else-transact-sql.md) und [EXISTS (Transact-SQL)](../../t-sql/language-elements/exists-transact-sql.md).

**Skript für abhängige Objekte generieren**  
Generiert ein Skript für zusätzliche Objekte, die erforderlich sind, wenn das Skript für das ausgewählte Objekt ausgeführt wird. Der Standardwert lautet False.  
  
**Schema für Objektnamen qualifizieren**  
Qualifiziert Objektnamen mit dem Objektschema. Der Standardwert lautet False. Weitere Informationen finden Sie unter [Erstellen eines Datenbankschemas](../../relational-databases/security/authentication-access/create-a-database-schema.md).  

**Optionen für die Skriptdatenkomprimierung** Schließt Datenkomprimierungsoptionen in das Skript ein. Der Standardwert lautet False.

**Skripterstellung für erweiterte Eigenschaften**  
Enthält erweiterte Eigenschaften im Skript, wenn das Objekt über erweiterte Eigenschaften verfügt. Der Standardwert lautet False. Weitere Informationen finden Sie unter [sp_addextendedproperty (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md).  
  
**Skriptbesitzer**  
Schließt den Besitzer im generierten Skript ein. Der Standardwert lautet False.  
  
**Skripterstellung für Berechtigungen**  
Schließt Berechtigungen für Datenbankobjekte im Skript ein. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [Berechtigungen](../../relational-databases/security/permissions-database-engine.md).  
  
### <a name="tableview-options"></a>Tabellen-/Sichtoptionen  
Die folgenden Optionen gelten nur für Skripts für Tabellen oder Sichten.  
  
**Benutzerdefinierte Datentypen in Basistypen konvertieren**  
Konvertiert benutzerdefinierte Datentypen in die Basistypen, aus denen sie erstellt wurden. Verwenden Sie True, wenn die benutzerdefinierten Datentypen der Quelldatenbank nicht in der Datenbank vorhanden sind, in der das Skript ausgeführt wird. Verwenden Sie False, um die benutzerdefinierten Datentypen beizubehalten. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE TYPE (Transact-SQL)](../../t-sql/statements/create-type-transact-sql.md).  
  
**SET ANSI PADDING-Befehle generieren**  
Fügt die SET ANSI_PADDING-Anweisung vor und hinter jeder CREATE TABLE-Anweisung hinzu. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [SET ANSI_PADDING (Transact-SQL)](../../t-sql/statements/set-ansi-padding-transact-sql.md).  
  
**Sortierung einschließen**  
Schließt eine Sortierung in die Spaltendefinition ein. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
**IDENTITY-Eigenschaft einschließen**  
Schließt Definitionen für den IDENTITY-Ausgangswert und das IDENTITY-Inkrement ein. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [IDENTITY (Eigenschaft) (Transact-SQL)](../../t-sql/statements/create-table-transact-sql-identity-property.md).  
  
**Schema für Fremdschlüsselverweise qualifizieren**  
Fügt Tabellenverweisen für FOREIGN KEY-Einschränkungen den Schemanamen hinzu. Der Standardwert lautet "True".  
  
**Skripterstellung für gebundene Standardwerte und Regeln**  
Schließt die Aufrufe für die bindenden gespeicherten Prozeduren **sp_bindefault** und **sp_bindrule** ein. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [sp_bindefault (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-bindefault-transact-sql.md) und [sp_bindrule (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-bindrule-transact-sql.md).  
  
**Skripterstellung für CHECK-Einschränkungen**  
Fügt dem Skript [CHECK-Einschränkungen](../../relational-databases/tables/unique-constraints-and-check-constraints.md) hinzu. Der Standardwert lautet "True".  
  
**Skripterstellung für Standard**  
Schließt Spaltenstandardwerte in das Skript ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE DEFAULT (Transact-SQL&amp;)](../../t-sql/statements/create-default-transact-sql.md).  
  
**Skripterstellung für Dateigruppen**  
Gibt die Dateigruppe in der ON -Klausel für Tabellendefinitionen an. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE TABLE (Transact-SQL&amp;)](../../t-sql/statements/create-table-transact-sql.md).  
  
**Skripterstellung für Fremdschlüssel**  
Schließt [FOREIGN KEY-Einschränkungen](../../relational-databases/tables/primary-and-foreign-key-constraints.md) in das Skript ein. Der Standardwert lautet False.  
  
**Skripterstellung für Volltextindizes**  
Schließt Volltextindizes in das Skript ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/create-fulltext-index-transact-sql.md).  
  
**Skripterstellung für Indizes**  
Schließt gruppierte Indizes, nicht gruppierte Indizes und XML-Indizes in das Skript ein. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md).  
  
**Skripterstellung für Partitionsschemas**  
Schließt Tabellenpartitionierungsschemas in das Skript ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/create-partition-scheme-transact-sql.md).  
  
**Skripterstellung für Primärschlüssel**  
Schließt [PRIMARY KEY- und FOREIGN KEY-Einschränkungen](../../relational-databases/tables/primary-and-foreign-key-constraints.md) in das Skript ein. Der Standardwert lautet "True".  
  
**Skripterstellung für Statistiken**  
Schließt benutzerdefinierte Statistiken in das Skript ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md).  
  
**Skripterstellung für Trigger**  
Schließt Trigger in das Skript ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md).  
  
**Skripterstellung für eindeutige Schlüssel**  
Schließt [UNIQUE-Einschränkungen und CHECK-Einschränkungen](../../relational-databases/tables/unique-constraints-and-check-constraints.md) in das Skript ein. Der Standardwert lautet False.  
  
**Skripterstellung für Sichtspalten**  
Deklariert Sichtspalten in Sichtheadern. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE VIEW (Transact-SQL)](../../t-sql/statements/create-view-transact-sql.md).  
  
**Include dri system names (Einschließen von DRI-Systemnamen)**  
Schließt vom System generierte Einschränkungsnamen ein, damit die deklarative referenzielle Integrität erzwungen wird. Der Standardwert lautet False. Weitere Informationen finden Sie unter [REFERENTIAL_CONSTRAINTS (Transact-SQL)](../../relational-databases/system-information-schema-views/referential-constraints-transact-sql.md).  
  
### <a name="version-options"></a>Versionsoptionen

**Skripteinstellungen mit Quelle abgleichen** Falls aktiviert, werden die generierte Zielversion, Engine-Edition und der generierte Engine-Typ des Skripts auf die Werte des Servers festgelegt, auf dem das Skript für das Objekt erstellt wird. Dadurch werden die anderen Versionsoptionen deaktiviert (und ignoriert). 

**Skript für das Datenbankmodul** Generierte Skripts werden auf die angegebene [Engine Edition (Modul-Edition)](/dotnet/api/microsoft.sqlserver.management.smo.edition) ausgerichtet.

**Skript für den Datenbankmodultyp** Generierte Skripts werden auf den angegebenen [Database Engine Type (Datenbankmodultyp)](/previous-versions/sql/sql-server-2014/ee642509(v=sql.120)) ausgerichtet.

**Skripterstellung für Serverversion**  
Generierte Skripts werden auf die angegebene Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ausgerichtet. Funktionen, die in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] neu sind, können für eine Skripterstellung für frühere Versionen nicht verwendet werden. Einige für [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] erstellte Skripts können weder auf Servern, auf denen eine frühere Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ausgeführt wird, noch in einer Datenbank mit einer früheren [Einstellung des Datenbankkompatibilitätsgrades](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)ausgeführt werden.  

## <a name="see-also"></a>Weitere Informationen:  
[Erstellen von Skripts (SQL Server Management Studio)](../scripting/generate-scripts-sql-server-management-studio.md)  
