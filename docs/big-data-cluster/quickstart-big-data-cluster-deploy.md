---
title: Bereitstellen von SQL Server-big Data-Cluster | Microsoft-Dokumentation
description: ''
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/01/2018
ms.topic: quickstart
ms.prod: sql
ms.openlocfilehash: 899a02996e6415cbf35ed903c276ca23b78c6961
ms.sourcegitcommit: 182d77997133a6e4ee71e7a64b4eed6609da0fba
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50050992"
---
# <a name="quickstart-deploy-sql-server-big-data-cluster-on-azure-kubernetes-service-aks"></a>Schnellstart: Bereitstellen von SQL Server-big Data-Cluster in Azure Kubernetes Service (AKS)

Installieren Sie SQL Server-big Data-Cluster in AKS in einer Standardkonfiguration für Entwicklungs-/testumgebungen geeignet ist. Zusätzlich zu einer Instanz des SQL-Master enthält der Cluster, eine Compute-Pool-Instanz, eine Daten-Pool-Instanz und zwei Instanzen von Speicher-Pool. Daten werden beibehalten, über persistente Kubernetes-Volumes, die Standard-Speicherklassen AKS verwenden. Zum weiteren Anpassen Ihrer Konfiguration finden Sie in der Umgebungsvariablen zur [bereitstellungsanleitung](deployment-guidance.md).

[!INCLUDE [Limited public preview note](../includes/big-data-cluster-preview-note.md)]

## <a name="prerequisites"></a>Erforderliche Komponenten

Diese schnellstartanleitung müssen Sie bereits einen AKS-Cluster mit einer Mindestversion v1.10 konfiguriert haben. Weitere Informationen finden Sie unter den [Bereitstellen in AKS](deploy-on-aks.md) Guide.

Installieren Sie auf dem Computer, die Sie verwenden, um die Befehle zum Installieren der SQL Server-big Data-Cluster ausgeführt wird, ["kubectl"](https://kubernetes.io/docs/tasks/tools/install-kubectl/). SQL Server-big Data-Cluster die Mindestversion 1,10 für Kubernetes, für Server und Client (Kubectl). Um "kubectl" zu installieren, finden Sie unter [Installieren von Kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl). 

So installieren Sie die **Mssqlctl** CLI-Tool zur Verwaltung der großen SQL Server-Datenverlustvorfalls zu Clustern, auf dem Clientcomputer, müssen Sie zunächst installieren [Python](https://www.python.org/downloads/) Mindestversion v3. 0 und [pip3](https://pip.pypa.io/en/stable/installing/). `pip` ist bereits installiert, wenn Sie eine Python-Version von mindestens 3.4, die heruntergeladen werden [python.org](https://www.python.org/).

Die Python-Installation fehlt die `requests` -Paket, die Sie installieren müssen `requests` mit `python -m pip install requests` (verwenden `python3` für diese Befehle unter Linux). Wenn Sie bereits haben eine `requests` -Paket, ein upgrade auf die neueste Version mithilfe `python -m pip install requests --upgrade`.

## <a name="verify-aks-configuration"></a>Überprüfen der AKS-Konfiguration

Nachdem Sie den AKS-Cluster bereitgestellt haben, können Sie Ausführen der folgenden Befehl aus "kubectl", um die Clusterkonfiguration anzuzeigen. Stellen Sie sicher, dass diese "kubectl" auf den richtigen Clusterkontext gezeigt wird.

```bash
kubectl config view
```

## <a name="install-mssqlctl-cli-management-tool"></a>Installieren Sie CLI-Verwaltungstool mssqlctl

Führen Sie den folgenden Befehl zum Installieren von **Mssqlctl** Tool auf dem Clientcomputer. Der Befehl funktioniert von einer Windows und Linux-Client, aber stellen Sie sicher, dass Sie von einer Cmd-Fenster, die mit Administratorrechten ausgeführt, auf die Windows wird ausführen oder voran `sudo` für Linux:

```
pip3 install --index-url https://private-repo.microsoft.com/python/ctp-2.0 mssqlctl  
```

> [!TIP]
> Wenn **Mssqlctl** nicht ordnungsgemäß installiert wird, überprüfen Sie die erforderlichen Schritte in diesem Artikel [installieren Mssqlctl](deployment-guidance.md#mssqlctl).

## <a name="define-environment-variables"></a>Definieren von Umgebungsvariablen

Festlegen der Umgebungsvariablen, die für die Bereitstellung von big Data-Cluster leicht, hängt davon ab, ob Sie Windows oder Linux/MacOS-Client verwenden.  Wählen Sie die folgenden Schritte aus je nach verwendetem, die Betriebssystem Sie verwenden.

Beachten Sie bevor Sie fortfahren die folgenden wichtigen Richtlinien:

- In der [Befehlsfenster](http://docs.microsoft.com/visualstudio/ide/reference/command-window), Anführungszeichen sind in den Umgebungsvariablen enthalten. Wenn Sie Anführungszeichen verwenden, um ein Kennwort zu umschließen, sind die Anführungszeichen im Kennwort enthalten.
- In bash bleibt sind die Anführungszeichen in der Variablen nicht enthalten. Unseren Beispielen verwenden Sie doppelte Anführungszeichen `"`.
- Sie können das Kennwort Umgebungsvariablen festlegen, um einen beliebigen Namen, aber stellen Sie sicher, dass sie ausreichend komplex sind und verwenden Sie nicht die `!`, `&`, oder `'` Zeichen.
- Ändern Sie bei der Version CTP 2.0 nicht die Standardports.
- Die `sa` Konto ist ein Systemadministrator für die Master für SQL Server-Instanz, die während des Setups erstellt wird. Nach dem Erstellen Ihres SQL Server-Containers wird die von Ihnen festgelegte `MSSQL_SA_PASSWORD` Umgebungsvariable sichtbar, wenn Sie sie in dem Container ausführen`echo $MSSQL_SA_PASSWORD`. Aus Sicherheitsgründen ändern Ihre `sa` Kennwort gemäß der dokumentierten bewährten Methoden [hier](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker?view=sql-server-2017#change-the-sa-password).

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
export ACCEPT_EULA="Y"
export CLUSTER_PLATFORM="aks"

export CONTROLLER_USERNAME="<controller_admin_name – can be anything>"
export CONTROLLER_PASSWORD="<controller_admin_password – can be anything, password complexity compliant>"
export KNOX_PASSWORD="<knox_password – can be anything, password complexity compliant>"
export MSSQL_SA_PASSWORD="<sa_password_of_master_sql_instance, password complexity compliant>"

export DOCKER_REGISTRY="private-repo.microsoft.com"
export DOCKER_REPOSITORY="mssql-private-preview"
export DOCKER_USERNAME="<your username, credentials provided by Microsoft>"
export DOCKER_PASSWORD="<your password, credentials provided by Microsoft>"
export DOCKER_EMAIL="<your Docker email, use the username provided by Microsoft>"
export DOCKER_PRIVATE_REGISTRY="1"
```

> [!NOTE]
> Während der begrenzten öffentlichen Vorschau werden die Docker-Anmeldeinformationen zum Herunterladen von SQL Server-Images für die big Data-Cluster für jeden Kunden von Microsoft bereitgestellt. Um Zugriff zu beantragen, registrieren [hier](https://aka.ms/eapsignup), und geben Sie Ihr Interesse an, um SQL Server-big Data-Cluster zu versuchen.

## <a name="deploy-a-big-data-cluster"></a>Bereitstellen eines big Data-Clusters

Um eine SQL Server 2019 CTP 2.0 big Data-Cluster in Ihrem Kubernetes-Cluster bereitzustellen, führen Sie den folgenden Befehl aus:

```bash
mssqlctl create cluster <name of your cluster>
```

> [!NOTE]
> Der Name Ihres Clusters muss nur Kleinbuchstaben alphanumerische Zeichen, keine Leerzeichen enthalten sein. Alle Kubernetes-Artefakte für die big Data-Cluster in einem Namespace mit demselben Namen wie der Cluster erstellt werden angegebenen Namen.


Im Befehlsfenster oder die Shell gibt den Bereitstellungsstatus zurück. Sie können auch den Bereitstellungsstatus überprüfen, indem Sie diese Befehle in einem anderen Cmd-Fenster ausführen:

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

## <a name="sample-deployment-script"></a>Beispielskript für die Bereitstellung

Ein Beispiel-Python-Skript, das sowohl AKS und SQL Server-big Data-Cluster bereitgestellt wird, finden Sie unter [stellen Sie eine SQL-Server, die big Data-in Azure Kubernetes Service (AKS Cluster)](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/deployment/aks).

## <a name="next-steps"></a>Nächste Schritte

Nun, dass der SQL Server-big Data-Cluster bereitgestellt wird, versuchen Sie es, einige der neuen Funktionen:

> [!div class="nextstepaction"]
> [Verwendung von Notebooks in der Vorschau von SQL Server-2019](notebooks-guidance.md)
