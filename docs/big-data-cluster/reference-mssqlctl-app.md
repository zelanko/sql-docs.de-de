---
title: Referenz zu app mssqlctl
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Mssqlctl app Befehle.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 850964adc9cd790a27cf69e3e0f5229cdaf589c8
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64775207"
---
# <a name="mssqlctl-app"></a>mssqlctl-App

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **app** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Mssqlctl-app-Vorlage](reference-mssqlctl-app-template.md) | Vorlagen.
[Mssqlctl app init](#mssqlctl-app-init) | KickStart neue Anwendung Gerüst.
[Mssqlctl-app erstellen](#mssqlctl-app-create) | Erstellen Sie die Anwendung.
[Aktualisieren der Mssqlctl-app](#mssqlctl-app-update) | Aktualisieren Sie die Anwendung.
[Mssqlctl app-Liste](#mssqlctl-app-list) | Auflisten von Anwendungen.
[mssqlctl app delete](#mssqlctl-app-delete) | Löschen Sie die Anwendung.
[Mssqlctl-app-Ausführung](#mssqlctl-app-run) | Führen Sie die Anwendung.
[mssqlctl app describe](#mssqlctl-app-describe) | Beschreiben Sie die Anwendung.
## <a name="mssqlctl-app-init"></a>Mssqlctl app init
Können Sie neue Anwendung-Gerüst Kickstart bzw. Spec-Dateien basierend auf Laufzeitumgebungen.
```bash
mssqlctl app init [--spec -s] 
                  [--name -n]  
                  [--version -v]  
                  [--template -t]  
                  [--destination -d]  
                  [--url -u]
```
### <a name="examples"></a>Beispiele
Erstellen des Gerüsts für einer neuen Anwendung `spec.yaml` nur.
```bash
mssqlctl app init --spec
```
Erstellen des Gerüsts für eine neue R-Anwendung Anwendung Gerüst basierend auf den `r` Vorlage.
```bash
mssqlctl app init --name reduce --template r
```
Erstellen ein neues Python-Anwendung Anwendung Gerüsts basierend auf den `python` Vorlage.
```bash
mssqlctl app init --name reduce --template python
```
Erstellen Sie ein neues SSIS-Anwendung Anwendung Grundgerüst basierend auf den `ssis` Vorlage.
```bash
mssqlctl app init --name reduce --template ssis            
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--spec -s`
Generieren Sie nur eine Anwendung spec.yaml.
#### `--name -n`
Anwendungsname
#### `--version -v`
Version der Anwendung.
#### `--template -t`
Name der Vorlage. Eine vollständige Liste deaktiviert unterstützten Vorlagennamen ausführen `mssqlctl app template list`
#### `--destination -d`
Die Position, um das Gerüst für die Anwendung zu platzieren. Standard: Aktuelles Arbeitsverzeichnis.
#### `--url -u`
Geben Sie einen andere Vorlage Repository-Speicherort. Standardwert: https://github.com/Microsoft/SQLBDC-AppDeploy.git
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
## <a name="mssqlctl-app-create"></a>Mssqlctl-app erstellen
Erstellen einer Anwendung.
```bash
mssqlctl app create --spec -s 
                    
```
### <a name="examples"></a>Beispiele
Erstellen Sie eine neue Anwendung aus einem Verzeichnis mit einer gültigen spec.yaml Bereitstellung-Spezifikation.
```bash
mssqlctl app create --spec /path/to/dir/with/spec/yaml
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--spec -s`
Der Pfad zu einem Verzeichnis mit einer Spezifikation YAML-Datei, die die Anwendung beschreibt.
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
## <a name="mssqlctl-app-update"></a>Aktualisieren der Mssqlctl-app
Aktualisieren einer Anwendung.
```bash
mssqlctl app update [--spec -s] 
                    [--yes -y]
```
### <a name="examples"></a>Beispiele
Aktualisieren Sie eine vorhandene Anwendung aus einem Verzeichnis mit einer gültigen spec.yaml Bereitstellung-Spezifikation.
```bash
mssqlctl app update --spec /path/to/dir/with/spec/yaml    
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--spec -s`
Der Pfad zu einem Verzeichnis mit einer Spezifikation YAML-Datei, die die Anwendung beschreibt.
#### `--yes -y`
Keine Aufforderung zur Bestätigung bei der Aktualisierung einer Anwendung aus der CWD spec.yaml-Datei.
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
## <a name="mssqlctl-app-list"></a>Mssqlctl app-Liste
Auflisten einer Anwendung(en).,
```bash
mssqlctl app list [--name -n] 
                  [--version -v]
```
### <a name="examples"></a>Beispiele
Listen Sie die Anwendung nach Name und Version.
```bash
mssqlctl app list --name reduce  --version v1
```
Alle Anwendungsprogrammversionen nach Name auflisten.
```bash
mssqlctl app list --name reduce
```
Alle Anwendungsprogrammversionen nach Name auflisten.
```bash
mssqlctl app list
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--name -n`
Anwendungsname
#### `--version -v`
Version der Anwendung.
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
## <a name="mssqlctl-app-delete"></a>Mssqlctl app löschen
Eine Anwendung zu löschen.
```bash
mssqlctl app delete --name -n 
                    --version -v
```
### <a name="examples"></a>Beispiele
Löschen Sie die Anwendung nach Name und Version.
```bash
mssqlctl app delete --name reduce --version v1    
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Anwendungsname
#### `--version -v`
Version der Anwendung.
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
## <a name="mssqlctl-app-run"></a>Mssqlctl-app-Ausführung
Eine Anwendung ausführen.
```bash
mssqlctl app run --name -n 
                 --version -v  
                 [--inputs]
```
### <a name="examples"></a>Beispiele
Führen Sie Anwendung ohne Eingabeparameter aus.
```bash
mssqlctl app run --name reduce --version v1
```
Führen Sie Anwendung mit 1 Eingabeparameter an.
```bash
mssqlctl app run --name reduce --version v1 --inputs x=10
```
Die Anwendung mit mehreren Eingabeparametern ausführen.
```bash
mssqlctl app run --name reduce --version v1 --inputs x=10,y5.6    
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Anwendungsname
#### `--version -v`
Version der Anwendung.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--inputs`
Parameter in eine CSV-Datei der eingabeanwendung `name=value` Format.
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
## <a name="mssqlctl-app-describe"></a>Beschreiben Sie Mssqlctl-app
Beschreiben einer Anwendung.
```bash
mssqlctl app describe [--spec -s] 
                      [--name -n]  
                      [--version -v]
```
### <a name="examples"></a>Beispiele
Eine Beschreibung der Anwendung.
```bash
mssqlctl app describe --name reduce --version v1    
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--spec -s`
Der Pfad zu einem Verzeichnis mit einer Spezifikation YAML-Datei, die die Anwendung beschreibt.
#### `--name -n`
Anwendungsname
#### `--version -v`
Version der Anwendung.
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