---
title: Mssqlctl Cluster Config Abschnitt Verweis
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Befehle für die Mssqlctl Cluster Config-Abschnitt.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e0c4f543f349d166962e65ea91338595d25308ce
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2019
ms.locfileid: "66800957"
---
# <a name="mssqlctl-cluster-config-section"></a>Abschnitt „Konfiguration des mssqlctl-Clusters“

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **Abschnitt "Config"-cluster** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Mssqlctl Cluster Config Abschnitt anzeigen](#mssqlctl-cluster-config-section-show) | Ruft einen Abschnitt aus einer Konfigurationsdatei ab.
[mssqlctl cluster config section set](#mssqlctl-cluster-config-section-set) | Legt einen Abschnitt für eine Config-Datei fest.
## <a name="mssqlctl-cluster-config-section-show"></a>Mssqlctl Cluster Config Abschnitt anzeigen
Ruft den angegebenen Abschnitt aus der ausgewählten Konfigurationsdatei entsprechend der gegebenen JSON-Pfad ab.
```bash
mssqlctl cluster config section show --json-path -j 
                                     --config-file -c  
                                     [--target -t]  
                                     [--force -f]
```
### <a name="examples"></a>Beispiele
Ruft einen Wert am Ende ein einfaches JSON-Pfad.
```bash
mssqlctl cluster config section show --config-file custom-config.json --json-path 'metadata.name' --target section.json
```
Ruft einen Wert am Ende einer JSON-Pfad mit einem bedingten
```bash
mssqlctl cluster config section show --config-file custom-config.json  --json-path '$.spec.pools[?(@.spec.type=="Storage")].spec' --target section.json
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--json-path -j`
Die JSON-Schlüsselpfad, der auf den Abschnitt oder den gewünschten Wert aus der Konfigurationsdatei, d. h. key1.key2.key3 führt. Verwendet die Jsonpath-Abfragesprache https://github.com/h2non/jsonpath-ng, z. B.: + j "$. spec.pools [? () @.spec.type == "Master")]... Endpunkte
#### `--config-file -c`
Pfad zur Konfigurationsdatei Cluster.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--target -t`
Dateipfad, in dem Sie die Abschnittsdatei im möchten platziert. Standardwert:, die an "stdout" weitergeleitet werden.
#### `--force -f`
Erzwingen Sie die Zieldatei zu überschreiben.
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
Legt den angegebenen Abschnitt in der ausgewählten Konfigurationsdatei entsprechend der gegebenen JSON-Pfad fest.  Alle Examplesbelow in bash bleibt erhalten.  Wenn Sie eine andere Befehlszeile verwenden, Bedenken Sie, dass Sie entsprechend Escapequotations müssen unter Umständen.  Alternativ können Sie die Funktionalität der Patch-Datei verwenden.
```bash
mssqlctl cluster config section set --config-file -c 
                                    [--json-values -j]  
                                    [--patch-file -p]
```
### <a name="examples"></a>Beispiele
Beispiel 1 (Inline) – legen Sie den Port für einen Endpunkt (Controller-Endpunkt).
```bash
mssqlctl cluster config section set --config-file custom-config.json --json-values '$.spec.controlPlane.spec.endpoints[?(@.name=="Controller")].port=30080'
```
Beispiel 1 (Patch): Legen Sie den Port für einen Endpunkt (Controller-Endpunkt) mit Patch-Datei fest.
```bash
mssqlctl cluster config section set --config-file custom-config.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.controlPlane.spec.endpoints[?(@.name=='Controller')].port","value":30080}]}
```
Beispiel 2 (Inline) - Speicherung von Steuerelement-Ebene.
```bash
mssqlctl cluster config section set --config-file custom-config.json --json-values 'spec.controlPlane.spec.storage=spec.controlPlane.spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
Beispiel 2 (Patch) - Steuerelement Ebene Speicherung mit Patch-Datei.
```bash
mssqlctl cluster config section set --config-file custom-config.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"spec.controlPlane.spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
Legen Sie z. B. 3(inline) - Poolspeicher gemeinsam, einschließlich Replikaten (Speicherpools).
```bash
mssqlctl cluster config section set --config-file custom-config.json --json-values '$.spec.pools[?(@.spec.type == "Storage")].spec={"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}'
```
Beispiel 3 (Patch): Legen Sie Poolspeicher gemeinsam, einschließlich der Replikate (Speicherpool) mit Patch-Datei.
```bash
mssqlctl cluster config section set --config-file custom-config.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.pools[?(@.spec.type == 'Storage')].spec","value":{"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}}]}
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--config-file -c`
Cluster-Pfad zur Konfigurationsdatei der Konfiguration, die Sie festlegen möchten.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--json-values -j`
Ein Schlüssel-Wert-Paar-Liste der Pfade der JSON-Werte: key1.subkey1=value1,key2.subkey2=value2. Sie können Inline bereitstellen, JSON-Werte wie z. B.: Key = "{"Kind":"cluster","name":"Test-Cluster"}", oder geben Sie einen Dateipfad an, wie z. B. key=./values.json. Falls Sie möchten, einen Wert festzulegen, der eine bedingte erforderlich sind, verwenden Sie die Jsonpath-Notation durch den Pfad ein $ ab. Dadurch können Sie Sie eine bedingte wie z. B. + j $. key1.key2 [? () @.key3== "SomeValue"] .key4 = Wert. Sie sehen möglicherweise folgenden Beispielen. Weitere Informationen finden Sie unter: https://jsonpath.com/
#### `--patch-file -p`
Pfad zu einer Patch-Json-Datei, die aus der Bibliothek Jsonpatch basiert: http://jsonpatch.com/. Mit einem Schlüssel namens "Patch", dessen Wert ein Array der Patch-Vorgänge ist, die Sie vornehmen möchten, müssen Sie die JSON-Patch-Datei starten. Für den Pfad des Patch-Vorgang ist können Sie die punktierte Schreibweise, wie z. B. key1.key2 für die meisten Vorgänge verwenden. Wenn einen Ersetzungsvorgang ausführen möchten, und Ersetzen Sie einen Wert in ein Array, das eine bedingte erfordert, verwenden Sie die Notation Jsonpath durch den Pfad ein $ ab. Dadurch können Sie eine bedingte wie z. B. $ zu tun. key1.key2 [? () @.key3== "SomeValue"] .key4. Informieren Sie die folgenden Beispielen. Weitere Informationen finden Sie unter: https://jsonpath.com/.
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