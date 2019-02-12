---
title: Write (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/23/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Write_TSQL
- Write
dev_langs:
- TSQL
helpviewer_keywords:
- Write [Database Engine]
ms.assetid: 7c554334-d2d9-4eae-a4ae-097aa4020e1a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 3ba1be72858cea8813b500020b7a429f63570da0
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56031271"
---
# <a name="write-database-engine"></a>Write (Datenbank-Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Write schreibt eine binäre Darstellung von **SqlHierarchyId** in den übergebenen **BinaryWriter**. Write kann nicht mit [!INCLUDE[tsql](../../includes/tsql-md.md)] aufgerufen werden. Verwenden Sie stattdessen CAST oder CONVERT.
  
## <a name="syntax"></a>Syntax  
  
```sql
void Write( BinaryWriter w )   
```  
  
## <a name="arguments"></a>Argumente  
*w*  
Ein **BinaryWriter**-Objekt, in das die binäre Darstellung dieses **hierarchyid**-Knotens geschrieben wird.
  
## <a name="return-types"></a>Rückgabetypen  
**CLR-Rückgabetyp: void**
  
## <a name="remarks"></a>Remarks  
Write wird wenn nötig intern von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet, z.B. beim Schreiben von Daten in die **hierarchyid**-Spalte. Write wird auch intern aufgerufen, wenn eine Konvertierung zwischen **hierarchyid** und **varbinary** ausgeführt wird.
  
## <a name="examples"></a>Beispiele  
  
```sql
MemoryStream stream = new MemoryStream();  
BinaryWriter bw = new BinaryWriter(stream);  
hid.Write(bw);  
byte[] encoding = stream.ToArray();  
  
```  
  
## <a name="see-also"></a>Siehe auch
[Read &#40;Database Engine&#41; (Read (Datenbank-Engine))](../../t-sql/data-types/read-database-engine.md)  
[ToString &#40;Datenbank-Engine&#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[hierarchyid-Datentyp-Methodenverweis](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  
