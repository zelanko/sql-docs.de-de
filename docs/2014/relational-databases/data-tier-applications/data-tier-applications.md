---
title: Datenebenenanwendungen| Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-data-tier-apps
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- designing DACs
- How to [DAC]
- data-tier application [SQL Server], designing
- wizard [DAC]
ms.assetid: a04a2aba-d07a-4423-ab8a-0a31658f6317
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 74e9a61fb053a1d861a6be732ae9a0ac0eb3060a
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152501"
---
# <a name="data-tier-applications"></a>Datenebenenanwendungen
  Eine Datenebenenanwendung (DAC) ist eine logische Datenbankverwaltungsentität, die alle [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Objekte definiert, beispielsweise Tabellen, Sichten und Instanzobjekte, einschließlich Anmeldenamen, die mit der Datenbank eines Benutzers verknüpft sind. Eine DAC ist eine in sich geschlossene Einheit der [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Datenbankbereitstellung, mit der Datenebenenentwickler und Datenbankadministratoren [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Objekte in ein portables Artefakt, das sog. "DAC-Paket", packen können. Selbiges ist auch als DACPAC bekannt.  
  
 Ein BACPAC ist ein verwandtes Artefakt, das das Datenbankschema sowie die in der Datenbank gespeicherten Daten kapselt.  
  
## <a name="benefits-of-data-tier-applications"></a>Vorteile von Datenebenenanwendungen  
 Der Lebenszyklus der meisten Datenbankanwendungen zwingt Entwickler und Datenbankadministratoren dazu, Skripts und Ad-hoc-Integrationsbenachrichtigungen für Anwendungsaktualisierungen und Wartungsaktivitäten freizugeben und auszutauschen. Dies stellt bei wenigen Datenbanken kein Problem dar. Es kann jedoch schnell dazu führen, dass sie nicht mehr skalierbar sind, wenn die Datenbanken in puncto Anzahl, Größe und Komplexität wachsen.  
  
 Eine DAC ist ein Datenbank-Lebenszyklusverwaltungs- und Produktivitätstool, womit die Entwicklung deklarativer Datenbanken ermöglicht wird, um Entwicklung und Verwaltung zu vereinfachen. Ein Entwickler kann eine Datenbank in einem SQL Server Data Tools-Datenbankprojekt erstellen und die Datenbank anschließend in einem DACPAC erstellen, um sie an einen Datenbankadministrator zu übergeben. Der Datenbankadministrator kann die DAC mit SQL Server Management Studio auf einer Test- oder Produktionsinstanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] oder [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] bereitstellen. Der Datenbankadministrator kann alternativ mit SQL Server Management Studio mithilfe des DACPAC eine zuvor bereitgestellte Datenbank aktualisieren. Zum Abschließen des Lebenszyklus kann der Datenbankadministrator die Datenbank in einen DACPAC extrahieren und sie einem Entwickler übergeben, damit entweder Test- oder Produktionsanpassungen reflektiert werden oder weitere Datenbankentwurfsänderungen als Reaktion auf Änderungen in der Anwendung ermöglicht werden können.  
  
 Der Vorteil einer DAC-gesteuerten Bereitstellung im Gegensatz zu einer skriptgesteuerten Bereitstellung besteht darin, dass das Tool dem Datenbankadministrator beim Identifizieren und Überprüfen von Verhaltensweisen verschiedener Quell- und Zieldatenbanken behilflich ist. Während der Upgrades warnt das Tool den Datenbankadministrator, wenn das Upgrade Datenverlust verursachen könnte, und es stellt auch einen Upgradeplan bereit. Der Datenbankadministrator kann den Plan auswerten und dann das Tool verwenden, um mit dem Upgrade fortzufahren.  
  
 Der DAC unterstützt auch die Versionsverwaltung, um dem Entwickler und dem Datenbankadministrator zu helfen, die Datenbankherkunft während des Lebenszyklus zu warten und zu verwalten.  
  
## <a name="dac-concepts"></a>Konzepte von DAC  
 Eine DAC vereinfacht die Entwicklung, Bereitstellung und Verwaltung der Datenebenenelemente, die eine Anwendung unterstützen:  
  
-   Eine Datenebenenanwendung (DAC) ist eine logische Datenbankverwaltungsentität, die alle SQL Server-Objekte definiert, beispielsweise Tabellen, Sichten und Instanzobjekte, einschließlich Anmeldenamen, die mit der Datenbank eines Benutzers verknüpft sind. Sie ist eine in sich geschlossene Einheit der SQL Server-Datenbankbereitstellung, mit der Datenebenenentwickler und Datenbankadministratoren SQL Server-Objekte in ein portables Artefakt, das sog. "DAC-Paket" oder die sog. DACPAC-Datei, packen können.  
  
-   Damit eine SQL Server-Datenbank als DAC behandelt wird, muss sie registriert werden, und zwar entweder explizit durch einen Benutzervorgang oder implizit durch eine der DAC-Vorgänge. Wenn eine Datenbank registriert wird, werden die DAC-Version und andere Eigenschaften als Teil der Metadaten der Datenbank aufgezeichnet. Umgekehrt kann die Registrierung einer Datenbank auch aufgehoben werden, wodurch die DAC-Eigenschaften entfernt werden.  
  
-   Im Allgemeinen können DAC-Tools DACPAC-Dateien lesen, die von DAC-Tools früherer SQL Server-Versionen generiert wurden. Zudem können von den DAC-Tools DACPAC-Dateien für frühere Versionen von SQL Server bereitgestellt werden. Demgegenüber können DAC-Tools früherer Versionen keine DACPAC-Dateien lesen, die mit höheren DAC-Tool-Versionen generiert wurden. Dies gilt insbesondere in folgenden Fällen:  
  
    -   DAC-Vorgänge wurden in SQL Server 2008 R2 eingeführt. Zusätzlich zu SQL Server 2008 R2-Datenbanken unterstützen die Tools die Generierung der DACPAC-Dateien von SQL Server 2008, SQL Server 2005 und SQL Server 2000-Datenbanken.  
  
    -   Zusätzlich zu [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]-Datenbanken können die im Lieferumfang von [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] enthaltenen Tools durch DAC-Tools, die im Lieferumfang von SQL Server 2008 R2 oder SQL Server 2012 enthalten sind, generierte DACPAC-Dateien lesen. Dies schließt Datenbanken der Version SQL Server 2012, SQL Server 2008 R2, SQL Server 2008 und SQL Server 2005 ein, aber nicht SQL Server 2000.  
  
    -   DAC-Tools von SQL Server 2008 R2 können keine DACPAC-Dateien lesen, die von [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]- oder [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]-Tools generiert wurden.  
  
-   Ein DACPAC ist eine Windows-Datei mit einer Erweiterung DACPAC. Die Datei unterstützt ein offenes Format. Es besteht aus mehreren XML-Abschnitten, die Details der DACPAC-Herkunft bereitstellen, sowie den Objekten in der Datenbank und anderen Eigenschaften. Ein erfahrener Benutzer kann die Datei mit dem Hilfsprogramm "DacUnpack.exe" entpacken, das mit dem Produkt geliefert wird, um jeden Abschnitt genauer zu überprüfen.  
  
-   Der Benutzer muss ein Mitglied der dbmanager-Rolle sein, oder er muss der CREATE DATABASE-Berechtigung zugeordnet sein, um eine Datenbank zu erstellen, einschließlich dem Erstellen einer Datenbank durch Bereitstellen eines DAC-Pakets. Der Benutzer muss ein Mitglied der dbmanager-Rolle sein, oder er muss der DROP DATABASE-Berechtigung zugeordnet sein, um eine Datenbank löschen zu können.  
  
## <a name="dac-tools"></a>DAC-Tools  
 Ein DACPAC kann nahtlos von mehreren Tools, die im Lieferumfang von [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] enthalten sind, verwendet werden. Diese Tools erfüllen die Anforderungen verschiedener physischer Benutzer, indem DACPAC als interoperable Einheit verwendet wird.  
  
-   Anwendungsentwickler  
  
    -   Ein Datenbankentwickler kann mithilfe eines SQL Server-Datentools-Datenbankprojekts eine Datenbank entwerfen. Eine erfolgreiche Erstellung dieses Projekts ergibt sich in der Generierung von einem DACPAC, der in einer DACPAC-Datei enthalten hat.  
  
    -   Außerdem kann der Entwickler einen DACPAC in ein Datenbankprojekt importieren und weiterhin die Datenbank entwerfen.  
  
    -   SQL Server Data Tools unterstützt auch Local DB für eine nicht verbundene, clientseitige Datenbankanwendungsentwicklung. Der Entwickler kann eine Momentaufnahme dieser lokalen Datenbank erstellen, um in einer DACPAC-Datei enthaltenen DACPAC zu erstellen.  
  
    -   Unabhängig davon kann der Entwickler ein Datenbankprojekt direkt in einer Datenbank veröffentlichen, und zwar ohne ein DACPAC zu generieren. Der Veröffentlichungsvorgang weist ein ähnliches Verwalten auf wie der Bereitstellungsvorgang anderer Tools.  
  
-   Datenbankadministrator  
  
    -   Ein Datenbankadministrator kann einen DACPAC mithilfe von SQL Server Management Studio aus einer vorhandenen Datenbank extrahieren und auch andere DAC-Vorgänge ausführen.  
  
    -   Außerdem kann der Datenbankadministrator für eine [!INCLUDE[ssSDS](../../includes/sssds-md.md)] das Verwaltungsportal für SQL Azure für DAC-Vorgänge verwenden.  
  
-   Unabhängiger Softwarehersteller  
  
    -   Hostende Dienste und andere Datenverwaltungsprodukte für SQL Server können die DACFx-API für DAC-Vorgänge verwenden.  
  
-   IT-Administrator  
  
    -   IT-Systemintegratoren und -Administratoren können das Befehlszeilentool "SqlPackage.exe" für DAC-Vorgänge verwenden.  
  
## <a name="dac-operations"></a>DAC-Vorgänge  
 Ein DAC unterstützt die folgenden Vorgänge:  
  
-   **EXTRACT**: Der Benutzer kann eine Datenbank in eine DACPAC-Datei extrahieren.  
  
-   **DEPLOY**: Der Benutzer kann eine DACPAC-Datei auf einem Hostserver bereitstellen. Wenn die Bereitstellung in einem Verwaltbarkeitstool wie SQL Server Management Studio oder dem Verwaltungsportal für SQL Azure ausgeführt wird, wird die resultierende Datenbank im Hostserver implizit als Datenebenenanwendung registriert.  
  
-   **REGISTER**: Der Benutzer kann eine Datenbank als Datenebenenanwendung registrieren.  
  
-   **UNREGISTER**: Die Registrierung einer zuvor als DAC registrierten Datenbank kann aufgehoben werden.  
  
-   **UPGRADE**: Eine Datenbank kann mit einer DACPAC-Datei aktualisiert werden. Ein Upgrade wird sogar auf Datenbanken, die zuvor nicht als Datenebenenanwendungen registriert waren, unterstützt, doch aufgrund des Upgrades wird die Datenbank implizit registriert.  
  
## <a name="backup-package-bacpac"></a>Sicherungspaket (BACPAC)  
 Ein BACPAC ist ein Artefakt, das das Datenbankschema sowie die in der Datenbank gespeicherten Daten kapselt. Das BACPAC ist eine Windows-Datei mit einer Erweiterung BACPAC. Das BACPAC-Dateiformat ist ein offenes Dateiformat (vergleichbar mit DACPAC). Die Schemainhalte von BACPAC sind mit DACPAC identisch. Die Daten werden im JSON-Format gespeichert.  
  
 DACPAC und BACPAC sind ähnlich, aber sie zielen auf andere Szenarien ab. Ein DACPAC dient zum Erfassen und Bereitstellen von Schemas, einschließlich der Aktualisierung einer vorhandenen Datenbank. Der Hauptverwendungszweck von DACPACs besteht in der Bereitstellung eines streng definierten Schemas für Entwicklungs-, Test- und anschließend Produktionsumgebungen und umgekehrt: dem Erfassen des Produktionsschemas und dem erneuten Anwenden auf Test- und Entwicklungsumgebung.  
  
 Ein BACPAC dient andererseits der Erfassung von Schemas und Daten. Ein BACPAC ist die logische Entsprechung einer Datenbanksicherung und kann nicht verwendet werden, um vorhandene Datenbanken zu aktualisieren. Der Hauptzweck eines BACPACs besteht darin, eine Datenbank von einem Server auf einen anderen zu verschieben – oder von einem lokalen Server in die Cloud – und eine vorhandene Datenbank in einem offenen Format zu archivieren.  
  
 Ein BACPAC unterstützt zwei Hauptvorgänge:  
  
-   **EXPORT**: Der Benutzer kann das Schema und die Daten einer Datenbank in eine BACPAC-Datei exportieren.  
  
-   **IMPORT**: Der Benutzer kann das Schema und die Daten in eine neue Datenbank auf dem Hostserver importieren.  
  
 Beide Funktionen werden von den Datenbankverwaltungstools unterstützt: Server Management Studio, das Verwaltungsportal für SQL Azure und die DACFx-API.  
  
## <a name="permissions"></a>Berechtigungen  
 Sie müssen Mitglied der `dbmanager` Rolle oder zugewiesene `CREATE DATABASE` Berechtigungen zum Erstellen einer Datenbank, z. B. zum Erstellen einer Datenbank durch Bereitstellen eines DAC-Pakets. Sie müssen Mitglied der `dbmanager` -Rolle oder zugewiesen wurden `DROP DATABASE` Berechtigungen für eine Datenbank zu löschen.  
  
## <a name="data-tier-application-tasks"></a>Tasks der Datenebenenanwendung  
  
|Taskbeschreibung|Thema|  
|----------------------|-----------|  
|Beschreibt, wie eine DAC-Paketdatei zum Erstellen einer neuen DAC-Instanz verwendet wird.|[Bereitstellen einer Datenebenenanwendung](deploy-a-data-tier-application.md)|  
|Beschreibt, wie eine neue DAC-Paketdatei zum Aktualisieren einer Instanz auf eine neue Version der DAC verwendet wird.|[Upgrade einer Datenebenenanwendung](upgrade-a-data-tier-application.md)|  
|Beschreibt, wie eine DAC-Instanz entfernt wird. Sie können auswählen, ob Sie die zugeordnete Datenbank auch trennen oder löschen möchten, oder ob die Datenbank intakt bleiben soll.|[Löschen einer Datenebenenanwendung](delete-a-data-tier-application.md)|  
|Beschreibt, wie die Integrität derzeit bereitgestellter DACs mithilfe des SQL Server-Hilfsprogramms angezeigt wird.|[Überwachen von Datenebenenanwendungen](data-tier-applications.md)|  
|Beschreibt, wie eine BACPAC-Datei erstellt wird, die ein Archiv der Daten und Metadaten einer DAC enthält.|[Exportieren einer Datenebenenanwendung](export-a-data-tier-application.md)|  
|Beschreibt, wie mit einer DAC-Archivdatei (.bacpac) entweder eine logische Wiederherstellung einer DAC ausgeführt wird oder die DAC auf einer anderen Instanz von [!INCLUDE[ssDE](../../includes/ssde-md.md)] oder [!INCLUDE[ssSDS](../../includes/sssds-md.md)] migriert wird.|[Importieren einer BACPAC-Datei zum Erstellen einer neuen Benutzerdatenbank](import-a-bacpac-file-to-create-a-new-user-database.md)|  
|Beschreibt, wie eine BACPAC-Datei importiert wird, um eine neue Benutzerdatenbank innerhalb einer Instanz von [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] zu erstellen.|[Extrahieren einer DAC aus einer Datenbank](extract-a-dac-from-a-database.md)|  
|Beschreibt, wie eine vorhandene Datenbank auf eine DAC-Instanz heraufgestuft wird. Eine DAC-Definition wird in der Systemdatenbank erstellt und gespeichert.|[Registrieren einer Datenbank als DAC](register-a-database-as-a-dac.md)|  
|Beschreibt, wie vor der Verwendung eines DAC-Pakets in einem Produktionssystem sein Inhalt und die Aktionen überprüft werden, die bei einem DAC-Upgrade ausgeführt werden.|[Überprüfen eines DAC-Pakets](validate-a-dac-package.md)|  
|Beschreibt, wie der Inhalt eines DAC-Pakets in einem Ordner abgelegt wird, in dem ein Datenbankadministrator vor der Bereitstellung auf einem Produktionsserver überprüfen kann, was die DAC bewirkt.|[Entpacken eines DAC-Pakets](unpack-a-dac-package.md)|  
|Beschreibt die Verwendung eines Assistenten, um eine vorhandene Datenbank bereitzustellen. Der Assistent führt die Bereitstellung mithilfe von DACs aus.|[Bereitstellen einer Datenbank mit DAC](deploy-a-database-by-using-a-dac.md)|  
  
## <a name="see-also"></a>Siehe auch  
 [DAC-Unterstützung für SQL Server-Objekte und -Versionen](dac-support-for-sql-server-objects-and-versions.md)  
  
  
