---
title: Erstellen einer Dashboarderweiterung
description: Dieses Tutorial veranschaulicht, wie Sie eine Dashboarderweiterung erstellen, um Azure Data Studio benutzerdefinierte Funktionen hinzuzufügen.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: how-to
author: yualan
ms.author: alayu
ms.reviewer: alayu, maghan
ms.custom: ''
ms.date: 08/28/2020
ms.openlocfilehash: 835b1fd4687dc5fd86afe300d7c6ed56dc2ed6ea
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "91111638"
---
# <a name="create-an-azure-data-studio-dashboard-extension"></a>Erstellen einer Azure Data Studio-Dashboarderweiterung

Dieses Tutorial veranschaulicht, wie Sie eine neue **Azure Data Studio-Dashboarderweiterung** erstellen. Die Erweiterung trägt zum Azure Data Studio-Verbindungsdashboard bei, sodass Sie die Funktionalität von Azure Data Studio so erweitern können, dass Sie für Benutzer leicht zu erkennen sind.

In diesem Tutorial lernen Sie Folgendes:
> [!div class="checklist"]
> - Installieren des Erweiterungsgenerators
> - Erstellen der Erweiterung
> - Beitragen zum Dashboard in der Erweiterung
> - Testen der Erweiterung
> - Packen der Erweiterung
> - Veröffentlichen der Erweiterung im Marketplace

## <a name="prerequisites"></a>Voraussetzungen

Azure Data Studio ist auf dem gleichen Framework wie Visual Studio Code aufgebaut, sodass Erweiterungen für Azure Data Studio mithilfe von Visual Studio Code erstellt werden. Sie benötigen die folgenden Komponenten:

- [Node.js](https://nodejs.org) – installiert und in Ihrem `$PATH` verfügbar. Node.js enthält [npm](https://www.npmjs.com/), den Node.js-Paket-Manager, der zum Installieren des Erweiterungsgenerators verwendet wird.
- [Visual Studio Code](https://code.visualstudio.com) zum Debuggen der Erweiterung.
- Die [Debugerweiterung](https://marketplace.visualstudio.com/items?itemName=ms-mssql.sqlops-debug) von Azure Data Studio (optional). Damit können Sie Ihre Erweiterung testen, ohne sie zu packen und in Azure Data Studio zu installieren.
- Stellen Sie sicher, dass sich `azuredatastudio` in Ihrem Pfad befindet. Wenn Sie unter Windows arbeiten, wählen Sie in „setup.exe“ die Option `Add to Path` aus. Wenn Sie unter Mac oder Linux arbeiten, führen Sie die Option *azuredatastudio-Befehl in PATH installieren* aus.

## <a name="install-the-extension-generator"></a>Installieren des Erweiterungsgenerators

Um den Prozess der Erstellung von Erweiterungen zu vereinfachen, haben wir einen [Erweiterungsgenerator](https://code.visualstudio.com/docs/extensions/yocode) erstellt, der Yeoman verwendet. Um diesen zu installieren, führen Sie an der Eingabeaufforderung folgenden Befehl aus:

```console
`npm install -g yo generator-azuredatastudio`
```

## <a name="create-your-dashboard-extension"></a>Erstellen Ihrer Dashboarderweiterung

### <a name="introduction-to-the-dashboard"></a>Einführung in das Dashboard

Das Verbindungsdashboard von Azure Data Studio ist ein leistungsstarkes Tool, das die Verbindungen eines Benutzers zusammenfasst und Einblick in diese gibt.

Es gibt zwei Variationen des Dashboards: das „Serverdashboard“, das den gesamten Server zusammenfasst, und das „Datenbankdashboard“, das eine einzelne Datenbank zusammenfasst. Sie können auf die beiden Dashboards zugreifen, indem Sie mit der rechten Maustaste im Viewlet „Verbindungen“ von Azure Data Studio auf einen Server oder eine Datenbank und dann auf **Verwalten** klicken:

:::image type="content" source="media/dashboard-extension/dashboard-summary.gif" alt-text="Einführung in Dashboards":::

Es gibt drei wichtige Beitragspunkte für Erweiterungen zum Hinzufügen von Funktionen zum Dashboard:

1. **Registerkarte „Vollständiges Dashboard“** : Eine separate Registerkarte im Dashboard für Ihre Erweiterung. Kann einem Server- oder einem Datenbankdashboard hinzugefügt werden. Anpassbar mit Widgets, einer Symbolleiste und einem Navigationsabschnitt.
2. **Homepageaktionen**: Aktionsschaltflächen am oberen Rand der Verbindungssymbolleiste.
3. **Widgets**: Diagramme, die für Ihre SQL Server-Instanz ausgeführt werden.

:::image type="content" source="media/dashboard-extension/dashboard-contrib-points.png" alt-text="Beitragspunkte":::

### <a name="run-the-extension-generator"></a>Ausführen des Erweiterungsgenerators

So erstellen Sie eine Erweiterung:

1. Starten Sie den Erweiterungsgenerator mit dem folgenden Befehl:

   `yo azuredatastudio`

2. Wählen Sie **Neues Dashboard** aus der Liste der Erweiterungstypen aus.

3. Nehmen Sie in den Eingabeaufforderungen die unten gezeigten Eingaben vor. Dadurch wird eine Erweiterung erstellt, die eine Registerkarte zum Serverdashboard beiträgt.

:::image type="content" source="media/dashboard-extension/dashboard-generator.png" alt-text="Erweiterungsgenerator":::

Es gibt viele Eingabeaufforderungen, daher hier ein wenig mehr Informationen dazu, was jede Frage bedeutet:

:::image type="content" source="media/dashboard-extension/dashboard-flowchart.png" alt-text="Flussdiagramm für Dashboards":::

Durch Ausführen der oben genannten Schritte wird ein neuer Ordner erstellt. Öffnen Sie den Ordner in Visual Studio Code, und schon sind Sie bereit, selbst eine Dashboarderweiterung zu erstellen!

### <a name="run-the-extension"></a>Ausführen der Erweiterung

Sehen wir uns nun an, was die Dashboardvorlage bietet, indem wir die Erweiterung ausführen. Stellen Sie vor der Ausführung sicher, dass die **Azure Data Studio-Debugerweiterung** in Visual Studio Code installiert ist.

Drücken Sie **F5** in Visual Studio Code, um Azure Data Studio mit ausgeführter Erweiterung im Debugmodus zu starten. Anschließend können Sie anzeigen, wie diese Standardvorlage zum Dashboard beiträgt.

Als nächstes sehen wir uns an, wie dieses Standarddashboard geändert werden kann.

### <a name="develop-the-dashboard"></a>Entwickeln des Dashboards

Die wichtigste Datei für den Einstieg in die Erweiterungsentwicklung ist `package.json`. Dies ist die Manifestdatei, in der die Dashboardbeiträge registriert werden. Beachten Sie die Abschnitte `dashboard.tabs`, `dashboard.insights` und `dashboard.containers`.

Im Folgenden sind einige Änderungen aufgeführt, die Sie ausprobieren sollten:

- Experimentieren Sie mit den Erkenntnistypen einschließlich „bar“, „horizontalBar“ und „timeSeries“.
- Schreiben Sie eigene Abfragen, um sie für Ihre SQL Server-Verbindung auszuführen.
- Weitere Informationen zu spezifischen Erkenntnissen finden Sie in diesem [Erkenntnisbeispieltutorial](../tutorial-qds-sql-server.md) oder [diesem Tutorial](../tutorial-table-space-sql-server.md).

## <a name="package-your-extension"></a>Packen der Erweiterung

Um Ihre Erweiterung für andere Benutzer freizugeben, müssen Sie sie in eine einzige Datei packen. Diese kann im Marketplace für Azure Data Studio-Erweiterungen veröffentlicht oder für Ihr Team oder Ihre Community freigegeben werden. Zu diesem Zweck müssen Sie über die Befehlszeile ein weiteres npm-Paket installieren:

```console
`npm install -g vsce`
```

Bearbeiten Sie `README.md` wie gewünscht, und navigieren Sie dann zum Basisverzeichnis der Erweiterung, und führen Sie `vsce package` aus. Optional können Sie ein Repository mit ihrer Erweiterung verknüpfen oder den Vorgang ohne Repository fortsetzen. Um ein Repository hinzuzufügen, fügen Sie der Datei `package.json` eine ähnliche Zeile hinzu.

```json
"repository": {
    "type": "git",
    "url": "https://github.com/anjalia/my-test-extension.git"
}
```

Nachdem diese Zeilen hinzugefügt wurden, wurde die Datei „my-test-extension-0.0.1.vsix“ erstellt und ist nun für die Installation in Azure Data Studio bereit.

:::image type="content" source="media/dashboard-extension/install-vsix.png" alt-text="Installieren der VSIX-Datei":::

## <a name="publish-your-extension-to-the-marketplace"></a>Veröffentlichen der Erweiterung im Marketplace

Der Marketplace für Azure Data Studio-Erweiterungen ist noch nicht vollständig implementiert. Zurzeit sieht der Prozess folgendermaßen aus: Sie hosten die VSIX-Datei der Erweiterung an einem beliebigen Ort (z.B. auf einer GitHub-Releaseseite) und führen einen Pull Request aus, mit dem [diese JSON-Datei](https://github.com/Microsoft/azuredatastudio/blob/release/extensions/extensionsGallery.json) mit Ihren Erweiterungsinformationen aktualisiert wird.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie Folgendes gelernt:
> [!div class="checklist"]
> - Installieren des Erweiterungsgenerators
> - Erstellen der Erweiterung
> - Beitragen zum Dashboard in der Erweiterung
> - Testen der Erweiterung
> - Packen der Erweiterung
> - Veröffentlichen der Erweiterung im Marketplace

Wir hoffen, dass dieser Artikel Sie auch dazu inspiriert, selbst eine Erweiterung für Azure Data Studio zu erstellen. Wir bieten Unterstützung für Dashboardeinblicke (ansprechende Diagramme, die in Ihrer SQL Server-Instanz ausgeführt werden können), eine Reihe von SQL-spezifischen APIs sowie eine Vielzahl von vorhandenen Erweiterungspunkten, die aus Visual Studio Code geerbt wurden.

Wenn Sie eine Idee haben, aber nicht sicher sind, wo Sie anfangen sollen, eröffnen Sie ein Issue, oder senden Sie einen Tweet an das Team: [azuredatastudio](https://twitter.com/azuredatastudio).

Sie können jederzeit im [Visual Studio Code-Erweiterungsleitfaden](https://code.visualstudio.com/docs/extensions/overview) nachschlagen, dieser enthält alle vorhandenen APIs und Muster.

Um zu erfahren, wie Sie mit T-SQL in Azure Data Studio arbeiten, führen Sie das Tutorial zum T-SQL-Editor aus:

> [!div class="nextstepaction"]
> [Verwenden des Transact-SQL-Editors zum Erstellen von Datenbankobjekten](../tutorial-sql-editor.md).
