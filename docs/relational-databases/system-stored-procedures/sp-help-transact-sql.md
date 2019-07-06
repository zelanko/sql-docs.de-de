---
title: Sp_help (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help
- sp_help_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help
ms.assetid: 913cd5d4-39a3-4a4b-a926-75ed32878884
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 39a1e699b52b29db74209aa5288bb5dc01896a3b
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2019
ms.locfileid: "67586249"
---
# <a name="sphelp-transact-sql"></a>sp_help (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Gibt Informationen zu einem Datenbankobjekt (alle Objekte aufgelistet, die der **sys.sysobjects** -kompatibilitätssicht angezeigt), einen benutzerdefinierten Datentyp oder einen Datentyp.  
  
 
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help [ [ @objname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @objname = ] 'name'` Ist der Name eines beliebigen Objekts im **Sysobjects** , oder geben Sie eine benutzerdefinierte Daten die **Systypes** Tabelle. *Namen* ist **Nvarchar (** 776 **)** , hat den Standardwert NULL. Datenbanknamen sind nicht zulässig.  Zwei bis drei Teilnamen müssen eingeschränkt werden, z.B. „Person.AddressType“ oder [Person.AddressType].   
   
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder 1 (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Das Resultset mit Vorwärtscursor, die zurückgegeben werden, hängt davon ab, ob *Namen* wird angegeben, wenn er angegeben wird, und welche Datenbankobjekt kann.  
  
1.  Wenn **Sp_help** erfolgt keine Argumente, zusammenfassende Informationen zu aller Objekttypen, die in der aktuellen Datenbank vorhanden sind zurückgegeben wird.  
  
    |Spaltenname|Datentyp|Beschreibung|  
    |-----------------|---------------|-----------------|  
    |**Name**|**nvarchar(** 128 **)**|Objektname|  
    |**Besitzer**|**nvarchar(** 128 **)**|Objektbesitzer (Dies ist der Datenbankprinzipal, der das Objekt besitzt. Wird standardmäßig auf den Besitzer des Schemas festgelegt, das das Objekt enthält.)|  
    |**Object_type**|**nvarchar(** 31 **)**|Objekttyp|  
  
2.  Wenn *Namen* ist eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentyp oder den benutzerdefinierten Datentyp **Sp_help** gibt dieses Resultset zurück.  
  
    |Spaltenname|Datentyp|Beschreibung|  
    |-----------------|---------------|-----------------|  
    |**Type_name**|**nvarchar(** 128 **)**|Name des Datentyps.|  
    |**Storage_type**|**nvarchar(** 128 **)**|Name des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typs|  
    |**Länge**|**smallint**|Physische Länge des Datentyps (in Bytes)|  
    |**prec**|**int**|Genauigkeit (Gesamtzahl der Ziffern)|  
    |**Dezimalstellen**|**int**|Anzahl der Stellen nach dem Dezimaltrennzeichen|  
    |**NULL zulassen**|**varchar(** 35 **)**|Gibt an, ob NULL-Werte zulässig sind: Ja oder nein.|  
    |**Default_name**|**nvarchar(** 128 **)**|Name eines an diesen Typ gebundenen Standards.<br /><br /> NULL = Es ist kein Standard gebunden.|  
    |**Rule_name**|**nvarchar(** 128 **)**|Name einer an diesen Typ gebundenen Regel.<br /><br /> NULL = Es ist kein Standard gebunden.|  
    |**Sortierung**|**sysname**|Sortierung des Datentyps. NULL für Nicht-Zeichen-Datentypen|  
  
3.  Wenn *Namen* beliebiges Datenbankobjekt außer einem Datentyp **Sp_help** dieses Ergebnis und zusätzliche Resultsets, basierend auf dem Typ des angegebenen Objekts zurück.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    |Spaltenname|Datentyp|Beschreibung|  
    |-----------------|---------------|-----------------|  
    |**Name**|**nvarchar(** 128 **)**|Tabellenname|  
    |**Besitzer**|**nvarchar(** 128 **)**|Tabellenbesitzer|  
    |**Typ**|**nvarchar(** 31 **)**|Tabellentyp|  
    |**Created_datetime**|**datetime**|Erstellungsdatum der Tabelle|  
  
     Depending on the database object specified, **sp_help** returns additional result sets.  
  
     If *name* is a system table, user table, or view, **sp_help** returns the following result sets. However, the result set that describes where the data file is located on a file group is not returned for a view.  
  
    -   Zusätzliches Resultset, das für Spaltenobjekte zurückgegeben wird:  
  
        |Spaltenname|Datentyp|Beschreibung|  
        |-----------------|---------------|-----------------|  
        |**Spaltenname**|**nvarchar(** 128 **)**|Name der Spalte.|  
        |**Typ**|**nvarchar(** 128 **)**|Datentyp der Spalte.|  
        |**Computed**|**varchar(** 35 **)**|Gibt an, ob die Werte in der Spalte berechnet werden: Ja oder nein.|  
        |**Länge**|**int**|Spaltenlänge in Bytes<br /><br /> Hinweis: Wenn der Datentyp der Spalte einen Typ mit umfangreichen Werten ist (**varchar(max)** , **nvarchar(max)** , **'varbinary(max)'** , oder **Xml**), wird der Wert als-1 angezeigt.|  
        |**prec**|**char(** 5 **)**|Spaltengenauigkeit|  
        |**Dezimalstellen**|**char(** 5 **)**|Dezimalstellen einer Spalte|  
        |**NULL zulassen**|**varchar(** 35 **)**|Gibt an, ob NULL-Werte in der Spalte zulässig sind: Ja oder nein.|  
        |**TrimTrailingBlanks**|**varchar(** 35 **)**|Nachfolgende Leerzeichen entfernen. Gibt Yes oder No zurück.|  
        |**FixedLenNullInSource**|**varchar(** 35 **)**|Nur aus Gründen der Abwärtskompatibilität beibehalten|  
        |**Sortierung**|**sysname**|Sortierung der Spalte. NULL für Nicht-Zeichen-Datentypen.|  
  
    -   Zusätzliches Resultset, das für Identitätsspalten zurückgegeben wird:  
  
        |Spaltenname|Datentyp|Beschreibung|  
        |-----------------|---------------|-----------------|  
        |**Identität**|**nvarchar(** 128 **)**|Name der Spalte, deren Datentyp als Identität deklariert wird|  
        |**Startwert**|**numeric**|Startwert für die Identitätsspalte|  
        |**Increment**|**numeric**|Schrittweite für Werte in dieser Spalte|  
        |**Not For Replication**|**int**|IDENTITY-Eigenschaft wird nicht erzwungen, wenn eine replikationsanmeldung wie z. B. **Sqlrepl**, fügt Daten in der Tabelle:<br /><br /> 1 = True<br /><br /> 0 = False|  
  
    -   Zusätzliches Resultset, das für Spalten zurückgegeben wird:  
  
        |Spaltenname|Datentyp|Beschreibung|  
        |-----------------|---------------|-----------------|  
        |**RowGuidCol**|**sysname**|Name der GUID-Spalte|  
  
    -   Zusätzliches Resultset, das für Dateigruppen zurückgegeben wird:  
  
        |Spaltenname|Datentyp|Beschreibung|  
        |-----------------|---------------|-----------------|  
        |**Data_located_on_filegroup**|**nvarchar(** 128 **)**|Dateigruppe, in dem die Daten gespeichert sind: Primär, sekundär oder Transaktionsprotokoll.|  
  
    -   Zusätzliches Resultset, das für Indizes zurückgegeben wird:  
  
        |Spaltenname|Datentyp|Beschreibung|  
        |-----------------|---------------|-----------------|  
        |**index_name**|**sysname**|Name des Indexes.|  
        |**Index_description**|**Varchar (** 210 **)**|Beschreibung des Index.|  
        |**index_keys**|**nvarchar(** 2078 **)**|Namen der Spalten, die für den Index verwendet werden. Gibt für speicheroptimierte xVelocity-columnstore-Indizes NULL zurück.|  
  
    -   Zusätzliches Resultset, das für Einschränkungen zurückgegeben wird:  
  
        |Spaltenname|Datentyp|Beschreibung|  
        |-----------------|---------------|-----------------|  
        |**constraint_type**|**nvarchar(** 146 **)**|Einschränkungstyp|  
        |**constraint_name**|**nvarchar(** 128 **)**|Der Name der Einschränkung.|  
        |**delete_action**|**nvarchar(** 9 **)**|Gibt an, ob die DELETE-Aktion: NO_ACTION, CASCADE, SET_NULL, SET_DEFAULT oder n/v.<br /><br /> Gilt nur für FOREIGN KEY-Einschränkungen.|  
        |**update_action**|**nvarchar(** 9 **)**|Gibt an, ob die UPDATE-Aktion: NO_ACTION, CASCADE, SET_NULL, SET_DEFAULT oder n/v.<br /><br /> Gilt nur für FOREIGN KEY-Einschränkungen.|  
        |**status_enabled**|**varchar(** 8 **)**|Gibt an, ob die Einschränkung aktiviert ist: Aktiviert, deaktiviert oder n/v.<br /><br /> Gilt nur für CHECK- und FOREIGN KEY-Einschränkungen.|  
        |**status_for_replication**|**Varchar (** 19 **)**|Zeigt an, ob die Einschränkung für die Replikation gilt.<br /><br /> Gilt nur für CHECK- und FOREIGN KEY-Einschränkungen.|  
        |**constraint_keys**|**nvarchar(** 2078 **)**|Die Namen der Spalten für die Einschränkung oder bei Standards und Regeln der Text, der den Standard oder die Regel definiert.|  
  
    -   Zusätzliches Resultset, das für verweisende Objekte zurückgegeben wird:  
  
        |Spaltenname|Datentyp|Beschreibung|  
        |-----------------|---------------|-----------------|  
        |**Die Tabelle wird durch verwiesen.**|**nvarchar(** 516 **)**|Identifiziert andere Datenbankobjekte, die auf die Tabelle verweisen.|  
  
    -   Zusätzliches Resultset, das für gespeicherte Prozeduren, Funktionen oder erweiterte gespeicherte Prozeduren zurückgegeben wird.  
  
        |Spaltenname|Datentyp|Beschreibung|  
        |-----------------|---------------|-----------------|  
        |**Parameter_name**|**nvarchar(** 128 **)**|Name des Parameters der gespeicherten Prozedur|  
        |**Typ**|**nvarchar(** 128 **)**|Datentyp des Parameters der gespeicherten Prozedur|  
        |**Länge**|**smallint**|Maximale physische Speicherlänge in Bytes|  
        |**prec**|**int**|Genauigkeit oder Gesamtzahl der Ziffern|  
        |**Dezimalstellen**|**int**|Die Anzahl der Ziffern rechts vom Dezimalzeichen|  
        |**Param_order**|**smallint**|Reihenfolge der Parameter|  
  
## <a name="remarks"></a>Hinweise  
 Die **Sp_help** für ein Objekt nur in der aktuellen Datenbank sucht.  
  
 Wenn *Namen* nicht angegeben ist, **Sp_help** Listen Objekt Objektnamen, Besitzer und Objekttypen für alle Objekte in der aktuellen Datenbank. **Sp_helptrigger** stellt Informationen zu Triggern bereit.  
  
 **Sp_help** macht nur Indexspalten; aus diesem Grund macht es keine Informationen über XML-Indizes oder räumliche Indizes verfügbar.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Der Benutzer muss mindestens eine Berechtigung verfügen, auf *Objname*. Um Spalteneinschränkungsschlüssel, Standards oder Regeln anzuzeigen, müssen Sie über die VIEW DEFINITION-Berechtigung für die Tabelle verfügen.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-returning-information-about-all-objects"></a>A. Zurückgeben von Informationen zu allen Objekten  
 Das folgende Beispiel führt Informationen zu jedem Objekt in der `master`-Datenbank auf.  
  
```  
USE master;  
GO  
EXEC sp_help;  
GO  
```  
  
### <a name="b-returning-information-about-a-single-object"></a>B. Zurückgeben von Informationen zu einem einzelnen Objekt  
 Das folgende Beispiel zeigt Informationen zur `Person`-Tabelle an.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_help 'Person.Person';  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Datenbank-Engine gespeicherten Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpindex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md)   
 [sp_helprotect &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.sysobjects &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysobjects-transact-sql.md)  
  
  
