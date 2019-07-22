---
title: Read (Datenbank-Engine) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/22/2017
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
ms.openlocfilehash: 9fb69a5c4e9d303ab0e3a7a3e2edeeeeed228391
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68000601"
---
# <a name="read-database-engine"></a>Read (Datenbank-Engine)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Read liest binäre Darstellung von **SqlHierarchyId** aus dem übergebenen **BinaryReader** und legt das **SqlHierarchyId**-Objekt auf diesen Wert fest. Read kann nicht mit [!INCLUDE[tsql](../../includes/tsql-md.md)] aufgerufen werden. Verwenden Sie stattdessen CAST oder CONVERT.
  
## <a name="syntax"></a>Syntax  
  
```sql
void Read( BinaryReader r )   
```  
  
## <a name="arguments"></a>Argumente  
*r*  
 Das **BinaryReader**-Objekt, das einen binären Datenstrom erzeugt, der einer binären Darstellung eines **hierarchyid**-Knotens entspricht.  
  
## <a name="return-types"></a>Rückgabetypen
 **CLR-Rückgabetyp: void**  
  
## <a name="remarks"></a>Remarks  
 Read überprüft seine Eingabe nicht. Wenn eine ungültige binäre Eingabe gegeben wird, löst Read möglicherweise eine Ausnahme aus. Oder der Vorgang ist erfolgreich und erzeugt ein ungültiges **SqlHierarchyId**-Objekt, dessen Methoden zu unvorhersagbaren Ergebnissen führen oder eine Ausnahme auslösen können.  
  
 Read kann nur für ein neu erstelltes **SqlHierarchyId**-Objekt aufgerufen werden.  
  
 Read wird wenn nötig intern von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] verwendet, z.B. beim Schreiben von Daten in die **hierarchyid**-Spalte. Read wird auch intern aufgerufen, wenn eine Konvertierung zwischen **varbinary** und **hierarchyid** ausgeführt wird.  
  
## <a name="examples"></a>Beispiele  
  
```sql
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
  
  
