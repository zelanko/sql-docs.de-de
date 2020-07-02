---
title: sp_help (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 57a435db1aca6c2ab9f093792e26f7e88dcbf21a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85727177"
---
# <a name="sp_help-transact-sql"></a>sp_help (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Meldet Informationen zu einem Datenbankobjekt (alle in dersys.sys-Objekt Kompatibilitäts Sicht aufgeführten **Objekte** ), einen benutzerdefinierten Datentyp oder einen-Datentyp.  
  
 
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_help [ [ @objname = ] 'name' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @objname = ] 'name'`Der Name eines beliebigen Objekts in **sysobjects** oder eines beliebigen benutzerdefinierten Datentyps in der **systypes** -Tabelle. *Name ist vom Datentyp* **nvarchar (** 776 **)** und hat den Standardwert NULL. Datenbanknamen sind nicht zulässig.  Zwei bis drei Teilnamen müssen eingeschränkt werden, z.B. „Person.AddressType“ oder [Person.AddressType].   
   
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="result-sets"></a>Resultsets  
 Die Resultsets, die zurückgegeben werden, hängen davon ab, ob der *Name* angegeben ist, wann er angegeben ist und welches Datenbankobjekt es ist.  
  
1.  Wenn **sp_help** ohne Argumente ausgeführt wird, werden zusammenfassende Informationen zu Objekten aller Typen zurückgegeben, die in der aktuellen Datenbank vorhanden sind.  
  
    |Spaltenname|Datentyp|BESCHREIBUNG|  
    |-----------------|---------------|-----------------|  
    |**Name**|**nvarchar (** 128 **)**|Objektname|  
    |**Besitzer**|**nvarchar (** 128 **)**|Objektbesitzer (Dies ist der Datenbankprinzipal, der das Objekt besitzt. Wird standardmäßig auf den Besitzer des Schemas festgelegt, das das Objekt enthält.)|  
    |**Object_type**|**nvarchar (** 31 **)**|Objekttyp|  
  
2.  Wenn *Name* ein [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datentyp oder ein benutzerdefinierter Datentyp ist, gibt **sp_help** dieses Resultset zurück.  
  
    |Spaltenname|Datentyp|BESCHREIBUNG|  
    |-----------------|---------------|-----------------|  
    |**Type_name**|**nvarchar (** 128 **)**|Name des Datentyps.|  
    |**Storage_type**|**nvarchar (** 128 **)**|Name des [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Typs|  
    |**Länge**|**smallint**|Physische Länge des Datentyps (in Bytes)|  
    |**Prec**|**int**|Genauigkeit (Gesamtzahl der Ziffern)|  
    |**Skalierung**|**int**|Anzahl der Stellen nach dem Dezimaltrennzeichen|  
    |**NULL zulassen**|**varchar (** 35 **)**|Zeigt an, ob NULL-Werte zulässig sind: Yes oder No.|  
    |**Default_name**|**nvarchar (** 128 **)**|Name eines an diesen Typ gebundenen Standards.<br /><br /> NULL = Es ist kein Standard gebunden.|  
    |**Rule_name**|**nvarchar (** 128 **)**|Name einer an diesen Typ gebundenen Regel.<br /><br /> NULL = Es ist kein Standard gebunden.|  
    |**Sortierung**|**sysname**|Sortierung des Datentyps. NULL für Nicht-Zeichen-Datentypen|  
  
3.  Wenn *Name* ein anderes Datenbankobjekt als ein-Datentyp ist, gibt **sp_help** dieses Resultset und auch zusätzliche Resultsets zurück, basierend auf dem angegebenen Objekttyp.  

    |Spaltenname|Datentyp|BESCHREIBUNG|  
    |-----------------|---------------|-----------------|  
    |**Name**|**nvarchar (** 128 **)**|Tabellenname|  
    |**Besitzer**|**nvarchar (** 128 **)**|Tabellenbesitzer|  
    |**Type**|**nvarchar (** 31 **)**|Tabellentyp|  
    |**Created_datetime**|**datetime**|Erstellungsdatum der Tabelle|  
  
     Abhängig vom angegebenen Datenbankobjekt gibt **sp_help** zusätzliche Resultsets zurück.  
  
     Wenn *Name* eine Systemtabelle, eine Benutzertabelle oder eine Sicht ist, gibt **sp_help** die folgenden Resultsets zurück. Das Resultset, das beschreibt, wo sich die Datendateien in einer Dateigruppe befinden, wird jedoch nicht für eine Sicht zurückgegeben.  
  
    -   Zusätzliches Resultset, das für Spaltenobjekte zurückgegeben wird:  
  
        |Spaltenname|Datentyp|BESCHREIBUNG|  
        |-----------------|---------------|-----------------|  
        |**Column_name**|**nvarchar (** 128 **)**|Spaltenname.|  
        |**Type**|**nvarchar (** 128 **)**|Der Spaltendatentyp.|  
        |**Berechnete**|**varchar (** 35 **)**|Zeigt an, ob die Werte in der Spalte berechnet werden: Yes oder No.|  
        |**Länge**|**int**|Spaltenlänge in Bytes<br /><br /> Hinweis: Wenn der Spaltendatentyp ein Typ mit umfangreichen Werten (**varchar (max)**, **nvarchar (max)**, **varbinary (max)** oder **XML**) ist, wird der Wert als-1 angezeigt.|  
        |**Prec**|**char (** 5 **)**|Spaltengenauigkeit|  
        |**Skalierung**|**char (** 5 **)**|Dezimalstellen einer Spalte|  
        |**NULL zulassen**|**varchar (** 35 **)**|Zeigt an, ob in der Spalte NULL-Werte zulässig sind: Yes oder No.|  
        |**TrimTrailingBlanks**|**varchar (** 35 **)**|Nachfolgende Leerzeichen entfernen. Gibt Yes oder No zurück.|  
        |**FixedLenNullInSource**|**varchar (** 35 **)**|Nur aus Gründen der Abwärtskompatibilität beibehalten|  
        |**Sortierung**|**sysname**|Sortierung der Spalte. NULL für Nicht-Zeichen-Datentypen.|  
  
    -   Zusätzliches Resultset, das für Identitätsspalten zurückgegeben wird:  
  
        |Spaltenname|Datentyp|BESCHREIBUNG|  
        |-----------------|---------------|-----------------|  
        |**Identität**|**nvarchar (** 128 **)**|Name der Spalte, deren Datentyp als Identität deklariert wird|  
        |**Seed**|**numeric**|Startwert für die Identitätsspalte|  
        |**Inkrement**|**numeric**|Schrittweite für Werte in dieser Spalte|  
        |**Nicht für Replikation**|**int**|Die Identity-Eigenschaft wird nicht erzwungen, wenn eine Replikations Anmeldung, z. b. **sqlrepl**, Daten in die Tabelle einfügt:<br /><br /> 1 = True<br /><br /> 0 = False|  
  
    -   Zusätzliches Resultset, das für Spalten zurückgegeben wird:  
  
        |Spaltenname|Datentyp|BESCHREIBUNG|  
        |-----------------|---------------|-----------------|  
        |**RowGuidCol**|**sysname**|Name der GUID-Spalte|  
  
    -   Zusätzliches Resultset, das für Dateigruppen zurückgegeben wird:  
  
        |Spaltenname|Datentyp|BESCHREIBUNG|  
        |-----------------|---------------|-----------------|  
        |**Data_located_on_filegroup**|**nvarchar (** 128 **)**|Die Dateigruppe, in der sich die Daten befinden: primäre oder sekundäre Dateigruppe oder Transaktionsprotokoll|  
  
    -   Zusätzliches Resultset, das für Indizes zurückgegeben wird:  
  
        |Spaltenname|Datentyp|BESCHREIBUNG|  
        |-----------------|---------------|-----------------|  
        |**index_name**|**sysname**|Indexname.|  
        |**Index_description**|**varchar (** 210 **)**|Beschreibung des Index.|  
        |**index_keys**|**nvarchar (** 2078 **)**|Namen der Spalten, die für den Index verwendet werden. Gibt für speicheroptimierte xVelocity-columnstore-Indizes NULL zurück.|  
  
    -   Zusätzliches Resultset, das für Einschränkungen zurückgegeben wird:  
  
        |Spaltenname|Datentyp|BESCHREIBUNG|  
        |-----------------|---------------|-----------------|  
        |**constraint_type**|**nvarchar (** 146 **)**|Einschränkungstyp|  
        |**constraint_name**|**nvarchar (** 128 **)**|Der Name der Einschränkung.|  
        |**delete_action**|**nvarchar (** 9 **)**|Zeigt den Wert der DELETE-Aktion an: NO_ACTION, CASCADE, SET_NULL, SET_DEFAULT oder N/A.<br /><br /> Gilt nur für FOREIGN KEY-Einschränkungen.|  
        |**update_action**|**nvarchar (** 9 **)**|Zeigt den Wert der UPDATE-Aktion an: NO_ACTION, CASCADE, SET_NULL, SET_DEFAULT oder N/A.<br /><br /> Gilt nur für FOREIGN KEY-Einschränkungen.|  
        |**status_enabled**|**varchar (** 8 **)**|Zeigt an, ob die Einschränkung aktiviert ist: Enabled (aktiviert), Disabled (deaktiviert) oder N/A (NV).<br /><br /> Gilt nur für CHECK- und FOREIGN KEY-Einschränkungen.|  
        |**status_for_replication**|**varchar (** 19 **)**|Zeigt an, ob die Einschränkung für die Replikation gilt.<br /><br /> Gilt nur für CHECK- und FOREIGN KEY-Einschränkungen.|  
        |**constraint_keys**|**nvarchar (** 2078 **)**|Die Namen der Spalten für die Einschränkung oder bei Standards und Regeln der Text, der den Standard oder die Regel definiert.|  
  
    -   Zusätzliches Resultset, das für verweisende Objekte zurückgegeben wird:  
  
        |Spaltenname|Datentyp|BESCHREIBUNG|  
        |-----------------|---------------|-----------------|  
        |**Table is referenced by**|**nvarchar (** 516 **)**|Identifiziert andere Datenbankobjekte, die auf die Tabelle verweisen.|  
  
    -   Zusätzliches Resultset, das für gespeicherte Prozeduren, Funktionen oder erweiterte gespeicherte Prozeduren zurückgegeben wird.  
  
        |Spaltenname|Datentyp|BESCHREIBUNG|  
        |-----------------|---------------|-----------------|  
        |**Parameter_name**|**nvarchar (** 128 **)**|Name des Parameters der gespeicherten Prozedur|  
        |**Type**|**nvarchar (** 128 **)**|Datentyp des Parameters der gespeicherten Prozedur|  
        |**Länge**|**smallint**|Maximale physische Speicherlänge in Bytes|  
        |**Prec**|**int**|Genauigkeit oder Gesamtzahl der Ziffern|  
        |**Skalierung**|**int**|Die Anzahl der Ziffern rechts vom Dezimalzeichen|  
        |**Param_order**|**smallint**|Reihenfolge der Parameter|  
  
## <a name="remarks"></a>Hinweise  
 Die Prozedur **sp_help** sucht nur in der aktuellen Datenbank nach einem Objekt.  
  
 Wenn *Name* nicht angegeben wird, werden in **sp_help** Objektnamen, Besitzer und Objekttypen für alle Objekte in der aktuellen Datenbank aufgelistet. **sp_helptrigger** enthält Informationen zu Triggern.  
  
 **sp_help** macht nur sortierbare Index Spalten verfügbar. Daher werden keine Informationen über XML-Indizes oder räumliche Indizes bereitgestellt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der **public** -Rolle. Der Benutzer muss mindestens eine Berechtigung für *objname*besitzen. Um Spalteneinschränkungsschlüssel, Standards oder Regeln anzuzeigen, müssen Sie über die VIEW DEFINITION-Berechtigung für die Tabelle verfügen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpindex &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md)   
 [sp_helprotect &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.sysObjekte &#40;Transact-SQL-&#41;](../../relational-databases/system-compatibility-views/sys-sysobjects-transact-sql.md)  
  
  
