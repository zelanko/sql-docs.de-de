---
title: Inkompatible Access-Features (AccessToSQL) | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: eb36afbcfe8d406708719fb7062510fd9f828a5b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47608358"
---
# <a name="incompatible-access-features-accesstosql"></a>Inkompatible Access-Features (AccessToSQL)
Nicht alle Funktionen von Access-Datenbank sind kompatibel mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Z. B. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] und Zugriff über andere Sätze von reservierten Schlüsselwörtern. Probleme wie z. B., wenn diese eine erfolgreiche Migration zu verhindern, können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Verwenden Sie die folgende Tabelle enthält Informationen über mögliche Migrationsprobleme und was Sie tun können, über diese.  
  
## <a name="database-settings-or-features-that-might-affect-migration"></a>Datenbankeinstellungen oder Funktionen, die Migration beeinflussen können  
  
|Zugriff auf Datenbankeinstellung oder Funktion|Migrationsproblem|  
|--------------------------------------|-------------------|  
|Zugreifen auf Tabellen müssen nicht eindeutige Indizes.|Wenn eine Tabelle, die nicht über einen eindeutigen Index verfügt, migriert wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], kann nicht in der Tabelle nach der Migration geändert. Dies kann zu Probleme mit der Anwendungskompatibilität führen.<br /><br />Wenn Sie den Zugriff auf Datenbankobjekte konvertieren, wird das Fenster "Ausgabe" alle Access-Tabellen aufgelistet, die nicht eindeutige Indizes verfügen.<br /><br />Sie können konfigurieren, fügen einen Primärschlüssel für den Zugriff auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Tabelle während der Konvertierung. Weitere Informationen finden Sie unter [Project Settings (Conversion)](http://msdn.microsoft.com/bcebc635-c638-4ddb-924c-b9ccfef86388).|  
|Zugreifen auf Tabellen haben Replikation Spalten.|Wenn Sie zu eine Access-Tabelle, die Replikationssystemspalten enthält migriert wird [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], Jet-Replikationsfunktionalität wird nach der Migration unterbrochen werden.<br /><br />Nach der Migration erwägen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Replikation synchronisierte Kopien Ihrer Datenbanken verwalten.|  
|Zugreifen auf Tabellen, die unique-Indizes enthalten mehrere null-Werte.|Zugreifen auf Tabellen, die eindeutige Indizes mit mehrere null-Werte aufweisen können nicht übertragen werden, um [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], da in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], eindeutige Indizes nicht mehrere NULL-Werte zulassen. Die Migration wird für diese Tabellen fehlschlagen.<br /><br />SSMA wird dieses Problem in Bewertungsberichte flag. Ein Bewertungsbericht erstellen zu können, finden Sie unter [Bewertung den Zugriff auf Datenbankobjekte für die Konvertierung](assessing-access-database-objects-for-conversion-accesstosql.md).<br /><br />Wenn dieses Problem vorhanden ist, müssen Sie sicherstellen, dass der primäre Schlüssel keine doppelt null-Werte. Oder entfernen Sie die primary key- oder unique-Indizes, die mehrere null-Werte enthalten.|  
|Zugreifen auf Tabellen enthalten die Date-Werten, die von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Bereich.|Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **"DateTime"** Datumsangaben im Bereich von 1 Jan. 1753 bis 31 Dez akzeptiert nur 9999. Access akzeptiert Datumsangaben im Bereich von 1 Januar 100 auf 31 Dezember 9999.<br /><br />SSMA wird dieses Problem in Bewertungsberichte flag. Ein Bewertungsbericht erstellen zu können, finden Sie unter [Bewertung den Zugriff auf Datenbankobjekte für die Konvertierung](assessing-access-database-objects-for-conversion-accesstosql.md).<br /><br />Sie können konfigurieren, wie Datumsangaben in SSMA aufgelöst wird, sind von der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Bereich. Weitere Informationen finden Sie unter [Project Settings (Migration)](http://msdn.microsoft.com/4caebc9c-8680-4b99-a8fa-89c43161c95d).|  
|Index-Länge in Access den Wert 900 Byte überschreitet.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Indizes weisen eine 900-Byte-Grenze für die Gesamtgröße der Indexschlüsselspalten. Wenn die Access-Tabellen größere Indizes verwenden, werden SSMA eine Warnung angezeigt.<br /><br />Wenn Sie die Datenmigration fortsetzen, kann die Migration fehl.|  
|Zugriff von Objektnamen wird die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schlüsselwörtern oder Sonderzeichen enthalten.|Zugriff und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] weisen verschiedene Sätze von reservierte Schlüsselwörter und Sonderzeichen. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Objekte, die mit Namen akzeptiert [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Schlüsselwörter oder die Sonderzeichen enthalten, wenn Sie in Klammern oder Anführungszeichen eingeschlossene Bezeichner, z. B. "Select" oder [] .p auswählen. Weitere Informationen finden Sie unter "Mit Trennzeichen, Bezeichner (Datenbank-Engine)" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.<br /><br />**Hinweis:** um Anführungszeichen zur Begrenzung von Bezeichnern zu verwenden, muss SET QUOTED_IDENTIFIER ON sein.<br /><br />Z. B. `CREATE TABLE [schema](c1 [FOR])` ist Sie eine gültige Anweisung, obwohl **Schema** und **für** sind reservierte Schlüsselwörter. Darüber hinaus `CREATE TABLE [xxx*yyy](c1 x&y)` eine gültige Anweisung ist, obwohl die Namen von Tabellen- und Spaltennamen enthalten, die Sonderzeichen nicht **\&#42;** und **&amp;**.<br /><br />Alle Abfragen, die auf diese Objekte verweisen, müssen auch die Namen mit Klammern oder Anführungszeichen verwenden. Angenommen, die Abfrage `SELECT * FROM schema` schlägt fehl. Die Abfrage korrekte ist: `SELECT * FROM [schema]`.<br /><br />Wenn Sie den Zugriff auf Datenbankobjekte konvertieren, wird im Ausgabebereich alle Access-Tabellen aufzulisten, die Schlüsselwörter oder Sonderzeichen zu verwenden. Sie können die Tabellen in Access ändern und entfernen Sie und fügen Sie die Datenbank erneut; oder Sie können Abfragen, die diese Objekte verweisen, damit die Abfragen eckige Klammern oder Anführungszeichen zur Begrenzung von Bezeichnern verwenden. Wenn Sie Ihre Abfragen nicht ändern, die Access-Anwendungen möglicherweise Fehler oder andere Probleme.|  
|Feldgrößen unterscheiden sich in einer Primär-/Fremdschlüssel-Beziehungen.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] die Jet-Funktionalität der Verknüpfung von Spalten mit unterschiedlichen Datentypen oder Größen mit foreign Key-Einschränkungen unterstützt nicht.<br /><br />Wenn Sie den Zugriff auf Datenbankobjekte konvertieren, listet das Fenster "Ausgabe" primary Key/foreign Key-Einschränkungen, die nicht konvertiert werden, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können Datentypen und-Größen für Spalten ändern, damit sie übereinstimmen, und klicken Sie dann zu entfernen und die Access-Datenbank erneut hinzufügen. Alternativ können Sie Daten migrieren, obwohl diese Einschränkungen nicht erstellt werden [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Referenzierte Tabellen in Access Beziehungen haben weder einen Primärschlüssel als auch einen eindeutigen Index.|Access akzeptiert die Beziehung zwischen Tabellen, wenn die referenzierte Tabelle kein Primärschlüssel oder einen eindeutigen Index verfügt. Dies wird jedoch nicht unterstützt von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br />Wenn Sie den Zugriff auf Datenbankobjekte konvertieren, wird das Fenster "Ausgabe" alle Tabellen aufgelistet, die Beziehungen jedoch keine primary key- oder unique-Index verfügen. Sie können die Tabellen, um den Primärschlüssel oder eindeutige Indizes hinzufügen und entfernen, und die Access-Datenbank erneut hinzufügen, ändern. Alternativ können Sie Daten migrieren, obwohl die Beziehung zwischen den Tabellen unterbrochen werden.|  
|Zugreifen auf Tabellen haben Hyperlink-Spalten.|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] unterstützt keine **Hyperlink** Spalten. Stattdessen werden die Spalten wie Access Memospalten behandelt. Standardmäßig werden diese Spalten in konvertiert **nvarchar(max)** Spalten in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Sie können die Zuordnung anpassen. Weitere Informationen finden Sie unter [Zuordnen von Quell- und Ziel-Datentypen](mapping-source-and-target-data-types-accesstosql.md).|  
|Standardinstanz oder Überprüfung regelausdrücke enthalten Access-Funktionen, die konvertiert werden können [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.|Zugriff Default-Ausdrücken oder Validierungsregeln sind zum Beispiel Zugriff Systemfunktionen oder benutzerdefinierte Funktionen, die nicht mit dem Zustandstyp [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure. Verwenden von Funktionen, die nicht mit dem Zustandstyp [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure ist es nicht geladen werden, die Default-Ausdrücken oder Regeln für die datenvalidierung in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder SQL Azure.|  
  
## <a name="see-also"></a>Siehe auch  
[Access-Datenbanken vorbereitet für die Migration.](preparing-access-databases-for-migration-accesstosql.md)  
[Migrieren von Access-Datenbanken zu SQLServer](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
