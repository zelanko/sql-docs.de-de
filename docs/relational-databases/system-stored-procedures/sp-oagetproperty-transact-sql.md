---
title: sp_OAGetProperty (Transact-SQL) | Microsoft-Dokumentation
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 753ee7cc87546c180a911ffef9c54efe143f1faf
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85734319"
---
# <a name="sp_oagetproperty-transact-sql"></a>sp_OAGetProperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Ruft einen Eigenschaftswert eines OLE-Objekts ab.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
  
 *PropertyValue* - **Ausgabe**  
 Der zurückgegebene Eigenschaftswert. Wenn angegeben, muss es sich um eine lokale Variable vom entsprechenden Datentyp handeln.  
  
 Wenn die Eigenschaft ein OLE-Objekt zurückgibt, muss *PropertyValue* eine lokale Variable vom Datentyp ' **int**' sein. Ein Objekt Token wird in der lokalen Variablen gespeichert, und dieses Objekt Token kann mit anderen gespeicherten Prozeduren der OLE-Automatisierung verwendet werden.  
  
 Wenn die Eigenschaft einen einzelnen Wert zurückgibt, geben Sie entweder eine lokale Variable für *PropertyValue*an, die den Eigenschafts Wert in der lokalen Variablen zurückgibt. oder geben Sie nicht *PropertyValue*an, der den Eigenschafts Wert an den Client als einspaltigen Resultset mit einer Zeile zurückgibt.  
  
 Wenn die Eigenschaft ein Array zurückgibt, ist PropertyValue auf NULL festgelegt, wenn *PropertyValue* angegeben wird.  
  
 Wenn *PropertyValue* angegeben wird, aber die-Eigenschaft keinen Wert zurückgibt, tritt ein Fehler auf. Gibt die Eigenschaft ein Array mit mehr als zwei Dimensionen zurück, tritt ebenfalls ein Fehler auf.  
  
 *Index*  
 Ein Indexparameter. Wenn angegeben, muss der *Index* ein Wert des entsprechenden Datentyps sein.  
  
 Einige Eigenschaften besitzen Parameter. Diese Eigenschaften werden als Indiziert-Eigenschaften und die Parameter als Indexparameter bezeichnet. Eine Eigenschaft kann mehrere Indexparameter aufweisen.  
  
> [!NOTE]  
>  Die Parameter für diese gespeicherte Prozedur werden durch die Position, nicht durch den Namen angegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler), die dem ganzzahligen Wert von HRESULT entspricht, der vom OLE-Automatisierungsobjekt zurückgegeben wird.  
  
 Weitere Informationen zu HRESULT-Rückgabecodes finden Sie unter [Rückgabecodes und Fehlerinformationen der OLE-Automatisierung](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Resultsets  
 Wenn die Eigenschaft ein Array mit ein oder zwei Dimensionen zurückgibt, wird das Array dem Client folgendermaßen als Resultset zurückgegeben:  
  
-   Ein eindimensionales Array wird dem Client als einzeiliges Resultset zurückgegeben, das so viele Spalten wie Elemente im Array enthält. Das Array wird also als Spalten zurückgegeben.  
  
-   Ein zweidimensionales Array wird dem Client als Resultset zurückgegeben, dessen Anzahl an Spalten der Anzahl der Elemente in der ersten Dimension des Arrays entspricht und dessen Anzahl an Zeilen der Anzahl der Elemente in der zweiten Dimension des Arrays entspricht. Das Array wird also als (Spalten, Zeilen) zurückgegeben.  
  
 Wenn der Rückgabewert einer Eigenschaft oder der Methodenrückgabewert ein Array ist, gibt **sp_OAGetProperty** oder **sp_OAMethod** ein Resultset an den Client zurück. (Ausgabeparameter für Methoden können nicht einem Array entsprechen.) Diese Prozeduren durchsuchen alle Datenwerte des Arrays, um die geeigneten [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Datentypen und -Datenlängen für jede Spalte des Resultsets zu ermitteln. Für eine bestimmte Spalte verwenden diese Prozeduren den Datentyp und die -länge, die erforderlich sind, um alle Datenwerte in dieser Spalte darzustellen.  
  
 Wenn alle Datenwerte einer Spalte denselben Datentyp aufweisen, wird dieser Datentyp für die gesamte Spalte verwendet. Wenn Datenwerte in einer Spalte unterschiedliche Datentypen verwenden, wird der Datentyp für die gesamte Spalte entsprechend der folgenden Tabelle ausgewählt.  
  
||INT|float|money|datetime|varchar|NVARCHAR|  
|------|---------|-----------|-----------|--------------|-------------|--------------|  
|**int**|**int**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**float**|**float**|**float**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**money**|**money**|**money**|**money**|**varchar**|**varchar**|**nvarchar**|  
|**datetime**|**varchar**|**varchar**|**varchar**|**datetime**|**varchar**|**nvarchar**|  
|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**varchar**|**nvarchar**|  
|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|**nvarchar**|  
  
## <a name="remarks"></a>Hinweise  
 Sie können auch **sp_OAMethod** verwenden, um einen Eigenschafts Wert zu erhalten.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** oder die EXECUTE-Berechtigung direkt für diese gespeicherte Prozedur. `Ole Automation Procedures`die Konfiguration muss **aktiviert** sein, um alle System Prozeduren für OLE-Automatisierung verwenden zu können.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-a-local-variable"></a>A. Verwenden einer lokalen Variablen  
 Im folgenden Beispiel wird die `HostName` -Eigenschaft (des zuvor erstellten **SQLServer** -Objekts) abgerufen und in einer lokalen Variablen gespeichert.  
  
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
 Im folgenden Beispiel wird die `HostName` -Eigenschaft (des zuvor erstellten **SQLServer** -Objekts) abgerufen und als Resultset an den Client zurückgegeben.  
  
```  
EXEC @hr = sp_OAGetProperty @object, 'HostName';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte OLE-Automatisierungs Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE-Automatisierungsbeispielskript](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
