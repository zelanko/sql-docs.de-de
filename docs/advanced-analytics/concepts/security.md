---
title: Übersicht über die Sicherheit für R und Python-Erweiterungen – SQL Server-Machine Learning
description: Übersicht über die Sicherheit für das Extensibility Framework in SQL Server-Machine Learning-Dienste. Sicherheit für die Anmeldung und Benutzerkonten, SQL Server Launchpad-Dienst, workerkonten, die mehrere Skripts und Dateiberechtigungen ausgeführt.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/17/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 1f19e3322b8aee78fdb5a76a29a719148cc6a0c7
ms.sourcegitcommit: 944af0f6b31bf07c861ddd4d7960eb7f018be06e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "66454535"
---
# <a name="security-overview-for-the-extensibility-framework-in-sql-server-machine-learning-services"></a>Übersicht über die Sicherheit für das Extensibility Framework in SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt die Sicherheitsarchitektur, die verwendet wird, um die SQL Server-Datenbank-Engine und die zugehörigen Komponenten mit dem Extensibility Framework zu integrieren. Er untersucht die sicherungsfähigen Elemente, Dienste, Prozess-ID und Berechtigungen. Weitere Informationen zu den wichtigsten Konzepten und Komponenten der Erweiterbarkeit in SQL Server finden Sie unter [erweiterbarkeitsarchitektur in SQL Server Machine Learning Services](extensibility-framework.md)].

## <a name="securables-for-external-script"></a>Sicherungsfähige Elemente für externe Skripts

Ein externes Skript, das in R oder Python geschriebenen gesendet wird, als ein Eingabeparameter für ein [gespeicherte Systemprozedur](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) für diesen Zweck erstellt oder in einer gespeicherten Prozedur, die Sie definieren umschlossen wird. Sie möglicherweise auch Modelle, die vorab und gespeichert, die in einem binären Format in einer Datenbanktabelle, in einer T-SQL aufgerufen [PREDICT](../../t-sql/queries/predict-transact-sql.md) Funktion.

Das Skript über die vorhandene Datenbank-Schemaobjekten, gespeicherte Prozeduren und Tabellen bereitgestellt wird, es sind keine neuen [sicherungsfähige Elemente](../../relational-databases/security/securables.md) für SQL Server-Machine Learning-Dienste.

Unabhängig davon, wie Sie Skripts verwenden oder, was sie bestehen Datenbankobjekte werden erstellt und wahrscheinlich gespeichert, aber keine neuen Objekttyp wird zum Speichern von Skripts eingeführt. Daher die Möglichkeit zu nutzen, erstellen und Speichern der Datenbank Objekte bei der hängt größtenteils von Datenbankberechtigungen, die für Ihre Benutzer bereits definiert.

<a name="permissions"></a>

## <a name="permissions"></a>Berechtigungen

SQL Server Daten-Sicherheitsmodell von Datenbank-Anmeldenamen und Rollen an R und Python-Skript erweitern. Ein SQL Server-Anmeldung oder der Windows-Benutzerkonto muss zum Ausführen von externen Skripts, die SQL Server-Daten verwenden, oder, die mit SQL Server als Compute Context ausgeführt. Datenbankbenutzer, die über Berechtigungen zum Ausführen einer ad-hoc-Abfrage können die gleichen Daten aus R oder Python-Skript zugreifen.

Gibt das Konto Anmeldenamen oder Benutzer an die *Sicherheitsprinzipal*, die möglicherweise mehrere Ebenen des Zugriffs, je nach den Anforderungen von externen Skript:

+ Berechtigung zum Zugriff auf die Datenbank, in dem externe Skripts aktiviert sind.
+ Berechtigungen zum Lesen von Daten aus gesicherten Objekten wie Tabellen.
+ Die Fähigkeit zum Schreiben von neuer Daten in eine Tabelle, z. B. ein Modell oder Bewertungsergebnisse.
+ Die Möglichkeit zum Erstellen neuer Objekte, z. B. Tabellen, gespeicherte Prozeduren, die das externe Skript verwenden oder benutzerdefinierte Funktionen, verwenden von R oder Python-Auftrags.
+ Das Recht, neue Pakete auf dem SQL Server-Computer installieren, oder verwenden für eine Gruppe von Benutzern bereitgestellte Pakete.

Jede Person, die ein externes Skript mithilfe von SQL Server als Ausführungskontext ausgeführt wird, muss zu einem Benutzer in der Datenbank zugeordnet werden. Statt einzeln Satz Berechtigungen des Datenbankbenutzers können Sie Rollen, um die Sätze von Berechtigungen, verwalten und diesen Rollen Benutzer zuweisen, statt Berechtigungen einzeln festzulegen, erstellen.

Weitere Informationen finden Sie unter [Vergabe von Benutzerberechtigungen für SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md).

## <a name="permissions-when-using-an-external-client-tool"></a>Berechtigungen, wenn ein externer Client-Tool verwenden.

Benutzer, die r oder Python in einem externen Client-Tool verwenden, müssen ihre Anmeldung oder das Konto zu einem Benutzer in der Datenbank zugeordnet werden, wenn sie ein externes Skript in der Datenbank, oder den Zugriff auf Datenbankobjekte und Daten ausführen müssen. Die gleichen Berechtigungen erforderlich sind, ob die externen Skripts aus einem Data Science-Remoteclient gesendet wird, oder führen Sie mithilfe einer gespeicherten T-SQL-Prozedur.

Nehmen wir beispielsweise an, dass Sie über ein externes Skript erstellt, das auf dem lokalen Computer ausgeführt wird, und das Skript in SQL Server ausgeführt werden soll. Sie müssen sicherstellen, dass die folgenden Bedingungen erfüllt sind:

+ Die Datenbank lässt Remoteverbindungen zu.
+ Die SQL-Anmeldung oder das Windows-Konto, die Sie für den Datenbankzugriff verwendet wurde mit der SQL Server auf Instanzebene hinzugefügt.
+ Die SQL-Anmeldung oder der Windows-Benutzer benötigen die Berechtigung zum Ausführen externer Skripts. Diese Berechtigung kann in der Regel nur von einem Datenbankadministrator hinzugefügt werden.
+ Die SQL-Anmeldung oder der Windows-Benutzer muss als Benutzer mit entsprechenden Berechtigungen in jeder Datenbank hinzugefügt werden, bei denen des externen Skripts für diese Vorgänge ausführt:
  + Abrufen von Daten aus.
  + Schreiben oder Aktualisieren von Daten.
  + Erstellen von neuen Objekten, z. B. Tabellen oder gespeicherte Prozeduren.

Nach der Anmeldung oder der Windows-Benutzerkonto bereitgestellt und die erforderlichen Berechtigungen zugewiesen wurde, können Sie ein externes Skript in SQL Server ausführen, indem Sie verwenden ein Datenquellenobjekt in R oder **Revoscalepy** -Bibliothek in Python oder durch Aufrufen einer gespeicherten die Prozedur mit dem externen Skript an.

Wenn ein externes Skript von SQL Server gestartet wird, ruft die Sicherheit der Datenbank-Engine den Sicherheitskontext des Benutzers, der der Auftrag gestartet, und verwaltet die Zuordnungen des Benutzers oder der Anmeldung zu sicherungsfähigen Objekten ab.

Aus diesem Grund müssen alle externen Skripts, die von einem Remoteclient aus initiiert werden die Anmeldenamen oder Benutzer Informationen als Teil der Verbindungszeichenfolge angeben.

<a name="launchpad"></a>

## <a name="services-used-in-external-processing-launchpad"></a>Dienste, die in externen Verarbeitung (Launchpad) verwendet werden.

Das Extensibility Framework Fügt eine neuen NT-Dienst, um die [Liste mit den Diensten](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md#Service_Details) in einer SQL Server-Installation: [**SQL Server Launchpad (MSSSQLSERVER)** ](extensibility-framework.md#launchpad).

Die Datenbank-Engine verwendet den SQL Server Launchpad-Dienst eine R- oder Python-Sitzung als separater Prozess instanziiert. Der Prozess unter einem Konto mit geringen Rechten ausgeführt wird; unterscheiden Sie SQL Server, Launchpad selbst und die Identität des Benutzers, unter der die gespeicherte Prozedur oder Host-Abfrage ausgeführt wurde. Ausführen von Skripts in einem separaten Prozess, unter dem Konto mit niedrigen Berechtigungen, bildet die Grundlage des Modells, Sicherheit und Isolation für R und Python in SQL Server.

Zusätzlich zum Starten von externer Prozessen, ist die Launchpad auch zuständig für die Überwachung der Identität des aufrufenden Benutzers und das mit geringen rechten workerkonto zum Starten des Prozesses verwendet diese Identität zuordnen. In einigen Szenarien, in denen Skripts oder Codeabschnitts zurück zu SQL Server für die Daten und Vorgänge aufruft, kann Launchpad in der Regel um Identität Übertragung nahtlos zu verwalten. Skripts, die SELECT-Anweisungen enthält oder Aufrufen von Funktionen und andere Programmiersprachen Objekte in der Regel erfolgreich, wenn der aufrufende Benutzer über ausreichende Berechtigungen verfügt.

> [!NOTE]
> In der Standardeinstellung [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] unter Ausführung konfiguriert ist **NT Service\MSSQLLaunchpad**, die mit allen erforderlichen Berechtigungen zum Ausführen externer Skripts bereitgestellt wird. Weitere Informationen zu konfigurierbaren Optionen, finden Sie unter [Konfiguration von SQL Server Launchpad-Diensts](../security/sql-server-launchpad-service-account.md).

<a name="sqlrusergroup"></a>

## <a name="identities-used-in-processing-sqlrusergroup"></a>Identitäten, die zum Verarbeiten (SQLRUserGroup)

**SQLRUserGroup** (SQL-Benutzer mit eingeschränkten Rechten-Gruppe) wird von SQL Server-Setup erstellt und enthält einen Pool von lokalen Windows-Benutzerkonten mit geringen Rechten. Wenn ein externer Prozess benötigt wird, Launchpad verwendet ein verfügbares workerkonto und verwendet es zum ein Prozess ausgeführt werden. Launchpad genauer gesagt: aktiviert ein verfügbares workerkonto, ordnet er die Identität des aufrufenden Benutzers und führt das Skript unter dem workerkonto.

+ **SQLRUserGroup** mit einer bestimmten Instanz verknüpft ist. Ein separater Pool von workerkonten ist für jede Instanz erforderlich, auf dem Machine Learning aktiviert wurde. Konten können nicht zwischen Instanzen freigegeben werden.

+ Die Größe des benutzerkontenpools ist statisch, und der Standardwert ist 20, 20 gleichzeitige Verbindungen unterstützt. Die Anzahl der externen-laufzeitsitzungen, die gleichzeitig gestartet werden kann, wird durch die Größe dieses benutzerkontenpools beschränkt. 

+ Worker-Kontonamen, im Pool weisen das Format SQLInstanceName*Nn*. Z. B. auf einer Standardinstanz **SQLRUserGroup** enthält Konten, die mit dem Namen MSSQLSERVER01, MSSQLSERVER02 usw. auf bis zu MSSQLSERVER20.

Parallelisierte Vorgänge beanspruchen zusätzliche Konten nicht. Wenn ein Benutzer eine Bewertung Aufgabe ausgeführt, die parallelen Verarbeitung verwendet wird, wird z. B. das gleiche workerkonto für alle Threads wiederverwendet. Wenn Sie beabsichtigen, die intensiven Gebrauch von Machine Learning machen, können Sie die Anzahl der Konten, die zum Ausführen externer Skripts erhöhen. Weitere Informationen finden Sie unter [Ändern des benutzerkontenpools für Machine Learning](../../advanced-analytics/administration/modify-user-account-pool.md).

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
### <a name="appcontainer-isolation-in-sql-server-2019"></a>AppContainer-Isolation in SQL Server-2019

In SQL Server-2019, erstellt Setup nicht mehr workerkonten für **SQLRUserGroup**. Isolation erfolgt stattdessen über [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation). Zur Laufzeit, wenn ein externes Skript in einer gespeicherten Prozedur oder Abfrage erkannt wird, ruft der SQL Server Launchpad mit einer Anforderung für ein Startprogramm spezifisch. Launchpad Ruft die entsprechenden Common Language Runtime-Umgebung in einem Prozess unter seiner Identität und instanziiert einen AppContainer enthält. Diese Änderung ist nützlich, da lokale Konto und Kennwort-Verwaltung nicht mehr benötigt wird. Für Installationen, in denen lokale Benutzerkonten gelten, verboten sind, bedeutet auch, Entfernung der Abhängigkeit Konto Lokaler Benutzer, dass Sie jetzt dieses Feature verwenden können.

Gemäß der Implementierung von SQL Server sind AppContainers einen internen Mechanismus. Während Sie physische Beweise des AppContainers im Monitor "Prozess" nicht angezeigt werden, finden Sie sie in Firewallregeln für ausgehenden Datenverkehr von Setup um zu verhindern, dass Prozesse Aufrufe Netzwerk erstellt wurde. Weitere Informationen finden Sie unter [Firewallkonfiguration für SQL Server Machine Learning Services](../../advanced-analytics/security/firewall-configuration.md).

> [!Note]
> In SQL Server-2019 **SQLRUserGroup** hat nur ein Element handelt es sich nun die einzelnen SQL Server Launchpad-Dienstkonto anstelle mehrerer Konten.
::: moniker-end

### <a name="permissions-granted-to-sqlrusergroup"></a>SQLRUserGroup erteilten Berechtigungen

Standardmäßig können Mitglieder der **SQLRUserGroup** über Lese- und Ausführungsberechtigungen für die Dateien in der SQL Server **Binn**, **R_SERVICES**, und **PYTHON_SERVICES** Verzeichnisse mit Zugriff auf ausführbare Dateien, Bibliotheken und integrierten Datasets in R und Python-Distributionen, die mit SQL Server installiert. 

Um vertrauliche Ressourcen auf SQL Server zu schützen, können Sie optional eine Zugriffssteuerungsliste (ACL), die Zugriff auf verweigert definieren **SQLRUserGroup**. Im Gegensatz dazu können Sie auch Berechtigungen für lokale Ressourcen gewähren, die auf dem Hostcomputer, abgesehen von SQL Server selbst vorhanden. 

Programmbedingt **SQLRUserGroup** verfügt nicht über eine Datenbank-Anmeldung oder Berechtigungen für alle Daten. Unter bestimmten Umständen empfiehlt es sich um eine Anmeldung, Loop Back Verbindungen zulassen, insbesondere dann, wenn eine vertrauenswürdige Windows-Identität des aufrufenden Benutzers ist zu erstellen. Diese Funktion wird aufgerufen, [ *implizite Authentifizierung*](#implied-authentication). Weitere Informationen finden Sie unter [Hinzufügen der SQLRUserGroup als Datenbankbenutzer](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md).

## <a name="identity-mapping"></a>Identitätszuordnung

Wenn eine Sitzung gestartet wird, ordnet Launchpad die Identität des aufrufenden Benutzers zu einem workerkonto. Die Zuordnung eines externen Windows-Benutzer oder eine gültige SQL-Anmeldung zu einem workerkonto gilt nur für die Lebensdauer des SQL Prozedur gespeicherten, externe Skript ausführt. Parallele Abfragen von derselben Anmeldung werden demselben Benutzerworkerkonto zugeordnet.

Während der Ausführung erstellt Launchpad temporären Ordner zum Speichern von Daten, löschen, wenn die Sitzung endet. Die Verzeichnisse sind zugreifen. Für R führt "rlauncher" für diese Aufgabe. Für Python führt PythonLauncher diese Aufgabe. Jedes einzelnen workerkonto ist beschränkt, in einem eigenen Ordner und Dateien in Ordnern über eine eigene kann nicht zugegriffen werden kann. Allerdings kann das workerkonto lesen, schreiben oder löschen die untergeordneten Elemente in der Sitzung Arbeitsordner an, der erstellt wurde. Wenn Sie Administrator auf dem Computer sind, können Sie die Verzeichnisse anzeigen, die für jeden Prozess erstellt wurden. Jedes Verzeichnis wird durch die Sitzungs-GUID identifiziert.

<a name="implied-authentication"></a>

## <a name="implied-authentication-loop-back-requests"></a>Implizite Authentifizierung (Loop Back Anforderungen)

*Implizite Authentifizierung* Verbindungsverhalten-Anforderung unter der Schleife externe Prozessen ausgeführt werden, wie Konten mit geringen Rechten in SQL Server auf als eine vertrauenswürdige Benutzeridentität dargestellt werden Back Anforderungen für Daten oder Vorgänge beschreibt. Als Konzept ist die implizite Authentifizierung nur für Windows-Authentifizierung in SQL Server-Verbindungszeichenfolgen, die eine vertrauenswürdige Verbindung mit auf Anforderungen von externen Prozessen, z. B. R oder Python-Skript angeben. Dies wird manchmal auch als bezeichnet ein *Schleife wieder*.

Vertrauenswürdige Verbindungen werden aus R und Python-Skript, jedoch nur durch eine zusätzliche Konfiguration funktionieren. In die erweiterbarkeitsarchitektur, R und Python-Prozesse ausgeführt, unter workerkonten Berechtigungen vom übergeordneten Element erben **SQLRUserGroup**. Wenn eine Verbindungszeichenfolge gibt `Trusted_Connection=True`, die Identität des Kontos Worker wird angezeigt, auf die verbindungsanforderung wird standardmäßig auf SQL Server unbekannt ist.

Um vertrauenswürdige Verbindungen erfolgreich zu machen, müssen Sie erstellen eine datenbankanmeldung für das **SQLRUserGroup**. Nach dem auf diese Weise, die eine vertrauenswürdige Verbindung von einem beliebigen Mitglied der **SQLRUserGroup** Anmelderechte für SQL Server hat. Schrittweise Anweisungen finden Sie unter [SQLRUserGroup hinzufügen, um eine andere datenbankanmeldung](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md).

Vertrauenswürdige Verbindungen sind nicht die am häufigsten verwendeten Formulierung des eine verbindungsanforderung. Wenn R oder Python-Skript eine Verbindung angegeben ist, kann es sein eher üblich, dass eine SQL-Anmeldung, oder vollständig angegebenen Benutzernamen und bestimmtes Kennwort verwenden, wenn die Verbindung mit einer ODBC-Datenquelle ist.

### <a name="how-implied-authentication-works-for-r-and-python-sessions"></a>Wie die implizite Authentifizierung funktioniert für Sitzungen, die R- und Python

Das folgende Diagramm zeigt die Interaktion des SQL Server-Komponenten mit der R-Laufzeit und wie der zwar impliziten Authentifizierung für R.

![Implizite Authentifizierung für R](../security/media/implied-auth-rsql.png)

Im nächste Diagramm zeigt die Interaktion des SQL Server-Komponenten mit der Python-Laufzeit und wie der zwar impliziten Authentifizierung für Python.

![Implizite Authentifizierung für Python](../security/media/implied-auth-python2.png)

## <a name="no-support-for-transparent-data-encryption-at-rest"></a>Keine Unterstützung für die transparente datenverschlüsselung ruhender Daten

[Transparent Data Encryption (TDE)](../../relational-databases/security/encryption/transparent-data-encryption.md) wird für die Daten gesendet oder empfangen wurden aus der externen Skript-Laufzeit nicht unterstützt. Der Grund ist, dass der externe Prozess (R oder Python) außerhalb von SQL Server-Prozess ausgeführt wird. Aus diesem Grund ist Daten, die von der externen Laufzeit verwendet, durch die Verschlüsselungsfunktionen von Datenbank-Engine nicht geschützt. Dieses Verhalten unterscheidet sich nicht als jeder andere Client auf dem SQL Server-Computer, der liest Daten aus der Datenbank und erstellt eine Kopie, ausgeführt wird.

Daher sind TDE **nicht** angewendet werden, um alle Daten, die Sie in R oder Python-Skripts verwenden und auf alle Daten, die auf dem Datenträger oder auf jegliche permanente Zwischenergebnisse gespeichert. Wie z. B. Windows BitLocker-Verschlüsselung oder Drittanbieter-Verschlüsselung auf dem Datei- oder Ordnerebene angewendet gelten jedoch andere Arten von Verschlüsselung, immer noch.

Im Fall von [Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md), externe Laufzeiten, die keinen Zugriff auf die Verschlüsselungsschlüssel. Aus diesem Grund können keine Daten an Skripts gesendet werden.

## <a name="next-steps"></a>Nächste Schritte

In diesem Artikel haben Sie gelernt, die Komponenten und das Interaktionsmodell der Security-Architektur integriert die [Erweiterungsframework](../../advanced-analytics/concepts/extensibility-framework.md). Wichtige Punkte, die in diesem Artikel behandelten enthalten den Zweck des Launchpad "," SQLRUserGroup "und" Worker Konten Prozessisolation von R und Python, und wie Benutzeridentitäten workerkonten zugeordnet werden. 

Als Nächstes überprüfen Sie die Anweisungen für [Erteilen von Berechtigungen](../../advanced-analytics/security/user-permission.md). Bei Servern, die Windows-Authentifizierung verwenden, überprüfen Sie außerdem [SQLRUserGroup hinzufügen, um eine andere datenbankanmeldung](../../advanced-analytics/security/create-a-login-for-sqlrusergroup.md) , erfahren, wenn die weitere Konfiguration erforderlich ist.