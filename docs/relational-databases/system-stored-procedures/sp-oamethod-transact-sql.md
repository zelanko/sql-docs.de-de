---
title: sp_OAMethod (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OAMethod
- sp_OAMethod_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAMethod
ms.assetid: 1dfaebe2-c7cf-4041-a586-5d04faf2e25e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 98a8b4ce231c907231646379a3730ab0c1c535db
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828264"
---
# <a name="sp_oamethod-transact-sql"></a>sp_OAMethod (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ruft eine Methode eines OLE-Objekts auf.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_OAMethod objecttoken , methodname  
    [ , returnvalue OUTPUT ]   
    [ , [ @parametername = ] parameter [ OUTPUT ] [ ...n ] ]   
```  
  
## <a name="arguments"></a>Argumente  
 *objecttoken*  
 Das Objekttoken eines zuvor mit **sp_OACreate**erstellten OLE-Objekts.  
  
 *MethodName*  
 Der Name der Methode des OLE-Objekts, das aufgerufen wird.  
  
 _ReturnValue_-**Ausgabe**    
 Der Rückgabewert der Methode des OLE-Objekts. Wenn angegeben, muss es sich um eine lokale Variable vom entsprechenden Datentyp handeln.  
  
 Wenn die Methode einen einzelnen Wert zurückgibt, geben Sie entweder eine lokale Variable für *ReturnValue*an, die den Rückgabewert der Methode in der lokalen Variablen zurückgibt, oder geben Sie keinen *ReturnValue*-Wert an, der den Methodenrückgabewert an den Client als einspaltige einzeilige Resultset zurückgibt.  
  
 Wenn der Rückgabewert der Methode ein OLE-Objekt ist, muss *ReturnValue* eine lokale Variable vom Datentyp **int**sein. Ein Objekt Token wird in der lokalen Variablen gespeichert, und dieses Objekt Token kann mit anderen gespeicherten Prozeduren der OLE-Automatisierung verwendet werden.  
  
 Wenn der Rückgabewert der Methode ein Array ist, wird bei Angabe von *ReturnValue* der Wert auf NULL festgelegt.  
  
 Unter folgenden Bedingungen wird ein Fehler ausgegeben:  
  
-   *ReturnValue* wird angegeben, aber die Methode gibt keinen Wert zurück.  
  
-   Die Methode gibt ein Array mit mehr als zwei Dimensionen zurück.  
  
-   Die Methode gibt ein Array als Ausgabeparameter zurück.  
  
`[ _@parametername = ] parameter[ OUTPUT ]`Ist ein Methoden Parameter. Wenn angegeben, muss der *Parameter* ein Wert des entsprechenden Datentyps sein.  
  
 Zum Abrufen des Rückgabewerts eines Ausgabe Parameters muss der *Parameter* eine lokale Variable des entsprechenden Datentyps sein, und die **Ausgabe** muss angegeben werden. Wenn ein konstanter Parameter angegeben wird oder wenn **Output** nicht angegeben wird, wird jeder Rückgabewert eines Ausgabe Parameters ignoriert.  
  
 Wenn angegeben, muss *Parameter Name* der Name des [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] benannten Parameters sein. Beachten Sie, dass **@** _parametername_is keine [!INCLUDE[tsql](../../includes/tsql-md.md)] lokale Variable ist. Das at-Zeichen ( **@** ) wird entfernt, und Parameter *Name*wird als Parameter Name an das OLE-Objekt übergeben. Alle benannten Parameter müssen nach den Positionsparametern angegeben werden.  
  
 *n*  
 Ein Platzhalter, der anzeigt, dass mehrere Parameter angegeben werden können.  
  
> [!NOTE]
>  Parameter Name kann ein * \@ benannter* Parameter sein, da er Teil der angegebenen Methode ist und an das-Objekt übergeben wird. Die anderen Parameter für diese gespeicherte Prozedur werden nicht nach dem Namen, sondern nach der Position angegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler), die dem ganzzahligen Wert von HRESULT entspricht, der vom OLE-Automatisierungsobjekt zurückgegeben wird.  
  
 Weitere Informationen zu HRESULT-Rückgabecodes, [Rückgabecodes und Fehlerinformationen der OLE-Automatisierung](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Resultsets  
 Wenn die Methode ein Array mit ein oder zwei Dimensionen zurückgibt, wird das Array dem Client folgendermaßen als Resultset zurückgegeben:  
  
-   Ein eindimensionales Array wird dem Client als einzeiliges Resultset zurückgegeben, das so viele Spalten wie Elemente im Array enthält. Das Array wird also als (Spalten) zurückgegeben.  
  
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
  
## <a name="remarks"></a>Bemerkungen  
 Sie können auch **sp_OAMethod** verwenden, um einen Eigenschafts Wert zu erhalten.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** oder die EXECUTE-Berechtigung direkt für diese gespeicherte Prozedur. `Ole Automation Procedures`die Konfiguration muss **aktiviert** sein, um alle System Prozeduren für OLE-Automatisierung verwenden zu können.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-calling-a-method"></a>A. Aufrufen einer Methode  
 Im folgenden Beispiel wird die- `Connect` Methode des zuvor erstellten **SQLServer** -Objekts aufgerufen.  
  
```  
EXEC @hr = sp_OAMethod @object, 'Connect', NULL, 'my_server',  
    'my_login', 'my_password';  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
```  
  
### <a name="b-getting-a-property"></a>B. Eine Eigenschaft wird erhalten.  
 Im folgenden Beispiel wird die `HostName` -Eigenschaft (des zuvor erstellten **SQLServer** -Objekts) abgerufen und in einer lokalen Variablen gespeichert.  
  
```  
DECLARE @property varchar(255);  
EXEC @hr = sp_OAMethod @object, 'HostName', @property OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object  
    RETURN  
END;  
PRINT @property;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte OLE-Automatisierungs Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE-Automatisierungsbeispielskript](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
