---
title: azdata-Steuerungs Referenz
titleSuffix: SQL Server big data clusters
description: Referenz Artikel zu azdata-Steuerungs Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2ce02ef0b212070b4a52944e055404137c78c98b
ms.sourcegitcommit: 0c6c1555543daff23da9c395865dafd5bb996948
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70304724"
---
# <a name="azdata-control"></a>azdata-Steuerelement

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Dieser Artikel ist ein Referenz Artikel für **azdata**. 

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
[azdata-Steuerelement erstellen](#azdata-control-create) | Erstellen Sie die Steuerungsebene.
[Löschen von azdata-Steuerelementen](#azdata-control-delete) | Löschen Sie die Steuerungsebene.
## <a name="azdata-control-create"></a>azdata-Steuerelement erstellen
Create Control Plane-Kube-Konfiguration ist auf Ihrem System zusammen mit den folgenden Umgebungsvariablen erforderlich [' CONTROLLER_USERNAME ', ' CONTROLLER_PASSWORD ', ' MSSQL_SA_PASSWORD ', ' KNOX_PASSWORD '].
```bash
azdata control create [--name -n] 
                      [--config-profile -c]  
                      [--accept-eula -a]  
                      [--node-label -l]  
                      [--force -f]
```
### <a name="examples"></a>Beispiele
Steuern der Bereitstellung.
```bash
azdata control create
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--name -n`
Der Name der Steuerungsebene, der für kubernetes-Namespaces verwendet wird.
#### `--config-profile -c`
Cluster Konfigurations Profil, das zum Bereitstellen des Clusters verwendet wird: [' AKS-dev-Test ', ' kubeadm-Prod ', ' minikube-dev-Test ', ' kubeadm-dev-Test ']
#### `--accept-eula -a`
Stimmen Sie den Lizenzbedingungen zu? [yes/no]. Wenn Sie dieses Argument nicht verwenden möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf „yes“ festlegen. 
#### `--node-label -l`
Knoten Bezeichnung, die verwendet wird, um anzugeben, für welche Knoten bereitgestellt werden soll.
#### `--force -f`
Das Erstellen wird erzwungen. Der Benutzer wird nicht zur Eingabe von Werten aufgefordert, und alle Probleme werden über stderr ausgegeben.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-control-delete"></a>Löschen von azdata-Steuerelementen
DELETE Control Plane-Kube-Konfiguration ist auf dem System erforderlich.
```bash
azdata control delete --name -n 
                      [--force -f]
```
### <a name="examples"></a>Beispiele
Steuern der Bereitstellung.
```bash
azdata control delete
```
### <a name="required-parameters"></a>Erforderliche Parameter
#### `--name -n`
Name der Steuerungsebene, der für den kubernetes-Namespace verwendet wird.
### <a name="optional-parameters"></a>Optionale Parameter
#### `--force -f`
Erzwingen der Steuerungsebene "Löschen".
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu anderen **azdata**-Befehlen finden Sie unter [azdata](reference-azdata.md). 

- Weitere Informationen zum Installieren des Tools **azdata** finden Sie unter [Install azdata to manage SQL Server 2019 big data clusters (Installieren von azdata zum Verwalten von Big-Data-Clustern von SQL Server 2019)](deploy-install-azdata.md).
