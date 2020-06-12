---
title: Nicht kompatible Zugriffs Features (accesstosql) | Microsoft-Dokumentation
description: Erfahren Sie mehr über mögliche Migrationsprobleme bei Access-Daten Bank Features, die nicht mit SQL Server kompatibel sind, und wie Sie Sie beheben können.
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access databases
- Access databases, features incompatible with SQL Azure
- Access databases, features incompatible with SQL Server
- dates
- default expressions
- foreign keys
- hyperlink columns
- incompatible Access features
- indexes
- indexes, length of
- keywords
- primary keys
- reference, incompatible features
- replication columns
- special characters
- unique indexes
- validation rules
ms.assetid: 99d45b9c-e3b9-4d56-8c25-b594b887ace1
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 8bccdd3ebb49e3694ca472525a7c76d81f1fcc7a
ms.sourcegitcommit: 59cda5a481cfdb4268b2744edc341172e53dede4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84293547"
---
# <a name="incompatible-access-features-accesstosql"></a>Nicht kompatible Zugriffs Features (accesstosql)
Nicht alle Access-Daten Bank Features sind mit kompatibel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Beispielsweise [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] haben und Access unterschiedliche Sätze von reservierten Schlüsselwörtern. Probleme wie diese können eine erfolgreiche Migration zu verhindern [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . In der folgenden Tabelle finden Sie Informationen zu möglichen Migrationsproblemen und zu deren Verwendung.  
  
## <a name="database-settings-or-features-that-might-affect-migration"></a>Datenbankeinstellungen oder-Features, die die Migration beeinträchtigen können  
  
|Access-Datenbankeinstellung oder-Funktion|Migrationsproblem|  
|--------------------------------------|-------------------|  
|Zugriffs Tabellen haben keine eindeutigen Indizes.|Wenn eine Tabelle, die nicht über einen eindeutigen Index verfügt, zu migriert wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , können Sie die Tabelle nach der Migration nicht mehr ändern. Dies kann zu Anwendungs Kompatibilitätsproblemen führen.<br /><br />Wenn Sie Access-Datenbankobjekte konvertieren, listet das Fenster Ausgabe alle Zugriffs Tabellen auf, die keine eindeutigen Indizes aufweisen.<br /><br />Sie können den Zugriff so konfigurieren, dass der Tabelle während der Konvertierung ein Primärschlüssel hinzugefügt wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Weitere Informationen finden Sie unter [Projekteinstellungen (Konvertierung)](https://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388).|  
|Zugriffs Tabellen haben Replikations Spalten.|Wenn eine Zugriffs Tabelle mit Replikationssystem Spalten zu migriert wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wird die Jet-Replikations Funktion nach der Migration beschädigt.<br /><br />Nach der Migration sollten Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Replikation verwenden, um synchronisierte Kopien Ihrer Datenbanken beizubehalten.|  
|Zugriffs Tabellen mit eindeutigen Indizes enthalten mehrere NULL-Werte.|Zugriffs Tabellen, die eindeutige Indizes mit mehreren NULL-Werten aufweisen, können nicht an übertragen werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , da in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] eindeutige Indizes mehrere Nullen nicht zulassen. Die Migration kann für diese Tabellen nicht ausgeführt werden.<br /><br />SSMA wird dieses Problem in Bewertungsberichten markieren. Informationen zum Erstellen eines Bewertungsberichts finden Sie unter [bewerten des Zugriffs auf Datenbankobjekte für die Konvertierung](assessing-access-database-objects-for-conversion-accesstosql.md).<br /><br />Wenn dieses Problem vorliegt, müssen Sie sicherstellen, dass der Primärschlüssel keine doppelten NULL-Werte enthält. Oder Sie müssen den Primärschlüssel oder eindeutige Indizes entfernen, die mehrere NULL-Werte enthalten.|  
|Zugriffs Tabellen enthalten Datumswerte, die außerhalb des gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Bereichs liegen.|Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **DateTime** -Typ akzeptiert Datumsangaben im Bereich von 1. Januar 1753 bis 31. Dezember 9999. Der Zugriff akzeptiert Datumsangaben im Bereich von 1. Januar 100 bis 31. Dezember 9999.<br /><br />SSMA wird dieses Problem in Bewertungsberichten markieren. Informationen zum Erstellen eines Bewertungsberichts finden Sie unter [bewerten des Zugriffs auf Datenbankobjekte für die Konvertierung](assessing-access-database-objects-for-conversion-accesstosql.md).<br /><br />Sie können konfigurieren, wie SSMA Datumsangaben auflöst, die außerhalb des gültigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Bereichs liegen. Weitere Informationen finden Sie unter [Projekteinstellungen (Migration)](https://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).|  
|Index Längen in Access überschreiten 900 Bytes.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Indizes haben eine 900-Byte-Grenze für die Gesamtgröße der Index Schlüssel Spalten. Wenn in ihren Zugriffs Tabellen größere Indizes verwendet werden, wird von SSMA eine Warnung angezeigt.<br /><br />Wenn Sie die Datenmigration fortsetzen, tritt bei der Migration möglicherweise ein Fehler auf.|  
|Zugriffs Objektnamen sind [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schlüsselwörter oder enthalten Sonderzeichen.|Greifen Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auf und verfügen über unterschiedliche Sätze von reservierten Schlüsselwörtern und Sonderzeichen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]akzeptiert Objekte, die mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schlüsselwörtern benannt werden oder Sonderzeichen enthalten, wenn Sie Bezeichner in Klammern oder Anführungszeichen verwenden, z. b. "Select" oder [Select]. p. Weitere Informationen finden Sie unter "Begrenzungs Bezeichner (Datenbank-Engine)" in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Online Dokumentation.<br /><br />**Hinweis:** Um Bezeichner mit Anführungszeichen zu begrenzen, legen Sie QUOTED_IDENTIFIER muss auf ON festgelegt sein.<br /><br />Beispielsweise `CREATE TABLE [schema](c1 [FOR])` ist eine gültige-Anweisung, auch wenn **Schema** und **für** reservierte Schlüsselwörter sind. Außerdem `CREATE TABLE [xxx*yyy](c1 x&y)` ist eine gültige-Anweisung, obwohl der Tabellen-und Spaltenname die Sonderzeichen ** \& #42,** und enthält **&amp;** .<br /><br />Alle Abfragen, die auf diese Objekte verweisen, müssen auch die Namen mit Klammern oder Anführungszeichen verwenden. Beispielsweise kann die Abfrage `SELECT * FROM schema` nicht ausgeführt werden. Die richtige Abfrage lautet: `SELECT * FROM [schema]` .<br /><br />Wenn Sie Access-Datenbankobjekte konvertieren, werden im Ausgabebereich alle Zugriffs Tabellen aufgelistet, die Schlüsselwörter oder Sonderzeichen verwenden. Sie können die Tabellen in Access ändern und anschließend die Datenbank entfernen und erneut hinzufügen. oder Sie können Abfragen, die auf diese Objekte verweisen, ändern, sodass die Abfragen eckige Klammern oder Anführungszeichen zum Begrenzen von bezeichlern verwenden. Wenn Sie Ihre Abfragen nicht ändern, geben Ihre Access-Anwendungen möglicherweise Fehler zurück oder haben andere Probleme.|  
|Die Feldgrößen unterscheiden sich in den Primär-/Fremdschlüssel-Beziehungen.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt nicht die Jet-Funktionalität des Verknüpfens von Spalten mit unterschiedlichen Datentypen oder Größen mit Foreign Key-Einschränkungen.<br /><br />Wenn Sie Access-Datenbankobjekte konvertieren, listet das Fenster Ausgabe alle PRIMARY KEY/FOREIGN KEY-Einschränkungen auf, die nicht in konvertiert werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Sie können Datentypen und Größen für Zugriffs Spalten ändern, sodass Sie einander entsprechen, und dann die Access-Datenbank entfernen und erneut hinzufügen. Oder Sie können Daten migrieren, obwohl diese Einschränkungen nicht in erstellt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|Referenzierte Tabellen in Zugriffs Beziehungen haben weder einen Primärschlüssel noch einen eindeutigen Index.|Access akzeptiert die Beziehung zwischen Tabellen, in denen die referenzierte Tabelle keinen Primärschlüssel oder eindeutigen Index besitzt. Dies wird jedoch von nicht unterstützt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br />Wenn Sie Access-Datenbankobjekte konvertieren, listet das Fenster Ausgabe alle Tabellen auf, die Beziehungen, aber keinen Primärschlüssel oder eindeutigen Index aufweisen. Sie können die Tabellen ändern, um Primärschlüssel oder eindeutige Indizes hinzuzufügen, und dann die Access-Datenbank entfernen und erneut hinzufügen. Oder Sie können Daten migrieren, obwohl die Beziehung zwischen den Tabellen beschädigt wird.|  
|Zugriffs Tabellen haben Link Spalten.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützt keine **Hyperlink** -Spalten. Stattdessen werden die Spalten wie Zugriffs Memo Spalten behandelt. Standardmäßig werden diese Spalten in in **nvarchar (max)** -Spalten konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Sie können die Zuordnung anpassen. Weitere Informationen finden Sie unter [Zuordnung von Quell-und Ziel Datentypen](mapping-source-and-target-data-types-accesstosql.md).|  
|Standard Ausdrücke oder Validierungs Regel Ausdrücke enthalten Zugriffs Funktionen, die nicht in konvertiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure werden können.|Access-Standard Ausdrücke oder-Validierungsregeln können Zugriffs Systemfunktionen oder benutzerdefinierte Funktionen enthalten, die nicht zugeordnet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure werden. Wenn Sie Funktionen verwenden, die nicht mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure werden, können Sie die Standard Ausdrücke oder Validierungsregeln nicht in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure laden.|  
  
## <a name="see-also"></a>Weitere Informationen  
[Vorbereiten der Zugriffs Datenbanken für die Migration](preparing-access-databases-for-migration-accesstosql.md)  
[Migration von Access-Datenbanken zu SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
