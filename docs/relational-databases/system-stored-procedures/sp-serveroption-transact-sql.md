---
title: sp_serveroption (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/11/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_serveroption_TSQL
- sp_serveroption
dev_langs:
- TSQL
helpviewer_keywords:
- 7343 (Database Engine error)
- sp_serveroption
ms.assetid: 47d04a2b-dbf0-4f15-bd9b-81a2efc48131
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1fcd6f158908893ce5eb86c24a3bb3882867bc2d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68104383"
---
# <a name="sp_serveroption-transact-sql"></a>sp_serveroption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Legt Serveroptionen für Remoteserver und Verbindungsserver fest.  
  
 
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
sp_serveroption [@server = ] 'server'   
      ,[@optname = ] 'option_name'       
      ,[@optvalue = ] 'option_value' ;  
```  
  
## <a name="arguments"></a>Argumente  
`[ @server = ] 'server'`Der Name des Servers, für den die Option festgelegt werden soll. *Server* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert.  
  
`[ @optname = ] 'option_name'`Die Option, die für den angegebenen Server festgelegt werden soll. *option_name* ist vom Datentyp **varchar (** 35 **)** und hat keinen Standardwert. *option_name* kann einen der folgenden Werte aufweisen.  
  
|value|BESCHREIBUNG|  
|-----------|-----------------|  
|**kompatibel mit Sortierung**|Betrifft die Ausführung verteilter Abfragen für Verbindungsserver. Wenn diese Option auf **true**festgelegt ist [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , wird davon ausgegangen, dass alle Zeichen auf dem Verbindungs Server in Bezug auf den Zeichensatz und die Sortierreihenfolge (oder die Sortierreihenfolge) mit dem lokalen Server kompatibel sind. Dies ermöglicht [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , Vergleiche für Zeichenspalten an den Provider zu senden. Wird diese Option nicht festgelegt, werden von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Vergleiche für Zeichenspalten immer lokal ausgewertet.<br /><br /> Diese Option sollte nur festgelegt werden, wenn sicher ist, dass die Datenquelle, die dem Verbindungsserver entspricht, den gleichen Zeichensatz und die gleiche Sortierreihenfolge wie der lokale Server verwendet.|  
|**Sortierungs Name**|Gibt den Namen der von der Remote Datenquelle verwendeten Sortierung an, wenn **use Remote COLLATIONS** auf **true** festgelegt ist und die Datenquelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] keine Datenquelle ist. Der Name muss eine von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]unterstützte Sortierung sein.<br /><br /> Verwenden Sie diese Option, wenn auf eine OLE DB-Datenquelle zugegriffen wird, die keine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenquelle ist, deren Sortierung jedoch mit einer der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sortierungen übereinstimmt.<br /><br /> Der Verbindungsserver muss eine einzige Sortierung unterstützen, die für alle Spalten in diesem Server verwendet wird. Legen Sie diese Option nicht fest, wenn der Verbindungsserver mehrere Sortierungen in einer einzelnen Datenquelle unterstützt oder wenn festgestellt wird, dass die Sortierung des Verbindungsservers nicht mit einer der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Sortierungen übereinstimmt.|  
|**Verbindungs Timeout**|Timeout Wert in Sekunden für das Herstellen einer Verbindung mit einem Verbindungs Server.<br /><br /> Wenn der Wert **0**ist, verwenden Sie den **sp_configure** Standard.|  
|**Datenzugriff**|Aktiviert und deaktiviert den Zugriff auf verteilte Abfragen für Verbindungsserver. Kann nur für **sys. Server** -Einträge verwendet werden, die über **sp_addlinkedserver**hinzugefügt wurden.|  
|**dist**|Verteiler|  
|**Verzögerte Schemaüberprüfung**|Bestimmt, ob das Schema von Remotetabellen überprüft wird.<br /><br /> Wenn der Wert **true**ist, wird die Schema Überprüfung von Remote Tabellen am Anfang der Abfrage übersprungen.|  
|**Kneipe**|Gebers.|  
|**Abfrage Timeout**|Der Timeout Wert für Abfragen für einen Verbindungs Server.<br /><br /> Wenn der Wert **0**ist, verwenden Sie den **sp_configure** Standard.|  
|**rpc**|Aktiviert RPC von dem betreffenden Server.|  
|**RPC-Ausgabe**|Aktiviert RPC zu dem betreffenden Server.|  
|**nationale**|Abonnenten.|  
|**Anlage**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**Remote Sortierung verwenden**|Bestimmt, ob die Sortierung einer Remotespalte oder eines lokalen Servers verwendet wird.<br /><br /> **True**gibt an, dass die Sortierung von Remote Spalten für [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquellen verwendet wird, und die im **Sortierungs Namen** angegebene Sortierung wird für nicht--[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Datenquellen verwendet.<br /><br /> Wenn der Wert **false**ist, verwenden verteilte Abfragen immer die Standardsortierung des lokalen Servers, während der **Sortierungs Name** und die Sortierung von Remote Spalten ignoriert werden. Der Standardwert ist **false**. (Der Wert **false** ist mit der in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7,0 verwendeten Sortierungs Semantik kompatibel.)|  
|**Remote Proc Transaction Promotion**|Verwenden Sie diese Option, um die Aktionen einer Server-zu-Server-Prozedur durch eine [!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator-Transaktion (MS DTC) zu schützen. Wenn diese Option auf TRUE (oder ON) festgelegt ist und eine remote gespeicherte Prozedur aufgerufen wird, wird eine verteilte Transaktion gestartet und bei MS DTC eingetragen. Die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz, die die remote gespeicherte Prozedur aufruft, wird als Transaktionsurheber bezeichnet und steuert die Beendigung der Transaktion. Wenn im Anschluss eine COMMIT TRANSACTION- oder ROLLBACK TRANSACTION-Anweisung für die Verbindung ausgegeben wird, fordert die steuernde Instanz MS DTC auf, die Beendigung der verteilten Transaktion auf den beteiligten Computern zu verwalten.<br /><br /> Nachdem eine verteilte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Transaktion gestartet wurde, können Aufrufe remote gespeicherter Prozeduren für weitere [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanzen erfolgen, die als Verbindungsserver definiert wurden. Alle Verbindungsserver werden in der verteilten [!INCLUDE[tsql](../../includes/tsql-md.md)]-Transaktion eingetragen, und MS DTC stellt sicher, dass die Transaktion für jeden Verbindungsserver abgeschlossen wird.<br /><br /> Wenn diese Option auf FALSE (oder OFF) festgelegt ist, wird eine lokale Transaktion beim Aufruf einer remote gespeicherten Prozedur für einen Verbindungsserver nicht zu einer verteilten Transaktion höher gestuft.<br /><br /> Falls die Transaktion vor dem Server-zu-Server-Prozeduraufruf bereits eine verteilte Transaktion ist, hat diese Option keine Auswirkung. Der Prozeduraufruf für einen Verbindungsserver wird unter der gleichen verteilten Transaktion ausgeführt.<br /><br /> Falls vor dem Server-zu-Server-Prozeduraufruf keine Transaktion in der Verbindung aktiv ist, hat diese Option keine Auswirkung. Die Prozedur wird dann für einen Verbindungsserver ohne aktive Transaktionen ausgeführt.<br /><br /> Der Standardwert für diese Option ist TRUE (oder ON).|  
  
`[ @optvalue = ] 'option_value'`Gibt an, ob der *option_name* aktiviert (**true** oder **on**) oder deaktiviert (**false** oder **Off**) sein soll. *option_value* ist vom Datentyp **varchar (** 10 **)** und hat keinen Standardwert.  
  
 *option_value* kann für die Optionen **Verbindungs Timeout** und **Abfrage Timeout** eine nicht negative ganze Zahl sein. Bei der Option **Sortierungs Name** kann *option_value* ein Sortierungs Name oder NULL sein.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn die Option " **Sortierungs kompatibel** " auf "true" festgelegt ist, wird der **Sortierungs Name** automatisch auf NULL festgelegt. Wenn der **Sortierungs Name** auf einen nicht-NULL-Wert festgelegt ist, wird die Sortierung mit der **Sortierung** automatisch auf false festgelegt.  
  
## <a name="permissions"></a>Berechtigungen  
 Erfordert ALTER ANY LINKED SERVER-Berechtigung auf dem Server.  
  
## <a name="examples"></a>Beispiele  
 Im folgenden Beispiel wird ein Verbindungsserver, der einer anderen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz (`SEATTLE3`) entspricht, so konfiguriert, dass seine Sortierung mit der Sortierung der lokalen [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz kompatibel ist.  
  
```sql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Gespeicherte Prozeduren für verteilte Abfragen &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_adddistpublisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addlinkedserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_dropdistpublisher &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [Gespeicherte Systemprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
