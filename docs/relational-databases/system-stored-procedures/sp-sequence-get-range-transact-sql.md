---
description: sp_sequence_get_range (Transact-SQL)
title: sp_sequence_get_range (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/08/2015
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_sequence_get_range
- sp_sequence_get_range_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sequence number object, sp_sequence_get_range procedure
- sp_sequence_get_range
ms.assetid: 8ca6b0c6-8d9c-4eee-b02f-51ddffab4492
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ca7253dc04d629f1bed01b8e952752af06b236b4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97484532"
---
# <a name="sp_sequence_get_range-transact-sql"></a>sp_sequence_get_range (Transact-SQL)
[!INCLUDE [sql-asdb-asdbmi-asa](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Gibt einen Bereich von Sequenzwerten eines Sequenzobjekts zurück. Das Sequenzobjekt generiert die angeforderte Anzahl der Werte, gibt diese aus und stellt Metadaten bezüglich des Bereichs für die Anwendung bereit.  
  
 Weitere Informationen zu Sequenznummern finden Sie unter [Sequenznummern](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_sequence_get_range [ @sequence_name = ] N'<sequence>'   
     , [ @range_size = ] range_size  
     , [ @range_first_value = ] range_first_value OUTPUT   
    [, [ @range_last_value = ] range_last_value OUTPUT ]  
    [, [ @range_cycle_count = ] range_cycle_count OUTPUT ]  
    [, [ @sequence_increment = ] sequence_increment OUTPUT ]  
    [, [ @sequence_min_value = ] sequence_min_value OUTPUT ]  
    [, [ @sequence_max_value = ] sequence_max_value OUTPUT ]  
    [ ; ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @sequence_name = ] N'sequence'` Der Name des Sequenz Objekts. Das Schema ist optional. *sequence_name* ist vom Datentyp **nvarchar (776)**.  
  
`[ @range_size = ] range_size` Die Anzahl der Werte, die aus der Sequenz abgerufen werden sollen. **\@ range_size** ist **bigint**.  
  
`[ @range_first_value = ] range_first_value` Der Output-Parameter gibt den ersten (minimalen oder maximalen) Wert des Sequenz Objekts zurück, das verwendet wird, um den angeforderten Bereich zu berechnen. **\@ range_first_value** wird mit dem gleichen Basistyp **sql_variant** wie das in der Anforderung verwendete Sequenz Objekt.  
  
`[ @range_last_value = ] range_last_value` Der optionale Ausgabeparameter gibt den letzten Wert des angeforderten Bereichs zurück. **\@ range_last_value** wird mit dem gleichen Basistyp **sql_variant** wie das in der Anforderung verwendete Sequenz Objekt.  
  
`[ @range_cycle_count = ] range_cycle_count` Optionaler OUTPUT-Parameter gibt die Anzahl der Wiederholungen zurück, die das Sequenz Objekt durchlaufen hat, um den angeforderten Bereich zurückzugeben. **\@ range_cycle_count** ist vom Datentyp **int**.  
  
`[ @sequence_increment = ] sequence_increment` Optionaler OUTPUT-Parameter gibt das Inkrement des Sequenz Objekts zurück, mit dem der angeforderte Bereich berechnet wird. **\@ sequence_increment** wird mit dem gleichen Basistyp **sql_variant** wie das in der Anforderung verwendete Sequenz Objekt.  
  
`[ @sequence_min_value = ] sequence_min_value` Der optionale Ausgabeparameter gibt den minimalen Wert des Sequenz Objekts zurück. **\@ sequence_min_value** wird mit dem gleichen Basistyp **sql_variant** wie das in der Anforderung verwendete Sequenz Objekt.  
  
`[ @sequence_max_value = ] sequence_max_value` Der optionale Ausgabeparameter gibt den maximalen Wert des Sequenz Objekts zurück. **\@ sequence_max_value** wird mit dem gleichen Basistyp **sql_variant** wie das in der Anforderung verwendete Sequenz Objekt.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 sp_sequence_get_rangeis in sys. Schema und können als sys.sp_sequence_get_range referenziert werden.  
  
### <a name="cycling-sequences"></a>Zyklussequenzen  
 Falls erforderlich, durchläuft das Sequenzobjekt die entsprechende Anzahl von Zyklen, um den angeforderten Bereich zu versorgen. Die Anzahl der Zyklussequenzen wird mit dem `@range_cycle_count`-Parameter an den Aufrufer zurückgegeben.  
  
> [!NOTE]  
>  Der Durchlauf des Sequenzobjekts beginnt beim Minimalwert, wenn es sich um eine aufsteigende Sequenz handelt, und beim Maximalwert, wenn es sich um eine absteigende Sequenz handelt, nicht beim Startwert des Sequenzobjekts.  
  
### <a name="non-cycling-sequences"></a>Nicht-zyklische Sequenzen  
 Wenn die Anzahl der Werte im angeforderten Bereich größer als die Anzahl der verbleibenden Werte im Sequenzobjekt ist, kann der angeforderte Bereich nicht vom Sequenzobjekt abgezogen werden, und der folgende Fehler 11732 wird zurückgegeben:  
  
 `The requested range for sequence object '%.*ls' exceeds the maximum or minimum limit. Retry with a smaller range.`  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die UPDATE-Berechtigung für das Sequenzobjekt oder das Schema des Sequenzobjekts.  
  
## <a name="examples"></a>Beispiele  
 In den folgenden Beispielen wird ein Sequenz Objekt mit dem Namen Test. rangeseq verwendet. Verwenden Sie die folgende Anweisung, um die Test. rangeseq-Sequenz zu erstellen.  
  
```  
CREATE SCHEMA Test ;  
GO  
  
CREATE SEQUENCE Test.RangeSeq  
    AS int   
    START WITH 1  
    INCREMENT BY 1  
    MINVALUE 1  
    MAXVALUE 25  
    CYCLE  
    CACHE 10  
;  
```  
  
### <a name="a-retrieving-a-range-of-sequence-values"></a>A. Abrufen eines Bereichs von Sequenzwerten  
 Mit der folgenden Anweisung werden vier Sequenznummern aus dem "Test. rangeseq"-Sequenz Objekt abgerufen, und die erste der Zahlen wird an den Benutzer zurückgegeben.  
  
```  
DECLARE @range_first_value_output sql_variant ;  
  
EXEC sys.sp_sequence_get_range  
@sequence_name = N'Test.RangeSeq'  
, @range_size = 4  
, @range_first_value = @range_first_value_output OUTPUT ;  
  
SELECT @range_first_value_output AS FirstNumber ;  
  
```  
  
### <a name="b-returning-all-output-parameters"></a>B. Zurückgeben aller Ausgabeparameter  
 Im folgenden Beispiel werden alle Ausgabewerte aus der sp_sequence_get_range Prozedur zurückgegeben.  
  
```  
DECLARE    
  @FirstSeqNum sql_variant  
, @LastSeqNum sql_variant  
, @CycleCount int  
, @SeqIncr sql_variant  
, @SeqMinVal sql_variant  
, @SeqMaxVal sql_variant ;  
  
EXEC sys.sp_sequence_get_range  
@sequence_name = N'Test.RangeSeq'  
, @range_size = 5  
, @range_first_value = @FirstSeqNum OUTPUT   
, @range_last_value = @LastSeqNum OUTPUT   
, @range_cycle_count = @CycleCount OUTPUT  
, @sequence_increment = @SeqIncr OUTPUT  
, @sequence_min_value = @SeqMinVal OUTPUT  
, @sequence_max_value = @SeqMaxVal OUTPUT ;  
  
-- The following statement returns the output values  
SELECT  
  @FirstSeqNum AS FirstVal  
, @LastSeqNum AS LastVal  
, @CycleCount AS CycleCount  
, @SeqIncr AS SeqIncrement  
, @SeqMinVal AS MinSeq  
, @SeqMaxVal AS MaxSeq ;  
  
```  
  
 Eine Änderung des `@range_size`-Arguments in einen sehr großen Wert wie 75 führt dazu, dass das Sequenzobjekt Zyklen durchläuft. Überprüfen Sie das `@range_cycle_count`-Argument, um zu ermitteln, ob und in welchem Ausmaß Zyklen vom Sequenzobjekt durchlaufen wurden.  
  
### <a name="c-example-using-adonet"></a>C. Beispiel für die Verwendung von ADO.NET  
 Im folgenden Beispiel wird ein Bereich aus dem Test. rangeseq mithilfe von ADO.net abgerufen.  
  
```  
SqlCommand cmd = new SqlCommand();  
cmd.Connection = conn;  
cmd.CommandType = CommandType.StoredProcedure;  
cmd.CommandText = "sys.sp_sequence_get_range";  
cmd.Parameters.AddWithValue("@sequence_name", "Test.RangeSeq");  
cmd.Parameters.AddWithValue("@range_size", 10);  
  
// Specify an output parameter to retrieve the first value of the generated range.  
SqlParameter firstValueInRange = new SqlParameter("@range_first_value", SqlDbType.Variant);  
firstValueInRange.Direction = ParameterDirection.Output;  
cmd.Parameters.Add(firstValueInRange);  
  
conn.Open();  
cmd.ExecuteNonQuery();  
  
// Output the first value of the generated range.  
Console.WriteLine(firstValueInRange.Value);  
  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [CREATE SEQUENCE &#40;Transact-SQL&#41;](../../t-sql/statements/create-sequence-transact-sql.md)   
 [ALTER SEQUENCE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [DROP SEQUENCE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [NEXT VALUE FOR &#40;Transact-SQL&#41;](../../t-sql/functions/next-value-for-transact-sql.md)   
 [Sequenznummern](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  
