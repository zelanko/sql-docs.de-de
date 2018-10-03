---
title: Erstellen systemintern kompilierter gespeicherter Prozeduren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e6b34010-cf62-4f65-bbdf-117f291cde7b
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 72c72dc551aa31dc22def397fb38fe09793478ef
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084510"
---
# <a name="creating-natively-compiled-stored-procedures"></a>Erstellen systemintern kompilierter gespeicherter Prozeduren
  Von systemintern kompilierten gespeicherten Prozeduren wird nicht die vollständige [!INCLUDE[tsql](../../includes/tsql-md.md)] -Programmier- und -Abfrageoberfläche implementiert. Es gibt bestimmte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Konstrukte, die innerhalb systemintern kompilierter gespeicherter Prozeduren nicht verwendet werden können. Weitere Informationen finden Sie unter [unterstützte Konstrukte in systemintern kompilierten gespeicherten Prozeduren](..\in-memory-oltp\supported-features-for-natively-compiled-t-sql-modules.md).  
  
 Allerdings gibt es auch mehrere [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktionen, die nur für systemintern kompilierte gespeicherte Prozeduren unterstützt werden:  
  
-   ATOMIC-Blöcke. Weitere Informationen finden Sie unter [ATOMIC-Blöcke](atomic-blocks-in-native-procedures.md).  
  
-   `NOT NULL`-Einschränkungen für Parameter von systemintern kompilierten gespeicherten Prozeduren und darin enthaltene Variablen. Sie können als `NULL` deklarierten Parametern oder Variablen keine `NOT NULL`-Werte zuweisen. Weitere Informationen finden Sie unter [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql).  
  
-   Schemabindung von systemintern kompilierten gespeicherten Prozeduren.  
  
 Systemintern kompilierte gespeicherte Prozeduren werden mithilfe von [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) erstellt. Das folgende Beispiel zeigt eine speicheroptimierte Tabelle und eine systemintern kompilierte gespeicherte Prozedur, die zum Einfügen von Zeilen in die Tabelle verwendet wird.  
  
```tsql  
create table dbo.Ord  
(OrdNo integer not null primary key nonclustered,   
 OrdDate datetime not null,   
 CustCode nvarchar(5) not null)   
 with (memory_optimized=on)  
go  
  
create procedure dbo.OrderInsert(@OrdNo integer, @CustCode nvarchar(5))  
with native_compilation, schemabinding, execute as owner  
as   
begin atomic with  
(transaction isolation level = snapshot,  
language = N'English')  
  
  declare @OrdDate datetime = getdate();  
  insert into dbo.Ord (OrdNo, CustCode, OrdDate) values (@OrdNo, @CustCode, @OrdDate);  
end  
go  
```  
  
 Im Codebeispiel `NATIVE_COMPILATION` gibt an, das von diesem [!INCLUDE[tsql](../../includes/tsql-md.md)] gespeicherte Prozedur ist eine systemintern kompilierte gespeicherte Prozedur. Die folgenden Optionen sind erforderlich:  
  
|Option|Description|  
|------------|-----------------|  
|`SCHEMABINDING`|Systemintern kompilierte gespeicherte Prozeduren müssen an das Schema der Objekte gebunden werden, auf die sie verweisen. Dies bedeutet, dass Tabellenverweise der Prozedur nicht gelöscht werden können. Tabellen, die in der Prozedur verwiesen wird, müssen ihre Schemaname und ein Platzhalter enthalten (\*) sind in Abfragen nicht zulässig. `SCHEMABINDING` wird nur für systemintern kompilierte gespeicherte Prozeduren in dieser Version unterstützt [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`EXECUTE AS`|Systemintern kompilierte gespeicherte Prozeduren bieten keine Unterstützung für den standardmäßigen Ausführungskontext `EXECUTE AS CALLER`. Daher muss der Ausführungskontext angegeben werden. Die Optionen `EXECUTE AS OWNER`, `EXECUTE AS` *Benutzer*, und `EXECUTE AS SELF` werden unterstützt.|  
|`BEGIN ATOMIC`|Der Text einer systemintern kompilierten gespeicherten Prozedur muss genau ein ATOMIC-Block sein. ATOMIC-Blöcke gewährleisten die unteilbare Ausführung der gespeicherten Prozedur. Wenn die Prozedur außerhalb des Kontexts einer aktiven Transaktion aufgerufen wird, wird eine neue Transaktion gestartet, für die am Ende des ATOMIC-Blocks ein Commit ausgeführt wird. ATOMIC-Blöcke in systemintern kompilierten gespeicherten Prozeduren weisen zwei erforderliche Optionen auf:<br /><br /> `TRANSACTION ISOLATION LEVEL`. installiert haben. Finden Sie unter [Isolationsstufen von Transaktionen](../../database-engine/transaction-isolation-levels.md) zu unterstützten Isolationsstufen.<br /><br /> `LANGUAGE`. installiert haben. Die Sprache der gespeicherten Prozedur muss auf eine der verfügbaren Sprachen bzw. einen der verfügbaren Sprachenaliase festgelegt werden.|  
  
 Bei `EXECUTE AS` und Windows-Anmeldungen kann ein Fehler aufgrund des Identitätswechsels auftreten, der über `EXECUTE AS` ausgeführt wird. Wenn ein Benutzerkonto die Windows-Authentifizierung verwendet, muss zwischen dem Dienstkonto, das für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz verwendet wird, und der Domäne der Windows-Anmeldung vollständige Vertrauenswürdigkeit bestehen. Wenn keine vollständige Vertrauenswürdigkeit vorliegt, wird die folgende Fehlermeldung zurückgegeben, wenn eine systemintern kompilierte gespeicherte Prozedur erstellt wird: Meldung 15404, Die Informationen über Windows NT-Gruppe oder -Benutzer 'username' konnten nicht abgerufen werden, Fehlercode 0x5.  
  
 Verwenden Sie eine der folgenden Schritte aus, um diesen Fehler zu beheben:  
  
-   Verwenden Sie für den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Dienst ein Konto, das aus derselben Domäne wie der Windows-Benutzer stammt.  
  
-   Wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ist durch die Domäne, in des Windows-Benutzers über ein Computerkonto wie Netzwerkdienst oder lokales System, den Computer vertrauenswürdig sein muss.  
  
-   Verwenden Sie die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Authentifizierung.  
  
 Möglicherweise wird auch Fehler 15517 angezeigt, wenn Sie eine systemintern kompilierte gespeicherte Prozedur erstellen. Weitere Informationen finden Sie unter [MSSQLSERVER_15517](../errors-events/mssqlserver-15517-database-engine-error.md).  
  
## <a name="updating-a-natively-compiled-stored-procedure"></a>Aktualisieren einer systemintern kompilierten gespeicherten Prozedur  
 Das Ausführen von Änderungsvorgängen für systemintern kompilierte gespeicherte Prozeduren wird nicht unterstützt. Eine Möglichkeit, eine systemintern kompilierte gespeicherte Prozedur zu ändern, ist das Löschen und erneute Erstellen der gespeicherten Prozedur:  
  
1.  Generieren Sie ein Skript mit Berechtigungen für die gespeicherte Prozedur.  
  
2.  Generieren Sie optional ein Skript für die gespeicherte Prozedur, und speichern Sie es als Sicherung.  
  
3.  Löschen Sie die gespeicherte Prozedur.  
  
4.  Erstellen Sie die geänderte gespeicherte Prozedur.  
  
5.  Wenden Sie das Skript mit den Berechtigungen erneut auf die gespeicherte Prozedur an.  
  
 Der Nachteil bei dieser Vorgehensweise besteht darin, dass die Anwendung vom Beginn von Schritt 3 bis zum Abschluss von Schritt 5 offline ist. Dies kann mehrere Sekunden dauern, und der Client, der die Anwendung verwendet, erhält in dieser Zeit möglicherweise Fehlermeldungen.  
  
 Eine andere (effektive) Möglichkeit zum Ändern einer systemintern kompilierten gespeicherten Prozedur besteht darin, zuerst eine neue Version der gespeicherten Prozedur zu erstellen. In diesem Fall erhält die systemintern kompilierte gespeicherte Prozedur eine zugehörige Versionsnummer. Die alte Version erhält die Bezeichnung SP_Vold und die neue Version die Bezeichnung SP_Vnew.  
  
1.  Generieren Sie ein Skript mit den Berechtigungen für SP_Vold.  
  
2.  Erstellen Sie SP_Vnew.  
  
3.  Wenden Sie die Berechtigungen von SP_Vold auf SP_Vnew an.  
  
4.  Aktualisieren Sie die Verweise auf SP_Vold, sodass sie auf SP_Vnew zeigen. Hierbei haben Sie verschiedene Möglichkeiten:  
  
     Verwenden Sie eine gespeicherte Wrapperprozedur (datenträgerbasiert), und ändern Sie diese Prozedur, sodass sie auf SP_Vnew zeigt. Der Nachteil bei dieser Vorgehensweise sind die Leistungsverluste durch die Dereferenzierung.  
  
    ```tsql  
    ALTER PROCEDURE dbo.SP p1,...,pn  
    AS  
      EXEC dbo.SP_Vnew p1,...,pn  
    GO  
    ```  
  
5.  Löschen Sie optional SP_Vold.  
  
 Der Vorteil dieser Vorgehensweise besteht darin, dass die Anwendung nicht offline geschaltet wird. Allerdings sind mehr Schritte erforderlich, um die Verweise beizubehalten und sicherzustellen, dass sie immer auf die neueste Version der gespeicherten Prozedur zeigen.  
  
## <a name="see-also"></a>Siehe auch  
 [Systemintern kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)  
  
  
