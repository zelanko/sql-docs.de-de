---
title: Übersicht über die Sicherheit für R-und Python-Erweiterungen
description: Sicherheitsübersicht für das Erweiterbarkeits Framework in SQL Server Machine Learning Services. Sicherheit für Anmelde-und Benutzerkonten, SQL Server-Launchpad-Dienst, workerkonten, Ausführen mehrerer Skripts und Dateiberechtigungen.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 51587878d4a16145ff53eaa397da69130c04d7d5
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68343370"
---
# <a name="security-overview-for-the-extensibility-framework-in-sql-server-machine-learning-services"></a>Sicherheitsübersicht für das Erweiterbarkeit Framework in SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

In diesem Artikel wird die allgemeine Sicherheitsarchitektur beschrieben, die verwendet wird, um die SQL Server Datenbank-Engine und zugehörige Komponenten in das Erweiterbarkeit Framework zu integrieren. Sie untersucht die Sicherungs fähigen Elemente, Dienste, Prozess Identität und Berechtigungen. Weitere Informationen zu den wichtigsten Konzepten und Komponenten der Erweiterbarkeit in SQL Server finden Sie unter [Erweiterbarkeits Architektur in SQL Server Machine Learning Services](extensibility-framework.md)].

## <a name="securables-for-external-script"></a>Sicherungs fähige Elemente für externes Skript

Ein in R oder Python geschriebenes externes Skript wird als Eingabeparameter an eine [gespeicherte System Prozedur](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) übermittelt, die zu diesem Zweck erstellt wurde oder von einer gespeicherten Prozedur umschließt, die Sie definieren. Sie können auch Modelle haben, die in einem Binärformat in einer Datenbanktabelle vortrainiert und gespeichert werden und in einer T-SQL- [Vorhersage](../../t-sql/queries/predict-transact-sql.md) Funktion aufgerufen werden können.

Da das Skript über vorhandene Datenbankschema Objekte, gespeicherte Prozeduren und Tabellen bereitgestellt wird, sind für SQL Server Machine Learning Services keine neuen Sicherungs fähigen Elemente [verfügbar](../../relational-databases/security/securables.md) .

Unabhängig davon, wie Sie Skripts oder verwenden, werden Datenbankobjekte erstellt und wahrscheinlich gespeichert, aber es wird kein neuer Objekttyp für das Speichern von Skripts eingeführt. Folglich hängt die Fähigkeit zum Nutzen, erstellen und Speichern von Datenbankobjekten größtenteils von Daten Bank Berechtigungen ab, die bereits für Ihre Benutzer definiert wurden.

<a name="permissions"></a>

## <a name="permissions"></a>Berechtigungen

Das Daten Sicherheitsmodell von SQL Server Daten Bank Anmeldungen und-Rollen wird auf das R-und Python-Skript erweitert. Zum Ausführen externer Skripts, die SQL Server Daten verwenden oder die mit SQL Server als computekontext ausgeführt werden, ist ein SQL Server-oder Windows-Benutzerkonto erforderlich. Datenbankbenutzer, die über Berechtigungen zum Ausführen einer Ad-hoc-Abfrage verfügen, können auf dieselben Daten aus R-oder Python-Skript zugreifen

Der Anmelde Name oder das Benutzerkonto identifiziert den *Sicherheits Prinzipal*, der abhängig von den externen Skript Anforderungen möglicherweise mehrere Zugriffsebenen benötigt:

+ Berechtigung für den Zugriff auf die Datenbank, in der externe Skripts aktiviert sind.
+ Berechtigungen zum Lesen von Daten aus gesicherten Objekten, wie z. b. Tabellen.
+ Die Möglichkeit, neue Daten in eine Tabelle zu schreiben, z. b. ein Modell oder Bewertungsergebnisse.
+ Die Fähigkeit zum Erstellen von neuen Objekten, z. b. Tabellen, gespeicherte Prozeduren, die das externe Skript verwenden, oder benutzerdefinierte Funktionen, die R-oder python-Aufträge verwenden.
+ Das Recht, neue Pakete auf dem SQL Server Computer zu installieren oder Pakete zu verwenden, die für eine Gruppe von Benutzern bereitgestellt werden.

Jede Person, die ein externes Skript mit SQL Server als Ausführungs Kontext ausführt, muss einem Benutzer in der Datenbank zugeordnet werden. Anstatt die Datenbankbenutzer Berechtigungen einzeln festzulegen, können Sie Rollen erstellen, um Berechtigungs Sätze zu verwalten und diesen Rollen Benutzer zuzuweisen, anstatt Benutzerberechtigungen einzeln festzulegen.

Weitere Informationen finden Sie unter [Erteilen von Benutzerberechtigungen für SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md).

## <a name="permissions-when-using-an-external-client-tool"></a>Berechtigungen bei Verwendung eines externen Client Tools

Benutzer, die R oder python in einem externen Client Tool verwenden, müssen Ihren Anmelde Namen oder Ihr Konto einem Benutzer in der-Datenbank zuordnen, wenn Sie ein externes Skript in-Database ausführen oder auf Datenbankobjekte und-Daten zugreifen müssen. Die gleichen Berechtigungen sind erforderlich, unabhängig davon, ob das externe Skript von einem Remote Data Science Client gesendet oder mithilfe einer gespeicherten T-SQL-Prozedur ausgeführt wird.

Nehmen Sie beispielsweise an, dass Sie ein externes Skript erstellt haben, das auf dem lokalen Computer ausgeführt wird, und Sie dieses Skript auf SQL Server ausführen möchten. Sie müssen sicherstellen, dass die folgenden Bedingungen erfüllt sind:

+ Die Datenbank lässt Remoteverbindungen zu.
+ Die SQL-Anmeldung oder das Windows-Konto, das Sie für den Datenbankzugriff verwendet haben, wurde dem SQL Server auf Instanzebene hinzugefügt.
+ Die SQL-Anmeldung oder der Windows-Benutzer muss über die Berechtigung zum Ausführen externer Skripts verfügen. Diese Berechtigung kann in der Regel nur von einem Datenbankadministrator hinzugefügt werden.
+ Die SQL-Anmeldung oder der Windows-Benutzer muss in jeder Datenbank, in der das externe Skript einen der folgenden Vorgänge ausführt, als Benutzer mit den entsprechenden Berechtigungen hinzugefügt werden:
  + Abrufen von Daten.
  + Schreiben oder Aktualisieren von Daten.
  + Erstellen neuer Objekte, z. b. Tabellen oder gespeicherte Prozeduren.

Nachdem die Anmeldung oder das Windows-Benutzerkonto bereitgestellt wurde und die erforderlichen Berechtigungen erteilt wurden, können Sie ein externes Skript auf SQL Server ausführen, indem Sie ein Datenquellen Objekt in R oder die **revoscalepy** -Bibliothek in Python verwenden oder eine gespeicherte Prozedur aufrufen, die enthält das externe Skript.

Wenn ein externes Skript von SQL Server gestartet wird, ruft die Datenbank-Engine-Sicherheit den Sicherheitskontext des Benutzers ab, der den Auftrag gestartet hat, und verwaltet die Zuordnungen des Benutzers oder der Anmeldung bei Sicherungs fähigen Objekten.

Daher müssen alle externen Skripts, die von einem Remote Client initiiert werden, die Anmelde-oder Benutzerinformationen als Teil der Verbindungs Zeichenfolge angeben.

<a name="launchpad"></a>

## <a name="services-used-in-external-processing-launchpad"></a>In externer Verarbeitung verwendete Dienste (Launchpad)

Das Erweiterbarkeit Framework fügt der [Liste der Dienste](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md#Service_Details) in einer SQL Server Installation einen neuen NT-Dienst hinzu: [**SQL Server-Launchpad (MSSSQLServer)** ](extensibility-framework.md#launchpad).

Die Datenbank-Engine verwendet den SQL Server-Launchpad-Dienst, um eine R-oder python-Sitzung als separaten Prozess zu instanziieren. Der Prozess wird unter einem Konto mit geringen Berechtigungen ausgeführt. unterscheidet sich von SQL Server, Launchpad selbst und der Benutzeridentität, unter der die gespeicherte Prozedur oder die Host Abfrage ausgeführt wurde. Das Ausführen von Skripts in einem separaten Prozess, unter dem Konto mit geringen Rechten, ist die Grundlage für das Sicherheits-und Isolations Modell für R und python in SQL Server.

Zusätzlich zum Starten externer Prozesse ist das Launchpad auch für das Nachverfolgen der Identität des aufrufenden Benutzers und das Mapping der Identität zum Workerkonto mit geringen Berechtigungen, das zum Starten des Prozesses verwendet wird, verantwortlich. In einigen Szenarien, in denen Skript-oder Code Aufrufe an SQL Server für Daten und Vorgänge zurückgibt, ist launchpad in der Regel in der Lage, die Identitäts Übertragung nahtlos zu verwalten. Skripts mit SELECT-Anweisungen oder aufrufenden Funktionen und anderen Programmier Objekten sind in der Regel erfolgreich, wenn der aufrufenden Benutzer über ausreichende Berechtigungen verfügt.

> [!NOTE]
> Standardmäßig [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] ist so konfiguriert, dass Sie unter **NT service\mssqllaunchpad**ausgeführt wird, das mit allen erforderlichen Berechtigungen zum Ausführen externer Skripts bereitgestellt wird. Weitere Informationen zu konfigurierbaren Optionen finden Sie unter [SQL Server-Launchpad-Dienst Konfiguration](../security/sql-server-launchpad-service-account.md).

<a name="sqlrusergroup"></a>

## <a name="identities-used-in-processing-sqlrusergroup"></a>Bei der Verarbeitung verwendete Identitäten (sqlrusergroup)

**Sqlrusergroup** (Eingeschränkte SQL-Benutzergruppe) wird durch SQL Server-Setup erstellt und enthält einen Pool mit lokalen Windows-Benutzerkonten mit geringen Rechten. Wenn ein externer Prozess erforderlich ist, nimmt Launchpad ein verfügbares Workerkonto an und verwendet es, um einen Prozess auszuführen. Genauer gesagt aktiviert Launchpad ein verfügbares Workerkonto, ordnet es der Identität des aufrufenden Benutzers zu und führt das Skript unter dem Worker-Konto aus.

+ **Sqlrusergroup** ist mit einer bestimmten-Instanz verknüpft. Für jede Instanz, auf der Machine Learning aktiviert wurde, wird ein separater Pool von workerkonten benötigt. Konten können nicht zwischen Instanzen freigegeben werden.

+ Die Größe des Benutzerkonten Pools ist statisch, und der Standardwert ist 20, wodurch 20 gleichzeitige Sitzungen unterstützt werden. Die Anzahl der externen Lauf Zeit Sitzungen, die gleichzeitig gestartet werden können, ist durch die Größe dieses Benutzerkonten Pools beschränkt. 

+ Die Namen der workerkonten im Pool weisen das Format "SqlInstanceName*NN*" auf. Beispielsweise enthält **sqlrusergroup** auf einer Standard Instanz die Konten MSSQLSERVER01, MSSQLSERVER02 usw. für bis MSSQLSERVER20.

Parallelisierte Tasks verbrauchen keine weiteren Konten. Wenn ein Benutzer beispielsweise eine Bewertungsaufgabe ausführt, die die parallele Verarbeitung verwendet, wird für alle Threads dasselbe Workerkonto verwendet. Wenn Sie Machine Learning intensiv nutzen möchten, können Sie die Anzahl der Konten erhöhen, die zum Ausführen externer Skripts verwendet werden. Weitere Informationen finden Sie unter [Ändern des Benutzerkonten Pools für Machine Learning](../../advanced-analytics/administration/modify-user-account-pool.md).

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
### <a name="appcontainer-isolation-in-sql-server-2019"></a>Appcontainer-Isolation in SQL Server 2019

In SQL Server 2019 werden workerkonten für **sqlrusergroup**nicht mehr von Setup erstellt. Stattdessen wird die Isolation durch [appcontainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation)erreicht. Wenn ein externes Skript in einer gespeicherten Prozedur oder Abfrage erkannt wird, ruft SQL Server zur Laufzeit Launchpad mit einer Anforderung für ein Erweiterungs spezifisches Start Programm auf. Launchpad Ruft die entsprechende Laufzeitumgebung in einem Prozess unter seiner Identität auf und instanziiert einen appcontainer, um ihn zu enthalten. Diese Änderung ist von Vorteil, da die Verwaltung lokaler Konten und Kenn Wörter nicht mehr erforderlich ist. Außerdem können Sie bei Installationen, bei denen lokale Benutzerkonten nicht zulässig sind, diese Funktion jetzt verwenden.

Gemäß der Implementierung durch SQL Server sind appcontainers ein interner Mechanismus. Obwohl im Prozess Monitor keine physischen Beweise von appcontainers angezeigt werden, können Sie diese in ausgehenden Firewallregeln finden, die vom-Setup erstellt wurden, um zu verhindern, dass Prozesse Netzwerk Aufrufe durchführen. Weitere Informationen finden Sie unter [Firewallkonfiguration für SQL Server Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md).

> [!Note]
> In SQL Server 2019 verfügt **sqlrusergroup** nur über einen Member, bei dem es sich um das einzige SQL Server-Launchpad Dienst Konto anstelle mehrerer workerkonten handelt.
::: moniker-end

### <a name="permissions-granted-to-sqlrusergroup"></a>Sqlrusergroup erteilte Berechtigungen

Standardmäßig verfügen Mitglieder von **sqlrusergroup** über Lese-und Ausführungs Berechtigungen für Dateien in den SQL Server **Binn**-, **R_SERVICES**-und **PYTHON_SERVICES** -Verzeichnissen mit Zugriff auf ausführbare Dateien, Bibliotheken und integrierte Datasets in R. und mit SQL Server installierte python-Distributionen. 

Um sensible Ressourcen auf SQL Server zu schützen, können Sie optional eine Zugriffs Steuerungs Liste (ACL) definieren, die den Zugriff auf **sqlrusergroup**verweigert. Umgekehrt können Sie auch lokalen Datenressourcen, die auf dem Host Computer vorhanden sind, Berechtigungen erteilen, abgesehen von SQL Server selbst. 

Der-Entwurf von **sqlrusergroup** besitzt keine Daten Bank Anmeldung oder Berechtigungen für Daten. Unter bestimmten Umständen möchten Sie möglicherweise einen Anmelde Namen erstellen, um Schleifen Rückrufe zuzulassen, insbesondere dann, wenn eine vertrauenswürdige Windows-Identität der aufrufende Benutzer ist. Diese Funktion wird als [*implizite Authentifizierung*](#implied-authentication)bezeichnet. Weitere Informationen finden Sie unter [Hinzufügen von sqlrusergroup als Datenbankbenutzer](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md).

## <a name="identity-mapping"></a>Identitäts Zuordnung

Wenn eine Sitzung gestartet wird, ordnet Launchpad die Identität des aufrufenden Benutzers einem Workerkonto zu. Die Zuordnung eines externen Windows-Benutzers oder einer gültigen SQL-Anmeldung zu einem Workerkonto ist nur für die Lebensdauer der gespeicherten SQL-Prozedur gültig, die das externe Skript ausführt. Parallele Abfragen von derselben Anmeldung werden demselben Benutzerworkerkonto zugeordnet.

Während der Ausführung erstellt Launchpad temporäre Ordner zum Speichern von Sitzungsdaten und löscht diese, wenn die Sitzung beendet wird. Die Verzeichnisse sind Zugriffs eingeschränkt. Für R führt rlauncher diese Aufgabe aus. Für python führt pythonlauncher diese Aufgabe aus. Jedes einzelne Workerkonto ist auf seinen eigenen Ordner beschränkt, und auf Dateien in Ordnern über der eigenen Ebene kann nicht zugegriffen werden. Das Workerkonto kann jedoch untergeordnete Elemente unter dem erstellten Sitzungs Arbeitsordner lesen, schreiben oder löschen. Wenn Sie Administrator auf dem Computer sind, können Sie die Verzeichnisse anzeigen, die für jeden Prozess erstellt wurden. Jedes Verzeichnis wird durch die Sitzungs-GUID identifiziert.

<a name="implied-authentication"></a>

## <a name="implied-authentication-loop-back-requests"></a>Implizite Authentifizierung (Schleifen-Back-Anforderungen)

Die *implizite Authentifizierung* beschreibt das Verhalten der Verbindungsanforderung, unter dem externe Prozesse, die als workerkonten mit geringen Rechten ausgeführt werden, als vertrauenswürdige Benutzeridentität für die SQL Server on-Schleifen Anforderungen für Daten oder Vorgänge dargestellt werden. Als Konzept gilt die implizite Authentifizierung für die Windows-Authentifizierung, in SQL Server Verbindungs Zeichenfolgen, die eine vertrauenswürdige Verbindung angeben, bei Anforderungen aus externen Prozessen, wie z. b. R-oder python-Skripts. Sie wird manchmal auch als *Schleifen Back*bezeichnet.

Vertrauenswürdige Verbindungen sind über R-und python-Skripts, jedoch nur mit zusätzlicher Konfiguration machbar. In der Erweiterbarkeits Architektur werden R-und python-Prozesse unter workerkonten ausgeführt und Erben Berechtigungen von der übergeordneten **sqlrusergroup**. Wenn eine Verbindungs Zeichenfolge angibt `Trusted_Connection=True`, wird die Identität des workerkontos in der Verbindungsanforderung angezeigt, die standardmäßig als SQL Server unbekannt ist.

Damit vertrauenswürdige Verbindungen erfolgreich hergestellt werden können, müssen Sie eine Daten Bank Anmeldung für **sqlrusergroup**erstellen. Danach verfügt jede vertrauenswürdige Verbindung von einem beliebigen Mitglied von **sqlrusergroup** über Anmelde Rechte für SQL Server. Schritt-für-Schritt-Anweisungen finden [Sie unter Hinzufügen von sqlrusergroup zu einer Daten Bank Anmeldung](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md).

Vertrauenswürdige Verbindungen sind nicht die am häufigsten verwendete Formulierung einer Verbindungsanforderung. Wenn das R-oder Python-Skript eine Verbindung angibt, kann es häufiger vorkommen, dass ein SQL-Anmelde Name oder ein vollständig angegebener Benutzername und dasselbe Kennwort verwendet werden, wenn die Verbindung mit einer ODBC-Datenquelle hergestellt wird.

### <a name="how-implied-authentication-works-for-r-and-python-sessions"></a>Funktionsweise der impliziten Authentifizierung für R-und python-Sitzungen

Das folgende Diagramm zeigt die Interaktion von SQL Server-Komponenten mit der r-Laufzeit und die Art der impliziten Authentifizierung für R.

![Implizite Authentifizierung für R](../security/media/implied-auth-rsql.png)

Das nächste Diagramm zeigt die Interaktion von SQL Server Komponenten mit der python-Laufzeit und die Art der impliziten Authentifizierung für python.

![Implizite Authentifizierung für python](../security/media/implied-auth-python2.png)

## <a name="no-support-for-transparent-data-encryption-at-rest"></a>Keine Unterstützung für ruhende transparent Data Encryption

[Transparent Data Encryption (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md) wird für Daten, die an die externe Skript Laufzeit gesendet oder von dieser empfangen werden, nicht unterstützt. Der Grund hierfür ist, dass der externe Prozess (R oder python) außerhalb des SQL Server Prozesses ausgeführt wird. Aus diesem Grund werden Daten, die von der externen Laufzeit verwendet werden, nicht durch die Verschlüsselungsfunktionen der Datenbank-Engine geschützt. Dieses Verhalten unterscheidet sich nicht von anderen Clients, die auf dem SQL Server Computer ausgeführt werden, der Daten aus der Datenbank liest und eine Kopie erstellt.

Folglich wird TDE **nicht** auf Daten angewendet, die Sie in R-oder python-Skripts verwenden, oder auf Daten, die auf einem Datenträger gespeichert sind, oder auf beibehaltene Zwischenergebnisse. Andere Verschlüsselungstypen, z. b. die Windows BitLocker-Verschlüsselung oder die Verschlüsselung von Drittanbietern, die auf Datei-oder Ordnerebene angewendet werden, gelten jedoch weiterhin.

Im Fall von [Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)haben externe Laufzeiten keinen Zugriff auf die Verschlüsselungsschlüssel. Daher können keine Daten an die Skripts gesendet werden.

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel haben Sie das Komponenten-und Interaktionsmodell der Sicherheitsarchitektur kennengelernt, die in das [Erweiterbarkeit Framework](../../advanced-analytics/concepts/extensibility-framework.md)integriert ist. Zu den in diesem Artikel behandelten wichtigen Punkten zählen der Zweck der Launchpad-, sqlrusergroup-und workerkonten, die Prozess Isolation von R und Python und die Zuordnung von Benutzer Identitäten zu workerkonten. 

Überprüfen Sie im nächsten Schritt die Anweisungen zum [Erteilen von Berechtigungen](../../advanced-analytics/security/user-permission.md). Für Server, die die Windows-Authentifizierung verwenden, sollten Sie auch das [Hinzufügen von sqlrusergroup zu einer Daten Bank Anmeldung](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md) lesen, um zu erfahren, wann eine zusätzliche Konfiguration erforderlich ist