---
title: Erweiterbarkeits-APIs
titleSuffix: Azure Data Studio
description: Weitere Informationen Sie zu den Erweiterungs-APIs für Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 55ab9fb45b37595c84303a5a52b83de14a05068d
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2019
ms.locfileid: "65105249"
---
# <a name="azure-data-studio-extensibility-apis"></a>Azure Data Studio-Erweiterbarkeits-APIs

[!INCLUDE[name-sos](../includes/name-sos.md)] Stellt eine API, die Erweiterungen für die Interaktion mit anderen Teilen von Azure Data Studio, z. B. die Objekt-Explorer verwenden können. Diese APIs stehen über die [ `src/sql/sqlops.d.ts` ](https://github.com/Microsoft/azuredatastudio/blob/master/src/sql/sqlops.d.ts) Datei, und werden unten beschrieben.

## <a name="connection-management"></a>Verbindungsverwaltung
`sqlops.connection`

### <a name="top-level-functions"></a>Funktionen der obersten Ebene

- `getCurrentConnection(): Thenable<sqlops.connection.Connection>` Ruft die aktuelle Verbindung basierend auf dem aktiven Editor oder die Objekt-Explorer-Auswahl ab.

- `getActiveConnections(): Thenable<sqlops.connection.Connection[]>` Ruft eine Liste der Verbindungen des Benutzers, die aktiv sind. Gibt eine leere Liste zurück, wenn es keine solche Verbindungen.

- `getCredentials(connectionId: string): Thenable<{ [name: string]: string }>` Ruft ein Wörterbuch mit den Anmeldeinformationen, die mit einer Verbindung verknüpft sind. Diese andernfalls als Teil der Optionen-Wörterbuch unter zurückgegeben werden würde eine `sqlops.connection.Connection` Objekt jedoch erhalten, die aus dem Objekt entfernt wurde. 

### `Connection`
- `options: { [name: string]: string }` Das Wörterbuch der Verbindungsoptionen
- `providerName: string` Der Name des Verbindungs-Anbieters (z.B.) "MSSQL")
- `connectionId: string` Der eindeutige Bezeichner für die Verbindung

### <a name="example-code"></a>Beispielcode
```
> let connection = sqlops.connection.getCurrentConnection();
connection: {
    providerName: 'MSSQL',
    connectionId: 'd97bb63a-466e-4ef0-ab6f-00cd44721dcc',
    options: {
        server: 'mairvine-sql-server',
        user: 'sa',
        authenticationType: 'sqlLogin',
        ...
    },
    ...
}
> let credentials = sqlops.connection.getCredentials(connection.connectionId);
credentials: {
    password: 'abc123'
}

```

## <a name="object-explorer"></a>Objekt-Explorer

`sqlops.objectexplorer`


### <a name="top-level-functions"></a>Funktionen der obersten Ebene
- `getNode(connectionId: string, nodePath?: string): Thenable<sqlops.objectexplorer.ObjectExplorerNode>` Erhalten Sie einen Objekt-Explorer-Knoten, der der angegebenen Verbindung und der Pfad entspricht. Wenn kein Pfad angegeben ist, wird der Knoten den obersten Ebene für die angegebene Verbindung zurückgegeben. Wenn kein Knoten im angegebenen Pfad vorhanden ist, gibt es zurück `undefined`. Hinweis: Die `nodePath` für ein Objekt von der SQL-Tools-Dienst-Back-End generiert wird und schwer zu manuell erstellen. Zukünftige Verbesserungen der API können Sie zum Abrufen von Knotens basierend auf Metadaten, die Sie über den Knoten, z. B. Name, Typ und Schema bereitstellen.

- `getActiveConnectionNodes(): Thenable<sqlops.objectexplorer.ObjectExplorerNode>` Rufen Sie alle aktive Knoten für die Objekt-Explorer-Verbindung.

- `findNodes(connectionId: string, type: string, schema: string, name: string, database: string, parentObjectNames: string[]): Thenable<sqlops.objectexplorer.ObjectExplorerNode[]>` Suchen Sie alle Objekt-Explorer-Knoten, die mit den angegebenen Metadaten überein. Die `schema`, `database`, und `parentObjectNames` Argumente muss `undefined` Wenn sie nicht anwendbar sind. `parentObjectNames` ist eine Liste der nicht mit der Datenbank übergeordnete Objekte, von der höchsten zur niedrigsten Ebene im Objekt-Explorer, der das gewünschte Objekt wird an. Bei der Suche für eine Spalte "column1", der eine Tabelle "schema1.table1" und die Datenbank "database1" angehört, mit dem Verbindungs-ID beispielsweise `connectionId`, rufen Sie `findNodes(connectionId, 'Column', undefined, 'column1', 'database1', ['schema1.table1'])`. Siehe auch die [Liste von Typen, die von Azure Data Studio standardmäßig unterstützt](https://github.com/Microsoft/azuredatastudio/wiki/Object-Explorer-types-supported-by-FindNodes-API) für diese API-Aufruf.

### <a name="objectexplorernode"></a>ObjectExplorerNode
- `connectionId: string` Die Id der Verbindung, der unter der Knoten vorhanden ist

- `nodePath: string` Der Pfad des Knotens wie bei einem Aufruf der `getNode` Funktion.

- `nodeType: string` Eine Zeichenfolge, die den Typ des Knotens darstellt.

- `nodeSubType: string` Eine Zeichenfolge, die den Untertyp des Knotens darstellt.

- `nodeStatus: string` Eine Zeichenfolge, die den Status des Knotens darstellt.

- `label: string` Die Bezeichnung für den Knoten, wie er angezeigt wird, im Objekt-Explorer

- `isLeaf: boolean` Gibt an, ob der Knoten um einen Blattknoten handelt, und aus diesem Grund hat keine untergeordneten Elemente

- `metadata: sqlops.ObjectMetadata` Metadaten zur Beschreibung des Objekts, das von diesem Knoten dargestellt wird.

- `errorMessage: string` Meldung, die angezeigt wird, wenn der Knoten in einem Fehlerzustand ist

- `isExpanded(): Thenable<boolean>` Gibt an, ob der Knoten im Objekt-Explorer gerade erweitert wird

- `setExpandedState(expandedState: vscode.TreeItemCollapsibleState): Thenable<void>` Festlegen Sie, ob der Knoten erweitert oder reduziert ist. Wenn der Status auf "None" festgelegt ist, wird der Knoten nicht geändert werden.

- `setSelected(selected: boolean, clearOtherSelections?: boolean): Thenable<void>` Festlegen Sie, ob der Knoten ausgewählt ist. Wenn `clearOtherSelections` ist "true" fest, die keine andere Auswahl zu löschen, wenn Sie die neue Auswahl vornehmen. Wenn sie falsch ist, lassen Sie keine vorhandenen Auswahl. `clearOtherSelections` Der Standardwert ist true, wenn `selected` ist "true" und "false", wenn `selected` ist "false".

- `getChildren(): Thenable<sqlops.objectexplorer.ObjectExplorerNode[]>` Erhalten Sie alle untergeordneten Knoten dieses Knotens. Gibt eine leere Liste zurück, wenn keine untergeordneten Elemente vorhanden sind.

- `getParent(): Thenable<sqlops.objectexplorer.ObjectExplorerNode>` Rufen Sie den übergeordneten Knoten dieses Knotens. Gibt nicht definiert, wenn es kein übergeordnetes Element.

### <a name="example-code"></a>Beispielcode

```cs
private async interactWithOENode(selectedNode: sqlops.objectexplorer.ObjectExplorerNode): Promise<void> {
    let choices = ['Expand', 'Collapse', 'Select', 'Select (multi)', 'Deselect', 'Deselect (multi)'];
    if (selectedNode.isLeaf) {
        choices[0] += ' (is leaf)';
        choices[1] += ' (is leaf)';
    } else {
        let expanded = await selectedNode.isExpanded();
        if (expanded) {
            choices[0] += ' (is expanded)';
        } else {
            choices[1] += ' (is collapsed)';
        }
    }
    let parent = await selectedNode.getParent();
    if (parent) {
        choices.push('Get Parent');
    }
    let children = await selectedNode.getChildren();
    children.forEach(child => choices.push(child.label));
    let choice = await vscode.window.showQuickPick(choices);
    let nextNode: sqlops.objectexplorer.ObjectExplorerNode = undefined;
    if (choice === choices[0]) {
        selectedNode.setExpandedState(vscode.TreeItemCollapsibleState.Expanded);
    } else if (choice === choices[1]) {
        selectedNode.setExpandedState(vscode.TreeItemCollapsibleState.Collapsed);
    } else if (choice === choices[2]) {
        selectedNode.setSelected(true);
    } else if (choice === choices[3]) {
        selectedNode.setSelected(true, false);
    } else if (choice === choices[4]) {
        selectedNode.setSelected(false);
    } else if (choice === choices[5]) {
        selectedNode.setSelected(false, true);
    } else if (choice === 'Get Parent') {
        nextNode = parent;
    } else {
        let childNode = children.find(child => child.label === choice);
        nextNode = childNode;
    }
    if (nextNode) {
        let updatedNode = await sqlops.objectexplorer.getNode(nextNode.connectionId, nextNode.nodePath);
        this.interactWithOENode(updatedNode);
    }
}

vscode.commands.registerCommand('mssql.objectexplorer.interact', () => {
    sqlops.objectexplorer.getActiveConnectionNodes().then(activeConnections => {
        vscode.window.showQuickPick(activeConnections.map(connection => connection.label + ' ' + connection.connectionId)).then(selection => {
            let selectedNode = activeConnections.find(connection => connection.label + ' ' + connection.connectionId === selection);
            this.interactWithOENode(selectedNode);
        });
    });
});
```

## <a name="proposed-apis"></a>Vorgeschlagene APIs

Wir haben vorgeschlagene APIs verwendet, um das Erweiterungen zum Anzeigen der benutzerdefinierten Benutzeroberfläche in den Dialogfeldern und Assistenten Dokumentregisterkarten, neben anderen Funktionen können hinzugefügt werden. Finden Sie unter den [vorgeschlagenen API-Typendatei](https://github.com/Microsoft/azuredatastudio/blob/master/src/sql/sqlops.proposed.d.ts) Weitere Dokumentationen, aber Bedenken Sie, dass diese APIs können jederzeit geändert werden. Beispiele für die Verwendung einiger dieser APIs finden Sie in der ["Sqlservices" Beispiel-Erweiterung](https://github.com/Microsoft/azuredatastudio/tree/master/samples/sqlservices).


