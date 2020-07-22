---
title: Read (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 04/16/2020
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Read_TSQL
- Read
dev_langs:
- TSQL
helpviewer_keywords:
- Read [Database Engine]
ms.assetid: f2b8207c-b69f-4327-a874-100b3a1f27d8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 89739f7e53ddccfc95cb9e84311f1ed18e147de6
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552585"
---
# <a name="read-database-engine-by-using-csharp"></a>Read (Datenbank-Engine) mit CSharp
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Read liest binäre Darstellung von **SqlHierarchyId** aus dem übergebenen **BinaryReader** und legt das **SqlHierarchyId**-Objekt auf diesen Wert fest. Read kann nicht mit [!INCLUDE[tsql](../../includes/tsql-md.md)] aufgerufen werden. Verwenden Sie stattdessen CAST oder CONVERT.
  
## <a name="syntax"></a>Syntax  

<!--
This is not T-SQL, despite the ```sql colorizer specified.
Neither should this be ```syntaxsql.
Rather, this is C# (or C# syntax).  Same for the later code blocks.
I am making this fix now, from ```sql to ```cs, on 2020/04/16.  GeneMi.
-->

```csharp
void Read( BinaryReader r )   
```  

## <a name="arguments"></a>Argumente
*r*  
 Das **BinaryReader**-Objekt, das einen binären Datenstrom erzeugt, der einer binären Darstellung eines **hierarchyid**-Knotens entspricht.  
  
## <a name="return-types"></a>Rückgabetypen
 **CLR-Rückgabetyp: void**  
  
## <a name="remarks"></a>Bemerkungen  
 Read überprüft seine Eingabe nicht. Wenn eine ungültige binäre Eingabe gegeben wird, löst Read möglicherweise eine Ausnahme aus. Oder der Vorgang ist erfolgreich und erzeugt ein ungültiges **SqlHierarchyId**-Objekt, dessen Methoden zu unvorhersagbaren Ergebnissen führen oder eine Ausnahme auslösen können.  
  
 Read kann nur für ein neu erstelltes **SqlHierarchyId**-Objekt aufgerufen werden.  
  
 Read wird wenn nötig intern von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet, z.B. beim Schreiben von Daten in die **hierarchyid**-Spalte. Read wird auch intern aufgerufen, wenn eine Konvertierung zwischen **varbinary** und **hierarchyid** ausgeführt wird.  
  
## <a name="examples"></a>Beispiele  
  
```csharp
Byte[] encoding = new byte[] { 0x58 };  
MemoryStream stream = new MemoryStream(encoding, false /*not writable*/);  
BinaryReader br = new BinaryReader(stream);  
SqlHierarchyId hid = new SqlHierarchyId();  
hid.Read(br);   
```  
  
## <a name="see-also"></a>Weitere Informationen  
[Write &#40;Datenbank-Engine&#41;](../../t-sql/data-types/write-database-engine.md)  
[ToString &#40;Datenbank-Engine&#41;](../../t-sql/data-types/tostring-database-engine.md)  
[CAST und CONVERT &#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)  
[hierarchyid-Datentyp-Methodenverweis](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  
