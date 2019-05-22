---
title: Referenz für Mssqlctl Cluster-Konfiguration
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Cluster-Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 984a3c50ac691df3759edc161baabc533bd9456f
ms.sourcegitcommit: be09f0f3708f2e8eb9f6f44e632162709b4daff6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65993336"
---
# <a name="mssqlctl-cluster-config"></a>Konfiguration des mssqlctl-Clusters

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **cluster Config** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[mssqlctl cluster config show](#mssqlctl-cluster-config-show) | Ruft die SQL Server Big Data-Cluster des aktuellen Konfiguration ab.
[Mssqlctl Cluster Config init](#mssqlctl-cluster-config-init) | Initialisiert ein Profil der Cluster-Konfiguration, die mit dem Cluster verwendet werden kann erstellen.
[Liste der Mssqlctl Cluster-Konfiguration](#mssqlctl-cluster-config-list) | Listet die verfügbaren Konfigurationsoptionen für Datei.
[mssqlctl cluster config section](reference-mssqlctl-cluster-config-section.md) | Befehle für die Arbeit mit einzelnen Teile der Clusterkonfigurationsdatei.
## <a name="mssqlctl-cluster-config-show"></a>Mssqlctl Cluster-Konfiguration anzeigen
Ruft ab, der SQL Server Big Data-Cluster des aktuellen-Konfigurationsdatei und gibt diesen an die Zieldatei, oder gibt es ziemlich an der Konsole.
```bash
mssqlctl cluster config show [--target -t] 
                             [--force -f]
```
### <a name="examples"></a>Beispiele
Die Cluster-Konfiguration in der Konsole anzeigen
```bash
mssqlctl cluster config show
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--target -t`
Die Ausgabedatei zum Speichern des Ergebnisses in. Standardwert:, die an "stdout" weitergeleitet werden.
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
## <a name="mssqlctl-cluster-config-init"></a>Mssqlctl Cluster Config init
Initialisiert ein Profil der Cluster-Konfiguration, die mit dem Cluster verwendet werden kann erstellen. Die jeweiligen Quelle des Profils kann in den Argumenten von 3 Optionen angegeben werden.
```bash
mssqlctl cluster config init [--target -t] 
                             [--src -s]  
                             [--force -f]
```
### <a name="examples"></a>Beispiele
Praktische Anleitung für Cluster-Konfiguration Init - erhalten Sie Anweisungen für die erforderlichen Werte.
```bash
mssqlctl cluster config init
```
Cluster-Config-Init mit Argumenten, erstellt ein Konfigurationsprofil des Aks-Dev-Test-in. / custom.json.
```bash
mssqlctl cluster config init --src aks-dev-test.json --target custom.json
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--target -t`
Dateipfad, in dem Sie die Config-Profil möchten platziert, der Standardwert ist Cwd mit benutzerdefinierten-"config.JSON".
#### `--src -s`
Konfigurationsquelle-Profil: ["Aks-Dev-Test.json', ' Kubeadm-Dev-Test.json', ' Minikube-Dev-Test.json']
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
## <a name="mssqlctl-cluster-config-list"></a>Liste der Mssqlctl Cluster-Konfiguration
Listet die verfügbaren Datei Konfigurationsoptionen für die Verwendung bei der Initialisierung der Cluster-Konfiguration
```bash
mssqlctl cluster config list [--config-file -c] 
                             
```
### <a name="examples"></a>Beispiele
Zeigt alle verfügbaren Konfigurationsoptionen-Profilnamen an.
```bash
mssqlctl cluster config list
```
Zeigt die JSON-Code des eines bestimmten Profils.
```bash
mssqlctl cluster config list --config-file aks-dev-test.json
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--config-file -c`
Default config file: ['aks-dev-test.json', 'kubeadm-dev-test.json', 'minikube-dev-test.json']
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