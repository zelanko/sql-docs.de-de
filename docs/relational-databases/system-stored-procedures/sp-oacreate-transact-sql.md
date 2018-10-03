---
title: Sp_OACreate (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OACreate
- sp_OACreate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OACreate
ms.assetid: eb84c0f1-26dd-48f9-9368-13ee4a30a27c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7e7ddb90a20b8d7d3c5aab323b803ca9fe3fcecf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47605238"
---
# <a name="spoacreate-transact-sql"></a>sp_OACreate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt eine Instanz eines OLE-Objekts.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_OACreate { progid | clsid } , objecttoken OUTPUT [ , context ]   
```  
  
## <a name="arguments"></a>Argumente  
 *ProgID*  
 Der programmtechnische Bezeichner (ProgID, Programmatic Identifier) des zu erstellenden OLE-Objekts. Diese Zeichenfolge beschreibt die Klasse des OLE-Objekts und weist das Format: **"***OLEComponent***. ***Objekt***"**  
  
 *OLEComponent* ist der Komponentenname des OLE-Automatisierungsservers, und *Objekt* ist der Name des OLE-Objekts. Das angegebene OLE-Objekt muss gültig sein und muss unterstützen die **IDispatch** Schnittstelle.  
  
 Beispielsweise ist SQLDMO. SQL Server ist die ProgID des SQL-DMO **SQLServer** Objekt. SQL-DMO besitzt den Komponentennamen SQLDMO, das **SQLServer** Objekt gültig ist, und (z. B. alle SQL-DMO-Objekte) die **SQLServer** -Objekt unterstützt **IDispatch**.  
  
 *clsid*  
 Die Klassen-ID (CLSID, Class Identifier) des zu erstellenden OLE-Objekts. Diese Zeichenfolge beschreibt die Klasse des OLE-Objekts und weist das Format: **"{***Nnnnnnnn-Nnnn-Nnnn-Nnnn-Nnnnnnnnnnnn***}'**. Das angegebene OLE-Objekt muss gültig sein und muss unterstützen die **IDispatch** Schnittstelle.  
  
 Beispielsweise ist {00026BA1-0000-0000-C000-000000000046} der CLSID des SQL-DMO **SQLServer** Objekt.  
  
 *Objecttoken* **Ausgabe**  
 Ist das zurückgegebene Objekttoken, und muss eine lokale Variable des Datentyps **Int**. Dieses Objekttoken identifiziert das erstellte OLE-Objekt und wird beim Aufruf von anderen gespeicherten Prozeduren der OLE-Automatisierung benötigt.  
  
 *context*  
 Gibt den Ausführungskontext an, in dem das neu erstellte OLE-Objekt ausgeführt wird. Wenn context angegeben wird, ist einer der folgenden Werte möglich:  
  
 **1** = nur in-Process-(DLL) OLE-Server.  
  
 **4** = lokal (.exe) OLE nur Server.  
  
 **5** = sowohl in-Process- und lokaler OLE-Server zulässig  
  
 Wenn nicht angegeben, wird der Standardwert ist **5**. Dieser Wert wird übergeben, als die *DwClsContext* Parameter des Aufrufs von **CoCreateInstance**.  
  
 Wenn die in-Process-OLE-Server zugelassen wird (mit einem Kontextwert, der **1** oder **5** oder kein Kontextwert angegeben), hat Sie Zugriff auf Speicher und andere Ressourcen im Besitz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ein In-Process-OLE-Server kann den Speicher und die Ressourcen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beschädigen und unvorhersehbare Ergebnisse verursachen, wie z. B. eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zugriffsverletzung.  
  
 Wenn Sie als Kontextwert angeben **4**, lokaler OLE-Server keinen Zugriff auf alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Ressourcen und kann nicht beschädigen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Arbeitsspeicher oder Ressourcen.  
  
> [!NOTE]  
>  Die Parameter für diese gespeicherte Prozedur werden nicht nach dem Namen, sondern nach der Position angegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler), die dem ganzzahligen Wert von HRESULT entspricht, der vom OLE-Automatisierungsobjekt zurückgegeben wird.  
  
 Weitere Informationen zu HRESULT-Rückgabecodes finden Sie unter [OLE Automation Rückgabecodes und Fehlerinformationen](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="remarks"></a>Hinweise  
 Wenn OLE-Automatisierungsprozeduren aktiviert sind, einen Aufruf von **Sp_OACreate** wird die freigegebene ausführungsumgebung für die OLE-Automatisierung gestartet. Weitere Informationen zum Aktivieren der OLE-Automatisierung finden Sie unter [Ole Automation Serverkonfigurationsoption](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md).  
  
 Das erstellte OLE-Objekt wird automatisch am Ende des [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungsbatches zerstört.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Serverrolle **sysadmin** .  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-progid"></a>A. Verwenden der ProgID  
 Das folgende Beispiel erstellt eine SQL-DMO **SQLServer** Objekt mithilfe seines ProgID.  
  
```  
DECLARE @object int;  
DECLARE @hr int;  
DECLARE @src varchar(255), @desc varchar(255);  
EXEC @hr = sp_OACreate 'SQLDMO.SQLServer', @object OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object, @src OUT, @desc OUT   
   raiserror('Error Creating COM Component 0x%x, %s, %s',16,1, @hr, @src, @desc)  
    RETURN  
END;  
GO  
```  
  
### <a name="b-using-clsid"></a>B. Verwenden der CLSID  
 Das folgende Beispiel erstellt eine SQL-DMO **SQLServer** Objekt mithilfe seines CLSID.  
  
```  
DECLARE @object int;  
DECLARE @hr int;  
DECLARE @src varchar(255), @desc varchar(255);  
EXEC @hr = sp_OACreate '{00026BA1-0000-0000-C000-000000000046}',  
    @object OUT;  
IF @hr <> 0  
BEGIN  
   EXEC sp_OAGetErrorInfo @object, @src OUT, @desc OUT   
   raiserror('Error Creating COM Component 0x%x, %s, %s',16,1, @hr, @src, @desc)  
    RETURN  
END;  
GO  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte OLE-Automatisierung Prozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE-Automatisierung Serverkonfigurationsoption](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)   
 [OLE-Automatisierungsbeispielskript](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
