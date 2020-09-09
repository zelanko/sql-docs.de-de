---
description: sp_OAGetErrorInfo (Transact-SQL)
title: sp_OAGetErrorInfo (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_OAGetErrorInfo_TSQL
- sp_OAGetErrorInfo
dev_langs:
- TSQL
helpviewer_keywords:
- sp_OAGetErrorInfo
ms.assetid: ceecea08-456f-4819-85d9-ecc9647d7187
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 89bb7dff2131d8463e26754148aa6e8032503fd7
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546011"
---
# <a name="sp_oageterrorinfo-transact-sql"></a>sp_OAGetErrorInfo (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Ruft OLE-Automatisierungsfehlerinformationen ab.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_OAGetErrorInfo [ objecttoken ]  
    [ , source OUTPUT ]   
    [ , description OUTPUT ]   
    [ , helpfile OUTPUT ]   
    [ , helpid OUTPUT ]   
```  
  
## <a name="arguments"></a>Argumente  
 *objecttoken*  
 Ist entweder das Objekt Token eines OLE-Objekts, das zuvor mit **sp_OACreate** erstellt wurde oder NULL ist. Wenn *objecttoken* angegeben wird, werden Fehlerinformationen für dieses Objekt zurückgegeben. Wird NULL angegeben, werden die Fehlerinformationen für den gesamten Batch zurückgegeben.  
  
 _Quell_ **Ausgabe**  
 Die Quelle der Fehlerinformation. Wenn angegeben, muss es sich um eine lokale Variable vom Typ **char**, **NCHAR**, **varchar**oder **nvarchar** handeln. Der Rückgabewert wird bei Bedarf entsprechend der Länge der lokalen Variablen abgeschnitten.  
  
 _description_ **Ausgabe** der Beschreibung  
 Die Beschreibung des Fehlers. Wenn angegeben, muss es sich um eine lokale Variable vom Typ **char**, **NCHAR**, **varchar**oder **nvarchar** handeln. Der Rückgabewert wird bei Bedarf entsprechend der Länge der lokalen Variablen abgeschnitten.  
  
 _HelpFile_ - **Ausgabe**  
 Die Hilfedatei des OLE-Objekts. Wenn angegeben, muss es sich um eine lokale Variable vom Typ **char**, **NCHAR**, **varchar**oder **nvarchar** handeln. Der Rückgabewert wird bei Bedarf entsprechend der Länge der lokalen Variablen abgeschnitten.  
  
 _HelpID_ - **Ausgabe**  
 Die Kontext-ID für die Hilfedatei. Wenn angegeben, muss es sich um eine lokale **int** -Variable handeln.  
  
> [!NOTE]  
>  Die Parameter für diese gespeicherte Prozedur werden durch die Position, nicht durch den Namen angegeben.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 0 (Erfolg) oder eine Zahl ungleich Null (Fehler), die dem ganzzahligen Wert von HRESULT entspricht, der vom OLE-Automatisierungsobjekt zurückgegeben wird.  
  
 Weitere Informationen zu HRESULT-Rückgabecodes finden Sie unter [Rückgabecodes und Fehlerinformationen der OLE-Automatisierung](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="result-sets"></a>Resultsets  
 Ist kein Ausgabeparameter angegeben, werden die Fehlerinformationen dem Client als Resultset zurückgegeben.  
  
|Spaltennamen|Datentyp|BESCHREIBUNG|  
|------------------|---------------|-----------------|  
|**Fehler**|**Binary (4)**|Binärdarstellung der Fehlernummer|  
|**Quelle**|**nvarchar (NN)**|Fehlerquelle|  
|**Beschreibung**|**nvarchar (NN)**|Beschreibung des Fehlers|  
|**HelpFile**|**nvarchar (NN)**|Hilfedatei für die Quelle|  
|**HelpID**|**int**|Hilfekontext-ID in der Hilfequelldatei|  
  
## <a name="remarks"></a>Hinweise  
 Jeder-Aufrufsatz einer gespeicherten OLE-Automatisierungs Prozedur (außer **sp_OAGetErrorInfo**) setzt die Fehlerinformationen zurück. aus diesem Grund werden von **sp_OAGetErrorInfo** nur Fehlerinformationen für den letzten gespeicherten Prozedur Aufrufs der OLE-Automatisierung abgerufen. Beachten Sie, dass **sp_OAGetErrorInfo** die Fehlerinformationen nicht zurücksetzt, dass Sie mehrmals aufgerufen werden kann, um dieselben Fehlerinformationen zu erhalten.  
  
 In der folgenden Tabelle werden OLE-Automatisierungsfehler und deren übliche Ursachen aufgelistet.  
  
|Fehler und HRESULT|Übliche Ursache|  
|-----------------------|------------------|  
|**Falscher Variablentyp (0x80020008)**|Der Datentyp eines [!INCLUDE[tsql](../../includes/tsql-md.md)] als Methoden Parameter übergebenen Werts entsprach nicht dem [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Datentyp des Methoden Parameters, oder ein NULL-Wert wurde als Methoden Parameter übergeben.|  
|**Unbekannter Name (0x8002006)**|Der angegebene Eigenschafts- oder Methodenname für das angegebene Objekt wurde nicht gefunden.|  
|**Ungültige Klassenzeichenfolge (0x800401f3)**|Die angegebene ProgID oder CLSID wurde in einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nicht als OLE-Objekt registriert. Benutzerdefinierte OLE-Automatisierungsserver müssen registriert werden, bevor Sie mit **sp_OACreate**instanziiert werden können. Hierzu können Sie das Regsvr32.exe-Hilfsprogramm für Prozess interne (dll-) Server oder den Befehls Zeilenschalter **/RegServer** für lokale (. exe-) Server verwenden.|  
|**Starten des Servers fehlgeschlagen (0x80080005)**|Das angegebene OLE-Objekt ist als lokaler OLE-Server (EXE-Datei) registriert, aber die EXE-Datei konnte nicht gefunden oder nicht ausgeführt werden.|  
|**Das angegebene Modul wurde nicht gefunden (0x8007007e)**|Das angegebene OLE-Objekt ist als In-Process-OLE-Server (DLL-Datei) registriert, aber die DLL-Datei konnte nicht gefunden oder nicht geladen werden.|  
|**Typenkonflikt (0x80020005)**|Der Datentyp einer lokalen [!INCLUDE[tsql](../../includes/tsql-md.md)]-Variablen, die zum Speichern eines zurückgegebenen Eigenschaftswertes oder eines Rückgabewertes einer Methode verwendet wird, entspricht nicht dem [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]-Datentyp des Rückgabewertes der Eigenschaft oder Methode. Oder der Rückgabewert einer Eigenschaft oder einer Methode wurde angefordert, gibt jedoch keinen Wert zurück.|  
|**Der Datentyp oder Wert des context-Parameters von sp_OACreate ist ungültig. (0x8004275b)**|Der Wert des Kontextparameters sollte 1, 4 oder 5 sein.|  
  
 Weitere Informationen zur Verarbeitung von HRESULT-Rückgabecodes finden Sie unter [Rückgabecodes und Fehlerinformationen der OLE-Automatisierung](../../relational-databases/stored-procedures/ole-automation-return-codes-and-error-information.md).  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert die Mitgliedschaft in der festen Server Rolle **sysadmin** oder die EXECUTE-Berechtigung direkt für diese gespeicherte Prozedur. `Ole Automation Procedures` die Konfiguration muss **aktiviert** sein, um alle System Prozeduren für OLE-Automatisierung verwenden zu können.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel werden OLE-Automatisierungsfehlerinformationen angezeigt.  
  
```  
DECLARE @output varchar(255);  
DECLARE @hr int;  
DECLARE @source varchar(255);  
DECLARE @description varchar(255);  
PRINT 'OLE Automation Error Information';  
EXEC @hr = sp_OAGetErrorInfo @object, @source OUT, @description OUT;  
IF @hr = 0  
BEGIN  
    SELECT @output = '  Source: ' + @source  
    PRINT @output  
    SELECT @output = '  Description: ' + @description  
    PRINT @output  
END  
ELSE  
BEGIN  
    PRINT '  sp_OAGetErrorInfo failed.'  
    RETURN  
END;  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte OLE-Automatisierungs Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql.md)   
 [OLE-Automatisierungsbeispielskript](../../relational-databases/stored-procedures/ole-automation-sample-script.md)  
  
  
