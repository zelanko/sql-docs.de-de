---
title: Schreiben von sicherem dynamischem SQL in SQL Server
description: Beschreibt Techniken zum Schreiben von sicherem dynamischem SQL mit gespeicherten Prozeduren.
ms.date: 09/26/2019
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: dd7b76e3333d51a94d6f215a6608511629f35fbe
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72451860"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a>Schreiben von sicherem dynamischem SQL in SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

SQL Injection ist der Prozess, bei dem ein böswilliger Benutzer anstelle einer gültigen Eingabe Transact-SQL-Anweisungen eingibt. Wenn die Eingabe ohne Validierung direkt an den Server übermittelt wird und die Anwendung versehentlich den injizierten Code ausführt, kann der Angriff Daten beschädigen oder zerstören.  
  
Sie sollten jede Prozedur, die SQL-Anweisungen erstellt, nach Injection-Anfälligkeiten überprüfen, denn SQL Server führt alle empfangenen gültigen Abfragen aus. Auch parametrisierte Daten können von einem technisch versierten Angreifer manipuliert werden. Wenn Sie dynamisches SQL verwenden, stellen Sie sicher, dass Sie die Befehle parametrisieren, und fügen Sie die Parameterwerte niemals direkt in die Abfrage Zeichenfolge ein.  
  
## <a name="anatomy-of-a-sql-injection-attack"></a>Anatomie eines SQL Injection-Angriffs  
Die Funktionalität des Injection-Prozesses besteht in der vorzeitigen Beendigung einer Textzeichenfolge und dem Anhängen eines neuen Befehls. Da vor der Ausführung des eingefügten Befehls möglicherweise weitere Zeichenfolgen daran angehängt wurden, beendet der Missetäter die eingefügte Zeichenfolge durch eine Kommentarmarkierung "--". Nachfolgender Text wird zur Ausführungszeit ignoriert. Mehrere Befehle können mithilfe eines Semikolons eingefügt werden (;) Trennzeichen.  
  
Solange der eingefügte SQL-Code syntaktisch richtig ist, kann eine Manipulation nicht programmgesteuert erkannt werden. Aus diesem Grund müssen Sie die Gültigkeit aller Benutzereingaben überprüfen und sorgfältig den Code überprüfen, der in dem von Ihnen verwendeten Server die erstellten SQL-Befehle ausführt. Verketten Sie niemals Benutzereingaben, die nicht überprüft wurden. Die Zeichenfolgenverkettung ist der primäre Eingangspunkt für Script-Injection.  
  
Im folgenden finden Sie einige hilfreiche Richtlinien:  
  
- Erstellen Sie niemals Transact-SQL-Anweisungen direkt aus der Benutzereingabe. Verwenden Sie gespeicherte Prozeduren zum Validieren von Benutzereingaben  
  
- Überprüfen Sie alle Benutzereingaben, indem Sie Typ, Länge, Format und Bereich testen. Verwenden Sie die Transact-SQL-QUOTENAME ()-Funktion, um Systemnamen und die Replace ()-Funktion mit Escapezeichen in einer Zeichenfolge zu versehen.  
  
- Implementieren Sie mehrere Validierungs Ebenen auf jeder Ebene der Anwendung.  
  
- Testen Sie Größe und Datentyp der Eingaben, und erzwingen Sie entsprechende Grenzwerte. Dies kann bei der Vermeidung absichtlicher Pufferüberläufe hilfreich sein.  
  
- Testen Sie den Inhalt der Zeichenfolgenvariablen, und akzeptieren Sie nur erwartete Werte. Lehnen Sie Einträge mit Binärdaten, Escapesequenzen und Befehlszeichen ab.  
  
- Überprüfen Sie alle Daten bei der Eingabe gegen das Schema, wenn Sie mit XML-Dokumenten arbeiten.  
  
- In Multi-Tier-Umgebungen sollten alle Daten vor dem Zugang zu einer vertrauensvollen Zone überprüft werden.  
  
- Akzeptieren Sie in Feldern, aus denen Dateinamen erstellt werden können, keine der folgenden Zeichenfolgen: AUX, CLOCK$, COM1 bis COM8, CON, CONFIG$, LPT1 bis LPT8, NUL und PRN.  
  
- Verwenden Sie <xref:Microsoft.Data.SqlClient.SqlParameter> Objekte mit gespeicherten Prozeduren und Befehlen, um die Typüberprüfung und Längen Validierung bereitzustellen.  
  
- Verwenden Sie <xref:System.Text.RegularExpressions.Regex> Ausdrücke im Client Code, um ungültige Zeichen zu filtern.  
  
## <a name="dynamic-sql-strategies"></a>Dynamische SQL-Strategien  
Wenn Sie dynamisch erstellte SQL-Anweisungen in Ihrem prozeduralen Code ausführen, wird die Besitz Kette unterbrochen, sodass SQL Server die Berechtigungen des Aufrufers für die Objekte überprüft, auf die der dynamische SQL-Server zugreift.  
  
SQL Server verfügt über Methoden, Benutzern mithilfe von gespeicherten Prozeduren und benutzerdefinierten Funktionen, die dynamisches SQL ausführen, den Zugriff auf Daten zu gewähren.  
  
- Identitätswechsel mit der Transact-SQL-EXECUTE AS-Klausel.  
  
- Signieren von gespeicherten Prozeduren mit Zertifikaten.  
  
### <a name="execute-as"></a>EXECUTE AS  
Die EXECUTE AS-Klausel ersetzt die Berechtigungen des Aufrufers durch die des Benutzers, der in der EXECUTE AS-Klausel angegeben ist. Gespeicherte gespeicherte Prozeduren oder Trigger werden im Sicherheitskontext des Proxy Benutzers ausgeführt. Dies kann Anwendungen unterbrechen, die auf Zeilen basierter Sicherheit basieren oder eine Überwachung erfordern. Einige Funktionen, die die Identität des Benutzers zurückgeben, geben den in der EXECUTE AS-Klausel angegebenen Benutzer und nicht den ursprünglichen Aufrufer zurück. Der Ausführungs Kontext wird erst nach der Ausführung der Prozedur oder bei der Ausgabe einer REVERT-Anweisung auf den ursprünglichen Aufrufer zurückgesetzt.  
  
### <a name="certificate-signing"></a>Zertifikatsignierung  
Wenn eine gespeicherte Prozedur, die mit einem Zertifikat signiert wurde, ausgeführt wird, werden die Berechtigungen, die dem Zertifikat Benutzer erteilt wurden, mit denen des Aufrufers zusammengeführt. Der Ausführungs Kontext bleibt unverändert. der Zertifikat Benutzer nimmt nicht die Identität des Aufrufers an. Zum Signieren gespeicherter Prozeduren müssen mehrere Schritte implementiert werden. Jedes Mal, wenn die Prozedur geändert wird, muss Sie erneut signiert werden.  
  
### <a name="cross-database-access"></a>Daten Bank übergreifender Zugriff  
Die datenbankübergreifende Besitz Verkettung funktioniert nicht in Fällen, in denen dynamisch erstellte SQL-Anweisungen ausgeführt werden. Dieses Problem können Sie in SQL Server umgehen, indem Sie eine gespeicherte Prozedur erstellen, die auf die Daten in einer anderen Datenbank zugreift, und die Prozedur mit einem Zertifikat signieren, das in beiden Datenbanken vorhanden ist. Dadurch erhalten Benutzer Zugriff auf die Datenbankressourcen, die von der Prozedur verwendet werden, ohne dass Ihnen Datenbankzugriff oder Berechtigungen gewährt werden.  
  
## <a name="external-resources"></a>Externe Ressourcen  
Weitere Informationen finden Sie in den folgenden Ressourcen.  
  
|Ressource|und Beschreibung|  
|--------------|-----------------|  
|[Gespeicherte Prozeduren](../../../relational-databases/stored-procedures/stored-procedures-database-engine.md) und [SQL Injection](../../../relational-databases/security/sql-injection.md) in der SQL Server-Onlinedokumentation|In den Themen wird beschrieben, wie gespeicherte Prozeduren erstellt werden und wie SQL Injection funktioniert.|  
  
## <a name="next-steps"></a>Nächste Schritte
- [Anwendungssicherheitsszenarios in SQL Server](application-security-scenarios-sql-server.md)
