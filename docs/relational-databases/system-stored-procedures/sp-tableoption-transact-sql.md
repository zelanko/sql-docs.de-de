---
description: sp_tableoption (Transact-SQL)
title: sp_tableoption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tableoption_TSQL
- sp_tableoption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tableoption
ms.assetid: 0a57462c-1057-4c7d-bce3-852cc898341d
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3920007400a4ae407303f3fddff50c0a5ace2328
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534802"
---
# <a name="sp_tableoption-transact-sql"></a>sp_tableoption (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Legt Optionswerte für benutzerdefinierte Tabellen fest. sp_tableoption kann verwendet werden, um das Verhalten von Tabellen in Zeilen mit Spalten vom Typ **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **XML**, **Text**, **ntext**, **Image**oder große benutzerdefinierte Spalten zu steuern.  
  
> [!IMPORTANT]  
>  Die Funktion text in row wird in einer zukünftigen Version von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] entfernt. Um Daten mit umfangreichen Werten zu speichern, empfiehlt es sich, die Datentypen **varchar (max)**, **nvarchar (max)** und **varbinary (max)** zu verwenden.  
  

 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_tableoption [ @TableNamePattern = ] 'table'   
     , [ @OptionName = ] 'option_name'   
     ,[ @OptionValue =] 'value'  
```  
  
## <a name="arguments"></a>Argumente  
 [ @TableNamePattern =] '*Tabelle*'  
 Der qualifizierte oder nicht qualifizierte Name einer benutzerdefinierten Datenbanktabelle. Bei Angabe eines voll gekennzeichneten Tabellennamens (einschließlich eines Datenbanknamens) muss der Datenbankname der Name der aktuellen Datenbank sein. Tabellenoptionen für mehrere Tabellen können nicht gleichzeitig festgelegt werden. *Table ist vom Datentyp* **nvarchar (776)** und hat keinen Standardwert.  
  
 [ @OptionName =] '*option_name*'  
 Der Name einer Tabellenoption. *option_name* ist vom Datentyp **varchar (35)** und hat den Standardwert NULL. *option_name* kann einen der folgenden Werte aufweisen.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|table lock on bulk load|Eine deaktivierte Option (Standard) führt dazu, dass der Massenladevorgang auf benutzerdefinierten Tabellen Zeilensperren erhält. Wenn diese Option aktiviert ist, erhalten die Massenladevorgänge auf benutzerdefinierten Tabellen eine Massenupdatesperre.|  
|insert row lock|Wird nicht mehr unterstützt.<br /><br /> Diese Option wirkt sich nicht auf das Sperrverhalten von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] aus und ist nur aus Gründen der Kompatibilität mit vorhandenen Skripts und Prozeduren enthalten.|  
|text in row|Beim Wert OFF oder 0 (deaktivierte Option, Standard) wird das aktuelle Verhalten nicht geändert, und es gibt keine BLOBs in Zeilen.<br /><br /> Wenn angegeben und @OptionValue auf on (aktiviert) oder einen ganzzahligen Wert von 24 bis 7000, werden neue **Text**-, **ntext**-oder **Image** -Zeichen folgen direkt in der Daten Zeile gespeichert. Alle vorhandenen BLOB-Daten (Binary Large Object: **Text**, **ntext**oder **Image** ) werden in das Format Text in row geändert, wenn der BLOB-Wert aktualisiert wird. Weitere Informationen finden Sie in den Hinweisen.|  
|LARGE VALUE TYPES OUT OF ROW|1 = **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **XML** und große benutzerdefinierte Typen (User-Defined Type, UDT) in der Tabelle werden außerhalb der Zeile gespeichert, mit einem 16-Byte-Zeiger auf den Stamm.<br /><br /> 0 = **varchar (max)**, **nvarchar (max)**, **varbinary (max)**, **XML** und große UDT-Werte werden direkt in der Daten Zeile gespeichert, bis zu einem Limit von 8000 Bytes, und solange der Wert in den Datensatz passt. Überschreitet der Wert die Größe des Datensatzes, wird ein Zeiger innerhalb der Zeilen gespeichert, während der Rest außerhalb der Zeilen im LOB-Speicherbereich gespeichert wird. Der Standardwert ist 0 (null).<br /><br /> Großer benutzerdefinierter Typ (User-Defined Type, UDT) gilt für: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher. <br /><br /> Verwenden Sie die Option TEXTIMAGE_ON von [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) , um einen Speicherort für die Speicherung großer Datentypen anzugeben. |  
|vardecimal-Speicherformat|**Gilt für**:  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höher.<br /><br /> Bei TRUE, ON oder 1 ist die festgelegte Tabelle für das vardecimal-Speicherformat aktiviert. Bei FALSE, OFF oder 0 ist die Tabelle für das vardecimal-Speicherformat nicht aktiviert. Das vardecimal--Speicherformat kann nur aktiviert werden, wenn die Datenbank mit [sp_db_vardecimal_storage_format](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md)für das vardecimal--Speicherformat aktiviert wurde. In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] und höheren Versionen ist das **vardecimal-** -Speicherformat veraltet. Verwenden Sie stattdessen die ROW-Komprimierung. Weitere Informationen finden Sie unter [Data Compression](../../relational-databases/data-compression/data-compression.md). Der Standardwert ist 0 (null).|  
  
 [ @OptionValue =] '*Wert*'  
 Gibt an, ob der *option_name* aktiviert (true, on oder 1) oder deaktiviert (false, Off oder 0) ist. der Wert ist vom Datentyp **varchar (12)** und hat keinen Standard *Wert* . beim *Wert* wird Groß-/Kleinschreibung  
  
 Gültige Werte für die text in row-Option sind: 0, ON, OFF oder eine Ganzzahl zwischen 24 und 7000. Wenn *value* auf on gesetzt ist, lautet der Standardwert 256 Bytes.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Fehlernummer (Fehler)  
  
## <a name="remarks"></a>Hinweise  
 sp_tableoption kann nur verwendet werden, um die Optionswerte für benutzerdefinierte Tabellen festzulegen. Verwenden Sie OBJECTPROPERTY, oder führen Sie die Abfrage sys. Tables aus, um Tabellen Eigenschaften anzuzeigen.  
  
 Die text in row-Option von sp_tableoption kann nur für Tabellen aktiviert oder deaktiviert werden, die Textspalten enthalten. Wenn die Tabelle nicht über eine Textspalte verfügt, löst [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] einen Fehler aus.  
  
 Wenn die Text in row-Option aktiviert ist, @OptionValue können Benutzer mit dem-Parameter die maximale Größe angeben, die in einer Zeile für ein BLOB gespeichert werden soll. Der Standardwert ist 256 Bytes. Gültige Werte sind 24 bis 7000 Bytes.  
  
 **Text**-, **ntext**-oder **Image** -Zeichen folgen werden in der Daten Zeile gespeichert, wenn die folgenden Bedingungen zutreffen:  
  
-   text in row ist aktiviert.  
  
-   Die Länge der Zeichenfolge ist kürzer als die in angegebene Grenze. @OptionValue  
  
-   Es steht genügend Speicherplatz in der Datenzeile zur Verfügung.  
  
 Wenn BLOB-Zeichen folgen in der Daten Zeile gespeichert werden, kann das Lesen und Schreiben von **Text**-, **ntext**-oder **Image** -Zeichen folgen so schnell wie das Lesen oder Schreiben von Zeichen-und Binär Zeichenfolgen sein. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] kann nicht auf separate Seiten zugreifen, um die BLOB-Zeichenfolge zu lesen oder zu schreiben.  
  
 Wenn eine **Text**-, **ntext**-oder **Image** -Zeichenfolge größer ist als die angegebene Grenze oder der verfügbare Speicherplatz in der Zeile, werden Zeiger stattdessen in der Zeile gespeichert. Die Bedingungen zum Speichern der BLOB-Zeichenfolgen sind jedoch trotzdem gültig: Für die Zeiger muss genügend Speicherplatz in der Datenzeile vorhanden sein.  
  
 BLOB-Zeichenfolgen und -Zeiger, die in der Zeile einer Tabelle gespeichert werden, werden ähnlich wie Zeichenfolgen mit variabler Länge behandelt. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet nur so viele Bytes, wie erforderlich sind, um die Zeichenfolge oder den Zeiger zu speichern.  
  
 Vorhandene BLOB-Zeichenfolgen werden nicht sofort konvertiert, wenn text in row aktiviert ist. Die Zeichenfolgen werden erst konvertiert, wenn sie aktualisiert werden. Wenn der Grenzwert für Text in row-Optionen zunimmt, werden die **Text**-, **ntext**-oder **Image** -Zeichen folgen, die sich bereits in der Daten Zeile befinden, nicht konvertiert, um den neuen Grenzwert bis zum Aktualisierungs Zeitpunkt einzuhalten.  
  
> [!NOTE]  
>  Wenn die text in row-Option deaktiviert oder der Grenzwert für diese Option verringert wird, müssen alle BLOBs konvertiert werden. Dieser Vorgang kann je nach der Anzahl der zu konvertierenden BLOB-Zeichenfolgen viel Zeit in Anspruch nehmen. Während des Konvertierungsvorgangs ist die Tabelle gesperrt.  
  
 Für eine Tabellenvariable sowie eine Funktion, die eine Tabellenvariable zurückgibt, ist die text in row-Option automatisch mit dem inline limit-Standardwert von 256 aktiviert. Diese Option kann nicht geändert werden.  
  
 Die Option text in row unterstützt die Funktionen TEXTPTR, WRITETEXT, UPDATETEXT und READTEXT. Benutzer können Teile eines BLOBs mit der SUBSTRING()-Funktion lesen, sollten jedoch berücksichtigen, dass Textzeiger in Zeilen andere Grenzwerte für Dauer und Anzahl haben als andere Textzeiger.  
  
 Wenn Sie eine Tabelle vom vardecimal-Speicherformat zurück in das normale decimal-Speicherformat konvertieren möchten, muss sich die Datenbank im SIMPLE-Wiederherstellungsmodus befinden. Durch das Ändern des Wiederherstellungsmodus wird die Protokollkette für Sicherungszwecke unterbrochen. Daher sollten Sie eine vollständige Datenbanksicherung erstellen, nachdem Sie das vardecimal-Speicherformat aus einer Tabelle entfernt haben.  
  
 Wenn Sie eine vorhandene LOB-Datentyp Spalte (Text, ntext oder Image) in kleine bis mittlere große Werttypen (varchar (max), nvarchar (max) oder varbinary (max)) ändern und die meisten Anweisungen nicht auf die Spalten mit großen Werttypen in Ihrer Umgebung verweisen, sollten Sie **large_value_types_out_of_row** in 1 ändern, um **eine** optimale Leistung zu erzielen. Wenn der Wert der **large_value_types_out_of_row** Option geändert wird, werden die vorhandenen Werte varchar (max), nvarchar (max), varbinary (max) und XML nicht sofort konvertiert. Der Speicherung der Zeichenfolgen ändert sich, wenn diese anschließend aktualisiert werden. Alle neuen Werte, die in eine Tabelle eingefügt werden, werden gemäß der aktivierten Tabellenoption gespeichert. Erstellen Sie für unmittelbare Ergebnisse entweder eine Kopie der Daten, und füllen Sie dann die Tabelle erneut aus, nachdem Sie die **large_value_types_out_of_row** Einstellung geändert haben, oder aktualisieren Sie jede kleine bis mittlere Spalte mit großen Werttypen auf sich selbst, damit die Speicherung der Zeichen folgen mit der gültigen Tabellen Option geändert wird. Erstellen Sie die Indizes für die Tabelle nach der Aktualisierung oder Neuauffüllung neu, um die Tabelle zu komprimieren. 
    
  
## <a name="permissions"></a>Berechtigungen  
 Für die Ausführung von sp_tableoption ist die ALTER-Berechtigung für die Tabelle erforderlich.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-storing-xml-data-out-of-the-row"></a>A. Speichern von XML-Daten außerhalb der Zeile  
 Im folgenden Beispiel wird angegeben, dass die **XML** -Daten in der `HumanResources.JobCandidate` Tabelle außerhalb der Zeile gespeichert werden.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_tableoption 'HumanResources.JobCandidate', 'large value types out of row', 1;  
```  
  
### <a name="b-enabling-vardecimal-storage-format-on-a-table"></a>B. Aktivieren des vardecimal-Speicherformats für eine Tabelle  
 Im folgenden Beispiel wird die- `Production.WorkOrderRouting` Tabelle so geändert, dass der- `decimal` Datentyp im `vardecimal` Speicherformat gespeichert wird.  

```sql  
USE master;  
GO  
-- The database must be enabled for vardecimal storage format  
-- before a table can be enabled for vardecimal storage format  
EXEC sp_db_vardecimal_storage_format 'AdventureWorks2012', 'ON';  
GO  
USE AdventureWorks2012;  
GO  
EXEC sp_tableoption 'Production.WorkOrderRouting',   
   'vardecimal storage format', 'ON';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [sys.tables &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Datenbank-Engine gespeicherter Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
