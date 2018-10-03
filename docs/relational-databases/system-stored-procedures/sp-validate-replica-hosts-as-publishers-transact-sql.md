---
title: Sp_validate_replica_hosts_as_publishers (Transact-SQL) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_validate_replica_hosts_as_publishers_TSQL
- sp_validate_replica_hosts_as_publishers
helpviewer_keywords:
- sp_validate_replica_hosts_as_publishers
ms.assetid: 45001fc9-2dbd-463c-af1d-aa8982d8c813
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9143c5c681ed9e992a06ccad6be4511c23be37b5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47639694"
---
# <a name="spvalidatereplicahostsaspublishers-transact-sql"></a>sp_validate_replica_hosts_as_publishers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  **Sp_validate_replica_hosts_as_publishers** ist eine Erweiterung der **Sp_validate_redirected_publisher** , mit der alle sekundären Replikate überprüft werden, statt nur das aktuelle primäre Replikat. **Sp_validate_replicat_hosts_as_publisher** eine gesamte AlwaysOn-Replikationstopologie überprüft. **Sp_validate_replica_hosts_as_publishers** muss direkt auf dem Verteiler ausgeführt werden, mithilfe einer Remotedesktopsitzung (21892) einen Doppel-Hop Sicherheitsfehler vermieden werden.  
  
 ![Themenlinksymbol](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions (Transact-SQL-Syntaxkonventionen)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntax  
  
```  
  
sp_validate_replica_hosts_as_publishers   
    [ @original_publisher = ] 'original_publisher',  
    [ @publisher_db = ] 'database_name',   
    [ @redirected_publisher = ] 'new_publisher' output  
```  
  
## <a name="arguments"></a>Argumente  
 [ **@original_publisher** =] **"***Original_publisher***"**  
 Der Name der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz, die die Datenbank ursprünglich veröffentlicht hat. *Original_publisher* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@publisher_db** = ] **'***publisher_db***'**  
 Der Name der zu veröffentlichenden Datenbank. *Publisher_db* ist **Sysname**, hat keinen Standardwert.  
  
 [ **@redirected_publisher** =] **"***Redirected_publisher***"**  
 Das Ziel der Umleitung beim **Sp_redirect_publisher** für den ursprünglichen Verleger und veröffentlichter-Paar Datenbank aufgerufen wurde. *Redirected_publisher* ist **Sysname**, hat keinen Standardwert.  
  
## <a name="return-code-values"></a>Rückgabecodewerte  
 **0** (Erfolg) oder **1** (Fehler)  
  
## <a name="result-sets"></a>Resultsets  
 Keine.  
  
## <a name="remarks"></a>Hinweise  
 Wenn kein Eintrag für den Verleger und die Veröffentlichungsdatenbank vorhanden ist **Sp_validate_redirected_publisher** gibt null für den Ausgabeparameter *@redirected_publisher*. Andernfalls wird der zugeordnete umgeleitete Verleger zurückgegeben, sowohl bei Erfolg und als auch bei Fehler.  
  
 Wenn die Überprüfung erfolgreich ist, **Sp_validate_redirected_publisher** eine erfolgsanzeige zurück.  
  
 Wenn die Überprüfung fehlschlägt, werden entsprechende Fehler ausgelöst.  **Sp_validate_redirected_publisher** bemüht sich, lösen alle Probleme und nicht nur das erste auftreten wird.  
  
> [!NOTE]  
>  **sp_validate_replica_hosts_as_publishers** schlägt bei der Überprüfung sekundärer Replikathosts, die keinen Lesezugriff zulassen oder die Angabe der Leseabsicht erfordern, mit dem folgenden Fehler fehl.  
>   
>  Meldung 21899, Ebene 11, Status 1, Prozedur **sp_hadr_verify_subscribers_at_publisher**, Zeile 109  
>   
>  Die Abfrage beim umgeleiteten Verleger 'MyReplicaHostName', mit der bestimmt werden sollte, ob sysserver-Einträge für die Abonnenten des ursprünglichen Verlegers 'MyOriginalPublisher' vorlagen, schlug mit Fehler '976', Fehlermeldung 'Fehler 976, Ebene 14, Status 1, Meldung fehl: Die Zieldatenbank, 'MyPublishedDB', nimmt an einer Verfügbarkeitsgruppe teil, und ist derzeit nicht für Abfragen verfügbar. Entweder die Datenverschiebung wurde angehalten, oder für das Verfügbarkeitsreplikat wurde kein Schreibzugriff aktiviert. Um schreibgeschützten Zugriff auf diese und andere Datenbanken in der Verfügbarkeitsgruppe zuzulassen, aktivieren Sie den Lesezugriff auf mindestens ein sekundäres Verfügbarkeitsreplikat in der Gruppe.  Weitere Informationen finden Sie in der **ALTER AVAILABILITY GROUP** -Anweisung in der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Onlinedokumentation.  
>   
>  Es sind ein oder mehrere Verlegerüberprüfungsfehler für Replikathost 'MyReplicaHostName' aufgetreten.  
  
## <a name="permissions"></a>Berechtigungen  
 Aufrufer muss entweder ein Mitglied der **Sysadmin** festen Serverrolle, die **Db_owner** -Datenbankrolle für die Verteilungsdatenbank oder ein Mitglied einer veröffentlichungszugriffsliste für eine definierte Veröffentlichung die Publisher-Datenbank zugeordnet ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Gespeicherte Replikationsprozeduren &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)   
 [Sp_get_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-get-redirected-publisher-transact-sql.md)   
 [Sp_redirect_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-redirect-publisher-transact-sql.md)   
 [Sp_validate_redirected_publisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validate-redirected-publisher-transact-sql.md)  
  
  
