---
title: Virtualisieren externer Daten in SQL Server 2019 CTP 2.0 | Microsoft-Dokumentation
description: ''
author: Abiola
ms.author: aboke
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: polybase
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: dfd4460c51e4aeef8e9faff8479e7edf2678c35f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627318"
---
# <a name="use-the-data-external-table-wizard-with-external-tables"></a>Verwenden des Assistenten zum Virtualisieren von Daten mit externen Tabellen

Eine der wichtigsten Funktionen in SQL Server 2019 CTP 2.0 ist die Datenvirtualisierung.  Damit können Sie Daten, die an ihrem ursprünglichen Speicherort bleiben, in einer SQL Server-Instanz **virtualisieren**. Dort können sie wie jede andere Tabelle in SQL Server abgefragt werden. So wird die Notwendigkeit von ETL-Vorgängen minimiert. Dies wird durch die Verwendung von PolyBase-Connectors ermöglicht. Weitere Informationen zur Datenvirtualisierung finden Sie im Artikel [Erste Schritte mit PolyBase](polybase-guide.md).

## <a name="launch-the-external-table-wizard"></a>Starten des Assistenten für externe Tabellen

Verbinden Sie sich mit der Masterinstanz über die IP-Adresse/Portnummer (31433), die das Bereitstellungsskript am Ende bereitstellt. Erweitern Sie im Objekt-Explorer den Knoten **Datenbanken**. Wählen Sie dann eine Datenbank aus, in der Sie die Daten aus einer vorhandenen SQL Server-Instanz virtualisieren möchten. Klicken Sie mit der rechten Maustaste auf die Datenbank, und wählen Sie im Kontextmenü **Externe Datenbank erstellen** aus. Daraufhin wird der Assistent zum Virtualisieren von Daten gestartet. Sie können den Assistenten zum Virtualisieren von Daten auch über die Befehlspalette starten, indem Sie „Strg+Shift+P“ (Windows) bzw. Cmd+Shift+P (Mac) eingeben.

![Assistent zum Virtualisieren von Daten](media/data-virtualization/virtualize-data-wizard.png)
## <a name="select-a-data-source"></a>Auswählen einer Datenquelle

Wenn Sie den Assistenten aus einer Datenbank starten, wird das Dropdownmenü im Ziel automatisch ausgefüllt. Auf diesem Bildschirm haben Sie auch die Möglichkeit, die Zieldatenbank anzugeben oder zu ändern. Die Typen der externen Datenquelle, die vom Assistenten unterstützt werden, sind SQL Server und Oracle.

> [!NOTE]
>SQL Server wird standardmäßig hervorgehoben.


![Auswählen einer Datenquelle](media/data-virtualization/select-data-source.png)

Klicken Sie auf „Weiter“, um mit dem nächsten Schritt im Assistenten fortzufahren: dem Festlegen des Datenbankhauptschlüssels.

## <a name="create-database-master-key"></a>Erstellen eines Datenbankhauptschlüssels

In diesem Schritt werden Sie aufgefordert, einen Datenbankhauptschlüssel zu erstellen. Dieser Schritt ist erforderlich, da dabei die von einer externen Datenquelle verwendeten Anmeldeinformationen gesichert werden. Wählen Sie für Ihren Hauptschlüssel ein sicheres Kennwort aus. Außerdem wird empfohlen, mit „BACKUP MASTER KEY“ eine Sicherung des Hauptschlüssels zu erstellen und diese an einem sicheren externen Ort aufzubewahren.

![Erstellen eines Datenbankhauptschlüssels](media/data-virtualization/virtualize-data-master-key.png)

> [!IMPORTANT]
> Wenn Sie bereits einen Datenbankhauptschlüssel haben, werden die Eingabefelder beschränkt. Sie können diesen Schritt überspringen, indem Sie auf „Weiter“ klicken. So gelangen Sie zur nächsten Seite im Assistenten.

> [!NOTE]
> Wenn Sie kein sicheres Kennwort auswählen, macht das der Assistent im letzten Schritt. Dies ist ein bekanntes Problem, das wir im nächsten Release beheben, um das Vorgehen intuitiver zu gestalten.

## <a name="enter-the-external-data-source-credentials"></a>Eingeben der Anmeldeinformationen für die externe Datenquelle

Geben Sie in diesem Schritt Ihre externe Datenquelle und die entsprechenden Anmeldeinformationen ein. Dieser Schritt erstellt ein externes Datenquellenobjekt und verwendet dann die Anmeldeinformationen für das Datenbankobjekt, um eine Verbindung zur Datenquelle herzustellen. Geben Sie einen Namen für die externe Datenquelle, z.B. „Test“, und die Details der SQL Server-Verbindung an, d.h. den Server- und den Datenbanknamen, unter dem Ihre externe Datenquelle auf dem Server erstellt werden soll.

Im nächsten Schritt werden die Anmeldeinformationen konfiguriert. Geben Sie einen Anmeldenamen ein, der Ihrem datenbankweit gültigen Anmeldeinformationsnamen entspricht, mit dem Sie die Anmeldeinfos für die von Ihnen erstellte externe Datenquelle (z.B. „TestCred“) sicher speichern, und geben Sie den Benutzernamen und das Kennwort für die Verbindung mit der Datenquelle an.

![Anmeldeinformationen für die externe Datenquelle](media/data-virtualization/data-source-credentials.png)

## <a name="external-data-table-mapping"></a>Zuordnungstabelle für externe Daten

Im nächsten Fenster können Sie die Tabellen auswählen, für die Sie externe Ansichten erstellen möchten. Die Auswahl übergeordneter Datenbanken schließt alle untergeordneten Tabellen ein. Wenn die Tabellen ausgewählt wurden, wird rechts eine Zuordnungstabelle angezeigt. Hier können Sie beliebige Änderungen für „Typ“ vornehmen oder den Namen der ausgewählten externen Tabelle ändern.

![Anmeldeinformationen für die externe Datenquelle](media/data-virtualization/data-table-mapping.png)

> [!NOTE]
>Wenn Sie auf eine andere ausgewählte Tabelle doppelklicken, ändert sich die Zuordnungsansicht.

> [!IMPORTANT]
>Der Fototyp wird vom Tool für externe Tabellen noch nicht unterstützt. Das Erstellen einer externen Ansicht mit einem darin enthaltenen Fototyp löst nach der Tabellenerstellung einen Fehler aus. Die Tabelle wird allerdings erstellt.

## <a name="summary"></a>Zusammenfassung

Dieser Schritt bietet eine Zusammenfassung Ihrer Auswahl. Sie enthält den Namen der datenbankweiten Anmeldeinformationen und der Objekte der externen Datenquelle, die in der Zieldatenbank erstellt werden. In diesem Schritt können Sie die beiden Optionen **Script generieren** und **Erstellen** auswählen. Mit „Skript generieren“ errichten Sie in T-SQL die Syntax zum Erstellen der externen Datenquelle, und mit „Erstellen“ erstellen Sie das Objekt der externen Datenquelle.

![Bildschirm „Zusammenfassung“](media/data-virtualization/virtualize-data-summary.png)

Wenn Sie auf „Erstellen“ klicken, können Sie das in der Zieldatenbank erstellte Objekt der externen Datenquelle sehen.

![Externe Datenquellen](media/data-virtualization/external-data-sources.png)

Wenn Sie auf **Skript generieren** klicken, wird angezeigt, wie die T-SQL-Abfrage zum Erstellen des Objekts der externen Datenquelle generiert wird.

![Skript generieren](media/data-virtualization/generated-script.png)

> [!NOTE]
> „Skript generieren“ soll nur auf der letzten Seite im Assistenten angezeigt werden. Derzeit erscheint die Option auf allen Seiten.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum SQL Server-Cluster für Big Data und die entsprechenden Szenarien finden Sie unter [Was ist der SQL Server-Cluster für Big Data?](../../big-data-cluster/big-data-cluster-overview.md).
