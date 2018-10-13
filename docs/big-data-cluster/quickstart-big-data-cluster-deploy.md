---
title: Bereitstellen von SQL Server-big Data-Cluster | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: quickstart
ms.prod: sql
ms.openlocfilehash: 5781b3acfd2262b3a3be540abb331839dfcc56c6
ms.sourcegitcommit: 08b3de02475314c07a82a88c77926d226098e23f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49120457"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Schnellstart: Bereitstellen von SQL Server-big Data-Cluster in Azure Kubernetes Service (AKS)

In dieser schnellstartanleitung installieren Sie SQL Server-big Data-Cluster in AKS in einer Standardkonfiguration für Entwicklungs-/testumgebungen geeignet ist. Zusätzlich zum Master für SQL-Instanz umfasst der Cluster einer Compute-Pool-Instanz, eine Pool-Instanz und zwei Instanzen von Speicher-Pool. Daten werden beibehalten, über persistente Kubernetes-Volumes, die zusätzlich zu AKS Standard Storage-Klassen bereitgestellt werden. In der [bereitstellungsanleitung](deployment-guidance.md) Thema finden Sie eine Reihe von Umgebungsvariablen, die Sie verwenden können, die Konfiguration anpassen.

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>Erforderliche Komponenten

Diese schnellstartanleitung müssen Sie bereits einen AKS-Cluster mit einer Mindestversion v1.10 konfiguriert haben. Weitere Informationen finden Sie unter den [Bereitstellen in AKS](deploy-on-aks.md) Guide.

Auf dem Computer, die Sie zum Ausführen der Befehle zum Installieren der SQL Server-big Data-Cluster verwenden, müssen Sie installieren ["kubectl"](https://kubernetes.io/docs/tasks/tools/install-kubectl/). SQL Server-big Data-Cluster die Mindestversion 1,10 für Kubernetes, für Server und Client (Kubectl). Um "kubectl" zu installieren, finden Sie unter [Installieren von Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). 

So installieren Sie die `mssqlctl` CLI-Tool zum Verwalten von SQL Server-Big-Data-cluster auf dem Clientcomputer, müssen Sie zunächst installieren [Python](https://www.python.org/downloads/) Mindestversion v3. 0 und [pip3](https://pip.pypa.io/en/stable/installing/). Beachten Sie, dass Pip bereits installiert ist, bei Verwendung eine Python-Version von mindestens 3.4 heruntergeladen [python.org](https://www.python.org/).

Wenn die Python-Installation fehlt die `requests` -Paket, die Sie installieren müssen `requests` mit `python -m pip install requests`. Wenn Sie bereits haben eine `requests` Paket aktualisieren sie auf die neueste Version mithilfe `python -m pip install requests --upgrade`.

## <a name="verify-aks-configuration"></a>Überprüfen der AKS-Konfiguration

Nachdem Sie den AKS-Cluster bereitgestellt haben, können Sie Ausführen der folgenden Befehl aus "kubectl", um die Clusterkonfiguration anzuzeigen. Stellen Sie sicher, dass diese "kubectl" auf den richtigen Clusterkontext gezeigt wird.

```bash
kubectl config view
```

## <a name="install-mssqlctl-cli-management-tool"></a>Installieren Sie CLI-Verwaltungstool mssqlctl

Führen Sie den folgenden Befehl zum Installieren von `mssqlctl` Tool auf dem Clientcomputer. Dieselben Befehl funktioniert von einer Windows und Linux-Client, jedoch stellen Sie sicher, dass Sie es in einem Cmd-Fenster, das mit administrativen Berechtigungen für Windows ausgeführt wird oder Sie als Präfix mit `sudo` für Linux:

```
pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl  
```

## <a name="define-environment-variables"></a>Definieren von Umgebungsvariablen

Festlegen der Umgebungsvariablen, die für die Bereitstellung von big Data-Cluster leicht, hängt davon ab, ob Sie Windows oder Linux/MacOS-Client verwenden.  Wählen Sie die folgenden Schritte aus je nach verwendetem, die Betriebssystem Sie verwenden.

Beachten Sie bevor Sie fortfahren die folgenden wichtigen Richtlinien:

- Stellen Sie sicher, dass Sie die Kennwörter in doppelte Anführungszeichen umschließen, wenn sie keine Sonderzeichen enthält. Beachten Sie, die doppelte Anführungszeichen Trennzeichen funktionieren nur in der bash-Befehle.
- Sie können das Kennwort Umgebungsvariablen festlegen, um einen beliebigen Namen, aber stellen Sie sicher, dass sie ausreichend komplex sind und verwenden Sie nicht die `!`, `&`, oder `‘` Zeichen.
- Ändern Sie bei der Version CTP 2.0 nicht die Standardports.
- Die **SA** Konto ist ein Systemadministrator für die Master für SQL Server-Instanz, die während des Setups erstellt wird. Nachdem erstellen Ihre SQL Server-Container, die MSSQL_SA_PASSWORD-Umgebungsvariable, die Sie angegeben haben erkennbar ausgeführt ist echo $MSSQL_SA_PASSWORD im Container. Ändern Sie aus Sicherheitsgründen Ihr SA-Kennwort gemäß der dokumentierten bewährten Methoden [hier](https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

Die folgenden Umgebungsvariablen zu initialisieren.  Sie sind für die Bereitstellung von big Data-Cluster erforderlich:

### <a name="windows"></a>Windows

Verwenden ein Befehlsfenster (nicht PowerShell), konfigurieren Sie die folgenden Umgebungsvariablen:

```cmd
SET ACCEPT_EULA=Y
SET CLUSTER_PLATFORM=aks

SET CONTROLLER_USERNAME=<controller_admin_name – can be anything>
SET CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
SET KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
SET MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

SET DOCKER_REGISTRY=private-repo.microsoft.com
SET DOCKER_REPOSITORY=mssql-private-preview
SET DOCKER_USERNAME=<your username, credentials provided by Microsoft>
SET DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
SET DOCKER_EMAIL=<your Docker email, use the username provided by Microsoft>
SET DOCKER_PRIVATE_REGISTRY="1"
```

### <a name="linuxmacos"></a>Linux/macOS

Initialisieren Sie die folgenden Umgebungsvariablen:

```bash
export ACCEPT_EULA=Y
export CLUSTER_PLATFORM=aks

export CONTROLLER_USERNAME=<controller_admin_name – can be anything>
export CONTROLLER_PASSWORD=<controller_admin_password – can be anything, password complexity compliant>
export KNOX_PASSWORD=<knox_password – can be anything, password complexity compliant>
export MSSQL_SA_PASSWORD=<sa_password_of_master_sql_instance, password complexity compliant>

export DOCKER_REGISTRY=private-repo.microsoft.com
export DOCKER_REPOSITORY=mssql-private-preview
export DOCKER_USERNAME=<your username, credentials provided by Microsoft>
export DOCKER_PASSWORD=<your password, credentials provided by Microsoft>
export DOCKER_EMAIL=<your Docker email, use the username provided by Microsoft>
export DOCKER_PRIVATE_REGISTRY="1"
```

> [!NOTE]
> Während der begrenzten öffentlichen Vorschau werden Docker-Anmeldeinformationen zum Herunterladen der SQL Server-Big Data-Cluster-Images für jeden Kunden von Microsoft bereitgestellt. Um Zugriff zu beantragen, registrieren [hier](https://aka.ms/eapsignup), und geben Sie Ihr Interesse an, um SQL Server-big Data-Cluster zu versuchen.

## <a name="deploy-a-big-data-cluster"></a>Bereitstellen eines big Data-Clusters

Um eine SQL Server 2019 CTP 2.0 big Data-Cluster in Ihrem Kubernetes-Cluster bereitzustellen, führen Sie den folgenden Befehl aus:

```bash
mssqlctl create cluster <name of your cluster>
```

> [!NOTE]
> Der Name Ihres Clusters muss nur Kleinbuchstaben alphanumerische Zeichen, keine Leerzeichen enthalten sein. Alle Kubernetes-Artefakte für die big Data-Cluster in einem Namespace mit demselben Namen wie der Cluster erstellt werden angegebenen Namen.


Im Befehlsfenster ausgegeben wird der Bereitstellungsstatus angezeigt. Sie können auch den Bereitstellungsstatus überprüfen, indem Sie diese Befehle in einem anderen Cmd-Fenster ausführen:

```bash
kubectl get all -n <name of your cluster>
kubectl get pods -n <name of your cluster>
kubectl get svc -n <name of your cluster>
```

Sie können eine präzisere Status und die Konfiguration für die einzelnen Pod mit finden Sie unter:
```bash
kubectl describe pod <pod name> -n <name of your cluster>
```

Sobald der Controller-Pod ausgeführt wird, können Sie das Cluster-Verwaltungsportal, zum Überwachen der Bereitstellung. Sie können den Portalzugriff mithilfe der externen IP-Adresse und den Port für die `service-proxy-lb` (z. B.: **https://\<Ip-Adresse\>: 30777**). Anmeldeinformationen für den Zugriff auf die Administratorportal die Werte sind `CONTROLLER_USERNAME` und `CONTROLLER_PASSWORD` oben angegebenen Umgebungsvariablen.

Sie können die IP-Adresse des Dienst-Proxy-lb-Diensts abrufen, mit dem folgenden Befehl in einem nachfolgenden bash- oder Cmd-Fenster:

```bash
kubectl get svc service-proxy-lb -n <name of your cluster>
```

> [!NOTE]
> Sie werden eine sicherheitswarnung angezeigt, wenn die Webseite zugreifen, da wir automatisch generierte SSL-Zertifikate verwenden. In zukünftigen Versionen werden wir die Möglichkeit, eigene selbstsignierte Zertifikate bieten bieten.
 

## <a name="connect-to-the-big-data-cluster"></a>Verbinden Sie mit der big Data-cluster

Nachdem das Bereitstellungsskript erfolgreich abgeschlossen wurde, erhalten Sie die IP-Adresse der master SQL Server-Instanz und den Spark/HDFS-Endpunkten, die mithilfe der unten beschriebenen Schritte. Alle clusterendpunkte werden im Abschnitt "Dienstendpunkte" im Verwaltungsportal auch zum einfachen Nachschlagen Cluster angezeigt.

Azure bietet den Azure-LoadBalancer-Dienst in AKS. Führen Sie folgenden Befehl eine cmd- oder die bash-Fenster:

```bash
kubectl get svc service-master-pool-lb -n <name of your cluster>
kubectl get svc service-security-lb -n <name of your cluster>
```

Suchen Sie nach der **externe IP-** Wert, der mit den Diensten zugewiesen ist. Verbinden mit der master SQL Server-Instanz, die die IP-Adresse für die `service-master-pool-lb` an Port 31433 (Beispiel:  **\<Ip-Adresse\>, 31433**) und für den SQL Server-big Data-clusterendpunkt mit dem External-IP-Adresse für die `service-security-lb` Service.   Big Data-cluster-Endpunkt ist können Sie interagieren mit HDFS und Übermitteln von Spark-Aufträge über Knox.

## <a name="next-steps"></a>Nächste Schritte

Nun, dass der SQL Server-big Data-Cluster bereitgestellt wird, versuchen Sie es, einige der neuen Funktionen:

> [!div class="nextstepaction"]
> [Verwendung von Notebooks in der Vorschau von SQL Server-2019](notebooks-guidance.md)
