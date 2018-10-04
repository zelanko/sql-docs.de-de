---
title: Sp_OAGetProperty (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OAGetProperty_TSQL
- sp_OAGetProperty
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAGetProperty
ms.assetid: 240eeeb9-6d8b-4930-b912-1d273ca0ab38
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0a8c87eb8ed41b1669cf423aaccb8b06ee8b0e54
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47690008"
---
# <a name="spoagetproperty-transact-sql"></a>sp_OAGetProperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ruft einen Eigenschaftswert eines OLE-Objekts ab.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_OAGetProperty objecttoken , propertyname   
    [ , propertyvalue OUTPUT ]  
    [ , index...]   
```  
  
## <a name="arguments"></a>Argumente  
 *objecttoken*  
 Das Objekttoken eines zuvor mit **sp_OACreate**erstellten OLE-Objekts.  
  
 *propertyname*  
 Der Eigenschaftsname des OLE-Objekts, dessen Wert zurückgegeben werden soll.  
  
 *PropertyValue* **Ausgabe**  
 Der zurückgegebene Eigenschaftswert. Wenn angegeben, muss es sich um eine lokale Variable vom entsprechenden Datentyp handeln.  
  
 Wenn die Eigenschaft ein OLE-Objekt zurückgibt *Propertyvalue* muss eine lokale Variable des Datentyps **Int**. Ein Objekttoken wird in der lokalen Variable gespeichert, und dieses Objekttoken kann in anderen gespeicherten Prozeduren der OLE-Automatisierung verwendet werden.  
  
 Wenn die Eigenschaft auf einen einzelnen Wert zurückgibt, geben Sie entweder eine lokale Variable für *Propertyvalue*, Wert in der lokalen Variablen, die die Eigenschaft zurückgibt, oder geben Sie nicht *Propertyvalue*, gibt die der Eigenschaftswert als ein einspaltiges, einzeiliges Resultset an den Client.  
  
 Wenn die Eigenschaft ein Array zurückgibt, wenn *Propertyvalue* angegeben ist, wird er auf NULL festgelegt.  
  
 Wenn *Propertyvalue* angegeben wird, ohne dass die Eigenschaft einen Wert, ein Fehler auftritt. Gibt die Eigenschaft ein Array mit mehr als zwei Dimensionen zurück, tritt ebenfalls ein Fehler auf.  
  
 *index*  
 Ein Indexparameter. Wenn angegeben, *Index* muss ein Wert, der den entsprechenden Datentyp sein.  
  
 Einige Eigenschaften besitzen Parameter. Diese Eigenschaften werden als Indiziert-Eigenschaften und die Parameter als Indexparameter bezeichnet. Eine Eigenschaft kann mehrere Indexparameter aufweisen.  
  
> [!NOTE]  
>  Die Parameter für diese gespeicherte Prozedur werden anhand der Position kein Name angegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler), die dem ganzzahligen Wert von HRESULT entspricht, der vom OLE-Automatisierungsobjekt zurückgegeben wird.  
  
 Weitere Informationen zu HRESULT-Rückgabecodes finden Sie unter [OLE Automation Rückgabecodes und Fehlerinformationen](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Resultsets  
 Wenn die Eigenschaft ein Array mit ein oder zwei Dimensionen zurückgibt, wird das Array dem Client folgendermaßen als Resultset zurückgegeben:  
  
-   Ein eindimensionales Array wird dem Client als einzeiliges Resultset zurückgegeben, das so viele Spalten wie Elemente im Array enthält. Das Array wird also als Spalten zurückgegeben.  
  
-   Ein zweidimensionales Array wird dem Client als Resultset zurückgegeben, dessen Anzahl an Spalten der Anzahl der Elemente in der ersten Dimension des Arrays entspricht und dessen Anzahl an Zeilen der Anzahl der Elemente in der zweiten Dimension des Arrays entspricht. Das Array wird also als (Spalten, Zeilen) zurückgegeben.  
  
 Beim Rückgabewert einer Eigenschaft oder Methode ist ein Array, **Sp_OAGetProperty** oder **Sp_OAMethod** gibt ein Resultset an den Client zurück. (Ausgabeparameter für Methoden können nicht einem Array entsprechen.) Diese Prozeduren durchsuchen alle Datenwerte des Arrays, um die geeigneten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datentypen und -Datenlängen für jede Spalte des Resultsets zu ermitteln. Für eine bestimmte Spalte verwenden diese Prozeduren den Datentyp und die -länge, die erforderlich sind, um alle Datenwerte in dieser Spalte darzustellen.  
  
 Wenn alle Datenwerte einer Spalte denselben Datentyp aufweisen, wird dieser Datentyp für die gesamte Spalte verwendet. Wenn Datenwerte in einer Spalte unterschiedliche Datentypen verwenden, wird der Datentyp für die gesamte Spalte entsprechend der folgenden Tabelle ausgewählt.  
  
||ssNoversion|FLOAT|money|DATETIME|varchar|NVARCHAR|  
|------|---------|-----------|-----------|--------------|-------------|--------------|  
|**int**|**int**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**float**|**float**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**money**|**money**|**money**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**datetime**|**varchar**|**varchar**|**varchar**|**datetime**|**varchar**|**nvarchar**|  
|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**nvarchar**|  
|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|  
  
## <a name="remarks"></a>Hinweise  
 Sie können auch **Sp_OAMethod** , einen Eigenschaftswert abzurufen.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-a-local-variable"></a>A. Verwenden einer lokalen Variablen  
 Im folgenden Beispiel wird die `HostName` -Eigenschaft (des zuvor erstellten **SQLServer** Objekt) und speichert es in eine lokale Variable.  
  
```  
DECLARE @property varchar(255);  
EXEC @hr = sp_OAGetProperty @object, 'HostName', @property OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END  
PRINT @property;  
```  
  
### <a name="b-using-a-result-set"></a>B. Verwenden eines Resultsets  
 Im folgenden Beispiel wird die `HostName` -Eigenschaft (des zuvor erstellten **SQLServer** Objekt) und gibt dem Client als Resultset zurück.  
  
```  
EXEC @hr = sp_OAGetProperty @object, 'HostName';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte OLE-Automatisierung Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE-Automatisierungsbeispielskript](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
