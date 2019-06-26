---
title: Mssqlctl BDC-Config-Referenz
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl BDC-Befehle.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f57ba87ea7cbd770380497bd340b5eaa4d80f29c
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394162"
---
# <a name="mssqlctl-bdc-config"></a>Mssqlctl BDC-Konfiguration

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **BDC-Config** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[mssqlctl bdc config show](#mssqlctl-bdc-config-show) | Ruft die aktuelle Konfiguration für die Big Data-Cluster ab.
[mssqlctl bdc config init](#mssqlctl-bdc-config-init) | Initialisiert eine Big Data-Cluster erstellen Konfigurationsprofil, die mit dem Cluster verwendet werden kann.
[mssqlctl bdc config list](#mssqlctl-bdc-config-list) | Listet die verfügbaren Konfigurationsoptionen-Profil.
[mssqlctl bdc config section](reference-mssqlctl-bdc-config-section.md) | Befehle für die Arbeit mit einzelnen Abschnitte des Profils Big Data-Cluster.
## <a name="mssqlctl-bdc-config-show"></a>Mssqlctl Bdc-Konfiguration anzeigen
Ruft ab, der Big Data-Cluster des aktuellen Profils und gibt diesen in das Zielverzeichnis, oder gibt es ziemlich an der Konsole.
```bash
mssqlctl bdc config show [--target -t] 
                         [--force -f]
```
### <a name="examples"></a>Beispiele
Die BDC-Konfiguration in der Konsole anzeigen
```bash
mssqlctl bdc config show
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
## <a name="mssqlctl-bdc-config-init"></a>Mssqlctl BDC-Config-init
Initialisiert eine Big Data-Cluster erstellen Konfigurationsprofil, die mit dem Cluster verwendet werden kann. Die jeweiligen Quelle des Profils kann in den Argumenten von 3 Optionen angegeben werden.
```bash
mssqlctl bdc config init [--target -t] 
                         [--source -s]  
                         [--force -f]
```
### <a name="examples"></a>Beispiele
Praktische Anleitung für BDC-Config Init - Anweisungen für die erforderlichen Werte erhalten.
```bash
mssqlctl bdc config init
```
BDC-Config Init mit Argumenten, erstellt ein Konfigurationsprofil des Aks-Dev-Test-in. / benutzerdefinierte.
```bash
mssqlctl bdc config init --source aks-dev-test --target custom
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--target -t`
Dateipfad, in dem Sie die Config-Profil möchten platziert, der Standardwert ist Cwd mit benutzerdefinierten-"config.JSON".
#### `--source -s`
Profil-Konfigurationsquelle: ["Aks-Dev-Test", "Kubeadm-Dev-Test", "Minikube-Dev-Test"]
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
## <a name="mssqlctl-bdc-config-list"></a>Mssqlctl BDC-Config-Liste
Listet verfügbare Profil Konfigurationsoptionen für die Verwendung in `bdc config init`
```bash
mssqlctl bdc config list [--config-profile -c] 
                         
```
### <a name="examples"></a>Beispiele
Zeigt alle verfügbaren Konfigurationsoptionen-Profilnamen an.
```bash
mssqlctl bdc config list
```
Zeigt die JSON-Code des eines bestimmten Profils.
```bash
mssqlctl bdc config list --config-profile aks-dev-test
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--config-profile -c`
Config-Standardprofil: ["Aks-Dev-Test", "Kubeadm-Dev-Test", "Minikube-Dev-Test"]
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