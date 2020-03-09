---
title: Anwendungssicherheitsszenarios in SQL Server
description: Enthält Themen, in denen verschiedene Anwendungssicherheitsszenarien für ADO.NET- und SQL Server-Anwendungen erläutert werden.
ms.date: 09/26/2019
ms.assetid: 0164f3a4-406e-4693-bec3-03c8e18b46d7
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 76ed05f39cba61ea7f26deaef6cd38552b11f199
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2020
ms.locfileid: "78897080"
---
# <a name="application-security-scenarios-in-sql-server"></a>Anwendungssicherheitsszenarios in SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

Es gibt kein universelles Standardverfahren, um eine sichere SQL Server-Clientanwendung zu erstellen. Die Anforderungen, Bereitstellungsumgebung und Benutzereigenschaften sind bei jeder Anwendung unterschiedlich. Bei einer Anwendung, die bei der anfänglichen Bereitstellung sicher ist, kann die Sicherheit im Laufe der Zeit nachlassen. Potenzielle Bedrohungen der Zukunft lassen sich nicht präzise vorhersagen.  
  
SQL Server wurde kontinuierlich weiterentwickelt und um die neuesten Sicherheitsfunktionen erweitert, mit denen Entwickler sichere Datenbankanwendungen erstellen können. Für maximale Sicherheit ist dennoch eine dauerhafte Überwachung und Aktualisierung erforderlich.  
  
## <a name="common-threats"></a>Gängige Bedrohungen  
Entwickler müssen sich kontinuierlich über Sicherheitsbedrohungen und die verfügbaren Tools informieren, um diesen Bedrohungen entgegenzuwirken. Darüber hinaus müssen sie wissen, wie sie selbstverschuldete Sicherheitslücken vermeiden. Die Sicherheit eines Systems ist mit einer Kette vergleichbar, bei der die Beschädigung eines Kettenglieds den Zusammenhalt der gesamten Kette gefährdet. In der folgenden Liste sind einige gängige Sicherheitsbedrohungen aufgeführt, die in den Themen dieses Abschnitts näher erläutert werden.  
  
### <a name="sql-injection"></a>Einschleusung von SQL-Befehlen  
Bei der Einschleusung von SQL-Befehlen gibt ein böswilliger Benutzer anstelle gültige Eingaben Transact-SQL-Anweisungen ein. Wenn die Eingabe ohne Überprüfung direkt an den Server weitergegeben wird und die Anwendung den eingeschleusten Code versehentlich ausführt, kann der Angriff Daten beschädigen oder zerstören. Sie können Angriffe, die das Ziel haben, SQL Server-Befehle einzuschleusen, abwehren, indem Sie gespeicherte Prozeduren und parametrisierte Befehle verwenden, dynamisches SQL vermeiden und die Berechtigungen aller Benutzer einschränken.  
  
### <a name="elevation-of-privilege"></a>Rechteerweiterungen  
Angriffe durch Rechteerweiterungen treten auf, wenn ein Benutzer die Berechtigungen eines vertrauenswürdigen Kontos (z.B. eines Besitzers oder Administrators) annehmen kann. Arbeiten Sie stets mit Benutzerkonten mit geringstmöglichen Berechtigungen, und weisen Sie nur die wirklich benötigten Berechtigungen zu. Vermeiden Sie bei der Ausführung von Code die Verwendung von Administrator- oder Besitzerkonten. Dadurch lässt sich der Schaden begrenzen, falls ein Angriff erfolgreich ist. Wenn Sie Aufgaben ausführen, für die zusätzliche Berechtigungen erforderlich sind, verwenden Sie für die Dauer der Aufgabe Prozedursignaturen oder einen Identitätswechsel. Sie können gespeicherte Prozeduren mit Zertifikaten signieren oder zur vorübergehenden Zuweisung von Berechtigungen mit Identitätswechsel arbeiten.  
  
### <a name="probing-and-intelligent-observation"></a>Probing und intelligente Beobachtung  
Bei einem Probing-Angriff können die von einer Anwendung generierten Fehlermeldungen verwendet werden, um nach Sicherheitslücken zu suchen. Implementieren Sie im gesamten prozeduralen Code eine Fehlerbehandlung, um zu verhindern, dass SQL Server-Fehlerinformationen an den Endbenutzer zurückgegeben werden.  
  
### <a name="authentication"></a>Authentifizierung  
Ein Angriff durch Einschleusung einer Verbindungszeichenfolge kann bei Verwendung von SQL Server-Anmeldungen auftreten, bei denen Verbindungszeichenfolgen zur Laufzeit basierend auf Benutzereingaben generiert werden. Wenn die Verbindungszeichenfolge nicht auf gültige Schlüsselwortkombinationen geprüft wird, kann ein Angreifer zusätzliche Zeichen einfügen und möglicherweise auf vertrauliche Daten oder andere Ressourcen auf dem Server zugreifen. Verwenden Sie nach Möglichkeit die Windows-Authentifizierung. Wenn Sie SQL Server-Anmeldungen nutzen müssen, verwenden Sie <xref:Microsoft.Data.SqlClient.SqlConnectionStringBuilder>, um Verbindungszeichenfolgen zur Laufzeit zu erstellen und zu überprüfen.  
  
### <a name="passwords"></a>Kennwörter  
Viele Angriffe sind erfolgreich, weil ein Eindringling ein Kennwort für einen Benutzer mit Administratorenrechten abrufen oder erraten konnte. Kennwörter dienen als erste Schutzmaßnahme gegen Eindringlinge, daher ist die Festlegung sicherer Kennwörter von entscheidender Bedeutung für die Systemsicherheit. Erstellen Sie Kennwortrichtlinien für die Authentifizierung im gemischten Modus, und setzen Sie diese Richtlinien durch.  
  
Weisen Sie dem `sa`-Konto immer ein sicheres Kennwort zu, auch wenn Sie die Windows-Authentifizierung verwenden.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
[Schreiben von sicherem dynamischem SQL in SQL Server](writing-secure-dynamic-sql.md)  
Beschreibt Verfahren, um mithilfe von gespeicherten Prozeduren sicheren dynamischen SQL-Code zu schreiben.  

## <a name="next-steps"></a>Nächste Schritte
- [SQL Server-Sicherheit](sql-server-security.md)
