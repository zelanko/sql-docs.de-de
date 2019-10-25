---
title: Aktivieren mehrerer aktiver Resultsets
description: Enthält eine Erläuterung zum Verwenden von MARS mit SQL Server.
ms.date: 09/30/2019
dev_langs:
- csharp
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: d0c40df5ec7648b7073f9efa369428b8d88f6d11
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452226"
---
# <a name="enabling-multiple-active-result-sets"></a>Aktivieren mehrerer aktiver Resultsets

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

MARS ist eine Funktion, die mit SQL Server verwendet wird und das Ausführen mehrerer Batches über eine einzelne Verbindung ermöglicht. Wenn MARS für die Verwendung mit SQL Server aktiviert wird, fügen die einzelnen verwendeten Befehlsobjekte der Verbindung eine Sitzung hinzu.  
  
> [!NOTE]
>  Eine einzelne MARS-Sitzung öffnet eine logische Verbindung, die von Mars verwendet werden soll, und dann eine logische Verbindung für jeden aktiven Befehl.  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>Aktivieren und Deaktivieren von Mars in der Verbindungs Zeichenfolge  
  
> [!NOTE]
>  Die folgenden Verbindungszeichenfolgen verwenden die **AdventureWorks**-Beispieldatenbank aus SQL Server. Die angegebenen Verbindungs Zeichenfolgen gehen davon aus, dass die Datenbank auf einem Server mit dem Namen MSSQL1 installiert ist. Ändern Sie die Verbindungs Zeichenfolge nach Bedarf für Ihre Umgebung.  
  
Die MARS-Feature ist standardmäßig deaktiviert. Sie kann aktiviert werden, indem Sie das Schlüsselwort Paar "MultipleActiveResultSets = True" zur Verbindungs Zeichenfolge hinzufügen. „True“ ist der einzige gültige Wert zum Aktivieren von MARS. Im folgenden Beispiel wird veranschaulicht, wie eine Verbindung mit einer Instanz von hergestellt wird SQL Server und wie angegeben wird, dass MARS aktiviert werden soll. 
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
Sie können Mars deaktivieren, indem Sie das Schlüsselwort Paar "MultipleActiveResultSets = false" zu ihrer Verbindungs Zeichenfolge hinzufügen. „False“ ist der einzige gültige Wert zum Deaktivieren von MARS. In der folgenden Verbindungs Zeichenfolge wird veranschaulicht, wie Mars deaktiviert wird.  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a>Besondere Überlegungen bei der Verwendung von Mars  
Im Allgemeinen sollten vorhandene Anwendungen nicht geändert werden, um eine Mars-aktivierte Verbindung zu verwenden. Wenn Sie jedoch MARS-Features in Ihren Anwendungen verwenden möchten, sollten Sie sich mit den folgenden Besonderheiten vertraut machen.  
  
### <a name="statement-interleaving"></a>Anweisungsüberlappung  
Mars-Vorgänge werden synchron auf dem Server ausgeführt. Die Austausch Vorgänge von SELECT-und BULK INSERT-Anweisungen sind zulässig. DML-Anweisungen (Data Manipulation Language) und DDL-Anweisungen (Data Definition Language, Datendefinitionssprache) werden jedoch atomarisch ausgeführt. Alle Anweisungen, die während der Ausführung eines atomaren Batches ausgeführt werden sollen, werden blockiert. Die parallele Ausführung auf dem Server ist keine Mars-Funktion.  
  
Wenn zwei Batches unter einer MARS-Verbindung übermittelt werden, von denen eine eine SELECT-Anweisung enthält, die andere, die eine DML-Anweisung enthält, kann die DML-Anweisung innerhalb der Ausführung der SELECT-Anweisung ausgeführt werden. Allerdings muss die DML-Anweisung bis zum Abschluss ausgeführt werden, bevor die SELECT-Anweisung fortgesetzt werden kann. Wenn beide Anweisungen in derselben Transaktion ausgeführt werden, sind alle Änderungen, die von einer DML-Anweisung vorgenommen wurden, nachdem die SELECT-Anweisung gestartet wurde, für den Lesevorgang nicht sichtbar.  
  
Eine WAITFOR-Anweisung innerhalb einer SELECT-Anweisung ergibt nicht die Transaktion, während Sie wartet, d. h. bis die erste Zeile erstellt wird. Dies bedeutet, dass keine anderen Batches innerhalb derselben Verbindung ausgeführt werden können, während eine WAITFOR-Anweisung wartet.  
  
### <a name="mars-session-cache"></a>Mars-Sitzungs Cache  
Wenn eine Verbindung mit aktiviertem MARS geöffnet wird, wird eine logische Sitzung erstellt, wodurch zusätzlicher Verwaltungsaufwand entsteht. Um den Mehraufwand zu minimieren und die Leistungsfähigkeit zu erhöhen, führt **SqlClient** eine Zwischenspeicherung der MARS-Sitzung in einer Verbindung durch. Der Cache enthält höchstens 10 Mars-Sitzungen. Dieser Wert kann nicht vom Benutzer angepasst werden. Wenn das Sitzungs Limit erreicht ist, wird eine neue Sitzung erstellt – es wird kein Fehler generiert. Der Cache und die darin enthaltenen Sitzungen sind pro Verbindung. Sie werden nicht über Verbindungen gemeinsam genutzt. Wenn eine Sitzung freigegeben wird, wird Sie an den Pool zurückgegeben, es sei denn, die Obergrenze des Pools wurde erreicht. Wenn der Cache Pool voll ist, wird die Sitzung geschlossen. Mars-Sitzungen laufen nicht ab. Sie werden nur bereinigt, wenn das Verbindungs Objekt verworfen wird. Der Mars-Sitzungs Cache ist nicht vorab geladen. Es wird geladen, da die Anwendung mehr Sitzungen benötigt.  
  
### <a name="thread-safety"></a>Threadsicherheit  
Mars-Vorgänge sind nicht Thread sicher.  
  
### <a name="connection-pooling"></a>Verbindungspooling  
Mars-fähige Verbindungen werden wie jede andere Verbindung in einem Pool zusammengefasst. Wenn eine Anwendung zwei Verbindungen öffnet, eine mit aktiviertem Mars und eine, bei der Mars deaktiviert ist, befinden sich die beiden Verbindungen in separaten Pools.
  
### <a name="sql-server-batch-execution-environment"></a>SQL Server Batch Ausführungsumgebung  
Wenn eine Verbindung geöffnet wird, wird eine Standardumgebung definiert. Diese Umgebung wird dann in eine logische MARS-Sitzung kopiert.  
  
Die Batch Ausführungsumgebung umfasst die folgenden Komponenten:  
  
- SET-Optionen (z. b. ANSI_NULLS, date_format, Language, TEXTSIZE)  
  
- Sicherheitskontext (Benutzer/Anwendungs Rolle)  
  
- Daten Bank Kontext (aktuelle Datenbank)  
  
- Ausführungs Zustandsvariablen (z. b. @ @ERROR, @ @ROWCOUNT, @ @FETCH_STATUS @ @IDENTITY)  
  
- Temporäre Tabellen der obersten Ebene  
  
Bei Mars ist eine Standard Ausführungsumgebung einer Verbindung zugeordnet. Jeder neue Batch, dessen Ausführung unter einer bestimmten Verbindung gestartet wird, erhält eine Kopie der Standardumgebung. Wenn Code unter einem bestimmten Batch ausgeführt wird, werden alle an der Umgebung vorgenommenen Änderungen auf den jeweiligen Batch beschränkt. Beim Abschluss der Ausführung werden die Ausführungseinstellungen in die Standardumgebung kopiert. Bei einem einzelnen Batch, der mehrere Befehle ausgibt, die in derselben Transaktion sequenziell ausgeführt werden, ist die Semantik identisch mit derjenigen, die von Verbindungen mit früheren Clients oder Servern verfügbar gemacht werden.  
  
### <a name="parallel-execution"></a>Parallele Ausführung  
Mars ist nicht darauf ausgelegt, alle Anforderungen für mehrere Verbindungen in einer Anwendung zu entfernen. Wenn eine Anwendung eine echte parallele Ausführung von Befehlen für einen Server benötigt, sollten mehrere Verbindungen verwendet werden.  
  
Betrachten Sie beispielsweise das folgende Szenario. Es werden zwei Befehls Objekte erstellt, eine für die Verarbeitung eines Resultsets und eine andere zum Aktualisieren von Daten. Sie haben eine gemeinsame Verbindung über Mars. In diesem Szenario kann `Transaction`.`Commit` erst erfolgreich ausgeführt werden, nachdem alle Ergebnisse des ersten Befehlsobjekts gelesen wurden. Daher wird eine entsprechende Ausnahme ausgelöst:  
  
Meldung: Der Transaktionskontext wird von einer anderen Sitzung verwendet.  
  
Quelle: Microsoft SqlClient Datenanbieter  
  
Erwartet: (null)  
  
Empfangen: Microsoft. Data. SqlClient. SqlException  
  
Es gibt drei Optionen für die Behandlung dieses Szenarios:  
  
- Starten Sie die Transaktion, nachdem der Reader erstellt wurde, sodass Sie nicht Teil der Transaktion ist. Jedes Update wird dann zu seiner eigenen Transaktion.  
  
- Commit für alle arbeiten nach dem Schließen des Readers. Dies hat das Potenzial für einen beträchtlichen Batch von Updates.  
  
- Verwenden Sie Mars nicht. Verwenden Sie stattdessen für jedes Befehls Objekt eine separate Verbindung wie vor Mars.  
  
### <a name="detecting-mars-support"></a>Erkennen der Unterstützung von MARS  
Eine Anwendung kann die Mars-Unterstützung überprüfen, indem Sie den `SqlConnection.ServerVersion` Wert liest. Die Hauptnummer sollte 9 für SQL Server 2005 und 10 für SQL Server 2008 lauten.  
  
## <a name="next-steps"></a>Nächste Schritte
- [Mehrere aktive Resultsets (MARS)](multiple-active-result-sets-mars.md)
