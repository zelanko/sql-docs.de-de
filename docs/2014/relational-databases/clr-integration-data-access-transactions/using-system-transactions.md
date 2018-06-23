---
title: Verwenden von System.Transactions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TransactionScope class
- Dispose method
- System.Transactions namespace
ms.assetid: 79656ce5-ce46-4c5e-9540-cf9869bd774b
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 44054210ce7bf889bdc6e38f181cf8b16e638215
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36059643"
---
# <a name="using-systemtransactions"></a>Verwenden von 'System.Transactions'
  Die `System.Transactions` Namespace bietet ein Transaktionsframework, die vollständig in ADO.NET integriert ist und [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Integration der common Language Runtime (CLR). Die `System.Transactions.TransactionScope` Klasse wird einen Codeblock transaktional, indem implizit Verbindungen in einer verteilten Transaktion einträgt. Sie müssen am Ende des Codeblocks, der durch `Complete` markiert wird, die `TransactionScope`-Methode aufrufen. Die `Dispose` Methode wird aufgerufen, wenn die programmausführung einen Codeblock, dass die Transaktion nicht fortgeführt wird verlässt die `Complete` Methode wird nicht aufgerufen. Wenn eine Ausnahme ausgelöst wurde, die dazu führt, dass der Code den Bereich verlässt, wird die Transaktion als nicht fortgeführt betrachtet.  
  
 Wir empfehlen die Verwendung einer `using` Block, um sicherzustellen, dass die `Dispose` Methode aufgerufen wird die `TransactionScope` Objekt bei der `using` -Block verlassen wird. Fehlschlagen von Commits oder Rollbacks ausstehender Transaktionen kann die Leistung erheblich beeinträchtigen, da das Zeitlimit für die `TransactionScope` eine Minute beträgt. Wenn Sie nicht verwenden eine `using` -Anweisung, führen Sie alle Arbeiten in einer `Try` blockieren und explizit aufrufen der `Dispose` Methode in der `Finally` Block.  
  
 Wenn innerhalb von `TransactionScope` eine Ausnahme auftritt, wird die Transaktion als inkonsistent markiert und aufgegeben. Es wird ein Rollback ausgeführt zurück, wenn die `TransactionScope` verworfen wird. Wenn keine Ausnahme auftritt, wird für teilnehmende Transaktionen ein Commit ausgeführt.  
  
 `TransactionScope` sollte verwendet werden, nur, wenn lokale und remote-Datenquellen oder externe Ressourcen-Manager zugegriffen wird. Der Grund dafür ist, dass die `TransactionScope`-Klasse immer zur Höherstufung von Transaktionen führt, selbst dann, wenn sie nur innerhalb einer Kontextverbindung verwendet wird.  
  
> [!NOTE]  
>  Die `TransactionScope`-Klasse erstellt `System.Transactions.Transaction.IsolationLevel` standardmäßig mit dem Wert `Serializable`. Je nach Ihrer Anwendung kann es vorteilhaft sein, die Isolationsstufe herabzusetzen, um ein hohes Konfliktpotenzial in der Anwendung zu vermeiden.  
  
> [!NOTE]  
>  Es empfiehlt sich, nur Updates, Einfügungen und Löschungen innerhalb verteilter Transaktionen für Remoteserver auszuführen, da sie erhebliche Datenbankressourcen in Anspruch nehmen. Wenn der Vorgang auf dem lokalen Server ausgeführt werden soll, ist keine verteilte Transaktion notwendig, sondern es reicht eine lokale Transaktion aus. SELECT-Anweisungen sperren unter Umständen Datenbankressourcen, ohne dass dies erforderlich ist. Und in einigen Szenarien ist die Verwendung von Auswahlen möglicherweise notwendig. Jeder Arbeitsschritt, der nicht die Datenbank betrifft, sollte außerhalb des Transaktionsbereichs durchgeführt werden, sofern keine anderen Ressourcen-Manager von der Transaktion betroffen sind. Wenngleich eine Ausnahme innerhalb des Transaktionsbereichs ein Transaktionscommit verhindert, verfügt die `TransactionScope`-Klasse nicht über die Möglichkeit, außerhalb des Bereichs der Transaktion selbst ein Rollback von Änderungen auszuführen, die Ihr Code vorgenommen hat. Wenn Sie beim Rollback der Transaktion Maßnahmen ergreifen müssen, müssen Sie Ihre eigene Implementierung der schreiben die `System.Transactions.IEnlistmentNotification` Schnittstelle, und in der Transaktion explizit eintragen.  
  
## <a name="example"></a>Beispiel  
 Um mit `System.Transactions` zu arbeiten, müssen Sie über einen Verweis auf die Datei System.Transactions.dll verfügen.  
  
 Der nachfolgende Code zeigt, wie eine Transaktion erstellt wird, die für zwei verschiedene Instanzen von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]heraufgestuft werden kann. Diese Instanzen werden durch zwei verschiedene dargestellt `System.Data.SqlClient.SqlConnection` Objekte, die umschlossen werden eine `TransactionScope` Block. Der Code erstellt den `TransactionScope`-Block mit einer `using`-Anweisung und öffnet die erste Verbindung, wodurch sie automatisch im `TransactionScope` eingetragen wird. Die Transaktion wird anfänglich als einfache Transaktion, nicht als vollständig verteilte Transaktion, eingetragen. Der Code geht von der Existenz bedingter Logik aus (welche der Kürze halber weggelassen wurde). Er öffnet die zweite Verbindung nur, wenn es benötigt wird, durch das Eintragen in die `TransactionScope`. Wenn die Verbindung geöffnet wird, wird die Transaktion automatisch auf eine vollständig verteilte Transaktion hochgestuft. Der Code ruft dann `TransactionScope.Complete` auf, was zur Ausführung eines Commits für die Transaktion führt. Der Code verwirft die beiden Verbindungen beim Beenden der `using` Anweisungen für die Verbindungen. Die `TransactionScope.Dispose` Methode für die `TransactionScope` wird automatisch aufgerufen, bei Beendigung des der `using` blockieren für die `TransactionScope`. Wenn an einem beliebigen Punkt in eine Ausnahme ausgelöst wurde die `TransactionScope` Block `Complete` nicht aufgerufen, und die verteilte Transaktion wird zurückgenommen zurück, wenn die `TransactionScope` verworfen wird.  
  
 Visual Basic  
  
```  
Using transScope As New TransactionScope()  
    Using connection1 As New SqlConnection(connectString1)  
        ' Opening connection1 automatically enlists it in the   
        ' TransactionScope as a lightweight transaction.  
        connection1.Open()  
  
        ' Do work in the first connection.  
  
        ' Assumes conditional logic in place where the second  
        ' connection will only be opened as needed.  
        Using connection2 As New SqlConnection(connectString2)  
            ' Open the second connection, which enlists the   
            ' second connection and promotes the transaction to  
            ' a full distributed transaction.  
            connection2.Open()  
  
            ' Do work in the second connection.  
  
        End Using  
    End Using  
  
    ' Commit the transaction.  
    transScope.Complete()  
End Using  
```  
  
 C#  
  
```  
using (TransactionScope transScope = new TransactionScope())  
{  
    using (SqlConnection connection1 = new   
       SqlConnection(connectString1))  
    {  
        // Opening connection1 automatically enlists it in the   
        // TransactionScope as a lightweight transaction.  
        connection1.Open();  
  
        // Do work in the first connection.  
  
        // Assumes conditional logic in place where the second  
        // connection will only be opened as needed.  
        using (SqlConnection connection2 = new   
            SqlConnection(connectString2))  
        {  
            // Open the second connection, which enlists the   
            // second connection and promotes the transaction to  
            // a full distributed transaction.   
            connection2.Open();  
  
            // Do work in the second connection.  
        }  
    }  
    //  The Complete method commits the transaction.  
    transScope.Complete();  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [CLR-Integration und -Transaktionen](../native-client-ole-db-transactions/transactions.md)  
  
  