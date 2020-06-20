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
ms.openlocfilehash: 3e8e8139427c7f2ad92eea856be8da542f65e344
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85050270"
---
# <a name="creating-natively-compiled-stored-procedures"></a>Erstellen systemintern kompilierter gespeicherter Prozeduren
  Von systemintern kompilierten gespeicherten Prozeduren wird nicht die vollständige [!INCLUDE[tsql](../../includes/tsql-md.md)] -Programmier- und -Abfrageoberfläche implementiert. Es gibt bestimmte [!INCLUDE[tsql](../../includes/tsql-md.md)] -Konstrukte, die innerhalb systemintern kompilierter gespeicherter Prozeduren nicht verwendet werden können. Weitere Informationen finden Sie [unter Unterstützte Konstrukte in System intern kompilierten gespeicherten Prozeduren](../in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md).  
  
 Allerdings gibt es auch mehrere [!INCLUDE[tsql](../../includes/tsql-md.md)] -Funktionen, die nur für systemintern kompilierte gespeicherte Prozeduren unterstützt werden:  
  
-   ATOMIC-Blöcke. Weitere Informationen finden Sie unter [ATOMIC-Blöcke](atomic-blocks-in-native-procedures.md).  
  
-   `NOT NULL`-Einschränkungen für Parameter von systemintern kompilierten gespeicherten Prozeduren und darin enthaltene Variablen. Sie können als `NULL` deklarierten Parametern oder Variablen keine `NOT NULL`-Werte zuweisen. Weitere Informationen finden Sie unter [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql).  
  
-   Schemabindung von systemintern kompilierten gespeicherten Prozeduren.  
  
 Systemintern kompilierte gespeicherte Prozeduren werden mithilfe von [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql) erstellt. Das folgende Beispiel zeigt eine speicheroptimierte Tabelle und eine systemintern kompilierte gespeicherte Prozedur, die zum Einfügen von Zeilen in die Tabelle verwendet wird.  
  
```sql  
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
  
 Im Codebeispiel ist an `NATIVE_COMPILATION` erkennbar, dass diese gespeicherte [!INCLUDE[tsql](../../includes/tsql-md.md)]-Prozedur eine systemintern kompilierte gespeicherte Prozedur ist. Die folgenden Optionen sind erforderlich:  
  
|Option|BESCHREIBUNG|  
|------------|-----------------|  
|`SCHEMABINDING`|Systemintern kompilierte gespeicherte Prozeduren müssen an das Schema der Objekte gebunden werden, auf die sie verweisen. Dies bedeutet, dass Tabellenverweise der Prozedur nicht gelöscht werden können. Tabellen, auf die in der Prozedur verwiesen wird, müssen ihren Schema Namen enthalten, und Platzhalter Zeichen ( \* ) sind in Abfragen nicht zulässig. `SCHEMABINDING` wird nur in dieser Version von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] für systemintern kompilierte gespeicherte Prozeduren unterstützt.|  
|`EXECUTE AS`|Systemintern kompilierte gespeicherte Prozeduren bieten keine Unterstützung für den standardmäßigen Ausführungskontext `EXECUTE AS CALLER`. Daher muss der Ausführungskontext angegeben werden. Die Optionen `EXECUTE AS OWNER` , der `EXECUTE AS` *Benutzer*und `EXECUTE AS SELF` werden unterstützt.|  
|`BEGIN ATOMIC`|Der Text einer systemintern kompilierten gespeicherten Prozedur muss genau ein ATOMIC-Block sein. ATOMIC-Blöcke gewährleisten die unteilbare Ausführung der gespeicherten Prozedur. Wenn die Prozedur außerhalb des Kontexts einer aktiven Transaktion aufgerufen wird, wird eine neue Transaktion gestartet, für die am Ende des ATOMIC-Blocks ein Commit ausgeführt wird. ATOMIC-Blöcke in systemintern kompilierten gespeicherten Prozeduren weisen zwei erforderliche Optionen auf:<br /><br /> `TRANSACTION ISOLATION LEVEL`. Siehe [Transaktions Isolations Stufen](../../database-engine/transaction-isolation-levels.md) für unterstützte Isolations Stufen.<br /><br /> `LANGUAGE`. Die Sprache der gespeicherten Prozedur muss auf eine der verfügbaren Sprachen bzw. einen der verfügbaren Sprachenaliase festgelegt werden.|  
  
 Bei `EXECUTE AS` und Windows-Anmeldungen kann ein Fehler aufgrund des Identitätswechsels auftreten, der über `EXECUTE AS` ausgeführt wird. Wenn ein Benutzerkonto die Windows-Authentifizierung verwendet, muss zwischen dem Dienstkonto, das für die [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Instanz verwendet wird, und der Domäne der Windows-Anmeldung vollständige Vertrauenswürdigkeit bestehen. Wenn keine volle Vertrauenswürdigkeit vorhanden ist, wird beim Erstellen einer System intern kompilierten gespeicherten Prozedur die folgende Fehlermeldung zurückgegeben: Meldung 15404, Informationen zum Windows NT-Gruppen-/Benutzerbenutzername ' username ' konnten nicht abgerufen werden. Fehlercode 0x5.  
  
 Um diesen Fehler zu beheben, verwenden Sie eine der folgenden Aktionen:  
  
-   Verwenden Sie für den [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Dienst ein Konto, das aus derselben Domäne wie der Windows-Benutzer stammt.  
  
-   Wenn [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ein Computer Konto wie Netzwerkdienst oder lokales System verwendet, muss der Computer von der Domäne, die den Windows-Benutzer enthält, als vertrauenswürdig eingestuft werden.  
  
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
  
    ```sql  
    ALTER PROCEDURE dbo.SP p1,...,pn  
    AS  
      EXEC dbo.SP_Vnew p1,...,pn  
    GO  
    ```  
  
5.  Löschen Sie optional SP_Vold.  
  
 Der Vorteil dieser Vorgehensweise besteht darin, dass die Anwendung nicht offline geschaltet wird. Allerdings sind mehr Schritte erforderlich, um die Verweise beizubehalten und sicherzustellen, dass sie immer auf die neueste Version der gespeicherten Prozedur zeigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [System intern kompilierte gespeicherte Prozeduren](natively-compiled-stored-procedures.md)  
  
  
