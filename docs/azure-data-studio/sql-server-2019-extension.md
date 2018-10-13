---
title: Azure Data Studio SQL Server-2019-Erweiterung (Vorschau) | Microsoft-Dokumentation
description: 2019-Vorschau von SQL Server-Erweiterung für Azure Data Studio
ms.custom: tools|sos
ms.date: 10/11/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: d73f4a0d55cbe3fe3bacc0b2bb68f191046fe01b
ms.sourcegitcommit: fc6a6eedcea2d98c93e33d39c1cecd99fbc9a155
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49168792"
---
# <a name="sql-server-2019-extension-preview"></a>SQL Server-2019-Erweiterung (Vorschau)

Die SQL Server-2019-Erweiterung (Vorschau) bietet vorschauunterstützung für die neuen Features und Tools, die Unterstützung des Protokollversands [!INCLUDE [sql-server-2019](..\includes\sssqlv15-md.md)]. Dies schließt die Unterstützung für die Vorschauversion [big Data-Cluster für SQL Server-2019](../big-data-cluster/big-data-cluster-overview.md), eine integrierte [notebookfeatures](../big-data-cluster/notebooks-guidance.md), einer PolyBase [Create External Table-Assistenten](../relational-databases/polybase/data-virtualization.md?toc=%2fsql%2fbig-data-cluster%2ftoc.json), und [Azure-Ressourcen-Explorer](azure-resource-explorer.md).

## <a name="install-the-sql-server-2019-extension-preview"></a>Installieren der Erweiterung für SQL Server-2019 (Vorschau)

Klicken Sie zum Installieren der SQL Server-2019-Erweiterungs (Vorschauversion) herunter, und installieren Sie die zugehörigen VSIX-Datei.

1. Laden Sie die SQL Server-2019-Erweiterung (Vorschauversion) VSIX-Datei in ein lokales Verzeichnis herunter:

   |Platform|Herunterladen|Veröffentlichungsdatum|
   |:---|:---|:---|
   |Windows|[VSIX](https://go.microsoft.com/fwlink/?linkid=2024911)|24. September 2018|
   |macOS|[VSIX](https://go.microsoft.com/fwlink/?linkid=2024587)|24. September 2018 |
   |Linux|[VSIX](https://go.microsoft.com/fwlink/?linkid=2024841)|24. September 2018 |

1. Wählen Sie in Azure Data Studio **Erweiterung aus der VSIX-Paket installieren** aus der **Datei** Menü, und wählen Sie die heruntergeladene VSIX-Datei.

1. Wählen Sie **Ja** bei der Aufforderung zum Bestätigen der Installation und warten Sie, bis die Benachrichtigung, die die Installation erfolgreich war.

1. Wählen Sie **Reload** zum Aktivieren der Erweiterung (nur beim ersten eine Erweiterung der Installation erforderlich).

1. Nach erneutem Laden, wird die Erweiterung Abhängigkeiten zu installieren. Sehen Sie den Fortschritt im Ausgabefenster angezeigt, und es kann einige Minuten dauern.

##  <a name="sql-server-2019-big-data-cluster-support"></a>Unterstützung für SQL Server 2019 Big Data-Cluster

* Klicken Sie auf **Verbindung hinzufügen** in *Objekt-Explorer* , und wählen Sie **SQL Server-big Data-Cluster** als Verbindungstyp.

   > [!TIP]
   > Wenn Sie nicht sehen die **SQL Server-big Data-Cluster** Verbindungstyp, starten Sie Azure Data Studio neu.

* Geben Sie den Hostnamen oder die IP-Adresse der clusterendpunkt sowie den Benutzernamen und das Kennwort, die die Verbindung verwendet.
* Optional, enthalten einen Anzeigenamen in den **Namen** Feld.
* Klicken Sie auf **Connect** und allgemeine Aufgaben klicken Sie dann starten auf dem Dashboard Durchsuchen **HDFS** im Objekt-Explorer, und die Ausführung von Tasks im Kontext von dort aus.
* Um einen Spark-Auftrag für den Cluster zu übermitteln, mit der Maustaste, auf den Serverknoten im *Objekt-Explorer* , und wählen Sie **Submit Spark Job** , um das Dialogfeld "Senden" zu öffnen.
* Um ein Notebook zu öffnen, finden Sie im nächsten Abschnitt aus.

Weitere Informationen finden Sie unter [Big Data-Cluster](../big-data-cluster/big-data-cluster-overview.md).


## <a name="azure-data-studio-notebooks"></a>Azure Data Studio Notebooks

* Öffnen Sie ein Notebook in einem der folgenden Methoden:
  * Öffnen Sie ein neues Notebook, aus der *Befehlspalette*.
  * Öffnen Sie die HDFS-Objekt-Explorer-Struktur für eine SQL Server-2019 big Data-Cluster und entweder ein:
    * Klicken Sie mit der rechten Maustaste auf den Serverknoten und wählen Sie **neuen Jupyter Notebooks**.
    * Klicken Sie mit der rechten Maustaste auf eine CSV-Datei, und wählen **Analysieren im Notebook**.
  * Öffnen Sie eine vorhandene ipynb-Datei aus dem **Datei** Menü- oder Datei-Explorer *(ipynb-Dateien müssen auf Version 4 oder höher, um das Laden von aktualisiert werden)*
* Wählen Sie einen Kernel. Wählen Sie für die Ausführung der lokalen Notebooks Python 3 ein. Wählen Sie für die Remoteausführung, PySpark oder Spark | Scala.
* Wählen Sie einen SQL Server-big Data-Cluster-Endpunkt für die Verbindung, wenn Remote ausgeführten (Dies ist nicht erforderlich, für die lokale Entwicklung mit Python 3).
* Hinzufügen von Code oder in Markdown Zellen, über die Schaltflächen im Header Notebooks. Zellen, die das Papierkorbsymbol auf der linken Seite jeder Zelle zu entfernen.
* Führen Sie Zellen mit die Wiedergabeschaltfläche für codezellen, umschalten Markdown bearbeiten und Vorschau mit das Augensymbol


## <a name="azure-resource-explorer"></a>Azure-Ressourcen-Explorer

* Melden Sie sich beim Azure, klicken auf das Personensymbol unten links auf der Azure Data Studio aus, und führen den Dialog, um sich bei Azure anmelden.
* Nach der Anmeldung klicken Sie auf die dreieckige Azure-Symbol in der linken Leiste von Azure Data Studio, und erweitern Sie die Struktur zum Anzeigen der SQL-Ressourcen, die Ihre Abonnements zugeordnet ist.
* Mit der rechten Maustaste, oder klicken Sie auf das Steckersymbol auf jedem SQL-Datenbank oder SQL Server, um das Dialogfeld "Verbindung" zu öffnen. Geben Sie Ihr Kennwort, um eine Verbindung herstellen und die Ressource im Objekt-Explorer von Azure Data Studio hinzufügen.

Weitere Informationen finden Sie unter [Azure-Ressourcen-Explorer](azure-resource-explorer.md).


## <a name="polybase-create-external-table-wizard"></a>Polybase Erstellen externer Tabellen-Assistent

* Von einer Instanz von SQL Server-2019 der *Assistenten zum Erstellen von externen Tabelle* kann auf drei verschiedene Arten geöffnet werden:
  * Klicken Sie mit der rechten Maustaste auf einen Server, wählen Sie **verwalten**, klicken Sie auf der Registerkarte für SQL Server-2019 (Vorschau), und wählen **Create External Table**.
  * Mit einer 2019 für SQL Server-Instanz, die im ausgewählten *Objekt-Explorer*, rufen Sie *externe Assistenten zum Erstellen von* über die *Befehlspalette*.
  * Klicken Sie mit der rechten Maustaste auf eine 2019 für SQL Server-Datenbank in *Objekt-Explorer* , und wählen Sie **Create External Table**.
* In dieser Version der Erweiterung können externe Tabellen erstellt werden, um den Zugriff auf remote SQL Server und Oracle-Tabellen.

  > [!NOTE]
  > Während die Funktionalität der externen Tabelle einer SQL-2019-Funktion ist, kann SQL-Remoteserver eine frühere Version von SQL Server ausgeführt werden.

* Wählen Sie, ob Sie SQL Server oder Oracle auf der ersten Seite des Assistenten zugreifen und fortsetzen.
* Werden Sie aufgefordert, eine Datenbank-Hauptschlüssel zu erstellen, wenn dieser nicht bereits erstellt wurde (Kennwörter von nicht genügend Komplexität blockiert werden).
* Erstellen Sie eine datenquellenverbindung und mit dem Namen Anmeldeinformationen für den Remoteserver.
* Wählen Sie die Objekte aus, um Ihre neue externe Tabelle zuzuordnen.
* Wählen Sie **-Skript generieren** oder **erstellen** um den Assistenten abzuschließen.
* Nach der Erstellung der externen Tabelle wird er sofort in der Objektstruktur der Datenbank, in dem es erstellt wurde.


## <a name="known-issues"></a>Bekannte Probleme

* Wenn das Kennwort nicht gespeichert wird, wenn Sie eine Verbindung zu erstellen, können einige Aktionen, z. B. per Übermittlung von Spark-Auftrag nicht erfolgreich.
* Vorhandene ipynb-Notebooks müssen auf Version 4 oder höher zum Laden von Inhalt im Viewer aktualisiert werden.
