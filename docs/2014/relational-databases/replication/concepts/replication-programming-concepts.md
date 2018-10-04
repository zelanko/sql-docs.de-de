---
title: Konzepte für die Replikationsprogrammierung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- replication
ms.topic: reference
helpviewer_keywords:
- replication [SQL Server], planning
- programming [SQL Server replication], planning
- programming [SQL Server replication]
ms.assetid: 2cd846e7-5bf3-4144-8772-703c4f439a2a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 11ea6b99818a1f1ffaf4b38019a234aa54294d2a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48186930"
---
# <a name="replication-programming-concepts"></a>Konzepte für die Replikationsprogrammierung
  Vor dem Entwickeln einer Anwendung, die Replikationsfunktionen verwendet, führen Sie die folgenden allgemeinen Planungsschritte aus:  
  
1.  Definieren Sie die Replikationstopologie.  
  
2.  Definieren Sie die Anwendungsfunktionen.  
  
3.  Erstellen Sie einen Sicherheitsplan.  
  
4.  Wählen Sie eine Entwicklungsumgebung.  
  
5.  Wählen Sie die geeignete Programmierschnittstelle für die Replikation.  
  
 Im restlichen Teil dieses Themas werden diese Schritte ausführlicher beschrieben. Der Planungsprozess wird an einem Beispiel veranschaulicht.  
  
## <a name="defining-the-replication-topology"></a>Definieren der Replikationstopologie  
 Der erste Schritt bei der Programmierung der Replikation besteht darin, die Replikationstopologie für die Anwendung zu definieren. Wenn Sie eine Anwendung schreiben, die eine vorhandene Replikationstopologie verwendet, z. B eine Clientanwendung, die auf Daten eines vorhandenen Abonnenten zugreift, fahren Sie mit dem nächsten Schritt fort.  
  
> [!NOTE]  
>  In einigen Fällen besteht der einzige Zweck der Anwendung in der Bereitstellung der Replikationstopologie.  
  
 Die Definition der Replikationstopologie hängt von vielen Faktoren ab. Dazu gehören:  
  
-   Ob replizierte Daten aktualisiert werden müssen und von wem.  
  
-   Die Datenverteilungsanforderungen an Konsistenz, Autonomie und Latenzzeit.  
  
-   Die Replikationsumgebung, einschließlich Geschäftsbenutzer, technischer Infrastruktur, Netzwerk und Sicherheit sowie Dateneigenschaften.  
  
-   Die Replikationstypen und Replikationsoptionen.  
  
-   Die Replikationstopologien und ihre Ausrichtung auf die Replikationstypen.  
  
 Wenn [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Replikation neu für Sie ist, finden Sie unter [Replikationstypen](../types-of-replication.md) weitere Informationen.  
  
## <a name="defining-application-functionality"></a>Definieren der Anwendungsfunktionen  
 Nachdem Sie die Replikationstopologie definiert haben, bestimmen Sie die Funktionen, die die Anwendung bieten soll. Diese Funktionen können von einem Skript zur Synchronisierung eines Abonnements über eine Anwendung mit einer Benutzerschnittstelle bis hin zur Konfiguration der Replikation reichen. Die Replikation unterstützt die folgenden allgemeinen Programmierungstasks:  
  
-   Einrichten der Replikation  
  
-   Synchronisieren von Abonnenten  
  
-   Warten einer Replikationstopologie  
  
-   Überwachen einer Replikationstopologie.  
  
-   Behandlung von Problemen mit der Replikation  
  
 Üblicherweise wird die Anwendung außerdem durch Kombinieren von Replikationsfunktionen mit anderen von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] bereitgestellten Funktionen erweitert. In der folgenden Tabelle werden einige erweiterte Funktionen hervorgehoben, die Sie in der Replikationsanwendung bereitstellen können.  
  
|Funktionalität|Beispiel|  
|-------------------|-------------|  
|Serververwaltung mit [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO)|Eine Anwendung, mit der ein Administrator eine Datenbank anhängen und als Verleger in einer Replikationstopologie konfigurieren kann.|  
|Datenzugriff mit ADO.NET|Eine Anwendung, mit der Benutzer programmgesteuert auf replizierte Verkaufsdaten in einer lokalen Abonnentendatenbank im Offlinemodus zugreifen und diese ändern können. Anschließend kann eine Verbindung hergestellt und das Pullabonnement per Mausklick synchronisiert werden.|  
  
## <a name="planning-for-security"></a>Erstellen eines Sicherheitsplans  
 Sicherheit ist in jeder Anwendung wichtig. Daher sollte ein Sicherheitsplan vor dem Schreiben von Code erstellt werden. Die Anwendungssicherheit kann in drei Hauptbestandteile unterteilt werden: Sichern der Datenbank, Sichern der Replikation und Schreiben von sicherem Code.  
  
 Die folgenden Themen stellen weitere Informationen über die Sicherheit bereit:  
  
-   [Sicherheit und Schutz &#40;Replikation&#41;](../security/security-and-protection-replication.md)  
  
-   [Sicherheitscenter für SQL Server-Datenbank-Engine und Azure SQL-Datenbank](../../security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
  
## <a name="choosing-a-development-environment"></a>Wählen einer Entwicklungsumgebung  
 Beim Entwickeln einer Replikationsanwendung kommen drei grundlegende Entwicklungsumgebungen in Betracht. Jede Entwicklungsumgebung hat Zugriff auf die gleichen Replikationsfunktionen. Dabei gibt es jedoch einige Ausnahmen. Replikationsanwendungen können in jeder der folgenden Umgebungen entwickelt werden.  
  
-   **Verwalteter Code**  
  
     Hierbei handelt es sich um eine objektorientierte Entwicklungsumgebung, die die Vorteile der [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]-Programmierung und der .NET Common Language Runtime (CLR) nutzt. Verwalteter Code wird als Programmierumgebung sowohl für .NET-Entwicklungs- als auch für [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anwendungen empfohlen. Verwaltete Replikationsschnittstellen ermöglichen die Programmierung der Replikationsverwaltung auf objektorientierte Weise, ohne dass [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Kenntnisse erforderlich sind. Außerdem bieten sie einige Rückruffunktionen beim Ausführen von Replikations-Agents, die nicht über Skripts verfügbar sind. Verwalteter Code ist die beste Umgebung zum Entwickeln von wiederverwendbaren Komponenten und Benutzeroberflächenanwendungen.  
  
-   **Skripterstellung**  
  
     Hierbei handelt es sich um einfache Anwendungen, die eine Reihe von Befehlen entweder als gespeicherte Systemprozeduren für die Replikation in [!INCLUDE[tsql](../../../includes/tsql-md.md)]-Skripts oder als Befehle in Batchdateien ausführen. Sie können einerseits Skripts in einer verwalteten Umgebung mit dem in Bearbeitung befindlichen verwalteten [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-Anbieter ausführen. Andererseits lässt sich die gleiche Funktionalität aber auch mit verwalteten Replikationsschnittstellen erzielen, die darüber hinaus Rückruffunktionen zur Verfügung stellen. Die Skripterstellung stellt die beste Umgebung zum Ausführen von Tasks dar, die nur einige Male ausgeführt werden und die keine Rückruffunktionen erfordern, z. B. das Installieren eines Replikationsservers.  
  
-   **Nativer Code**  
  
     Hierbei handelt es sich um eine objektorientierte Entwicklungsumgebung, die direkten Zugriff auf das System oder COM-Objekte so nutzt, dass Code nicht von der CLR verwaltet wird. Systemeigene Codereplikationsschnittstellen sind veraltet oder werden nicht mehr unterstützt. Weitere Informationen finden Sie unter [Als veraltet markierte Funktionen in SQL Server-Replikation](../deprecated-features-in-sql-server-replication.md) oder [Abwärtskompatibilität von Replikationen](../replication-backward-compatibility.md).  
  
## <a name="choose-the-appropriate-replication-programming-interface"></a>Auswählen der geeigneten Programmierschnittstelle für die Replikation  
 Der letzte Planungsschritt besteht darin, die geeignete Programmierschnittstelle für die Replikation auszuwählen, die die gewünschten Replikationsfunktionen für die ausgewählte Entwicklungsumgebung implementiert. In der folgenden Tabelle sind die verfügbaren Programmierschnittstellen für die Replikation aufgeführt.  
  
|Schnittstelle|Umgebung|Verwendungszweck|  
|---------------|-----------------|----------|  
|[Replication Management Objects Concepts](replication-management-objects-concepts.md)|Verwalteter Code|Verwaltung, Überwachung und Synchronisierung|  
|<xref:Microsoft.SqlServer.Replication>|Verwalteter Code|Synchronisierung|  
|<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|Verwalteter Code|Erstellen von Geschäftslogikhandlern, um benutzerdefinierte Logik in den Mergesynchronisierungsvorgang zu integrieren|  
|[Gespeicherte Automatisierungsprozeduren &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql)|Skripterstellung|Administration und Überwachung.|  
|[Ausführbare Konzepte für die Programmierung von Replikations-Agent](replication-agent-executables-concepts.md)|Skripterstellung|Synchronisierung|  
  
## <a name="example"></a>Beispiel  
 Unter [!INCLUDE[ssSampleDBCoShort](../../../includes/sssampledbcoshort-md.md)] müssen Daten für 200 Vertriebsmitarbeiter weltweit veröffentlicht werden. Die Vertriebsmitarbeiter sind viel im Außendienst unterwegs und müssen Laptops oder PDAs (Personal Digital Assistants) verwenden, um Kundendaten zu ändern und neue Bestellungen hinzuzufügen. Die Änderungen müssen anschließend mit dem Verleger synchronisiert werden, wenn die Vertriebsmitarbeiter über den Laptop eine Verbindung mit dem Netzwerk herstellen.  
  
 Für diese Anwendung könnten die Planungsschritte wie folgt aussehen:  
  
1.  Die Replikationstopologie für diese Anwendung ist bereits vorhanden. Es muss jedoch ein neues Pullabonnement clientseitig erstellt werden. Die Veröffentlichung sollte parametrisierte Filter verwenden, um für jeden Vertriebsmitarbeiter einen eindeutigen Satz Daten zu replizieren.  
  
2.  Zusätzlich zu dem regulären Datenzugriff, der für eine Vertriebsanwendung erforderlich ist, sollte diese Anwendung einen Vertriebsmitarbeiter in die Lage versetzen, das Pullabonnement bei Bedarf per Mausklick zu synchronisieren. Da die Anwendung von einem Vertriebsmitarbeiter installiert und ausgeführt wird, muss sie außerdem die Möglichkeit bieten, ein Abonnement zu konfigurieren und die Anfangsmomentaufnahme clientseitig zu übernehmen. Die Anwendung verwendet wahlweise die unter Windows zur Verfügung gestellte Infrastruktur zur Erkennung von Funkverbindungen, um das Abonnement automatisch zu synchronisieren, sobald eine Verbindung erkannt wird.  
  
3.  Beachten Sie alle Sicherheitsrichtlinien für die Replikation, einschließlich der Verwendung der Windows-Authentifizierung und eines virtuellen privaten Netzwerks (VPN), wenn Sie die Verbindung mit dem Verleger herstellen. Wenn Sie die Websynchronisierung implementieren, verwenden Sie eine SSL-Verbindung (Secure Sockets Layer). Weitere Informationen finden Sie unter [Configure Web Synchronization](../configure-web-synchronization.md).  
  
4.  Um die Vorteile der Funktionen von [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zu nutzen, wird die Anwendung mit einer verwalteten Codesprache entwickelt.  
  
5.  Auf Grundlage dieser Anforderungen kann die verwaltete Schnittstelle für Replikationsverwaltungsobjekte (RMO) alle erforderlichen Replikationsfunktionen für diese Anwendung bereitstellen.  
  
 Dieses Beispielszenario wurde in einer Beispielanwendung implementiert, die im Lieferumfang von [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] enthalten ist.  
  
  
