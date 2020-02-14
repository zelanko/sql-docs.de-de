---
title: money and smallmoney (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- money_TSQL
- money
- smallmoney
- smallmoney_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- money data type, about money data type
- money data type
- smallmoney data type
- values [SQL Server], monetary
- currency [SQL Server]
ms.assetid: 57861137-89ea-4b89-b361-390597d7bccc
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7ad26acc2f1e23b61e9692dcf2720d7ee6dd8639
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "68077809"
---
# <a name="money-and-smallmoney-transact-sql"></a>money und smallmoney (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Datentypen zur Darstellung von Währungswerten.
  
## <a name="remarks"></a>Bemerkungen  
  
|Datentyp|Range|Storage|  
|---|---|---|
|**money**|-922.337.203.685.477,5808 bis 922.337.203.685.477,5807 (-922.337.203.685.477,58<br />bis 922.337.203.685.477,58 für Informatica.  Informatica unterstützt nur zwei Dezimalstellen, nicht vier.)|8 Byte|  
|**smallmoney**|-214.748,3648 bis 214.748,3647|4 Byte|  
  
Die Datentypen **money** und **smallmoney** weisen die Genauigkeit eines Zehntausendstels der dargestellten Währungseinheiten auf. Für Informatica weisen die Datentypen **money** und **smallmoney** die Genauigkeit eines Hundertstels der dargestellten Währungseinheiten auf.
  
Mit einem Punkt werden Währungsuntereinheiten, wie z. B. Cent, von ganzen Währungseinheiten getrennt. Die Zahl 2.15 gibt z. B. 2 Dollar und 15 Cent an.
  
Diese Datentypen können eines der folgenden Währungssymbole verwenden.
  
![Tabelle mit Währungssymbolen, hexadezimale Werte](../../t-sql/data-types/media/money01.gif "Tabelle mit Währungssymbolen, hexadezimale Werte")
  
Währungsdaten müssen nicht in einfache Anführungszeichen (') eingeschlossen werden. Sie sollten stets bedenken, dass Sie zwar Währungswerte angeben können, denen ein Währungssymbol vorangestellt ist, dass [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] jedoch keinerlei mit diesem Symbol verbundene Währungsinformationen speichert, sondern lediglich den nummerischen Wert.
  
## <a name="converting-money-data"></a>Konvertieren von money-Daten
Beim Konvertieren von Ganzzahldatentypen in **money**-Datentypen wird davon ausgegangen, dass es sich bei den Einheiten um Währungseinheiten handelt. Der ganze Zahl 4 entspricht nach der Konvertierung in den **money**-Datentyp 4 Währungseinheiten.
  
Das folgende Beispiel konvertiert **smallmoney**- und **money**-Werte jeweils in **varchar**- und **decimal**-Datentypen.
  
```sql
DECLARE @mymoney_sm smallmoney = 3148.29,  
        @mymoney    money = 3148.29;  
SELECT  CAST(@mymoney_sm AS varchar) AS 'SM_MONEY varchar',  
        CAST(@mymoney AS decimal)    AS 'MONEY DECIMAL';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
SM_MONEY VARCHAR               MONEY DECIMAL  
------------------------------ ----------------------  
3148.29                        3148    
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>Weitere Informationen
[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
[CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)
[Data Types &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)
[DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)
[SET @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/set-local-variable-transact-sql.md)
[sys.types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-types-transact-sql.md)
  
  
