---
title: Schreiben von sicherem dynamischem SQL in SQL Server
description: Beschreibt Verfahren, um mithilfe von gespeicherten Prozeduren sicheren dynamischen SQL-Code zu schreiben.
ms.date: 09/26/2019
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 22d64b260d8d700afc8ed354d87de730e8c3b21f
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253372"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>Schreiben von sicherem dynamischem SQL in SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Bei der Einschleusung von SQL-Befehlen gibt ein böswilliger Benutzer anstelle gültiger Eingaben Transact-SQL-Anweisungen ein. Wenn die Eingabe ohne Überprüfung direkt an den Server weitergegeben wird und die Anwendung den eingeschleusten Code versehentlich ausführt, kann der Angriff Daten beschädigen oder zerstören.  
  
Sie sollten jede Prozedur, die SQL-Anweisungen erstellt, nach Injection-Anfälligkeiten überprüfen, denn SQL Server führt alle empfangenen gültigen Abfragen aus. Auch parametrisierte Daten können von einem technisch versierten Angreifer manipuliert werden. Wenn Sie dynamisches SQL verwenden, stellen Sie sicher, dass Sie Ihre Befehle parametrisieren und Parameterwerte niemals direkt in die Abfragezeichenfolge einschließen.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Anatomie eines Angriffs durch Einschleusung von SQL-Befehlen  
Die Funktionalität des Injection-Prozesses besteht in der vorzeitigen Beendigung einer Textzeichenfolge und dem Anhängen eines neuen Befehls. Da vor der Ausführung des eingefügten Befehls möglicherweise weitere Zeichenfolgen daran angehängt wurden, beendet der Missetäter die eingefügte Zeichenfolge durch eine Kommentarmarkierung "--". Nachfolgender Text wird zur Ausführungszeit ignoriert. Mehrere Befehle können mit einem Semikolon (;) als Trennzeichen eingefügt werden.  
  
Solange der eingefügte SQL-Code syntaktisch richtig ist, kann eine Manipulation nicht programmgesteuert erkannt werden. Aus diesem Grund müssen Sie die Gültigkeit aller Benutzereingaben überprüfen und sorgfältig den Code überprüfen, der in dem von Ihnen verwendeten Server die erstellten SQL-Befehle ausführt. Verketten Sie niemals Benutzereingaben, die nicht überprüft wurden. Die Zeichenfolgenverkettung ist der primäre Eingangspunkt für Script-Injection.  
  
Hier einige nützliche Leitlinien:  
  
- Erstellen Sie niemals Transact-SQL-Anweisungen direkt aus Benutzereingaben. Verwenden Sie zur Überprüfung von Benutzereingaben gespeicherte Prozeduren.  
  
- Überprüfen Sie alle Benutzereingaben, indem Sie Typ, Länge, Format und Bereich testen. Verwenden Sie die Transact-SQL-Funktion QUOTENAME(), um Systemnamen mit Escapezeichen zu versehen, oder die Funktion REPLACE(), um ein beliebiges Zeichen in einer Zeichenfolge mit Escapezeichen zu versehen.  
  
- Implementieren Sie auf jeder Ebene Ihrer Anwendung mehrere Überprüfungsschichten.  
  
- Testen Sie Größe und Datentyp der Eingaben, und erzwingen Sie entsprechende Grenzwerte. Dies kann bei der Vermeidung absichtlicher Pufferüberläufe hilfreich sein.  
  
- Testen Sie den Inhalt der Zeichenfolgenvariablen, und akzeptieren Sie nur erwartete Werte. Lehnen Sie Einträge mit Binärdaten, Escapesequenzen und Befehlszeichen ab.  
  
- Überprüfen Sie alle Daten bei der Eingabe gegen das Schema, wenn Sie mit XML-Dokumenten arbeiten.  
  
- In Multi-Tier-Umgebungen sollten alle Daten vor dem Zugang zu einer vertrauensvollen Zone überprüft werden.  
  
- Folgende Zeichenfolge dürfen in Feldern, aus denen Dateiname erstellt werden können, nicht zugelassen werden: AUX, CLOCK$, COM1 bis COM8, CON, CONFIG$, LPT1 bis LPT8, NUL und PRN.  
  
- Verwenden Sie <xref:Microsoft.Data.SqlClient.SqlParameter>-Objekte mit gespeicherten Prozeduren und Befehlen, um eine Typ- und Längenüberprüfung durchzuführen.  
  
- Verwenden Sie <xref:System.Text.RegularExpressions.Regex>-Ausdrücke im Clientcode, um ungültige Zeichen herauszufiltern.  
  
## <a name="dynamic-sql-strategies"></a>Strategien für dynamisches SQL  
Die Ausführung dynamisch erstellter SQL-Anweisungen in Ihrem Prozedurcode unterbricht die Besitzkette und veranlasst SQL Server, die Berechtigungen des Aufrufers für die Objekte zu prüfen, auf die dynamisches SQL zugreift.  
  
SQL Server verfügt über Methoden, Benutzern mithilfe von gespeicherten Prozeduren und benutzerdefinierten Funktionen, die dynamisches SQL ausführen, den Zugriff auf Daten zu gewähren.  
  
- Identitätswechsel mit der Transact-SQL-EXECUTE AS-Klausel.  
  
- Signieren von gespeicherten Prozeduren mit Zertifikaten.  
  
### <a name="execute-as"></a>EXECUTE AS  
Die EXECUTE AS-Klausel ersetzt die Berechtigungen des Aufrufers durch die Berechtigungen des in der EXECUTE AS-Klausel angegebenen Benutzers. Geschachtelte gespeicherte Prozeduren oder Trigger werden unter dem Sicherheitskontext des Proxybenutzers ausgeführt. Dies kann Anwendungen stören, die Sicherheit auf Zeilenebene oder eine Überprüfung erfordern. Einige Funktionen, die die Identität des Benutzers zurückgeben, geben den in der Klausel EXECUTE AS angegebenen Benutzer zurück und nicht den ursprünglichen Aufrufer. Der Ausführungskontext wird erst nach Ausführung der Prozedur oder bei Ausführung einer REVERT-Anweisung auf den ursprünglichen Aufrufer zurückgesetzt.  
  
### <a name="certificate-signing"></a>Zertifikatsignierung  
Wenn eine gespeicherte Prozedur, die mit einem Zertifikat signiert wurde, ausgeführt wird, werden die dem Zertifikatsbenutzer erteilten Berechtigungen mit denen des Aufrufers zusammengeführt. Der Ausführungskontext bleibt derselbe. Der Zertifikatsbenutzer übernimmt nicht die Identität des Aufrufers. Das Signieren gespeicherter Prozeduren muss in mehreren Schritten implementiert werden. Bei jeder Änderung der Prozedur muss sie erneut signiert werden.  
  
### <a name="cross-database-access"></a>Datenbankübergreifender Zugriff  
Die datenbankübergreifende Besitzverkettung funktioniert nicht in Fällen, in denen dynamisch erstellte SQL-Anweisungen ausgeführt werden. Dieses Problem können Sie in SQL Server umgehen, indem Sie eine gespeicherte Prozedur erstellen, die auf die Daten in einer anderen Datenbank zugreift, und die Prozedur mit einem Zertifikat signieren, das in beiden Datenbanken vorhanden ist. Dadurch erhalten Benutzer Zugriff auf die von der Prozedur verwendeten Datenbankressourcen, ohne dass ihnen Datenbankzugriff gewährt wird oder Berechtigungen erteilt werden.  
  
## <a name="external-resources"></a>Externe Ressourcen  
Weitere Informationen finden Sie in den folgenden Ressourcen.  
  
|Resource|Beschreibung|  
|--------------|-----------------|  
|[Gespeicherte Prozeduren](../../../relational-databases/stored-procedures/stored-procedures-database-engine.md) und [SQL Injection](../../../relational-databases/security/sql-injection.md) in der SQL Server-Onlinedokumentation|In den Themen wird beschrieben, wie gespeicherte Prozeduren erstellt werden und die Einschleusung von SQL-Befehlen funktioniert.|  
  
## <a name="next-steps"></a>Nächste Schritte
- [Anwendungssicherheitsszenarios in SQL Server](application-security-scenarios-sql-server.md)
