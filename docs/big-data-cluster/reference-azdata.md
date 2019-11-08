---
title: Referenz zu azdata
titleSuffix: SQL Server big data clusters
description: Referenzartikel zu azdata-Befehlen.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4ef2ba9c68f3586e159c326863ef76ba231f01b9
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531649"
---
# <a name="azdata"></a>azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Der folgende Artikel enthält Referenzinformationen zu den `sql`-Befehlen im `azdata`-Tool. Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md).

## <a name="commands"></a>Befehle
|     |     |
| --- | --- |
|[azdata bdc](reference-azdata-bdc.md) | Auswählen, Verwalten und Betreiben von SQL Server-Big Data-Clustern. |
|[azdata app](reference-azdata-app.md) | Erstellen, Löschen, Ausführen und Verwalten von Anwendungen. |
[azdata login](#azdata-login) | Melden Sie sich beim Controllerendpunkt des Clusters an, und legen Sie seinen Namespace als aktiven Kontext fest. Sie müssen die Umgebungsvariable AZDATA_PASSWORD festlegen, um ein Kennwort für die Anmeldung zu verwenden.
[azdata logout](#azdata-logout) | Abmelden beim Cluster.
|[azdata-Kontext](reference-azdata-context.md) | Befehle für die Kontextverwaltung. |
|[azdata-Steuerelement](reference-azdata-control.md) | Erstellen, Entfernen und Verwalten von Steuerungsebenen |
|[azdata sql](reference-azdata-sql.md) | Die SQL-Datenbank-CLI ermöglicht dem Benutzer, über T-SQL mit SQL Server zu interagieren. |
|[azdata notebook](reference-azdata-notebook.md) | Befehle zum Anzeigen, Ausführen und Verwalten von Notebooks über ein Terminal. |
## <a name="azdata-login"></a>azdata login
Wenn Ihr Cluster bereitgestellt wird, wird der Controllerendpunkt während der Bereitstellung aufgelistet, den Sie für die Anmeldung verwenden sollten.  Wenn Sie den Controllerendpunkt nicht kennen, können Sie sich anmelden, wenn sich die Kube-Konfiguration Ihres Clusters auf Ihrem System am Standardspeicherort „<user home>/.kube/config“ befindet, oder Sie die KUBECONFIG-Umgebungsvariable verwenden, d.h. „KUBECONFIG=path/to/.kube/config“ exportieren.  Wenn Sie sich anmelden, wird der Namespace dieses Clusters als Ihr aktiver Kontext festgelegt.
```bash
azdata login [--auth] 
             [--endpoint -e]  
             [--accept-eula -a]  
             [--namespace -n]  
             [--username -u]  
             [--principal -p]
```
### <a name="examples"></a>Beispiele
Anmeldung mithilfe der Standardauthentifizierung
```bash
azdata login --auth basic --username johndoe --endpoint https://<ip or domain name>:30080            
```
Anmeldung mithilfe von Active Directory
```bash
azdata login --auth ad --endpoint https://<ip or domain name>:30080                
```
Anmeldung mithilfe von Active Directory mit einem expliziten Prinzipal
```bash
azdata login --auth ad --principal johndoe@COSTOSO.COM --endpoint https://<ip or domain name>:30080
```
Melden Sie sich interaktiv an. Der Clustername wird immer angefordert, wenn er nicht als Argument angegeben ist. Wenn Sie die Umgebungsvariablen AZDATA_USERNAME, AZDATA_PASSWORD und ACCEPT_EULA auf Ihrem System festgelegt haben, wird deren Eingabe nicht angefordert. Wenn sich die Kube-Konfiguration auf Ihrem System befindet, oder Sie mit der KUBECONFIG-Umgebungsvariablen den Pfad zur Konfiguration angeben, versucht die interaktive Benutzeroberfläche zunächst, die Konfiguration zu verwenden, und fordert Sie dann zur Eingabe auf, wenn bei der Konfiguration ein Fehler auftritt.
```bash
azdata login
```
Melden Sie sich an (nicht interaktiv). Melden Sie sich mit Clustername, Controllerbenutzername, Controllerendpunkt und EULA-Akzeptanzsatz als Argumente an. Die Umgebungsvariable AZDATA_PASSWORD muss festgelegt werden.  Wenn Sie den Controllerendpunkt nicht angeben möchten, sorgen Sie dafür, dass sich die Kube-Konfiguration auf Ihrem Computer am Standardspeicherort „<user home>/.kube/config“ befindet, oder verwenden Sie die KUBECONFIG-Umgebungsvariable, d.h. exportieren Sie „KUBECONFIG=path/to/.kube/config“.
```bash
azdata login --namespace ClusterName --username johndoe@contoso.com  --endpoint https://<ip or domain name>:30080 --accept-eula yes
```
Melden Sie sich mit der Kube-Konfiguration auf dem Computer an, und legen Sie die Umgebungsvariablen AZDATA_USERNAME, AZDATA_PASSWORD und ACCEPT_EULA fest.
```bash
azdata login -n ClusterName
```
### <a name="optional-parameters"></a>Optionale Parameter
#### `--auth`
Die Authentifizierungsstrategie. Standardauthentifizierung oder Active Directory-Authentifizierung. Standardwert ist die Standardauthentifizierung.
#### `--endpoint -e`
Clustercontroller-Endpunkt „https://host:port“. Wenn Sie dieses Argument nicht verwenden möchten, können Sie die Kube-Konfiguration auf Ihrem Computer verwenden. Stellen Sie sicher, dass sich die Konfiguration am Standardspeicherort „<user home>/.kube/config“ befindet, oder verwenden Sie die Umgebungsvariable KUBECONFIG.
#### `--accept-eula -a`
Stimmen Sie den Lizenzbedingungen zu? [yes/no]. Wenn Sie dieses Argument nicht verwenden möchten, können Sie die Umgebungsvariable ACCEPT_EULA auf „yes“ festlegen. Die Lizenzbedingungen für dieses Produkt finden Sie unter https://aka.ms/eula-azdata-en.
#### `--namespace -n`
Der Namespace der Clustersteuerungsebene
#### `--username -u`
Kontobenutzer. Wenn Sie dieses Argument nicht verwenden möchten, können Sie die Umgebungsvariable AZDATA_USERNAME festlegen.
#### `--principal -p`
Ihr Kerberos-Bereich In den meisten Fällen ist Ihr Kerberos-Bereich Ihr Domänenname in Großbuchstaben.
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.
## <a name="azdata-logout"></a>azdata logout
Abmelden beim Cluster.
```bash
azdata logout 
```
### <a name="examples"></a>Beispiele
Abmelden dieses Benutzers.
```bash
azdata logout
```
### <a name="global-arguments"></a>Globale Argumente
#### `--debug`
Ausführlichkeit der Protokollierung erhöhen, um alle Debugprotokolle anzuzeigen.
#### `--help -h`
Zeigen Sie diese Hilfemeldung an, und schließen Sie sie.
#### `--output -o`
Ausgabeformat.  Zulässige Werte: json, jsonc, table, tsv.  Standardwert: json.
#### `--query -q`
JMESPath-Abfragezeichenfolge. Weitere Informationen und Beispiele finden Sie unter [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Ausführlichkeit der Protokollierung erhöhen. „--debug“ für vollständige Debugprotokolle verwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu anderen `azdata`-Befehlen finden Sie in der [Referenz zu azdata](reference-azdata.md). Weitere Informationen zum Installieren des `azdata`-Tools finden Sie unter [Installieren von azdata zum Verwalten von Big Data-Clustern von SQL Server 2019](deploy-install-azdata.md).
