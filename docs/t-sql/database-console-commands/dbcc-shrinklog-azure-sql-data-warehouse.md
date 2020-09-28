---
description: DBCC SHRINKLOG (Parallel Data Warehouse)
title: DBCC SHRINKLOG (Parallel Data Warehouse)
ms.custom: ''
ms.date: 03/16/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
author: pmasl
ms.author: umajay
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bae2ef1468110ba89d77d5f7a6360aecb324abd0
ms.sourcegitcommit: 1126792200d3b26ad4c29be1f561cf36f2e82e13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2020
ms.locfileid: "90076696"
---
# <a name="dbcc-shrinklog-parallel-data-warehouse"></a>DBCC SHRINKLOG (Parallel Data Warehouse)

[!INCLUDE [pdw](../../includes/applies-to-version/pdw.md)]

Reduziert die Größe des Transaktionsprotokolls *anwendungsübergreifend* für die aktuelle [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]-Datenbank. Die Daten werden defragmentiert, um das Transaktionsprotokoll zu verkleinern. Mit der Zeit kann es sein, dass das Datenbanktransaktionsprotokoll zu viele Bestandteile hat und dadurch nicht effizient verwendet werden kann. Verwenden Sie DBCC SHRINKLOG, um diese Fragmentierung und damit auch die Protokollgröße zu verringern.
  
![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Syntax  
  
```syntaxsql
DBCC SHRINKLOG   
    [ ( SIZE = { target_size [ MB | GB | TB ]  } | DEFAULT ) ]   
    [ WITH NO_INFOMSGS ]   
[;]  
```  

## <a name="arguments"></a>Argumente

SIZE = { *target_size* [ MB \| **GB** \| TB ]  } \| **DEFAULT**.  
*target_size* ist die gewünschte Größe des Transaktionsprotokolls auf sämtlichen Computeknoten, nachdem DBCC SHRINKLOG abgeschlossen wurde. Dabei handelt es sich um einen Integer größer als 0 (null).  
Die Protokollgröße wird in Megabyte (MB), Gigabyte (GB) oder Terabyte (TB) angegeben. Dabei handelt es sich um die Gesamtgröße aller Transaktionsprotokolle auf den Computeknoten.  
Standardmäßig reduziert DBCC SHRINKLOG das Transaktionsprotokoll auf die Protokollgröße, die in den Metadaten der Datenbank gespeichert ist. Die Protokollgröße in den Metadaten wird von dem LOG_SIZE-Parameter in [CREATE DATABASE &#40;Azure Synapse Analytics&#41;](../../t-sql/statements/create-database-azure-sql-data-warehouse.md) oder [ALTER DATABASE &#40;Azure Synapse Analytics&#41;](../../t-sql/statements/alter-database-azure-sql-data-warehouse.md) bestimmt. DBCC SHRINKLOG reduziert die Größe des Transaktionsprotokolls, wenn `SIZE=DEFAULT` angegeben oder die `SIZE`-Klausel weggelassen wird.
  
WITH NO_INFOMSGS  
Informationsmeldungen werden nicht in den DBCC SHRINKLOG-Ergebnissen angezeigt.  
  
## <a name="permissions"></a>Berechtigungen

Erfordert die ALTER SERVER STATE-Berechtigung.

## <a name="general-remarks"></a>Allgemeine Hinweise

DBCC SHRINKLOG ändert nicht die Protokollgröße, die in den Metadaten der Datenbank gespeichert ist. Die Metadaten enthalten weiterhin den LOG_SIZE-Parameter, der in den Anweisungen CREATE DATABASE oder ALTER DATABASE angegeben wurde.
  
## <a name="examples"></a>Beispiele

### <a name="a-shrink-the-transaction-log-to-the-original-size-specified-by-create-database"></a>A. Reduzieren Sie das Transaktionsprotokoll auf die ursprüngliche von CREATE DATABASE angegebene Größe.  
Angenommen, das Transaktionsprotokoll für die Adressdatenbank wurde bei der Erstellung der Adressdatenbank auf 100 MB festgelegt. D.h., die CREATE DATABASE-Anweisung für Adressen entspricht LOG_SIZE = 100 MB. Jetzt hat die Größe des Protokolls allerdings 150 MB erreicht und Sie möchten diese wieder auf 100 MB reduzieren.
  
Sie können eine der folgenden Anweisungen verwenden, um zu versuchen, das Transaktionsprotokoll der Adressdatenbank auf seine Standardgröße von 100 MB zu verkleinern. Wenn das Verkleinern des Protokolls auf 100 MB zu Datenverlusten führen würde, verkleinert DBCC SHRINKLOG es so weit wie möglich auf eine Größe von mehr als 100 MB, wobei jedoch keine Daten verloren gehen.

```sql
USE Addresses;  
DBCC SHRINKLOG ( SIZE = 100 MB );  
DBCC SHRINKLOG ( SIZE = DEFAULT );  
DBCC SHRINKLOG;  
```
