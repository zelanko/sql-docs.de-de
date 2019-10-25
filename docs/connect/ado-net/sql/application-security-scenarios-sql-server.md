---
title: Anwendungssicherheitsszenarios in SQL Server
description: Enthält Themen, in denen verschiedene Anwendungssicherheitsszenarien für ADO.NET- und SQL Server-Anwendungen erläutert werden.
ms.date: 09/26/2019
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
ms.reviewer: rothja
ms.openlocfilehash: 711086e881951d9e82fd34851c451e5472e49d7e
ms.sourcegitcommit: 9c993112842dfffe7176decd79a885dbb192a927
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72452339"
---
# <a name="application-security-scenarios-in-sql-server"></a>Anwendungssicherheitsszenarios in SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[ADO.NET herunterladen](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Es gibt keine einzige korrekte Methode zum Erstellen einer sicheren SQL Server Client Anwendung. Jede Anwendung ist in Ihren Anforderungen, in der Bereitstellungs Umgebung und in der Benutzer Population eindeutig. Eine Anwendung, die bei der anfänglichen Bereitstellung einigermaßen sicher ist, kann im Laufe der Zeit weniger sicher werden. Es ist nicht möglich, vorherzusagen, welche Bedrohungen in Zukunft auftreten können.  
  
SQL Server als Produkt hat sich über viele Versionen entwickelt, um die neuesten Sicherheitsfunktionen zu bieten, die es Entwicklern ermöglichen, sichere Datenbankanwendungen zu erstellen. Sicherheit ist jedoch nicht in der Box enthalten. hierfür ist eine kontinuierliche Überwachung und Aktualisierung erforderlich.  
  
## <a name="common-threats"></a>Allgemeine Bedrohungen  
Entwickler müssen Sicherheitsbedrohungen verstehen, die Tools bereitstellen, mit denen Sie gegen Angriffe gegen Sie durchgesetzt werden können, und wie Sie selbst verursachte Sicherheitslücken vermeiden. Die Sicherheit kann am besten als Kette betrachtet werden, bei der eine Unterbrechung in einem Link die Stärke des ganzen beeinträchtigt. In der folgenden Liste sind einige häufige Sicherheitsbedrohungen enthalten, die in den Themen in diesem Abschnitt ausführlicher erläutert werden.  
  
### <a name="sql-injection"></a>Einschleusung von SQL-Befehlen  
SQL Injection ist der Prozess, bei dem ein böswilliger Benutzer anstelle einer gültigen Eingabe Transact-SQL-Anweisungen eingibt. Wenn die Eingabe ohne Validierung direkt an den Server weitergeleitet wird und die Anwendung den injizierten Code versehentlich ausführt, kann der Angriff Daten beschädigen oder zerstören. Sie können Angriffe, die das Ziel haben, SQL Server-Befehle einzuschleusen, abwehren, indem Sie gespeicherte Prozeduren und parametrisierte Befehle verwenden, dynamisches SQL vermeiden und die Berechtigungen aller Benutzer einschränken.  
  
### <a name="elevation-of-privilege"></a>Rechteerweiterungen  
Angriffe durch Rechte Erweiterungen treten auf, wenn ein Benutzer die Berechtigungen eines vertrauenswürdigen Kontos (z. b. Besitzer oder Administrator) annehmen kann. Führen Sie immer die Benutzerkonten mit den geringsten Rechten aus, und weisen Sie nur erforderliche Berechtigungen zu. Vermeiden Sie die Verwendung von Verwaltungs-oder Besitzer Konten zum Ausführen von Code. Dadurch wird die Menge an Schäden beschränkt, die auftreten können, wenn ein Angriff erfolgreich ist. Wenn Sie Aufgaben ausführen, die zusätzliche Berechtigungen erfordern, verwenden Sie die Prozedur Signierung oder den Identitätswechsel nur für die Dauer der Aufgabe. Sie können gespeicherte Prozeduren mit Zertifikaten signieren oder zur vorübergehenden Zuweisung von Berechtigungen mit Identitätswechsel arbeiten.  
  
### <a name="probing-and-intelligent-observation"></a>Überprüfung und intelligente Beobachtung  
Bei einem Überprüfungs Angriff können von einer Anwendung generierte Fehlermeldungen verwendet werden, um nach Sicherheitsrisiken zu suchen. Implementieren Sie die Fehlerbehandlung im gesamten prozeduralen Code, um zu verhindern, dass SQL Server Fehlerinformationen an den Endbenutzer zurückgegeben werden.  
  
### <a name="authentication"></a>Authentifizierung  
Ein einschleusungs Angriff für Verbindungs Zeichenfolgen kann auftreten, wenn SQL Server Anmeldungen verwendet wird, wenn eine auf Benutzereingaben basierende Verbindungs Zeichenfolge zur Laufzeit erstellt wird. Wenn die Verbindungs Zeichenfolge nicht auf gültige Schlüsselwort Paare geprüft wird, kann ein Angreifer zusätzliche Zeichen einfügen und möglicherweise auf sensible Daten oder andere Ressourcen auf dem Server zugreifen. Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn Sie SQL Server Anmeldungen verwenden müssen, verwenden Sie die <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder>, um Verbindungs Zeichenfolgen zur Laufzeit zu erstellen und zu überprüfen.  
  
### <a name="passwords"></a>Kennwörter  
Viele Angriffe sind erfolgreich, da ein Eindringling ein Kennwort für einen privilegierten Benutzer abrufen oder erraten konnte. Kennwörter dienen als erste Schutzmaßnahme gegen Eindringlinge, daher ist die Festlegung sicherer Kennwörter von entscheidender Bedeutung für die Systemsicherheit. Erstellen und Erzwingen von Kenn Wort Richtlinien für die Authentifizierung im gemischten Modus.  
  
Weisen Sie dem `sa` Konto immer ein sicheres Kennwort zu, auch wenn Sie die Windows-Authentifizierung verwenden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Schreiben von sicherem dynamischem SQL in SQL Server](writing-secure-dynamic-sql.md)  
Beschreibt Techniken zum Schreiben von sicherem dynamischem SQL mit gespeicherten Prozeduren.  

## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Sicherheit](sql-server-security.md)
