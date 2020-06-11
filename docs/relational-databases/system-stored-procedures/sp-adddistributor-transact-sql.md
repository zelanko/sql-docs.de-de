---
title: sp_adddistributor (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/09/2020
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddistributor
- sp_adddistributor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_adddistributor
ms.assetid: 35415502-68d0-40f6-993c-180e50004f1e
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5c82ffa7ad254fc56f1c544a714d8633b7d1a33c
ms.sourcegitcommit: 1be90e93980a8e92275b5cc072b12b9e68a3bb9a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84627181"
---
# <a name="sp_adddistributor-transact-sql"></a>sp_adddistributor (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Erstellt einen Eintrag in der [sys.sysServer](../../relational-databases/system-compatibility-views/sys-sysservers-transact-sql.md) -Tabelle (sofern nicht vorhanden), markiert den Server Eintrag als Verteiler und speichert Eigenschafts Informationen. Diese gespeicherte Prozedur wird auf dem Verteiler für die master-Datenbank ausgeführt, um den Server als Verteiler zu registrieren und zu markieren. Im Falle eines Remoteverteilers wird sie zusätzlich auf dem Verleger für die master-Datenbank ausgeführt, um den Remoteverteiler zu registrieren.  
  
 ![Symbol für Themenlink](../../database-engine/configure-windows/media/topic-link.gif "Symbol für Themenlink") [Transact-SQL-Syntaxkonventionen](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_adddistributor [ @distributor= ] 'distributor'   
    [ , [ @heartbeat_interval= ] heartbeat_interval ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @from_scripting= ] from_scripting ]  
```  
  
## <a name="arguments"></a>Argumente  
`[ @distributor = ] 'distributor'`Der Name des Verteilungs Servers. *Distributor* ist vom **Datentyp vom Datentyp sysname**und hat keinen Standardwert. Dieser Parameter wird nur bei der Einrichtung eines Remoteverteilers verwendet. Es werden Einträge für die Verteiler Eigenschaften in der msdb-Datenbank hinzugefügt **. MSdistributor** -Tabelle.  

> [!NOTE]
> Der Server Name kann als angegeben werden `<Hostname>,<PortNumber>` . Möglicherweise müssen Sie die Portnummer für die Verbindung angeben, wenn SQL Server unter Linux oder Windows mit einem benutzerdefinierten Port bereitgestellt wird und der-Browser Dienst deaktiviert ist.

`[ @heartbeat_interval = ] heartbeat_interval`Die maximale Anzahl von Minuten, die ein Agent durchlaufen werden kann, ohne eine Fortschrittsmeldung zu protokollieren. *heartbeat_interval* ist vom Datentyp **int**. der Standardwert ist 10 Minuten. Ein Auftrag des SQL Server-Agents wird erstellt, der nach diesem Zeitraum ausgeführt wird, um den Status der ausgeführten Replikations-Agents zu überprüfen.  
  
`[ @password = ] 'password']`Das Kennwort des **distributor_admin** Anmelde namens. *Password* ist vom **Datentyp vom Datentyp sysname**und hat den Standardwert NULL. Bei NULL oder einer leeren Zeichenfolge wird das Kennwort auf einen Zufallswert festgelegt. Das Kennwort muss konfiguriert sein, wenn der erste Remoteverteiler hinzugefügt wird. **distributor_admin** Anmelde Name und das *Kennwort* werden für den Eintrag für den Verbindungs Server gespeichert, der für eine *Verteiler* -RPC-Verbindung verwendet wird Wenn der *Verteiler* lokal ist, wird das Kennwort für **distributor_admin** auf einen neuen Wert festgelegt. Für Verleger mit einem Remote Verteiler muss beim Ausführen von **sp_adddistributor** sowohl auf dem Verleger als auch auf dem Verteiler der gleiche Wert für das *Kennwort* angegeben werden. [sp_changedistributor_password](../../relational-databases/system-stored-procedures/sp-changedistributor-password-transact-sql.md) kann verwendet werden, um das Verteiler Kennwort zu ändern.  
  
> [!IMPORTANT]  
>  Benutzer sollten nach Möglichkeit dazu aufgefordert werden, Anmeldeinformationen zur Laufzeit anzugeben. Wenn Anmeldeinformationen in einer Skriptdatei gespeichert werden müssen, muss die Datei an einem sicheren Ort gespeichert werden, um unberechtigten Zugriff zu vermeiden.  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 „0“ (erfolgreich) oder „1“ (fehlerhaft)  
  
## <a name="remarks"></a>Bemerkungen  
 **sp_adddistributor** wird bei der Momentaufnahme-, Transaktions-und Mergereplikation verwendet.  
  
## <a name="example"></a>Beispiel  
 [!code-sql[HowTo#AddDistPub](../../relational-databases/replication/codesnippet/tsql/sp-adddistributor-transa_1.sql)]  
  
## <a name="permissions"></a>Berechtigungen  
 Nur Mitglieder der festen Server Rolle **sysadmin** können **sp_adddistributor**ausführen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Konfigurieren der Veröffentlichung und der Verteilung](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistributor_property &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)   
 [sp_dropdistributor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md)   
 [sp_helpdistributor &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [Gespeicherte System Prozeduren &#40;Transact-SQL-&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Verteilung konfigurieren](../../relational-databases/replication/configure-distribution.md)  
  
  
