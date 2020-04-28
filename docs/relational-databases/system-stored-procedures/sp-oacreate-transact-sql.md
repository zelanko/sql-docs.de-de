---
title: sp_OACreate (Transact-SQL) | Microsoft-Dokumentation
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
ms.openlocfilehash: 2ad8059466ac520b6f9f793af7670cbd73b96b38
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "68107935"
---
# <a name="sp_oacreate-transact-sql"></a>sp_OACreate (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Erstellt eine Instanz eines OLE-Objekts.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_OACreate { progid | clsid } , objecttoken OUTPUT [ , context ]   
```  
  
## <a name="arguments"></a>Argumente  
 *ProgID*  
 Der programmtechnische Bezeichner (ProgID, Programmatic Identifier) des zu erstellenden OLE-Objekts. Diese Zeichenfolge beschreibt die Klasse des OLE-Objekts und weist das folgende Format auf: **'**_OLEComponent_**.** _Objekt_**'**  
  
 *OLEComponent* ist der Komponenten Name des OLE-Automatisierungs Servers, und *Object* ist der Name des OLE-Objekts. Das angegebene OLE-Objekt muss gültig sein und die **IDispatch** -Schnittstelle unterstützen.  
  
 Beispiel: SQLDMO. SQLServer ist die ProgID des SQL-DMO **SQLServer** -Objekts. SQL-DMO verfügt über den Komponentennamen SQLDMO, das **SQLServer** -Objekt ist gültig, und (wie alle SQL-DMO-Objekte), unterstützt das **SQLServer** -Objekt **IDispatch**.  
  
 *CLSID*  
 Die Klassen-ID (CLSID, Class Identifier) des zu erstellenden OLE-Objekts. Diese Zeichenfolge beschreibt die Klasse des OLE-Objekts und weist das folgende Format auf: **"{**_NNNNNNNNN-nnnn-nnnn-nnnn-nnnnnnnnnnnnn_**}"**. Das angegebene OLE-Objekt muss gültig sein und die **IDispatch** -Schnittstelle unterstützen.  
  
 Beispielsweise ist {00026BA1-0000-0000-C000-000000000046} die CLSID des SQL-DMO **SQLServer** -Objekts.  
  
 _objecttoken_ - **Ausgabe**  
 Ist das zurückgegebene Objekt Token und muss eine lokale Variable vom Datentyp " **int**" sein. Dieses Objekt Token identifiziert das erstellte OLE-Objekt und wird in Aufrufen der anderen gespeicherten OLE-Automatisierungs Prozeduren verwendet.  
  
 *context*  
 Gibt den Ausführungskontext an, in dem das neu erstellte OLE-Objekt ausgeführt wird. Wenn context angegeben wird, ist einer der folgenden Werte möglich:  
  
 **1** = nur in-Process-OLE-Server (. dll).  
  
 **4** = lokaler OLE-Server (. exe).  
  
 **5** = sowohl Prozess interne als auch lokaler OLE-Server zulässig  
  
 Wenn kein Wert angegeben wird, ist der Standardwert **5**. Dieser Wert wird als *dwClsContext* -Parameter des Aufrufes **cokreateinstance**übergeben.  
  
 Wenn ein Prozess interner OLE-Server (unter Verwendung eines Kontext Werts von **1** oder **5** oder durch Angabe eines Kontext Werts) zulässig ist, hat er Zugriff auf den Arbeitsspeicher und andere Ressourcen, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]die im Besitz von sind. Ein In-Process-OLE-Server kann den Speicher und die Ressourcen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] beschädigen und unvorhersehbare Ergebnisse verursachen, wie z. B. eine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Zugriffsverletzung.  
  
 Wenn Sie einen Kontextwert von **4**angeben, verfügt ein lokaler OLE-Server nicht über Zugriff auf [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Ressourcen und kann keinen Arbeitsspeicher [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder keine Ressourcen beschädigen.  
  
> [!NOTE]  
>  Die Parameter für diese gespeicherte Prozedur werden nicht nach dem Namen, sondern nach der Position angegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler), die dem ganzzahligen Wert von HRESULT entspricht, der vom OLE-Automatisierungsobjekt zurückgegeben wird.  
  
 Weitere Informationen zu HRESULT-Rückgabecodes finden Sie unter [Rückgabecodes und Fehlerinformationen der OLE-Automatisierung](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn OLE-Automatisierungs Prozeduren aktiviert sind, wird durch einen **sp_OACreate** die freigegebene Ausführungsumgebung der OLE-Automatisierung gestartet. Weitere Informationen zum Aktivieren der OLE-Automatisierung finden Sie unter [OLE-Automatisierungs Prozeduren (Server Konfigurations Option](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)).  
  
 Das erstellte OLE-Objekt wird automatisch am Ende des [!INCLUDE[tsql](../../includes/tsql-md.md)]-Anweisungsbatches zerstört.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** oder die EXECUTE-Berechtigung direkt für diese gespeicherte Prozedur. `Ole Automation Procedures`die Konfiguration muss **aktiviert** sein, um alle System Prozeduren für OLE-Automatisierung verwenden zu können.  
  
## <a name="examples"></a>Beispiele  
  
### <a name="a-using-progid"></a>A. Verwenden der ProgID  
 Im folgenden Beispiel wird ein SQL-DMO- **SQLServer** -Objekt mithilfe der ProgID erstellt.  
  
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
 Im folgenden Beispiel wird ein SQL-DMO- **SQLServer** -Objekt mithilfe seiner CLSID erstellt.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte OLE-Automatisierungs Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE Automation Procedures (Server Konfigurations Option)](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)   
 [OLE-Automatisierungsbeispielskript](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
