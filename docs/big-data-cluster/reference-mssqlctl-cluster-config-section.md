---
title: Mssqlctl Cluster Config Abschnitt Verweis
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Befehle für die Mssqlctl Cluster Config-Abschnitt.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d5a793e7d0fcaf782a09a4981491ef0a8d90ab5a
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63759137"
---
# <a name="mssqlctl-cluster-config-section"></a>Abschnitt „Konfiguration des mssqlctl-Clusters“

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Abschnitt "Config"-cluster** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[mssqlctl cluster config section get](#mssqlctl-cluster-config-section-get) | Ruft einen Abschnitt aus einer Konfigurationsdatei ab.
[mssqlctl cluster config section set](#mssqlctl-cluster-config-section-set) | Legt einen Abschnitt für eine Config-Datei fest.
## <a name="mssqlctl-cluster-config-section-get"></a>Abschnitt "Config" der Mssqlctl-Cluster zu erhalten.
Ruft den angegebenen Abschnitt aus der ausgewählten Konfigurationsdatei entsprechend der gegebenen JSON-Pfad ab.
```bash
mssqlctl cluster config section get --json-path -j 
                                    --config-file -f  
                                    [--target -t]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--json-path -j`
Die JSON-Schlüsselpfad, der auf den Abschnitt oder den gewünschten Wert aus der Konfigurationsdatei, d. h. key1.key2.key3 führt. Verwendet die Jsonpath-Abfragesprache https://github.com/h2non/jsonpath-ng, z. B.: + j "$. spec.pools [? () @.spec.type == "Master")]... Endpunkte
#### `--config-file -f`
Pfad zur Konfigurationsdatei Cluster.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--target -t`
Dateipfad, in dem Sie die Abschnittsdatei im möchten platziert.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.
## <a name="mssqlctl-cluster-config-section-set"></a>Mssqlctl Clustersatz Config Abschnitt
Legt den angegebenen Abschnitt in der ausgewählten Konfigurationsdatei entsprechend der gegebenen JSON-Pfad fest.
```bash
mssqlctl cluster config section set --config-file -f 
                                    [--json-values -j]  
                                    [--patch-file -p]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--config-file -f`
Cluster-Pfad zur Konfigurationsdatei der Konfiguration, die Sie festlegen möchten.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--json-values -j`
Ein Schlüssel-Wert-Paar-Liste der Pfade der JSON-Werte: key1.subkey1=value1,key2.subkey2=value2. Sie können Inline bereitstellen, JSON-Werte wie z. B.: Key = "{"Kind":"cluster","name":"Test-Cluster"}", oder geben Sie einen Dateipfad an, wie z. B. key=./values.json
#### `--patch-file -p`
Pfad zu einer Patch-Json-Datei, die Jsonpatch-Bibliothek und Jsonpath basiert: https://github.com/stefankoegl/python-json-patch , https://github.com/h2non/jsonpath-ng – ein einfaches Beispiel: {"Patch": [{"Op": "hinzufügen", "Path": "metadata.name", "Value": "test"}, {"Op": "hinzufügen", "Path": "metadata.array", "Value": [1, 2, 3]}]} Bitte schließen Sie den Schlüssel "Patch" aus, und haben Sie den Wert ein Array von Patches, die Sie vornehmen möchten.  Es wird daher ausgeführt werden. A more complex example: {"patch": [{"op": "replace", "path": "$.spec.pools[?(@.spec.type == 'Master')]..endpoints","value": {"name": "Neuer Endpunkt"}}]}
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöht die protokollierungsausführlichkeit, sodass alle Debugprotokolle angezeigt.
#### `--help -h`
Zeigen Sie diese hilfemeldung an und beendet.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: Json, Jsonc, Table, Tsv.  Standardwert: Json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Finden Sie unter [ http://jmespath.org/ ](http://jmespath.org/]) für Weitere Informationen und Beispiele.
#### `--verbose`
Erhöht die protokollierungsausführlichkeit. Verwenden Sie--Debug, wenn Sie vollständige Debugprotokolle wünschen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md). Weitere Informationen zum Installieren der **Mssqlctl** finden Sie unter [Mssqlctl zum Verwalten von SQL Server-2019 big Data-Cluster installieren](deploy-install-mssqlctl.md).