---
title: Optionen (SQLServer Objekt-Explorer-Scripting-Seite) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.ObjectExplorerScripting
- VS.ToolsOptionsPages.Sql_Server_Object_Explorer.ObjectExplorerScripting
ms.assetid: 6105aec9-1b72-4cb2-bd24-fc35f6d95240
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 74dfa7eec9ed7f014e9baf09cf4ddcf30cd12901
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36150496"
---
# <a name="options-sql-server-object-explorer-scripting-page"></a>Optionen (SQLServer Objekt-Explorer-Scripting-Seite)
  Auf dieser Seite können Sie Skripterstellungsoptionen festlegen, die auf die folgenden Befehle in Objektkontextmenüs im **Objekt-Explorer**angewendet werden:  
  
-   **Bearbeiten**-Befehle für Benutzertabellen und Sichten.  
  
-   **Skript \<Objekt > als** Befehle für vom Benutzer erstellte Objekte.  
  
-   Befehl **Ändern** für vom Benutzer erstellte Objekte.  
  
-   Auf dieser Seite werden zudem die Standardwerte der Skripterstellungsoptionen für den **Assistenten zum Generieren von SQL Server-Skripts**festgelegt.  
  
## <a name="remarks"></a>Hinweise  
 Die **bearbeiten** und **ändern** Befehle können Ergebnisse erzeugen, die sich von der **Skript \<Objekt > als** -Befehl für die gleiche optionseinstellung. Die Befehle **Bearbeiten** und **Ändern** sind für das Ändern von Objekten in der aktuellen Datenbank während einer Abfrage-Editor-Sitzung vorgesehen. Die **Skript \<Objekt > als** Befehl wurde entwickelt, um ein Skript generieren, damit sie später zum Erstellen von Objekten verwendet werden kann.  
  
## <a name="options"></a>Tastatur  
 Geben Sie Skriptoptionen an, indem Sie eine Auswahl aus den verfügbaren Einstellungen in der Liste rechts neben den einzelnen Optionen treffen.  
  
### <a name="general-scripting-options"></a>Allgemeine Skripterstellungsoptionen  
 **Einzelne Anweisungen begrenzen**  
 Trennt die einzelnen [!INCLUDE[tsql](../../includes/tsql-md.md)] -Anweisungen mithilfe eines Batchtrennzeichens voneinander ab. Wenn Sie das Standardbatchtrennzeichen für **Abfrage-Editor**ändern möchten, wählen Sie **Extras**/**Optionen**/**Abfrageausführung**/**SQL Server**/**Allgemein**/**Batchtrennzeichen**aus. Der Standardwert lautet False. Weitere Informationen finden Sie unter [GO &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/sql-server-utilities-statements-go).  
  
 **Beschreibende Header einschließen**  
 Fügt dem Skript beschreibende Kommentare hinzu, indem das Skript in Abschnitte für die einzelnen Objekte aufgeteilt wird. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [Kommentar &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/comment-transact-sql).  
  
 **vardecimal-Optionen einschließen**  
 Schließt die vardecimal-Speicheroptionen ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter und [Sp_db_vardecimal_storage_format &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql).  
  
 **Skript für Änderungsnachverfolgung erstellen**  
 Schließt Nachverfolgungsinformationen für Änderungen im Skript ein.  
  
 **Skripterstellung für Serverversion**  
 Erstellt ein Skript, das für die ausgewählte Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ausgeführt werden kann. Funktionen, die in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] neu sind, können für eine Skripterstellung für frühere Versionen nicht verwendet werden. Einige für [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] erstellte Skripts können weder auf Servern, auf denen eine frühere Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ausgeführt wird, noch in einer Datenbank mit einer früheren [Einstellung des Datenbankkompatibilitätsgrades](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)ausgeführt werden.  
  
 **Skripterstellung für Volltextkataloge**  
 Schließt ein Skript für Volltextkataloge ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE FULLTEXT CATALOG &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-catalog-transact-sql).  
  
 **Skript verwenden \<Datenbank >**  
 Fügt die USE DATABASE-Anweisung dem Skript hinzu, mit dem Datenbankobjekte im Kontext der aktuellen **Objekt-Explorer** -Datenbank erstellt werden. Wenn das Skript für die Verwendung in einer anderen Datenbank vorgesehen ist, wählen Sie False aus, um dies auszulassen. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).  
  
### <a name="object-scripting-options"></a>Skriptoptionen für Objekte  
 **Skript für abhängige Objekte generieren**  
 Generiert ein Skript für zusätzliche Objekte, die erforderlich sind, wenn das Skript für das ausgewählte Objekt ausgeführt wird. Der Standardwert lautet False.  
  
 **IF NOT EXISTS-Klausel einschließen**  
 Schließt eine Anweisung ein, mit der überprüft wird, ob die einzelnen Objekte nicht in der Datenbank vorhanden sind, bevor versucht wird, das Objekt zu erstellen. Der Standardwert lautet False. Weitere Informationen finden Sie unter [IF... ELSE &#40;Transact-SQL&#41; ](/sql/t-sql/language-elements/if-else-transact-sql) und [EXISTS &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/exists-transact-sql).  
  
 **Schema für Objektnamen qualifizieren**  
 Qualifiziert Objektnamen mit dem Objektschema. Der Standardwert lautet False. Weitere Informationen finden Sie unter [Erstellen eines Datenbankschemas](../../relational-databases/security/authentication-access/create-a-database-schema.md).  
  
 **Skripterstellung für erweiterte Eigenschaften**  
 Enthält erweiterte Eigenschaften im Skript, wenn das Objekt über erweiterte Eigenschaften verfügt. Der Standardwert lautet False. Weitere Informationen finden Sie unter [sp_addextendedproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql).  
  
 **Skriptbesitzer**  
 Schließt den Besitzer im generierten Skript ein. Der Standardwert lautet False.  
  
 **Skripterstellung für Berechtigungen**  
 Schließt Berechtigungen für Datenbankobjekte im Skript ein. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [Berechtigungen &#40;Datenbankmodul&#41;](../../relational-databases/security/permissions-database-engine.md).  
  
### <a name="tableview-options"></a>Tabellen-/Sichtoptionen  
 Die folgenden Optionen gelten nur für Skripts für Tabellen oder Sichten.  
  
 **Benutzerdefinierte Datentypen in Basistypen konvertieren**  
 Konvertiert benutzerdefinierte Datentypen in die Basistypen, aus denen sie erstellt wurden. Verwenden Sie True, wenn die benutzerdefinierten Datentypen der Quelldatenbank nicht in der Datenbank vorhanden sind, in der das Skript ausgeführt wird. Verwenden Sie False, um die benutzerdefinierten Datentypen beizubehalten. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE TYPE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-type-transact-sql).  
  
 **SET ANSI PADDING-Befehle generieren**  
 Fügt die SET ANSI_PADDING-Anweisung vor und hinter jeder CREATE TABLE-Anweisung hinzu. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).  
  
 **Sortierung einschließen**  
 Schließt eine Sortierung in die Spaltendefinition ein. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
 **IDENTITY-Eigenschaft einschließen**  
 Schließt Definitionen für den IDENTITY-Ausgangswert und das IDENTITY-Inkrement ein. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [IDENTITY &#40;Eigenschaft&#41; &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql-identity-property).  
  
 **Schema für Fremdschlüsselverweise qualifizieren**  
 Fügt Tabellenverweisen für FOREIGN KEY-Einschränkungen den Schemanamen hinzu. Der Standardwert lautet "True".  
  
 **Skripterstellung für gebundene Standardwerte und Regeln**  
 Schließt die Aufrufe für die bindenden gespeicherten Prozeduren **sp_bindefault** und **sp_bindrule** ein. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [Sp_bindefault &#40;Transact-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-bindefault-transact-sql) und [Sp_bindrule &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-bindrule-transact-sql).  
  
 **Skripterstellung für CHECK-Einschränkungen**  
 Fügt dem Skript [CHECK-Einschränkungen](../../relational-databases/tables/unique-constraints-and-check-constraints.md) hinzu. Der Standardwert lautet "True".  
  
 **Skripterstellung für Standard**  
 Schließt Spaltenstandardwerte in das Skript ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE DEFAULT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-default-transact-sql).  
  
 **Skripterstellung für Dateigruppen**  
 Gibt die Dateigruppe in der ON -Klausel für Tabellendefinitionen an. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).  
  
 **Skripterstellung für Fremdschlüssel**  
 Schließt [FOREIGN KEY-Einschränkungen](../../relational-databases/tables/primary-and-foreign-key-constraints.md) in das Skript ein. Der Standardwert lautet False.  
  
 **Skripterstellung für Volltextindizes**  
 Schließt Volltextindizes in das Skript ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE FULLTEXT INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-index-transact-sql).  
  
 **Skripterstellung für Indizes**  
 Schließt gruppierte Indizes, nicht gruppierte Indizes und XML-Indizes in das Skript ein. Der Standardwert lautet "True". Weitere Informationen finden Sie unter [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql).  
  
 **Skripterstellung für Partitionsschemas**  
 Schließt Tabellenpartitionierungsschemas in das Skript ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE PARTITION SCHEME &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-partition-scheme-transact-sql).  
  
 **Skripterstellung für Primärschlüssel**  
 Schließt [PRIMARY KEY- und FOREIGN KEY-Einschränkungen](../../relational-databases/tables/primary-and-foreign-key-constraints.md) in das Skript ein. Der Standardwert lautet "True".  
  
 **Skripterstellung für Statistiken**  
 Schließt benutzerdefinierte Statistiken in das Skript ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE STATISTICS &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-statistics-transact-sql).  
  
 **Skripterstellung für Trigger**  
 Schließt Trigger in das Skript ein. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql).  
  
 **Skripterstellung für eindeutige Schlüssel**  
 Schließt [UNIQUE-Einschränkungen und CHECK-Einschränkungen](../../relational-databases/tables/unique-constraints-and-check-constraints.md) in das Skript ein. Der Standardwert lautet False.  
  
 **Skripterstellung für Sichtspalten**  
 Deklariert Sichtspalten in Sichtheadern. Der Standardwert lautet False. Weitere Informationen finden Sie unter [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).  
  
 **ScriptDriIncludeSystemNames**  
 Schließt vom System generierte Einschränkungsnamen ein, damit die deklarative referenzielle Integrität erzwungen wird. Der Standardwert lautet False. Weitere Informationen finden Sie unter [REFERENTIAL_CONSTRAINTS &#40;Transact-SQL&#41;](/sql/relational-databases/system-information-schema-views/referential-constraints-transact-sql).  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Skripts &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/generate-scripts-sql-server-management-studio.md)  
  
  
