---
title: Referenz zu azdata context
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata context-Befehlen
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 36b670ee8485c2e8db58847e9439dfb5fa9920ce
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531681"
---
# <a name="azdata-context"></a>azdata context

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Der folgende Artikel enthält Referenzinformationen zu den `sql`-Befehlen im `azdata`-Tool. Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata context list](#azdata-context-list) | Listet die verfügbaren Kontexte im Benutzerprofil auf
[azdata context delete](#azdata-context-delete) | Löscht den Kontext mit dem angegebenen Namespace aus dem Benutzerprofil
[azdata context set](#azdata-context-set) | Legt den Kontext mit dem angegebenen Namespace als den aktiven Kontext im Benutzerprofil fest
## <a name="azdata-context-list"></a>azdata context list
Sie können beliebige Kontexte mit `azdata context set` oder `azdata context delete` festlegen oder löschen. Verwenden Sie `azdata login`, um sich bei einem neuen Kontext anzumelden.
```bash
azdata context list [--active -a] 
  ```
### <a name="examples"></a>Beispiele
Listet alle verfügbaren Kontexte im Benutzerprofil auf.
```bash
azdata context list
```
Listet den aktiven Kontext im Benutzerprofil auf.
```bash
azdata context list --active
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--active -a`
Listet nur den derzeit aktiven Kontext auf.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-context-delete"></a>azdata context delete
Ist der gelöschte Kontext aktiv, muss der Benutzer einen neuen aktiven Kontext festlegen. Mit `azdata context list` können Sie die Kontexte anzeigen, die zum Festlegen oder Löschen verfügbar sind.
```bash
azdata context delete --namespace -n 
    ```
### Examples
Deletes contextNamespace from the user profile.
```bash
azdata context delete -n contextNamespace
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -n`
Namespace des Kontexts, den Sie löschen möchten.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-context-set"></a>azdata context set
Mit `azdata context list` können Sie die Kontexte anzeigen, die zum Festlegen verfügbar sind. Werden keine Kontexte angezeigt, müssen Sie sich mit `azdata login` anmelden, um in Ihrem Benutzerprofil einen Kontext zu erstellen. Der Kontext, bei dem Sie sich anmelden, wird zu Ihrem aktiven Kontext. Wenn Sie sich bei mehreren Entitäten anmelden, können Sie mit diesem Befehl zwischen den aktiven Kontexten wechseln. Mit `azdata context list --active` wird der derzeit aktive Kontext angezeigt.
```bash
azdata context set --namespace -n 
 ```
### <a name="examples"></a>Beispiele
Legt contextNamespace als den aktiven Kontext im Benutzerprofil fest.
```bash
azdata context set -n contextNamespace
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--namespace -n`
Namespace des Kontexts, den Sie festlegen möchten.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md). Weitere Informationen zur Installation des `azdata`-Tools finden Sie unter [Installieren von azdata zum Verwalten von Big Data-Clustern für SQL Server 2019](deploy-install-azdata.md).
