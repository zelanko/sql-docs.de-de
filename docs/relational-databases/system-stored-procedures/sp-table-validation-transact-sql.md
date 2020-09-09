---
description: sp_table_validation (Transact-SQL)
title: sp_table_validation (Transact-SQL) | Microsoft-Dokumentation
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 88ee13025153fff3018fadfa8d64becf7a534303
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545927"
---
# <a name="sp_table_validation-transact-sql"></a>sp_table_validation (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

  Gibt Zeilenanzahl- oder Prüfsummeninformationen für eine Tabelle oder indizierte Sicht zurück oder vergleicht die angegebenen Zeilenanzahl- oder Prüfsummeninformationen mit der angegebenen Tabelle oder indizierten Sicht. Diese gespeicherte Prozedur wird auf dem Verleger für die Veröffentlichungsdatenbank und auf dem Abonnenten für die Abonnementdatenbank ausgeführt. *Wird für Oracle-Verleger nicht unterstützt*.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
`[ @table = ] 'table'` Der Name der Tabelle. *Table* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @expected_rowcount = ] expected_rowcountOUTPUT` Gibt an, ob die erwartete Anzahl von Zeilen in der Tabelle zurückgegeben werden soll. *expected_rowcount* ist vom Datentyp **int**und hat den Standardwert NULL. Mit NULL wird die tatsächliche Zeilenanzahl als Ausgabeparameter zurückgegeben. Wenn ein Wert angegeben wird, wird dieser mit der tatsächlichen Zeilenanzahl verglichen, um etwaige Unterschiede festzustellen.  
  
`[ @expected_checksum = ] expected_checksumOUTPUT` Gibt an, ob die erwartete Prüfsumme für die Tabelle zurückgegeben werden soll. *expected_checksum* ist **numerisch**und hat den Standardwert NULL. Mit NULL wird die tatsächliche Prüfsumme als Ausgabeparameter zurückgegeben. Wenn ein Wert angegeben wird, wird dieser mit der tatsächlichen Prüfsumme verglichen, um etwaige Unterschiede festzustellen.  
  
`[ @rowcount_only = ] type_of_check_requested` Gibt an, welche Art von Prüfsumme oder Zeilen Anzahl durchgeführt werden soll. *type_of_check_requested* ist vom Datentyp **smallint**. der Standardwert ist **1**.  
  
 Wenn der Wert **0**ist, führen Sie eine Zeilen Anzahl und eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7,0-kompatible Prüfsumme aus.  
  
 Wenn **1**, wird nur eine Überprüfung der Zeilen Anzahl durchgeführt.  
  
 Wenn **2**, führen Sie eine Zeilen Anzahl und eine binäre Prüfsumme aus.  
  
`[ @owner = ] 'owner'` Der Name des Besitzers der Tabelle. *Owner* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL.  
  
`[ @full_or_fast = ] full_or_fast` Die Methode, die zum Berechnen der Zeilen Anzahl verwendet wird. *full_or_fast* ist vom Datentyp **tinyint**. der Standardwert ist **2**. die folgenden Werte sind möglich.  
  
|Wert|BESCHREIBUNG|  
|-----------|-----------------|  
|**0**|Führt eine vollständige Zählung mit COUNT(*) durch.|  
|**1**|Führt eine schnelle Anzahl von **sysindexes. Rows**aus. Das zählen von Zeilen in **sysindexes** ist wesentlich schneller als das zählen der Zeilen in der eigentlichen Tabelle. Da **sysindexes** jedoch verzögert aktualisiert wird, ist die Zeilen Anzahl möglicherweise nicht korrekt.|  
|**2** (Standardwert)|Führt eine bedingte schnelle Zählung durch, indem zunächst versucht wird, die schnelle Methode anzuwenden. Ergeben sich mit der schnellen Methode Unterschiede, wird die Methode für die vollständige Zählung verwendet. Wenn *expected_rowcount* NULL ist und die gespeicherte Prozedur verwendet wird, um den Wert zu erhalten, wird immer eine vollständige Anzahl (*) verwendet.|  
  
`[ @shutdown_agent = ] shutdown_agent` Wenn die Verteilungs-Agent **sp_table_validation**ausgeführt wird, gibt an, ob die Verteilungs-Agent sofort nach Abschluss der Überprüfung heruntergefahren werden soll. *shutdown_agent* ist vom Typ **Bit**. der Standardwert ist **0**. Bei **0**wird der Replikations-Agent nicht heruntergefahren. Wenn der Wert **1**ist, wird Fehler 20578 ausgelöst, und der Replikations-Agent wird zum Herunterfahren signalisiert. Dieser Parameter wird ignoriert, wenn **sp_table_validation** direkt von einem Benutzer ausgeführt wird.  
  
`[ @table_name = ] table_name` Der Tabellenname der Sicht, die für Ausgabemeldungen verwendet wird. *table_name* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert ** \@ Table**.  
  
`[ @column_list = ] 'column_list'` Die Liste der Spalten, die in der Prüfsummen Funktion verwendet werden sollen. *column_list* ist vom Datentyp **nvarchar (4000)** und hat den Standardwert NULL. Aktiviert die Überprüfung von Mergeartikeln, um eine Spaltenliste anzugeben, die berechnete Spalten und Timestampspalten ausschließt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 Wenn eine Prüfsummen Überprüfung durchgeführt wird und die erwartete Prüfsumme der Prüfsumme in der Tabelle gleicht, gibt **sp_table_validation** eine Meldung zurück, dass die Tabelle die Überprüfung der Prüfsumme bestanden hat. Andernfalls wird eine Meldung zurückgegeben, die besagt, dass die Tabelle möglicherweise nicht mehr synchronisiert ist, und der Unterschied zwischen der erwarteten und der tatsächlichen Zeilenanzahl wird angezeigt.  
  
 Wenn die Überprüfung der Zeilen Anzahl und die erwartete Anzahl von Zeilen der Anzahl in der Tabelle entsprechen, gibt **sp_table_validation** eine Meldung zurück, dass die Tabelle die Überprüfung der Zeilen Anzahl bestanden hat. Andernfalls wird eine Meldung zurückgegeben, die besagt, dass die Tabelle möglicherweise nicht mehr synchronisiert ist, und der Unterschied zwischen der erwarteten und der tatsächlichen Zeilenanzahl wird angezeigt.  
  
## <a name="remarks"></a>Hinweise  
 **sp_table_validation** wird bei allen Replikations Typen verwendet. **sp_table_validation** wird für Oracle-Verleger nicht unterstützt.  
  
 Der Prüfsummenalgorithmus berechnet eine zyklische 32-Bit-Redundanzprüfung (CRC, Redundancy Check) des gesamten Zeilenbilds auf der Seite. Er überprüft Spalten nicht selektiv und kann nicht für eine Sicht oder eine vertikale Partition der Tabelle ausgeführt werden. Außerdem überspringt die Prüfsumme den Inhalt von **Text** -und **Image** -Spalten (Entwurfs bedingt).  
  
 Beim Ausführen einer Prüfsummenberechnung muss die Struktur der Tabelle auf den beiden Servern identisch sein. Das heißt, für die Tabellen müssen dieselben Spalten in derselben Reihenfolge vorhanden sein, dieselben Datentypen und Längen, und sie müssen dieselben NULL- bzw. NOT NULL-Bedingungen aufweisen. Wenn auf dem Verleger beispielsweise CREATE TABLE und dann ALTER TABLE zum Hinzufügen von Spalten ausgeführt wurden, aber das auf dem Abonnenten angewendete Skript ein einfaches CREATE für eine Tabelle darstellt, dann ist die Struktur nicht dieselbe. Wenn Sie nicht sicher sind, dass die Struktur der beiden Tabellen identisch ist, betrachten Sie [syscolumns](../../relational-databases/system-compatibility-views/sys-syscolumns-transact-sql.md) , und vergewissern Sie sich, dass der Offset in den einzelnen Tabellen identisch ist.  
  
 Gleit Komma Werte generieren wahrscheinlich Prüfsummen Unterschiede, wenn **bcp** im Zeichenmodus verwendet wurde. Dies ist der Fall, wenn die Veröffentlichung nicht-- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Abonnenten enthält. Diese Unterschiede sind durch geringfügige und unvermeidbare Genauigkeitsunterschiede bedingt, die auftreten, wenn Konvertierungen in den und aus dem Zeichenmodus durchgeführt werden.  
  
## <a name="permissions"></a>Berechtigungen  
 Um **sp_table_validation**auszuführen, benötigen Sie SELECT-Berechtigungen für die Tabelle, die überprüft wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Prüfsumme &#40;Transact-SQL-&#41;](../../t-sql/functions/checksum-transact-sql.md)   
 [@@ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/rowcount-transact-sql.md)   
 [sp_article_validation &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-article-validation-transact-sql.md)   
 [sp_publication_validation &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-publication-validation-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
