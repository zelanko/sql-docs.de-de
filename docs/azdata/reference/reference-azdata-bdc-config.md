---
title: Referenz zu „azdata bdc config“
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata bdc config-Befehlen
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a823daa4864bf2b730a8746f46f0120a8f063564
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914638"
---
# <a name="azdata-bdc-config"></a>azdata bdc config

Gilt für `azdata`e

Der folgende Artikel enthält Referenzinformationen zu den **sql**-Befehlen im **azdata**-Tool. Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md).

## <a name="commands"></a>Befehle

|Get-Help|BESCHREIBUNG|
| --- | --- |
[azdata bdc config init](#azdata-bdc-config-init) | Hiermit wird ein Konfigurationsprofil für Big Data-Cluster konfiguriert, das für deren Erstellung verwendet werden kann.
[azdata bdc config list](#azdata-bdc-config-list) | Listet die verfügbaren Optionen für das Konfigurationsprofil auf.
[azdata bdc config show](#azdata-bdc-config-show) | Zeigt die aktuelle Konfiguration des BDC oder die Konfiguration einer lokalen Datei an, die Sie angeben, z. B. custom/bdc.json.
[azdata bdc config add](#azdata-bdc-config-add) | Fügt einen Wert in einem JSON-Pfad in einer Konfigurationsdatei hinzu.
[azdata bdc config remove](#azdata-bdc-config-remove) | Entfernt einen Wert in einem JSON-Pfad in einer Konfigurationsdatei.
[azdata bdc config replace](#azdata-bdc-config-replace) | Ersetzt einen Wert in einem JSON-Pfad in einer Konfigurationsdatei.
[azdata bdc config patch](#azdata-bdc-config-patch) | Patcht eine Konfigurationsdatei auf der Grundlage einer JSON-Patchdatei.
## <a name="azdata-bdc-config-init"></a>azdata bdc config init
Hiermit wird ein Konfigurationsprofil für Big Data-Cluster konfiguriert, das für deren Erstellung verwendet werden kann. Die jeweilige Quelle des Konfigurationsprofils kann in den Argumenten angegeben werden.
```bash
azdata bdc config init [--path -p] 
                       [--source -s]  
                       
[--force -f]  
                       
[--accept-eula -a]
```
### <a name="examples"></a>Beispiele
Angeleitete Ausführung von „BDC config init“: Sie erhalten Aufforderungen für die Eingabe der erforderlichen Werte.
```bash
azdata bdc config init
```
„BDC config init mit Argumenten“ erstellt ein Konfigurationsprofil von aks-dev-test in „./custom“.
```bash
azdata bdc config init --source aks-dev-test --target custom
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--path -p`
Der Dateipfad, in dem das Konfigurationsprofil platziert werden soll, ist standardmäßig <cwd>/custom.
#### `--source -s`
Konfigurationsprofilquelle: ['openshift-prod', 'aks-dev-test-ha', 'aro-dev-test-ha', 'aks-dev-test', 'kubeadm-prod', 'aro-dev-test', 'openshift-dev-test', 'kubeadm-dev-test']
#### `--force -f`
Erzwingen der Überschreibung der Zieldatei
#### `--accept-eula -a`
Stimmen Sie den Lizenzbedingungen zu? [yes/no]. Wenn Sie dieses Argument nicht verwenden möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf „yes“ festlegen. Die Lizenzbedingungen für dieses Produkt finden Sie unter https://aka.ms/eula-azdata-en.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-bdc-config-list"></a>azdata bdc config list
Listet die verfügbaren Optionen für das Konfigurationsprofil zur Verwendung in `bdc config init` auf.
```bash
azdata bdc config list [--config-profile -c] 
                       [--type -t]  
                       
[--accept-eula -a]
```
### <a name="examples"></a>Beispiele
Listet alle verfügbaren Namen für das Konfigurationsprofil auf.
```bash
azdata bdc config list
```
Zeigt JSON eines bestimmten Konfigurationsprofils an.
```bash
azdata bdc config list --config-profile aks-dev-test
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--config-profile -c`
Standardkonfigurationsprofil: ['openshift-prod', 'aks-dev-test-ha', 'aro-dev-test-ha', 'aks-dev-test', 'kubeadm-prod', 'aro-dev-test', 'openshift-dev-test', 'kubeadm-dev-test']
#### `--type -t`
Welchen Konfigurationstyp Sie sehen möchten.
#### `--accept-eula -a`
Stimmen Sie den Lizenzbedingungen zu? [yes/no]. Wenn Sie dieses Argument nicht verwenden möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf „yes“ festlegen. Die Lizenzbedingungen für dieses Produkt finden Sie unter https://aka.ms/eula-azdata-en.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-bdc-config-show"></a>azdata bdc config show
Zeigt die aktuelle Konfiguration des BDC oder die Konfiguration einer lokalen Datei an, die Sie angeben, z. B. custom/bdc.json. Der Befehl kann auch einen JSON-Pfad verwenden, wenn Sie nur einen Abschnitt erhalten möchten.  Sie können auch eine Zieldatei angeben, in die die Ausgabe ausgegeben werden soll.  Wenn keine Zieldatei angegeben ist, wird sie nur an das Terminal ausgegeben.
```bash
azdata bdc config show [--config-file -c] 
                       [--target -t]  
                       
[--json-path -j]  
                       
[--force -f]
```
### <a name="examples"></a>Beispiele
Anzeigen der BDC-Konfiguration in der Konsole
```bash
azdata bdc config show
```
In einer lokalen Konfigurationsdatei wird ein Wert am Ende eines einfachen JSON-Schlüsselpfads abgerufen.
```bash
azdata bdc config show --config-file custom-config/bdc.json --json-path "metadata.name" --target section.json
```
In einer lokalen Konfigurationsdatei werden die Ressourcen in einem Dienst abgerufen.
```bash
azdata bdc config show --config-file custom-config/bdc.json --json-path "$.spec.services.sql.resources" --target section.json
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--config-file -c`
Pfad für die Konfigurationsdatei eines Big Data-Clusters, wenn nicht die Konfiguration des Clusters, bei dem Sie aktuell angemeldet sind, abgerufen werden soll (z. B. custom/bdc.json).
#### `--target -t`
Ausgabedatei, in der das Ergebnis gespeichert werden soll. Standard: wird an STDOUT weitergeleitet.
#### `--json-path -j`
Der JSON-Schlüsselpfad, der zu dem von der Konfiguration gewünschten Abschnitt oder Wert führt, z. B. key1.key2.key3. Verwendet die Abfragesprache JSONPATH, https://jsonpath.com/ z. B.: -j '$.spec.pools[?(@.spec.type == "Master")]..endpoints'
#### `--force -f`
Erzwingen der Überschreibung der Zieldatei
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-bdc-config-add"></a>azdata bdc config add
Fügt den Wert im JSON-Pfad in der Konfigurationsdatei hinzu.  Alle nachfolgenden Beispiele sind in Bash angegeben.  Beachten Sie bei Verwenden einer anderen Befehlszeile, dass Sie möglicherweise entsprechende Escapezeichen hinzufügen müssen.  Alternativ können Sie auch die Patchdateifunktionen verwenden.
```bash
azdata bdc config add --path -p 
                      --json-values -j
```
### <a name="examples"></a>Beispiele
Bsp. 1.: Hinzufügen von Speicher auf Steuerungsebene
```bash
azdata bdc config add --path custom/control.json --json-values "spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}"
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Pfad für die Konfigurationsdatei eines Big Data-Clusters der Konfiguration, die Sie festlegen möchten, z. B. custom/cluster.json.
#### `--json-values -j`
Eine Schlüssel-Wert-Paar-Liste von JSON-Pfaden zu Werten: key1.subkey1=value1,key2.subkey2=value2 Sie können JSON-Inlinewerte angeben, z. B.: key='{"kind":"cluster","name":"test-cluster"}' oder einen Dateipfad, z. B. key=./values.json. Der Vorgang „Hinzufügen“ unterstützt KEINE Bedingungen.  Wenn der Inlinewert, den Sie bereitstellen, selbst ein Schlüssel-Wert-Paar mit „=“ und „,“ ist, vermeiden Sie diese Zeichen.  Zum Beispiel key1=„key2\=val2\,key3\=val3“. Beispiele dazu, wie Ihr Pfad aussehen sollte, finden Sie unter http://jsonpatch.com/.  Wenn Sie auf ein Array zugreifen möchten, müssen Sie dazu den Index angeben, z. B. key.0=value.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-bdc-config-remove"></a>azdata bdc config remove
Entfernt den Wert im JSON-Pfad in der Konfigurationsdatei.  Alle nachfolgenden Beispiele sind in Bash angegeben.  Beachten Sie bei Verwenden einer anderen Befehlszeile, dass Sie möglicherweise entsprechende Escapezeichen hinzufügen müssen.  Alternativ können Sie auch die Patchdateifunktionen verwenden.
```bash
azdata bdc config remove --path -p 
                         --json-path -j
```
### <a name="examples"></a>Beispiele
Bsp. 1.: Entfernen von Speicher auf Steuerungsebene
```bash
azdata bdc config remove --path custom/control.json --json-path ".spec.storage"
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Pfad für die Konfigurationsdatei eines Big Data-Clusters der Konfiguration, die Sie festlegen möchten, z. B. custom/cluster.json.
#### `--json-path -j`
Eine Liste von JSON-Pfaden, die auf der JSONPATCH-Bibliothek basiert und angibt, welche Werte entfernt werden sollen, z. B.: key1.subkey1,key2.subkey2. Der Vorgang „Entfernen“ unterstützt KEINE Bedingungen. Beispiele dazu, wie Ihr Pfad aussehen sollte, finden Sie unter http://jsonpatch.com/.  Wenn Sie auf ein Array zugreifen möchten, müssen Sie dazu den Index angeben, z. B. key.0=value.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-bdc-config-replace"></a>azdata bdc config replace
Ersetzt den Wert im JSON-Pfad in der Konfigurationsdatei.  Alle nachfolgenden Beispiele sind in Bash angegeben.  Beachten Sie bei Verwenden einer anderen Befehlszeile, dass Sie möglicherweise entsprechende Escapezeichen hinzufügen müssen.  Alternativ können Sie auch die Patchdateifunktionen verwenden.
```bash
azdata bdc config replace --path -p 
                          --json-values -j
```
### <a name="examples"></a>Beispiele
Bsp. 1: Ersetzen des Ports eines einzelnen Endpunkts (Controller-Endpunkt)
```bash
azdata bdc config replace --path custom/control.json --json-values "$.spec.endpoints[?(@.name=="Controller")].port=30080"
```
Bsp. 2: Ersetzen von Speicher auf Steuerungsebene
```bash
azdata bdc config replace --path custom/control.json --json-values "spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}"
```
Bsp. 3: Ersetzen der Ressourcenspezifikation storage-0 einschließlich der Replikate.
```bash
azdata bdc config replace --path custom/bdc.json --json-values "$.spec.resources.storage-0.spec={"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}"
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path -p`
Pfad für die Konfigurationsdatei eines Big Data-Clusters der Konfiguration, die Sie festlegen möchten, z. B. custom/cluster.json.
#### `--json-values -j`
Eine Schlüssel-Wert-Paar-Liste von JSON-Pfaden zu Werten: key1.subkey1=value1,key2.subkey2=value2 Sie können JSON-Inlinewerte angeben, z. B.: key='{"kind":"cluster","name":"test-cluster"}' oder einen Dateipfad, z. B. key=./values.json. Der Vorgang „Ersetzen“ unterstützt Bedingungen über die JSONPATH-Bibliothek.  Um diesen Parameter zu verwenden, starten Sie den Pfad mit „$“. Dies ermöglicht die Verwendung einer Bedingung wie z. B. „-j $.key1.key2[?(@.key3=='someValue'].key4=value“. Wenn der Inlinewert, den Sie bereitstellen, selbst ein Schlüssel-Wert-Paar mit „=“ und „,“ ist, vermeiden Sie diese Zeichen.  Zum Beispiel key1=„key2\=val2\,key3\=val3“. Nachfolgend sehen Sie hierzu Beispiele. Zusätzliche Hilfe finden Sie unter https://jsonpath.com/.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-bdc-config-patch"></a>azdata bdc config patch
Patcht die Konfigurationsdatei entsprechend der angegebenen Patchdatei. Informationen zum besseren Verständnis der Zusammensetzung der Pfade finden Sie unter http://jsonpatch.com/. Der Vorgang „Ersetzen“ kann Bedingungen im Pfad aufgrund der JSONPATH-Bibliothek verwenden (https://jsonpath.com/ ). Alle JSON-Patchdateien müssen mit einem „Patch“-Schlüssel beginnen, der über ein Array von Patches mit dem entsprechenden Vorgang (Hinzufügen, Ersetzen, Entfernen), Pfad und Wert verfügt. Der Vorgang „Entfernen“ erfordert keinen Wert, sondern nur einen Pfad. Siehe hierzu folgende Beispiele.
```bash
azdata bdc config patch --path 
                        --patch-file -p
```
### <a name="examples"></a>Beispiele
Bsp. 1: Ersetzen des Ports eines einzelnen Endpunkts (Controller-Endpunkt) mit Patchdatei
```bash
azdata bdc config patch --path custom/control.json --patch ./patch.json

    Patch File Example (patch.json):
        {"patch":[{"op":"replace","path":"$.spec.endpoints[?(@.name=="Controller")].port","value":30080}]}
```
Bsp. 2: Ersetzen von Speicher auf Steuerungsebene mit Patchdatei
```bash
azdata bdc config patch --path custom/control.json --patch ./patch.json

    Patch File Example (patch.json):
        {"patch":[{"op":"replace","path":".spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
Bsp. 3: Ersetzen von Poolspeicher, einschließlich Replikaten (Speicherpool), mit Patchdatei
```bash
azdata bdc config patch --path custom/bdc.json --patch ./patch.json

    Patch File Example (patch.json):
        {"patch":[{"op":"replace","path":"$.spec.resources.storage-0.spec","value":{"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}}]}
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--path`
Pfad für die Konfigurationsdatei eines Big Data-Clusters der Konfiguration, die Sie festlegen möchten, z. B. custom/cluster.json.
#### `--patch-file -p`
Pfad zu einer JSON-Patchdatei, die auf der JSONPATCH-Bibliothek basiert: http://jsonpatch.com/ Sie müssen die JSON-Patchdatei mit einem Schlüssel mit der Bezeichnung „Patch“ starten, bei dessen Wert es sich um ein Array von Patchvorgängen handelt, die Sie ausführen möchten. Für den Pfad eines Patchvorgangs können Sie für die meisten Vorgänge die Punktnotation verwenden, z. B. „key1.key2“. Wenn Sie einen „Ersetzen“-Vorgang durchführen möchten und einen Wert in einem Array ersetzen, das eine Bedingung erfordert, verwenden Sie die JSONPATH-Notation, indem Sie den Pfad mit einem Dollarzeichen („$“) beginnen. Dies ermöglicht die Verwendung einer Bedingung wie z. B. „$.key1.key2[?(@.key3=='someValue'].key4“. Siehe hierzu folgende Beispiele. Zusätzliche Hilfe zu Bedingungen finden Sie unter https://jsonpath.com/.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md). 

Weitere Informationen zur Installation des Tools **azdata** finden Sie unter [Installieren von azdata](..\install\deploy-install-azdata.md).

