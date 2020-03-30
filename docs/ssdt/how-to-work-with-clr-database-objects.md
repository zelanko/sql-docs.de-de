---
title: Arbeiten mit CLR-Datenbankobjekten
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- sql.data.tools.allowsqlclrdebugging
ms.assetid: 4a28d43d-eb5e-444d-aace-5df691f38709
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: f8aa504554cc973e5babbfe3c8512f59932fa147
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75226727"
---
# <a name="how-to-work-with-clr-database-objects"></a>Vorgehensweise: Arbeiten mit CLR-Datenbankobjekten

Neben der Programmiersprache Transact\-SQL können Sie .NET Framework-Sprachen zum Erstellen von Datenbankobjekten verwenden, durch die Daten abgerufen und aktualisiert werden. Datenbankobjekte, die in verwaltetem Code geschrieben sind, werden als SQL Server-CLR-Datenbankobjekte (Common Language Runtime) bezeichnet. Eine Erläuterung der Vorteile bei der Verwendung von CLR-Datenbankobjekten in SQL Server sowie der Kriterien für die Wahl zwischen Transact\-SQL und CLR finden Sie unter [Vorteile der CLR-Integration](../relational-databases/clr-integration/clr-integration-overview.md) und [Vorteile von verwaltetem Code bei der Erstellung von Datenbankobjekten](https://msdn.microsoft.com/library/k2e1fb36.aspx).  
  
Zum Erstellen eines CLR-Datenbankobjekts in SQL Server Data Tools erstellen Sie ein Datenbankprojekt und fügen ihm dann ein CLR-Datenbankobjekt hinzu. Im Unterschied zu früheren Versionen von Visual Studio müssen Sie kein eigenes CLR-Projekt erstellen und dann einen Verweis vom Datenbankprojekt auf dieses CLR-Projekt hinzufügen. Wenn Sie das Datenbankprojekt erstellen und veröffentlichen, werden die CLR-Objekte zur selben Zeit automatisch im Projekt veröffentlicht. Nachdem Sie die CLR-Objekte veröffentlicht haben, können sie wie jedes andere Datenbankobjekt aufgerufen und ausgeführt werden.  
  
Die Eigenschaftenseiten CLR und CLR Build enthalten viele Einstellungen zum Verwenden von CLR-Datenbankobjekten im Projekt. Insbesondere enthält die Eigenschaftenseite CLR eine Berechtigungsstufeneinstellung zum Festlegen von Berechtigungen für die CLR-Assembly. Sie enthält außerdem die Einstellung DDL generieren, um zu steuern, ob DDL für die dem Projekt hinzugefügten CLR-Datenbankobjekte generiert wird. Die Eigenschaftenseite CLR Build enthält alle Compileroptionen, die Sie festlegen können, um die Kompilierung des CLR-Codes im Projekt zu konfigurieren. Sie können auf diese Eigenschaftenseiten zugreifen, indem Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt klicken und **Eigenschaften** auswählen.  
  
Zum Aktivieren des Debuggens von CLR-Datenbankobjekten öffnen Sie den **SQL Server-Objekt-Explorer**. Klicken Sie mit der rechten Maustaste auf den Server mit den CLR-Datenbankartefakten, die Sie debuggen möchten, und wählen Sie **SQL/CLR-Debuggen zulassen** aus. Es wird ein Meldungsfeld mit folgender Warnung angezeigt: "Beachten Sie, dass während des Debuggens alle verwalteten Threads auf diesem Server beendet werden. Möchten Sie das SQL CLR-Debugging auf diesem Server aktivieren?“ Beim Debuggen von CLR-Datenbankobjekten werden durch Unterbrechen der Ausführung alle Threads auf dem Server unterbrochen. Dies hat Auswirkungen auf andere Benutzer. Daher sollten Sie Anwendungen für CLR-Datenbankobjekte nicht auf einem Produktionsserver debuggen. Außerdem sollten Sie berücksichtigen, dass die Einstellungen nicht mehr im **SQL Server-Objekt-Explorer** geändert werden können, sobald Sie mit dem Debuggen begonnen haben. Im **SQL Server-Objekt-Explorer** vorgenommene Änderungen werden erst beim Start der nächsten Debugsitzung wirksam.  
  
Weitere Informationen über die Anforderungen zum Erstellen von CLR-Datenbankobjekten finden Sie in den entsprechenden Themen unter [Erstellen von Datenbankobjekten mit CLR-Integration (Common Language Runtime)](https://msdn.microsoft.com/library/ms131046.aspx).  
  
> [!WARNING]  
> Bei den folgenden Vorgehensweisen werden Entitäten verwendet, die in vorherigen Vorgehensweisen in den Abschnitten [Entwicklung verbundener Datenbanken](../ssdt/connected-database-development.md) und [Projektorientierte Entwicklung von Offlinedatenbanken](../ssdt/project-oriented-offline-database-development.md) erstellt wurden.  
  
### <a name="to-add-a-clr-database-object-to-your-project"></a>So fügen Sie einem Projekt ein CLR-Datenbankobjekt hinzu  
  
1.  Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Datenbankprojekt **TradeDev**, wählen Sie **Hinzufügen** aus, und klicken Sie auf **Neues Element**.  
  
2.  Wählen Sie die Vorlage **C# SQL CLR** und dann **SQL CLR – benutzerdefinierte Funktion** aus. Übernehmen Sie den Standardnamen, und klicken Sie auf **Hinzufügen**.  
  
3.  Fügen Sie der Klassendefinition folgenden Code hinzu: Diese Funktion überprüft eine US-Telefonnummer. Die Nummer muss aus 3 numerischen Zeichen bestehen, die optional in Klammern eingeschlossen sind, gefolgt von einem Satz 3 numerischer Zeichen und dann einem Satz 4 numerischer Zeichen. Beispiele für unterstützte Formate sind (425) 555-0123, 425-555-0123, 425 555 0123 und 1-425-555-0123.  
  
    ```  
  
    [SqlFunction(IsDeterministic = true, IsPrecise = true)]  
    public static SqlBoolean validatePhone(SqlString phone)  
    {  
        string aNorthAmericanPhoneNumberPattern = @"^[01]?[- .]?(\([2-9]\d{2}\)|[2-9]\d{2})[- .]?\d{3}[- .]?\d{4}$";  
        if (!phone.IsNull)  
        {  
           Regex regex = new Regex(aNorthAmericanPhoneNumberPattern);  
           return regex.IsMatch(phone.Value);  
        }  
        return true;  
     }  
    ```  
  
4.  Beachten Sie, dass `Regex` rot unterstrichen ist. Klicken Sie mit der rechten Maustaste auf `Regex`, wählen Sie **Auflösen** und dann **using System.Text.RegularExpressions** aus.  
  
5.  Wenn Sie für eine Microsoft SQL Server 2012-Serverinstanz entwickeln, können Sie diesen Schritt überspringen. SQL Server 2005 und SQL Server 2008 unterstützen nur Datenbankprojekte, die mit Version 2.0, 3.0 oder 3.5 von .NET Framework erstellt wurden. Um sicherzustellen, dass die .NET-Zielplattform ordnungsgemäß festgelegt ist, klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Datenbankprojekt **TradeDev**, und wählen Sie **Eigenschaften** aus. Ändern Sie auf der Eigenschaftenseite **SQLCLR** die **Zielplattform** in **.NET Framework 3.5** oder eine niedrigere Version. Klicken Sie im letzten Bildschirm auf **Ja**, um das Projekt zu schließen und erneut zu öffnen.  
  
6.  Klicken Sie mit der rechten Maustaste auf das Projekt **TradeDev**, und wählen Sie **Erstellen** aus, um das Projekt zu erstellen.  
  
7.  Doppelklicken Sie auf „Suppliers.sql“, und wählen Sie **Sicht-Designer** aus, um im Tabellen-Designer die Tabelle „Suppliers“ zu öffnen.  
  
8.  Klicken Sie auf die leere Zeile im Spaltenraster, um der Tabelle eine neue Spalte hinzuzufügen. Geben Sie im Feld **Name** **phone** und für **Datentyp** **nvarchar (128)** ein, und lassen Sie das Feld **NULL-Werte zulassen** markiert.  
  
9. Klicken Sie im Kontextbereich mit der rechten Maustaste auf den Knoten **CHECK-Einschränkungen**, und wählen Sie **Neue CHECK-Einschränkung hinzufügen** aus.  
  
10. Ersetzen Sie im Skriptbereich die Standarddefinition der Einschränkung durch die folgende Definition.  
  
    ```  
    CONSTRAINT [CK_Suppliers_CheckPhone] CHECK (dbo.validatePhone(phone)=1),  
    ```  
  
    Dadurch wird sichergestellt, dass jede Eingabe in das neue Feld "phone" mit der CLR-UDF überprüft wird, die zuvor hinzugefügt wurde.  
  
11. Drücken Sie F5, um das Projekt zu erstellen und in der lokalen Datenbank bereitzustellen.  
  
### <a name="to-use-clr-database-objects"></a>So verwenden Sie CLR-Datenbankobjekte  
  
1.  Navigieren Sie im **SQL Server-Objekt-Explorer** zu der lokalen Datenbank, in der Sie das Projekt bereitstellen.  
  
2.  Standardmäßig ist die CLR-Integration in SQL Server deaktiviert. Um CLR-Datenbankobjekte verwenden zu können, müssen Sie die CLR-Integration aktivieren. Verwenden Sie zu diesem Zweck die Option „CLR-fähig“ der gespeicherten Prozedur „sp_configure“. Weitere Informationen finden Sie im Thema [Aktivieren der CLR-Integration](../relational-databases/clr-integration/clr-integration-enabling.md).  
  
    Klicken Sie mit der rechten Maustaste auf die Datenbank, und wählen Sie **Neue Abfrage** aus. Fügen Sie im Abfragebereich den folgenden Code ein, und klicken Sie auf die Schaltfläche **Abfrage ausführen**.  
  
    ```  
  
    sp_configure 'clr enabled', 1;  
    GO  
    RECONFIGURE;  
    GO  
    ```  
  
3.  Klicken Sie mit der rechten Maustaste auf die Tabelle „Suppliers“, und wählen Sie **Daten anzeigen** aus.  
  
4.  Geben Sie für **id** **5** und für **name** **Contoso** ein, lassen Sie das Feld **Address** leer, und geben Sie für **phone** **425 3122 1222** ein. Verlassen Sie durch Drücken der TAB-TASTE das Feld **phone**, und beachten Sie die eingeblendete Meldung, dass die `INSERT`-Anweisung einen Konflikt mit der vorhandenen CHECK-Einschränkung verursacht, die die Eingabe im Feld **phone** mit einem vordefinierten Telefonmuster überprüft.  
  
5.  Ändern Sie die Eingabe in **425 312 1222**, und verlassen Sie das Feld mit der TAB-TASTE. Beachten Sie, dass die Eingabe jetzt akzeptiert wird.  
  
## <a name="see-also"></a>Weitere Informationen  
[Vorteile der CLR-Integration](../relational-databases/clr-integration/clr-integration-overview.md)  
[Vorteile der Verwendung von verwaltetem Code beim Erstellen von Datenbankobjekten](https://msdn.microsoft.com/library/k2e1fb36.aspx)  
[Erstellen von Datenbankobjekten mit CLR-Integration (Common Language Runtime)](https://msdn.microsoft.com/library/ms131046.aspx)  
  
