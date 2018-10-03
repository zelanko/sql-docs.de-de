---
title: Häufig gestellte Fragen (FAQ) zum JDBC-Treiber | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cbc0e397-ecf2-4494-87b2-a492609bceae
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2f0197ed97f8d03784cd89d2bede5a4e7744e80f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613418"
---
# <a name="frequently-asked-questions-faq-for-jdbc-driver"></a>Häufig gestellte Fragen (FAQ) zum JDBC-Treiber

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Dieser Artikel enthält Antworten auf häufig gestellte Fragen zum Microsoft JDBC-Treiber für SQL Server.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

**Wie kann ich helfen, den JDBC-Treiber zu verbessern?**  
Der JDBC-Treiber ist Open Source- und der Quellcode finden Sie auf [GitHub](https://github.com/microsoft/mssql-jdbc). Sie können den Treiber zu verbessern, indem Sie mögliche Probleme und die Mitwirkung an der Codebasis.

**Welche Versionen von SQL Server und Java werden vom Treiber unterstützt?**  
Detaillierte Informationen hierzu finden Sie auf der Seite [Supportmatrix für den Microsoft JDBC-Treiber für SQL Server](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md).

**Was ist der Unterschied zwischen der JDBC-Treiberpakete, die auf dem Microsoft Download Center verfügbar und JDBC-Treiber auf GitHub verfügbar?**  
JDBC-Treiber auf das GitHub-Repository für die verfügbaren Dateien des Microsoft JDBC-Treibers sind der Kern des JDBC-Treibers und unter der Open-Source-Lizenz, die im Repository aufgeführt sind. Die Treiberpakete aus, auf dem Microsoft Download Center enthalten zusätzliche Bibliotheken für die integrierte Windows-Authentifizierung und XA-Transaktionen mit dem JDBC-Treiber zu aktivieren. Diese zusätzliche Bibliotheken sind unter der Lizenz, die im herunterladbaren Paket.

**Was sollte ich wissen, bevor ich meinen Treiber aktualisiere?**  
 Der Microsoft JDBC-Treiber-7.0 unterstützt der JDBC 4.2 und 4.3 (teilweise)-Spezifikationen und enthält zwei JAR-Klassenbibliotheken in das Installationspaket für das wie folgt:

| JAR                        | JDBC-Spezifikation            | JDK-Version |
| -------------------------- | ----------------------------- | ----------- |
| mssql-jdbc-7.0.0.jre10.jar | JDBC 4.3 (teilweise) und 4.2 | JDK 10.0    |
| mssql-jdbc-7.0.0.jre8.jar  | JDBC 4.2                      | JDK 8.0     |

Der Microsoft JDBC-Treiber 6.4 unterstützt der JDBC 4.1, 4.2 und 4.3 (teilweise)-Spezifikationen und enthält drei JAR-Klassenbibliotheken in das Installationspaket für das wie folgt:

| JAR                       | JDBC-Spezifikation                 | JDK-Version |
| ------------------------- | ---------------------------------- | ----------- |
| mssql-jdbc-6.4.0.jre9.jar | JDBC 4.3 (teilweise), 4.2 und 4.1 | JDK 9.0     |
| mssql-jdbc-6.4.0.jre8.jar | JDBC 4.2 und 4.1                  | JDK 8.0     |
| mssql-jdbc-6.4.0.jre7.jar | JDBC 4.1                           | JDK 7.0     |

Der Microsoft JDBC-Treiber 6.2 unterstützt die JDBC 4.0, 4.1 und 4.2-Spezifikationen und enthält zwei JAR-Klassenbibliotheken in das Installationspaket für das wie folgt:

| JAR                       | JDBC-Spezifikation     | JDK-Version |
| ------------------------- | ---------------------- | ----------- |
| MSSQL-Jdbc-6.2.2.jre8.jar | JDBC 4.2, 4.1 und 4.0 | JDK 8.0     |
| MSSQL-Jdbc-6.2.2.jre7.jar | JDBC 4.1 und 4.0       | JDK 7.0     |

Der Microsoft JDBC-Treiber 6.0 4.2 für SQL Server unterstützt die JDBC 4.0, 4.1 und 4.2-Spezifikationen und enthalten zwei JAR-Klassenbibliotheken in das Installationspaket für das wie folgt:

| JAR           | JDBC-Spezifikation     | JDK-Version |
| ------------- | ---------------------- | ----------- |
| sqljdbc42.jar | JDBC 4.2, 4.1 und 4.0 | JDK 8.0     |
| sqljdbc41.jar | JDBC 4.1 und 4.0       | JDK 7.0     |

Der Microsoft JDBC-Treiber 4.1 für SQL Server unterstützt die JDBC 4.0-Spezifikation und enthält ein Class-Bibliothek von JAR-Datei in das Installationspaket für das wie folgt:

| JAR           | JDBC-Spezifikation | JDK-Version     |
| ------------- | ------------------ | --------------- |
| sqljdbc41.jar | JDBC 4.0           | JDK 7.0 und 6.0 |

**Muss ich Änderungen am Code meiner Anwendung vornehmen, um den neuesten Treiber mit meiner bestehenden Version von SQL Server verwenden zu können?**  
In der Regel wird der Treiber abwärtskompatibel entworfen, sodass Sie Ihre vorhandenen Anwendungen bei einem Treiberupgrade nicht anpassen müssen. Wenn eine neue Treiberversion eine bedeutende Änderung führt die [Anmerkungen zu dieser Version für den JDBC-Treiber](../../connect/jdbc/release-notes-for-the-jdbc-driver.md) Abschnitt enthält detaillierte Informationen zu dieser Änderung und die Auswirkungen auf vorhandene Anwendungen. Darüber hinaus finden Sie in den Versionsanmerkungen des Treibers eine Liste bekannter Probleme und der in diesem Release behobenen Fehler.

**Wie viel kostet der Treiber?**  
Der Microsoft JDBC-Treiber für SQL steht Ihnen kostenlos zur Verfügung.

**Kann ich den Treiber weiterverteilen?**
Die JDBC-Treiber 4.1, 4.2, 6.0, 6.2, 6.4 und 7.0 sind weiterverteilbar. Überprüfen Sie die Klausel "Verteilbarer Code" in der Lizenzverträge.

**Kann ich mithilfe des Treibers von einem Linux-Computer aus auf Microsoft SQL Server zugreifen?**
Ja! Sie können den Treiber verwenden, um von Linux, Unix und anderen nicht-Windows-Plattformen auf SQL Server zuzugreifen. Weitere Informationen finden Sie unter [Microsoft JDBC-Treiber für SQL Server-Support-Matrix](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md).

**Unterstützt der Treiber die SSL-Verschlüsselung (Secure Sockets Layer)?**
Die SSL-Verschlüsselung wird seit Version 1.2 des Treibers unterstützt. Weitere Informationen finden Sie unter [Verwenden der SSL-Verschlüsselung](../../connect/jdbc/using-ssl-encryption.md).

**Welche Authentifizierungstypen werden vom Microsoft JDBC-Treiber für SQL Server unterstützt?**  
Die verfügbaren Authentifizierungsoptionen sind in der folgenden Tabelle aufgelistet. Eine reine Java Kerberos-Authentifizierung ist seit Version 4.0 des Treibers verfügbar.

|             |                                       |
| ----------- | ------------------------------------- |
| Platform    | Authentifizierung                        |
| Nicht-Windows-System | Reine Java Kerberos                    |
| Nicht-Windows-System | SQL Server                            |
| Nicht-Windows-System | Azure Active Directory-Authentifizierung |
| Windows     | Reine Java Kerberos                    |
| Windows     | SQL Server                            |
| Windows     | Kerberos mit NTLM als Backup             |
| Windows     | NTLM                                  |
| Windows     | Azure Active Directory-Authentifizierung |

**Unterstützt der Treiber IPv6-Internetadressen (Internetprotokoll, Version 6)?**  
Ja. Der Treiber unterstützt die Verwendung von IPv6-Adressen. Verwenden Sie die Verbindungseigenschaften und die Verbindungszeichenfolgen ServerName-Eigenschaft. Weitere Informationen finden Sie unter [Erstellen der Verbindungs-URL](../../connect/jdbc/building-the-connection-url.md).

**Was ist die adaptive Pufferung?**  
Die Adaptive Pufferung wurde erstmals in Microsoft SQL Server 2005 JDBC Driver, Version 1.2. Mit der adaptiven Pufferung können Daten mit einer großen Menge an Werten ohne den durch Servercursor verursachten Overhead abgerufen werden. Die adaptive Pufferung des Microsoft SQL Server JDBC Drivers stellt mit „responseBuffering“ eine Eigenschaft für Verbindungszeichenfolgen bereit, die auf „adaptive“ oder „full“ festgelegt werden kann. In Version 1.2 lautet der Puffermodus standardmäßig „full“, und die Anwendung muss den Modus für die adaptive Pufferung explizit festlegen. Ab Version 2.0 des JDBC-Treibers ist das Standardverhalten des Treibers „adaptive“. Daher muss Ihre Anwendung das adaptive Verhalten nicht explizit anfordern, um ein adaptives Pufferverhalten zu erzielen. Weitere Informationen finden Sie unter [Verwenden der adaptiven Pufferung](../../connect/jdbc/using-adaptive-buffering.md) und im Blogartikel [What is adaptive response buffering and why should I use it?](http://go.microsoft.com/fwlink/?LinkId=111575) (Was ist die adaptive Antwortpufferung und warum sollte ich sie verwenden?).

**Unterstützt der Treiber das Verbindungspooling?**  
Der Treiber unterstützt das Verbindungspooling unter Java Platform, Enterprise Edition 5 (Java EE 5). Der Treiber implementiert die erforderlichen JDBC 3.0-Schnittstellen, damit er implementiertes Verbindungspooling von Anbietern für Anwendungsserver auf Middleware-Ebene nutzen kann. Der Treiber nutzt in diesen Umgebungen Verbindungspool. Weitere Informationen finden Sie unter [Verwenden des Verbindungspoolings](../../connect/jdbc/using-connection-pooling.md). Der Treiber bietet keine eigene Implementierung des Poolings, sondern es beruht auf Java-Anwendungsservern von Drittanbietern.

**Steht für den Treiber Support zur Verfügung?**  
Es sind zahlreiche Optionen verfügbar. Sie können Ihre Frage oder ausgeben, um unsere [GitHub-Repository](https://github.com/microsoft/mssql-jdbc) die von Microsoft überwacht wird. [Foren](http://go.microsoft.com/fwlink/?LinkID=246673) werden von Microsoft, MVPs und der Community überwacht. Sie können sich auch an den Microsoft Kundendienst wenden. Das Entwicklungsteam bittet Sie möglicherweise, das Problem außerhalb von Anwendungsservern von Drittanbietern zu reproduzieren. Wenn das Problem nicht außerhalb der Hostumgebung des Java-Containers reproduziert werden kann, müssen Sie den Drittanbieter hinzuziehen, damit das Team Ihnen weiterhin helfen kann. Das Team kann auch zu, bitten Sie, Ihr Problem auf einem Betriebssystem wie Windows zu reproduzieren, sodass das Problem am besten unterstützt werden kann.

**Ist der Treiber für die Verwendung mit Anwendungsservern von Drittanbietern zertifiziert?**
Der Treiber wurde mit allen wichtigen Anwendungsserver getestet, wie z. B. IBM WebSphere und SAP NetWeaver.

**Wie aktiviere ich die Ablaufverfolgung?**  
Der Treiber unterstützt die Verwendung der Ablaufverfolgung (oder Protokollierung). Dies hilft Probleme zu lösen, die bei der Verwendung des JDBC-Treibers in Ihrer Anwendung auftreten können. Der JDBC-Treiber verwendet die Logging-API in java.util.logging, um die clientseitige JAR-Ablaufverfolgung zu aktivieren. Weitere Informationen finden Sie unter [Tracing Driver Operation (Ablaufverfolgung für Treibervorgänge)](../../connect/jdbc/tracing-driver-operation.md). Weitere Informationen zur serverseitigen XA-Ablaufverfolgung finden Sie unter [Verfolgung des Datenzugriffs in SQL Server](http://go.microsoft.com/fwlink/?LinkId=248705).

**Wo kann ich ältere Versionen des Treibers herunterladen, z.B. den JDBC-Treiber für SQL Server 2000, den 2005-Treiber oder Treiber für 1.0, 1.1 oder 1.2?**  
Diese Treiberversionen stehen nicht zum Download zur Verfügung, da sie nicht mehr unterstützt werden. Wir arbeiten laufend daran, die Unterstützung der Java-Konnektivität zu verbessern. Daher raten wir dringend zur Verwendung der neuesten Version des Microsoft JDBC-Treibers.

**Ich verwende JRE 1.4. Welcher Treiber ist mit JRE 1.4 kompatibel?**  
Kunden, die SAP-Produkte verwenden und die Unterstützung für JRE 14. benötigen, können [SAP Service Marketplace](http://service.sap.com/) um den Microsoft JDBC-Treiber 1.2 zu erhalten.

**Kann der Treiber mit durch FIPS validierten Algorithmen kommunizieren?**  
Der Microsoft JDBC-Treiber enthält keine kryptografischen Algorithmen. Wenn ein Kunde Algorithmen für Betriebssysteme, Anwendungen und JVM verwendet, die entsprechend der Federal Information Processing Standards (FIPS) zulässig sind, und der Kunde den Treiber für die Verwendung dieser Algorithmen konfiguriert, dann verwendet der Treiber nur die festgelegten Algorithmen für die Kommunikation.

## <a name="see-also"></a>Weitere Informationen finden Sie unter

[Overview of the JDBC Driver (Übersicht über den JDBC-Treiber)](../../connect/jdbc/overview-of-the-jdbc-driver.md)
