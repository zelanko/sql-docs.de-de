---
title: Sicherheit für SQL Server-Machine Learning | Microsoft-Dokumentation
description: Übersicht über die Sicherheit für das Extensibility Framework in SQL Server-Machine Learning-Dienste. Sicherheit für die Anmeldung und Benutzerkonten, SQL Server Launchpad-Dienst, workerkonten, die mehrere Skripts und Dateiberechtigungen ausgeführt.
ms.prod: sql
ms.technology: machine-learning
ms.date: 10/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: bee8e2162c56ac1b26273873943d848c2167dbda
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100401"
---
# <a name="security-overview-for-the-extensibility-framework-in-sql-server-machine-learning-services"></a>Übersicht über die Sicherheit für das Extensibility Framework in SQL Server Machine Learning Services

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dieser Artikel beschreibt die Sicherheitsarchitektur, die Verbindung von der SQL Server-Datenbank-Engine und die zugehörigen Komponenten mit dem Extensibility Framework verwendet wird. Komponenten und Interaktionen beschrieben. 

<a name="launchpad"></a>

## <a name="sql-server-launchpad-service"></a>SQL Server Launchpad-Dienst

Um externe Prozesse zu instanziieren, enthält die Datenbank-Engine den SQL Server Launchpad-Dienst zum Erstellen einer Sitzung R- oder Python. Eine Separate [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] Dienst erstellt und für die Datenbank-Engine-Instanz, die zu dem Sie SQL Server Machine learning (R oder Python)-Integration, ein Dienst pro Instanz hinzugefügt haben.

In der Standardeinstellung [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] unter Ausführung konfiguriert ist **NT Service\MSSQLLaunchpad**, die mit allen erforderlichen Berechtigungen zum Ausführen externer Skripts bereitgestellt wird. Entfernen von Berechtigungen, die dieses Konto kann dazu führen, [!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)] Fehler bei der starten oder SQL Server-Instanz für den Zugriff auf dem externer Skripts ausgeführt werden soll. Launchpad-Dienst ist im Allgemeinen als verwendet – ist, aber die Weitere Informationen zu konfigurierbaren Optionen, finden Sie unter [Konfiguration von SQL Server Launchpad-Diensts](../security/sql-server-launchpad-service-account.md).

<a name="sqlrusergroup"></a>

## <a name="sqlrusergroup-and-worker-accounts"></a>SQLRUserGroup und Worker-Konten

Externe Skripts auszuführen, in externen Prozessen, unter der Identität des Least-Priviledged lokalen workerkonten, unterliegt die Zugriffssteuerungsliste (ACL) des übergeordneten Elements **SQLRUserGroup** (SQL-Benutzer mit eingeschränkten Rechten-Gruppe). 

**SQLRUserGroup** vom SQL Server-Setup erstellt wird, und der Pool von lokalen Windows-Benutzerkonten enthält. Wenn ein externer Prozess benötigt wird, Launchpad verwendet ein verfügbares workerkonto und verwendet es zum ein Prozess ausgeführt werden. Launchpad genauer gesagt: aktiviert ein verfügbares workerkonto, ordnet er die Identität des aufrufenden Benutzers und führt das Skript unter dem workerkonto. 

+ **SQLRUserGroup** mit einer bestimmten Instanz verknüpft ist. Ein separater Pool von workerkonten ist für jede Instanz erforderlich, auf dem Machine Learning aktiviert wurde. Konten können nicht zwischen Instanzen freigegeben werden.

+ Die Größe des benutzerkontenpools ist statisch, und der Standardwert ist 20, 20 gleichzeitige Verbindungen unterstützt. Die Anzahl der externen-laufzeitsitzungen, die gleichzeitig gestartet werden kann, wird durch die Größe dieses benutzerkontenpools beschränkt. 

+ Worker-Kontonamen, im Pool weisen das Format SQLInstanceName*Nn*. Z. B. auf einer Standardinstanz **SQLRUserGroup** enthält Konten, die mit dem Namen MSSQLSERVER01, MSSQLSERVER02 usw. auf bis zu MSSQLSERVER20.

Parallelisierte Vorgänge beanspruchen zusätzliche Konten nicht. Wenn ein Benutzer eine Bewertung Aufgabe ausgeführt, die parallelen Verarbeitung verwendet wird, wird z. B. das gleiche workerkonto für alle Threads wiederverwendet. Wenn Sie beabsichtigen, die intensiven Gebrauch von Machine Learning machen, können Sie die Anzahl der Konten, die zum Ausführen externer Skripts erhöhen. Weitere Informationen finden Sie unter [Ändern des benutzerkontenpools für Machine Learning](../../advanced-analytics/administration/modify-user-account-pool.md).

### <a name="permissions-granted-to-sqlrusergroup"></a>SQLRUserGroup erteilten Berechtigungen

Standardmäßig können Mitglieder der **SQLRUserGroup** über Lese- und Ausführungsberechtigungen für die Dateien in der SQL Server **Binn**, **R_SERVICES**, und **PYTHON_SERVICES** Verzeichnisse mit Zugriff auf ausführbare Dateien, Bibliotheken und integrierten Datasets in R und Python-Distributionen, die mit SQL Server installiert. 

Um vertrauliche Ressourcen auf SQL Server zu schützen, können Sie optional eine Zugriffssteuerungsliste (ACL), die Zugriff auf verweigert definieren **SQLRUserGroup**. Im Gegensatz dazu können Sie auch Berechtigungen für lokale Ressourcen gewähren, die auf dem Hostcomputer, abgesehen von SQL Server selbst vorhanden. 

Programmbedingt **SQLRUserGroup** verfügt nicht über eine Datenbank-Anmeldung oder Berechtigungen für alle Daten. Unter bestimmten Umständen empfiehlt es sich um eine Anmeldung, Loop Back Verbindungen zulassen, insbesondere dann, wenn eine vertrauenswürdige Windows-Identität des aufrufenden Benutzers ist zu erstellen. Diese Funktion wird aufgerufen, [ *implizite Authentifizierung*](#implied-authentication). Weitere Informationen finden Sie unter [Hinzufügen der SQLRUserGroup als Datenbankbenutzer](../../advanced-analytics/security/add-sqlrusergroup-to-database.md).

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"
### <a name="appcontainer-isolation-in-sql-server-2019"></a>AppContainer-Isolation in SQL Server-2019

In SQL Server-2019, erstellt Setup nicht mehr workerkonten für **SQLRUserGroup**. Isolation erfolgt stattdessen über [AppContainers](https://docs.microsoft.com/windows/desktop/secauthz/appcontainer-isolation). Zur Laufzeit bei eingebetteten Skripts oder Code in einer gespeicherten Prozedur oder Abfrage erkannt wird, ruft der SQL Server Launchpad mit einer Anforderung für ein Startprogramm spezifisch. Launchpad Ruft die entsprechenden Common Language Runtime-Umgebung in einem Prozess unter seiner Identität und instanziiert einen AppContainer enthält. Diese Änderung ist nützlich, da lokale Konto und Kennwort-Verwaltung nicht mehr benötigt wird. Für Installationen, in denen lokale Benutzerkonten gelten, verboten sind, bedeutet auch, Entfernung der Abhängigkeit Konto Lokaler Benutzer, dass Sie jetzt dieses Feature verwenden können.

Gemäß der Implementierung von SQL Server sind AppContainers einen internen Mechanismus. Während Sie physische Beweise des AppContainers im Monitor "Prozess" nicht angezeigt werden, finden Sie sie in Firewallregeln für ausgehenden Datenverkehr von Setup um zu verhindern, dass Prozesse Aufrufe Netzwerk erstellt wurde.

> [!Note]
> In SQL Server-2019 **SQLRUserGroup** hat nur ein Element handelt es sich nun die einzelnen SQL Server Launchpad-Dienstkonto anstelle mehrerer Konten.
::: moniker-end

## <a name="user-security"></a>Benutzersicherheit

SQL Server Daten-Sicherheitsmodell von Datenbank-Anmeldenamen und Rollen an R und Python-Skript erweitern. Datenbank-Anmeldenamen können auf Windows-Identitäten oder der Benutzer einer SQL Server-Datenbank basieren. 

Als Datenbankbenutzer Wenn Sie Berechtigungen zum Ausführen einer bestimmten Abfrage, hat jedem R oder Python-Skript, das Ausführen auf SQL Server auch über die Berechtigung zum Abrufen derselben Daten. Die Möglichkeit zu nutzen, erstellen und Speichern der Datenbank-Objekten hängt von Berechtigungen für die Datenbank. Weitere Informationen finden Sie unter [Vergabe von Benutzerberechtigungen für SQL Server Machine Learning Services](../../advanced-analytics/security/user-permission.md).

### <a name="mapping-user-identities-to-worker-accounts"></a>Zuordnen von Benutzeridentitäten zu workerkonten

Wenn eine Sitzung gestartet wird, ordnet Launchpad die Identität des aufrufenden Benutzers zu einem workerkonto. Die Zuordnung eines externen Windows-Benutzer oder eine gültige SQL-Anmeldung zu einem workerkonto gilt nur für die Lebensdauer des SQL Prozedur gespeicherten, externe Skript ausführt. Parallele Abfragen von derselben Anmeldung werden demselben Benutzerworkerkonto zugeordnet.

Während der Ausführung erstellt Launchpad temporären Ordner zum Speichern von Daten, löschen, wenn die Sitzung endet. Die Verzeichnisse sind zugreifen. Für R führt "rlauncher" für diese Aufgabe. Für Python führt PythonLauncher diese Aufgabe. Jedes einzelnen workerkonto ist beschränkt, in einem eigenen Ordner und Dateien in Ordnern über eine eigene kann nicht zugegriffen werden kann. Allerdings kann das workerkonto lesen, schreiben oder löschen die untergeordneten Elemente in der Sitzung Arbeitsordner an, der erstellt wurde. Wenn Sie Administrator auf dem Computer sind, können Sie die Verzeichnisse anzeigen, die für jeden Prozess erstellt wurden. Jedes Verzeichnis wird durch die Sitzungs-GUID identifiziert.

<a name="implied-authentication"></a>

### <a name="implied-authentication"></a>Implizite Authentifizierung

*Implizite Authentifizierung* Verbindungsverhalten-Anforderung unter der Schleife externe Prozessen ausgeführt werden, wie Konten mit geringen Rechten in SQL Server auf als eine vertrauenswürdige Benutzeridentität dargestellt werden Back Anforderungen für Daten oder Vorgänge beschreibt. Als Konzept ist die implizite Authentifizierung nur für Windows-Authentifizierung in SQL Server-Verbindungszeichenfolgen, die eine vertrauenswürdige Verbindung mit auf Anforderungen von externen Prozessen, z. B. R oder Python-Skript angeben. Dies wird manchmal auch als bezeichnet ein *Schleife wieder*.

Vertrauenswürdige Verbindungen werden aus R und Python-Skript, jedoch nur durch eine zusätzliche Konfiguration funktionieren. In die erweiterbarkeitsarchitektur, R und Python-Prozesse ausgeführt, unter workerkonten Berechtigungen vom übergeordneten Element erben **SQLRUserGroup**. Wenn eine Verbindungszeichenfolge gibt "Trusted_Connection = True", die Identität des Kontos Worker wird angezeigt, auf die verbindungsanforderung wird standardmäßig auf SQL Server unbekannt ist. 

Um vertrauenswürdige Verbindungen erfolgreich zu machen, müssen Sie erstellen eine datenbankanmeldung für das **SQLRUserGroup**. Nach dem auf diese Weise, die eine vertrauenswürdige Verbindung von einem beliebigen Mitglied der **SQLRUserGroup** Anmelderechte für SQL Server hat. Schrittweise Anweisungen finden Sie unter [SQLRUserGroup hinzufügen, um eine andere datenbankanmeldung](../../advanced-analytics/security/add-sqlrusergroup-to-database.md).

Vertrauenswürdige Verbindungen sind nicht die am häufigsten verwendeten Formulierung des eine verbindungsanforderung. Wenn R oder Python-Skript eine Verbindung angegeben ist, kann es sein eher üblich, dass eine SQL-Anmeldung, oder vollständig angegebenen Benutzernamen und bestimmtes Kennwort verwenden, wenn die Verbindung mit einer ODBC-Datenquelle ist.

#### <a name="how-implied-authentication-works-for-r-and-python-sessions"></a>Wie die implizite Authentifizierung funktioniert für Sitzungen, die R- und Python

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

Als Nächstes überprüfen Sie die Anweisungen für [Erteilen von Berechtigungen](../../advanced-analytics/security/user-permission.md). Bei Servern, die Windows-Authentifizierung verwenden, überprüfen Sie außerdem [SQLRUserGroup hinzufügen, um eine andere datenbankanmeldung](../../advanced-analytics/security/add-sqlrusergroup-to-database.md) , erfahren, wenn die weitere Konfiguration erforderlich ist.