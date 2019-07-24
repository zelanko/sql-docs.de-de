---
title: azdata BDC-Konfigurations Referenz
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu azdata BDC-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ed777391af3695da69e04c0e2693cff912c76771
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426290"
---
# <a name="azdata-bdc-config"></a>azdata-BDC-Konfiguration

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel enthält einen Verweis auf die **BDC-Konfigurations** Befehle im **azdata** -Tool. Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata BDC config init](#azdata-bdc-config-init) | Initialisiert ein Big Data-Cluster Konfigurations Profil, das mit der Cluster Erstellung verwendet werden kann.
[azdata-BDC-Konfigurations Liste](#azdata-bdc-config-list) | Listet die verfügbaren Konfigurations Profil Optionen auf.
[azdata BDC config Show](#azdata-bdc-config-show) | Zeigt die aktuelle Konfiguration des BDC oder die Konfiguration einer lokalen Datei an, die Sie angeben, z. b. "Custom"/"Cluster. JSON".
[azdata-BDC-Konfiguration hinzufügen](#azdata-bdc-config-add) | Fügen Sie einen Wert für einen JSON-Pfad in einer Konfigurationsdatei hinzu.
[azdata-BDC-Konfiguration entfernen](#azdata-bdc-config-remove) | Entfernen Sie einen Wert für einen JSON-Pfad in einer Konfigurationsdatei.
[azdata-BDC-Konfiguration ersetzen](#azdata-bdc-config-replace) | Ersetzen Sie einen Wert für einen JSON-Pfad in einer Konfigurationsdatei.
[Konfigurations Patch für azdata-BDC](#azdata-bdc-config-patch) | Patcht eine Konfigurationsdatei auf der Grundlage einer JSON-Patchdatei.
## <a name="azdata-bdc-config-init"></a>azdata BDC config init
Initialisiert ein Big Data-Cluster Konfigurations Profil, das mit der Cluster Erstellung verwendet werden kann. Die jeweilige Quelle des Konfigurations Profils kann in den Argumenten aus drei Optionen angegeben werden.
```bash
azdata bdc config init [--target -t] 
                       [--source -s]  
                       [--force -f]  
                       [--accept-eula -a]
```
### <a name="examples"></a>Beispiele
Geleitete BDC config Init-Funktion: Sie erhalten Eingabe Aufforderungen für erforderliche Werte.
```bash
azdata bdc config init
```
BDC config init with Arguments erstellt ein Konfigurations Profil von AKS-dev-Test in./Custom.
```bash
azdata bdc config init --source aks-dev-test --target custom
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--target -t`
Der Dateipfad, in dem das Konfigurations Profil platziert werden soll. der Standardwert ist CWD mit "Custom-config. JSON".
#### `--source -s`
Quelle des Konfigurations Profils: [' AKS-dev-Test ', ' kubeadm-dev-Test ', ' minikube-dev-Test ']
#### `--force -f`
Erzwingen Sie das Überschreiben der Zieldatei.
#### `--accept-eula -a`
Akzeptieren Sie die Lizenzbedingungen? [Ja/Nein]. Wenn Sie dieses arg nicht verwenden möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf "yes" festlegen. Die Lizenzbedingungen für dieses Produkt können unter https://aka.ms/azdata-eula angezeigt werden.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-config-list"></a>azdata-BDC-Konfigurations Liste
Listet verfügbare Konfigurations Profil Optionen für die Verwendung in auf`bdc config init`
```bash
azdata bdc config list [--config-profile -c] 
                       [--type -t]  
                       [--accept-eula -a]
```
### <a name="examples"></a>Beispiele
Zeigt alle verfügbaren Konfigurations Profilnamen an.
```bash
azdata bdc config list
```
Zeigt JSON eines bestimmten Konfigurations Profils an.
```bash
azdata bdc config list --config-profile aks-dev-test
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--config-profile -c`
Standardmäßiges Konfigurations Profil: [' AKS-dev-Test ', ' kubeadm-dev-Test ', ' minikube-dev-Test ']
#### `--type -t`
Welcher Konfigurationstyp Sie sehen möchten.
`cluster`
#### `--accept-eula -a`
Akzeptieren Sie die Lizenzbedingungen? [Ja/Nein]. Wenn Sie dieses arg nicht verwenden möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf "yes" festlegen. Die Lizenzbedingungen für dieses Produkt können unter https://aka.ms/azdata-eula angezeigt werden.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-config-show"></a>azdata BDC config Show
Zeigt die aktuelle Konfiguration des BDC oder die Konfiguration einer lokalen Datei an, die Sie angeben, z. b. "Custom"/"Cluster. JSON". Der Befehl kann auch einen JSON-Pfad annehmen, wenn Sie nur einen Abschnitt erhalten möchten.  Sie können auch eine Zieldatei angeben, in die die Ausgabe ausgegeben werden soll.  Wenn keine Zieldatei angegeben ist, wird Sie nur an das Terminal ausgegeben.
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
In einer lokalen Konfigurationsdatei erhalten Sie einen Wert am Ende eines einfachen JSON-Schlüssel Pfads.
```bash
azdata bdc config show --config-file custom-config/cluster.json --json-path 'metadata.name' --target section.json
```
Ruft in einer lokalen Konfigurationsdatei einen Wert am Ende eines JSON-Schlüssel Pfads mit einem bedingten ab.
```bash
azdata bdc config show --config-file custom-config/cluster.json  --json-path '$.spec.pools[?(@.spec.type=="Storage")].spec' --target section.json
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--config-file -c`
Dateipfad für Big Data-Cluster Konfigurationsdatei, wenn Sie nicht möchten, dass die Konfiguration des Clusters, in dem Sie currentlyangemeldet sind, d. h. Benutzer definiert/Cluster. JSON
#### `--target -t`
Ausgabedatei, in der das Ergebnis gespeichert werden soll. Standard: wird an stdout weitergeleitet.
#### `--json-path -j`
Der JSON-Schlüssel Pfad, der zu dem von der Konfiguration gewünschten Abschnitt oder Wert führt, d. h. key1. key2. key3. Verwendet die Abfragesprache jsonpath, https://jsonpath.com/ z. b.:-j ' $. spec. Pools [? ( @.spec.type = = "Master")].. Endpunkte
#### `--force -f`
Erzwingen Sie das Überschreiben der Zieldatei.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-config-add"></a>azdata-BDC-Konfiguration hinzufügen
Fügt den Wert im JSON-Pfad in der Konfigurationsdatei hinzu.  Alle nachfolgenden Beispiele sind in bash angegeben.  Wenn Sie eine andere Befehlszeile verwenden, beachten Sie bitte, dass Sie möglicherweise eine angemessene escapesequnungen durchführen müssen.  Alternativ dazu können Sie auch die patchdateifunktionen verwenden.
```bash
azdata bdc config add --config-file -c 
                      --json-values -j
```
### <a name="examples"></a>Beispiele
1\. Fügen Sie den Speicher der Steuerungsebene hinzu.
```bash
azdata bdc config add --config-file custom/control.json --json-values 'spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--config-file -c`
Big Data-Cluster Konfigurationsdateipfad der Konfiguration, die Sie festlegen möchten, z. b. "Custom"/"Cluster. JSON"
#### `--json-values -j`
Eine Schlüssel-Wert-Paar-Liste von JSON-Pfaden zu Werten: key1. SubKey1 = value1, key2. subkey2 = Value2. Sie können JSON-Inline Werte angeben, z. b.: Key = ' {"Kind": "Cluster", "Name": "Test-Cluster"} "oder einen Dateipfad angeben, z. b. Key =./Values.JSON. Add bietet keine Unterstützung für Conditionals.  http://jsonpatch.com/ Beispiele dazu, wie ihr Pfad aussehen sollte, finden Sie unter.  Wenn Sie auf ein Array zugreifen möchten, müssen Sie dazu den Index angeben, z. b. Key. 0 = Value.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-config-remove"></a>azdata-BDC-Konfiguration entfernen
Entfernt den Wert im JSON-Pfad in der Konfigurationsdatei.  Alle nachfolgenden Beispiele sind in bash angegeben.  Wenn Sie eine andere Befehlszeile verwenden, beachten Sie bitte, dass Sie möglicherweise eine angemessene escapesequnungen durchführen müssen.  Alternativ dazu können Sie auch die patchdateifunktionen verwenden.
```bash
azdata bdc config remove --config-file -c 
                         --json-path -j
```
### <a name="examples"></a>Beispiele
Ex 1: Entfernen Sie den Speicher der Steuerungsebene.
```bash
azdata bdc config remove --config-file custom/control.json --json-path '.spec.storage'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--config-file -c`
Big Data-Cluster Konfigurationsdateipfad der Konfiguration, die Sie festlegen möchten, z. b. "Custom"/"Cluster. JSON"
#### `--json-path -j`
Eine Liste von JSON-Pfaden, die auf der jsonpatch-Bibliothek basiert und angibt, welche Werte entfernt werden sollen, z. b.: key1. SubKey1, key2. subkey2. Remove unterstützt keine Conditionals. http://jsonpatch.com/ Beispiele dazu, wie ihr Pfad aussehen sollte, finden Sie unter.  Wenn Sie auf ein Array zugreifen möchten, müssen Sie dazu den Index angeben, z. b. Key. 0 = Value.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-config-replace"></a>azdata-BDC-Konfiguration ersetzen
Ersetzt den Wert im JSON-Pfad in der Konfigurationsdatei.  Alle examplesbelow werden in bash angegeben.  Wenn Sie eine andere Befehlszeile verwenden, beachten Sie bitte, dass Sie möglicherweise eine angemessene escapesequnungen durchführen müssen.  Alternativ dazu können Sie auch die patchdateifunktionen verwenden.
```bash
azdata bdc config replace --config-file -c 
                          --json-values -j
```
### <a name="examples"></a>Beispiele
Ex 1-ersetzen Sie den Port eines einzelnen Endpunkts (Controller Endpunkt).
```bash
azdata bdc config replace --config-file custom/control.json --json-values '$.spec.endpoints[?(@.name=="Controller")].port=30080'
```
2\. ersetzen Sie den Speicher der Steuerungsebene.
```bash
azdata bdc config replace --config-file custom/control.json --json-values 'spec.storage={"accessMode":"ReadWriteOnce","className":"managed-premium","size":"10Gi"}'
```
3\. ersetzen Sie den Pool Speicher, einschließlich Replikate (Speicherpool).
```bash
azdata bdc config replace --config-file custom/cluster.json --json-values '$.spec.pools[?(@.spec.type == "Storage")].spec={"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}'
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--config-file -c`
Big Data-Cluster Konfigurationsdateipfad der Konfiguration, die Sie festlegen möchten, z. b. "Custom"/"Cluster. JSON"
#### `--json-values -j`
Eine Schlüssel-Wert-Paar-Liste von JSON-Pfaden zu Werten: key1. SubKey1 = value1, key2. subkey2 = Value2. Sie können JSON-Inline Werte angeben, z. b.: Key = ' {"Kind": "Cluster", "Name": "Test-Cluster"} "oder einen Dateipfad angeben, z. b. Key =./Values.JSON. Replace unterstützt Bedingungen durch die jsonpath-Bibliothek.  Um dies zu verwenden, starten Sie den Pfad mit "$". Auf diese Weise können Sie eine bedingte Bedingung wie z. b.-j $. key1. key2 [? ( @.key3= = ' someValue ']. key4 = Value. Möglicherweise werden unten Beispiele angezeigt. Weitere Informationen finden Sie unter: https://jsonpath.com/
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.
## <a name="azdata-bdc-config-patch"></a>Konfigurations Patch für azdata-BDC
Patcht die Konfigurationsdatei entsprechend der angegebenen Patchdatei. http://jsonpatch.com/ Weitere Informationen zur Zusammensetzung der Pfade finden Sie unter. Der Replace-Vorgang kann Bedingungen in seinem Pfad aufgrund der jsonpath-Bibliothek https://jsonpath.com/ verwenden. Alle Patch-JSON-Dateien müssen mit dem Schlüssel "Patch" beginnen, der über ein Array von Patches mit dem entsprechenden op (hinzufügen, ersetzen, entfernen), Pfad und Wert verfügt. Der "Remove"-op erfordert keinen Wert, sondern nur einen Pfad. Weitere Informationen finden Sie in den folgenden Beispielen.
```bash
azdata bdc config patch --config-file -c 
                        --patch-file -p
```
### <a name="examples"></a>Beispiele
Ex 1-ersetzen Sie den Port eines einzelnen Endpunkts (Controller Endpunkt) durch eine Patchdatei.
```bash
azdata bdc config patch --config-file custom/control.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.endpoints[?(@.name=='Controller')].port","value":30080}]}
```
2\. ersetzen Sie den Speicher der Steuerungsebene durch die Patchdatei.
```bash
azdata bdc config patch --config-file custom/control.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":".spec.storage","value":{"accessMode":"ReadWriteMany","className":"managed-premium","size":"10Gi"}}]}
```
3\. ersetzen Sie den Pool Speicher, einschließlich Replikate (Speicherpool), durch die Patchdatei.
```bash
azdata bdc config patch --config-file custom/cluster.json --patch ./patch.json

    Patch File Example (patch.json): 
        {"patch":[{"op":"replace","path":"$.spec.pools[?(@.spec.type == 'Storage')].spec","value":{"replicas": 2,"storage": {"className": "managed-premium","size": "10Gi","accessMode": "ReadWriteOnce"},"type": "Storage"}}]}
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--config-file -c`
Big Data-Cluster Konfigurationsdateipfad der Konfiguration, die Sie festlegen möchten, z. b. "Custom"/"Cluster. JSON"
#### `--patch-file -p`
Pfad zu einer JSON-Patchdatei, die auf der jsonpatch-Bibliothek http://jsonpatch.com/ basiert:. Sie müssen die Patch-JSON-Datei mit einem Schlüssel namens "Patch" starten, dessen Wert ein Array von patchvorgängen ist, die Sie vornehmen möchten. Für den Pfad eines Patchvorgangs können Sie für die meisten Vorgänge die Punkt Notation verwenden, z. b. key1. key2. Wenn Sie einen Replace-Vorgang durchführen möchten und einen Wert in einem Array ersetzen, das eine bedingte Bedingung erfordert, verwenden Sie die jsonpath-Notation, indem Sie Ihren Pfad mit einem $ beginnen. Auf diese Weise können Sie eine bedingte, z. b. $. key1. key2 [? ( @.key3= = ' someValue ']. key4. Weitere Informationen finden Sie in den folgenden Beispielen. Weitere Informationen zu Bedingungen finden Sie unter: https://jsonpath.com/.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Erhöhen Sie die Protokollierungs Ausführlichkeit, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Diese Hilfe Meldung anzeigen und beenden.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: JSON, jsonc, Table, TSV.  Standardwert: JSON.
#### `--query -q`
Jmespath-Abfrage Zeichenfolge. Weitere [http://jmespath.org/](http://jmespath.org/]) Informationen und Beispiele finden Sie unter.
#### `--verbose`
Erhöhen Sie die Protokollierungs Ausführlichkeit. Verwenden Sie "--Debug" für vollständige Debugprotokolle.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen **azdata** -Befehlen finden Sie unter [azdata-Referenz](reference-azdata.md). Weitere Informationen zum Installieren des Tools **azdata** finden [Sie unter Install azdata to Manage SQL Server 2019 Big Data Clusters](deploy-install-azdata.md).