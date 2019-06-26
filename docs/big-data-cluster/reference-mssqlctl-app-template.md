---
title: Referenz zu Mssqlctl app-Vorlagen
titleSuffix: SQL Server big data clusters
description: Der Referenzartikel für die Befehle für Mssqlctl app-Vorlage.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 20d8b332643c9ef749aae5be0ab9e778a593d6ff
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67388185"
---
# <a name="mssqlctl-app-template"></a>mssqlctl-App-Vorlage

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Der folgende Artikel bietet Referenz für die **-app-Vorlage** Befehle in der **Mssqlctl** Tool. Weitere Informationen zu anderen **Mssqlctl** Befehle finden Sie unter [Mssqlctl Verweis](reference-mssqlctl.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[Liste der Mssqlctl app-Vorlage](#mssqlctl-app-template-list) | Rufen Sie die unterstützte Vorlagen.
[Mssqlctl app-Vorlage pull](#mssqlctl-app-template-pull) | Download unterstützt Vorlagen.
## <a name="mssqlctl-app-template-list"></a>Liste der Mssqlctl app-Vorlage
Rufen Sie die unterstützten Vorlagen unter dem angegebenen [URL]-Github-Repository.
```bash
mssqlctl app template list [--url -u] 
                           
```
### <a name="examples"></a>Beispiele
Rufen Sie alle Vorlagen unter dem Standardspeicherort des Repositorys Vorlage.
```bash
mssqlctl app template list
```
Rufen Sie alle Vorlagen unter einem anderen Repository-Speicherort ab.
```bash
mssqlctl app template list --url https://github.com/diffrent/templates.git
```
### <a name="optional-parameters"></a>Optionale Parameter
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
## <a name="mssqlctl-app-template-pull"></a>Mssqlctl app-Vorlage pull
Laden Sie die unterstützten Vorlagen unter dem angegebenen [URL]-Github-Repository herunter.
```bash
mssqlctl app template pull [--name -n] 
                           [--url -u]  
                           [--destination -d]
```
### <a name="examples"></a>Beispiele
Laden Sie alle Vorlagen unter dem Standardspeicherort des Repositorys Vorlage herunter.
```bash
mssqlctl app template pull
```
Laden Sie alle Vorlagen unter einem anderen Repository-Speicherort herunter.
```bash
mssqlctl app template list --url https://github.com/diffrent/templates.git
```
Laden Sie einzelne Vorlage anhand des Namens.
```bash
mssqlctl app template pull --name ssis            
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--name -n`
Name der Vorlage. Eine vollständige Liste deaktiviert unterstützten Vorlage namesrun `mssqlctl app template list`
#### `--url -u`
Geben Sie einen andere Vorlage Repository-Speicherort. Standardwert: https://github.com/Microsoft/SQLBDC-AppDeploy.git
#### `--destination -d`
Position, an die Skelett-Anwendungsvorlage platzieren.
`./templates`
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