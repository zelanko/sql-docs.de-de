---
title: Sp_table_validation (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_table_validation_TSQL
- sp_table_validation
helpviewer_keywords:
- sp_table_validation
ms.assetid: 31b25f9b-9b62-496e-a97e-441d5fd6e767
author: stevestein
ms.author: sstein
ms.openlocfilehash: 42d2535dedb1161a78362f17a1ad7c79ca49bb87
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096124"
---
# <a name="sptablevalidation-transact-sql"></a>sp_table_validation (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Gibt Zeilenanzahl- oder Prüfsummeninformationen für eine Tabelle oder indizierte Sicht zurück oder vergleicht die angegebenen Zeilenanzahl- oder Prüfsummeninformationen mit der angegebenen Tabelle oder indizierten Sicht. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank und auf dem Abonnenten für die Abonnementdatenbank ausgeführt. *Nicht für Oracle-Verleger unterstützt*.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_table_validation [ @table = ] 'table'  
    [ , [ @expected_rowcount = ] type_of_check_requested OUTPUT]  
    [ , [ @expected_checksum = ] expected_checksum OUTPUT]  
    [ , [ @rowcount_only = ] rowcount_only ]  
    [ , [ @owner = ] 'owner' ]  
    [ , [ @full_or_fast = ] full_or_fast ]  
    [ , [ @shutdown_agent = ] shutdown_agent ]  
    [ , [ @table_name = ] table_name ]  
    [ , [ @column_list = ] 'column_list' ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @table = ] 'table'` Ist der Name der Tabelle. *Tabelle* ist **Sysname**, hat keinen Standardwert.  
  
`[ @expected_rowcount = ] expected_rowcountOUTPUT` Gibt an, ob die erwartete Anzahl von Zeilen in der Tabelle zurückgegeben werden soll. *Expected_rowcount* ist **Int**, hat den Standardwert NULL. Mit NULL wird die tatsächliche Zeilenanzahl als Ausgabeparameter zurückgegeben. Wenn ein Wert angegeben wird, wird dieser mit der tatsächlichen Zeilenanzahl verglichen, um etwaige Unterschiede festzustellen.  
  
`[ @expected_checksum = ] expected_checksumOUTPUT` Gibt an, ob die erwartete Prüfsumme für die Tabelle zurückgegeben werden soll. *Expected_checksum* ist **numerischen**, hat den Standardwert NULL. Mit NULL wird die tatsächliche Prüfsumme als Ausgabeparameter zurückgegeben. Wenn ein Wert angegeben wird, wird dieser mit der tatsächlichen Prüfsumme verglichen, um etwaige Unterschiede festzustellen.  
  
`[ @rowcount_only = ] type_of_check_requested` Gibt an, welcher Typ von Prüfsumme oder Zeilenanzahl berechnet werden soll. *Type_of_check_requested* ist **Smallint**, hat den Standardwert **1**.  
  
 Wenn **0**, eine Zeilenzählung und eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 kompatible prüfsummenberechnung.  
  
 Wenn **1**, nur eine Zeilenzählung durchgeführt.  
  
 Wenn **2**, Zeilenanzahl und binäre Prüfsumme.  
  
`[ @owner = ] 'owner'` Ist der Name des Besitzers der Tabelle. *Besitzer* ist **Sysname**, hat den Standardwert NULL.  
  
`[ @full_or_fast = ] full_or_fast` Wird die Methode, die zum Berechnen der Zeilenanzahl verwendet wird. *Full_or_fast* ist **Tinyint**, hat den Standardwert **2**, und kann einen der folgenden Werte sein.  
  
|Wert|Description|  
|-----------|-----------------|  
|**0**|Führt eine vollständige Zählung mit COUNT(*) durch.|  
|**1**|Führt eine schnelle Zählung von **sysindexes.rows**. Zählen der Zeilen im **"sysindexes"** ist wesentlich schneller als das Zählen von Zeilen in der eigentlichen Tabelle. Aber da **"sysindexes"** nur verzögert aktualisiert, die Zeilenanzahl möglicherweise nicht ganz genau.|  
|**2** (Standardwert)|Führt eine bedingte schnelle Zählung durch, indem zunächst versucht wird, die schnelle Methode anzuwenden. Ergeben sich mit der schnellen Methode Unterschiede, wird die Methode für die vollständige Zählung verwendet. Wenn *Expected_rowcount* NULL ist und die gespeicherte Prozedur wird verwendet, um den Wert abzurufen, wird immer eine vollständige Zählung mit COUNT(*) verwendet.|  
  
`[ @shutdown_agent = ] shutdown_agent` Wenn der Verteilungs-Agent ausgeführt wird, **Sp_table_validation**, gibt an, ob der Verteilungs-Agent sofort nach dem Abschluss der Überprüfung heruntergefahren werden soll. *Shutdown_agent* ist **Bit**, hat den Standardwert **0**. Wenn **0**, Replikations-Agent nicht heruntergefahren. Wenn **1**Fehler 20578 wird ausgelöst, und der Replikations-Agent das Signal zum Herunterfahren. Dieser Parameter wird ignoriert, wenn **Sp_table_validation** direkt von einem Benutzer ausgeführt wird.  
  
`[ @table_name = ] table_name` Ist der Tabellenname der für ausgabemeldungen verwendeten Sicht. *TABLE_NAME* ist **Sysname**, hat den Standardwert **@table** .  
  
`[ @column_list = ] 'column_list'` Ist die Liste der Spalten, die in der Prüfsummenfunktion verwendet werden soll. *Column_list* ist **nvarchar(4000)** , hat den Standardwert NULL. Aktiviert die Überprüfung von Mergeartikeln, um eine Spaltenliste anzugeben, die berechnete Spalten und Timestampspalten ausschließt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Wenn die Prüfsumme in der Tabelle ausführen, eine Prüfsumme überprüfen und die erwartete Prüfsumme gleich ist. **Sp_table_validation** gibt eine Meldung, dass die Tabelle die Überprüfung bestanden. Andernfalls wird eine Meldung zurückgegeben, die besagt, dass die Tabelle möglicherweise nicht mehr synchronisiert ist, und der Unterschied zwischen der erwarteten und der tatsächlichen Zeilenanzahl wird angezeigt.  
  
 Wenn die Anzahl in der Tabelle ausführen, eine Zeilenanzahl überprüfen und die erwartete Anzahl von Zeilen gleich ist. **Sp_table_validation** gibt eine Meldung, dass die Tabelle die Überprüfung bestanden. Andernfalls wird eine Meldung zurückgegeben, die besagt, dass die Tabelle möglicherweise nicht mehr synchronisiert ist, und der Unterschied zwischen der erwarteten und der tatsächlichen Zeilenanzahl wird angezeigt.  
  
## <a name="remarks"></a>Hinweise  
 **Sp_table_validation** wird in allen Replikationstypen verwendet. **Sp_table_validation** wird für Oracle-Verlegern nicht unterstützt.  
  
 Der Prüfsummenalgorithmus berechnet eine zyklische 32-Bit-Redundanzprüfung (CRC, Redundancy Check) des gesamten Zeilenbilds auf der Seite. Er überprüft Spalten nicht selektiv und kann nicht für eine Sicht oder eine vertikale Partition der Tabelle ausgeführt werden. Darüber hinaus lässt die prüfsummenberechnung den Inhalt der **Text** und **Image** -Spalten (entwurfsbedingt).  
  
 Beim Ausführen einer Prüfsummenberechnung muss die Struktur der Tabelle auf den beiden Servern identisch sein. Das heißt, für die Tabellen müssen dieselben Spalten in derselben Reihenfolge vorhanden sein, dieselben Datentypen und Längen, und sie müssen dieselben NULL- bzw. NOT NULL-Bedingungen aufweisen. Wenn auf dem Verleger beispielsweise CREATE TABLE und dann ALTER TABLE zum Hinzufügen von Spalten ausgeführt wurden, aber das auf dem Abonnenten angewendete Skript ein einfaches CREATE für eine Tabelle darstellt, dann ist die Struktur nicht dieselbe. Wenn Sie nicht sicher sind, dass die Struktur der beiden Tabellen identisch ist, sehen Sie sich [Syscolumns](../../relational-databases/system-compatibility-views/sys-syscolumns-transact-sql.md) und vergewissern Sie sich, dass der Offset in den einzelnen Tabellen identisch ist.  
  
 Gleitkommawerte sind wahrscheinlich Prüfsumme Unterschiede zu generieren, wenn im Zeichenmodus **Bcp** verwendet wurde, dies ist der Fall, wenn die Veröffentlichung nicht- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten. Diese Unterschiede sind durch geringfügige und unvermeidbare Genauigkeitsunterschiede bedingt, die auftreten, wenn Konvertierungen in den und aus dem Zeichenmodus durchgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Auszuführende **Sp_table_validation**, benötigen Sie SELECT-Berechtigungen für die Tabelle, die überprüft wird.  
  
## <a name="see-also"></a>Siehe auch  
 [CHECKSUM &#40;Transact-SQL&#41;](../../t-sql/functions/checksum-transact-sql.md)   
 [@@ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/rowcount-transact-sql.md)   
 [sp_article_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)   
 [sp_publication_validation &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
