---
description: float und real (Transact-SQL)
title: float und real (Transact-SQL)
ms.custom: ''
ms.date: 09/10/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- float
- real_TSQL
- real
- float_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- numeric data type, floating point
- float data type
- floating point data [SQL Server]
- real data type
ms.assetid: 08ea66b7-624e-4d8b-86bc-750ff76cdfc5
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8fdbe0c896a5aba4cc68abf2b2c572a82ad9ca7b
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97482118"
---
# <a name="float-and-real-transact-sql"></a>float und real (Transact-SQL)

[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

Ungefähre Zahlendatentypen für numerische Gleitkommadaten. Gleitkommadaten sind Näherungswerte, deshalb können nicht alle Werte im Bereich des Datentyps exakt dargestellt werden. Das ISO-Synonym für **real** ist **float(24)** .
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
**float** [ **(** _n_ **)** ]. Hierbei entspricht *n* der Anzahl von Bits, die zum Speichern der Mantisse der **Gleitkommazahl** in der wissenschaftlichen Schreibweise verwendet werden. Dadurch werden die Genauigkeit und die Speichergröße festlegt. Wenn *n* angegeben wird, muss es sich um einen Wert zwischen **1** und **53** handeln. Der Standardwert von *n* lautet **53**.
  
|Wert *n*|Precision|Speichergröße|  
|---|---|---|
|**1-24**|7 Stellen|4 Byte|  
|**25-53**|15 Stellen|8 Byte|  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verarbeitet *n* als einen von zwei möglichen Werten. Wenn **1**<=n<=**24** gegeben ist, wird *n* als **24** behandelt. Wenn **25**<=n<=**53** gegeben ist, wird *n* als **53** behandelt.  
  
Der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentyp **float**[ **(n)** ] entspricht dem ISO-Standard für alle Werte von *n* zwischen **1** und **53**. Das Synonym für **double precision** lautet **float(53)** .

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="remarks"></a>Bemerkungen  
  
|Datentyp|Range|Storage|  
|---|---|---|
|**float**|- 1,79E+308 bis -2,23E-308, 0 und 2,23E-308 bis 1,79E+308|Hängt vom Wert für *n* ab.|  
|**real**|- 3,40E + 38 bis -1,18E - 38, 0 und 1,18E - 38 bis 3,40E + 38|4 Byte|  
  
##  <a name="converting-float-and-real-data"></a>Konvertieren von float- und real-Daten  
Werte des Typs **float** werden bei der Konvertierung in einen Integertyp abgeschnitten.
  
Für das Konvertieren von **float**- oder **real**-Daten in Zeichendaten eignet sich die STR-Zeichenfolgenfunktion normalerweise besser als CAST( ). Der Grund hierfür ist, dass STR Ihnen bessere Steuerungsmöglichkeiten über die Formatierung bietet. Weitere Informationen finden Sie unter [STR &#40;Transact-SQL&#41;](../../t-sql/functions/str-transact-sql.md) und [Aggregatfunktionen &#40;Transact-SQL&#41;](../../t-sql/functions/functions.md).
  
Vor [!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] ist die Konvertierung von **float**-Werten in **decimal**- oder **numeric**-Werte auf Werte mit einer Genauigkeit von 17 Stellen beschränkt. Jeder **float**-Wert kleiner als 5E-18 (der entweder in der wissenschaftlichen Schreibweise als 5E-18 oder in der Dezimalschreibweise als 0,0000000000000000050000000000000005 festgelegt ist) wird auf 0 (null) abgerundet. Dies stellt ab [!INCLUDE[ssSQL16](../../includes/sssql16-md.md)] keine Einschränkung mehr dar.
  
## <a name="see-also"></a>Weitere Informationen
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)  
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)  
[Datentypkonvertierung &#40;Datenbank-Engine&#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)  
[Datentypen &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)  
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
  
  
