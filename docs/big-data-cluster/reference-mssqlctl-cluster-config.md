---
title: Referenz für Mssqlctl Cluster-Konfiguration
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl Cluster-Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 3a4693c5ffb68ad555d97d02f983fadf4e6bbd9a
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473293"
---
# <a name="mssqlctl-cluster-config"></a>Konfiguration des mssqlctl-Clusters

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **cluster Config** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[mssqlctl cluster config get](#mssqlctl-cluster-config-get) | Abrufen von Cluster-Konfiguration – Kube Konfiguration ist erforderlich, auf dem System.
[Mssqlctl Cluster Config init](#mssqlctl-cluster-config-init) | Initialisiert eine Clusterkonfiguration.
[Liste der Mssqlctl Cluster-Konfiguration](#mssqlctl-cluster-config-list) | Listet die verfügbaren Konfigurationsoptionen für Datei.
[mssqlctl cluster config section](reference-mssqlctl-cluster-config-section.md) | Befehle für die Arbeit mit einzelnen Abschnitte der Konfigurationsdatei.
## <a name="mssqlctl-cluster-config-get"></a>Mssqlctl Cluster-Konfiguration zu erhalten.
Ruft die SQL Server Big Data-Cluster des aktuellen der Konfigurationsdatei ab.
```bash
mssqlctl cluster config get --name -n 
                            [--output-file -f]
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Clustername für Kubernetes-Namespace verwendet.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--output-file -f`
Die Ausgabedatei zum Speichern des Ergebnisses in. Standardwert:, die an "stdout" weitergeleitet werden.
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
Initialisiert eine Cluster-Konfigurationsdatei für den Benutzer basierend auf den angegebenen Typ.
```bash
mssqlctl cluster config init [--target -t] 
                             [--src -s]
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--target -t`
Der Dateipfad der, in dem Sie die Config-Datei eingefügt, der Standardwert ist Cwd mit benutzerdefinierten-config.json möchten.
#### `--src -s`
Konfigurationsquelle: ["Aks-Dev-Test.json', ' Kubeadm-Dev-Test.json', ' Minikube-Dev-Test.json']
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
mssqlctl cluster config list [--config-file -f] 
                             
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--config-file -f`
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