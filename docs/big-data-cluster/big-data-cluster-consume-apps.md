---
title: Verwenden von Anwendungen
titleSuffix: SQL Server Big Data Clusters
description: Verwenden Sie eine auf Big Data-Clustern für SQL Server bereitgestellte Anwendung mithilfe eines RESTful-Webdiensts.
author: cloudmelon
ms.author: melqin
ms.reviewer: bilia
ms.date: 06/22/2020
ms.metadata: seo-lt-2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 45161a879adadb0de78c4b2b0d3c62a5c2e18f55
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85719067"
---
# <a name="consume-an-app-deployed-on-big-data-clusters-2019-using-a-restful-web-service"></a>Verwenden einer auf [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] bereitgestellten App mithilfe eines RESTful-Webdiensts

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel wird beschrieben, wie Sie mithilfe eines RESTful-Webdiensts eine auf einem Big Data-Cluster für SQL Server bereitgestellte App verwenden.

## <a name="prerequisites"></a>Voraussetzungen

- [Big Data-Cluster für SQL Server](deployment-guidance.md)
- [Befehlszeilen-Hilfsprogramm „azdata“](deploy-install-azdata.md)
- Eine App, die entweder mithilfe von [azdata](big-data-cluster-create-apps.md) oder der [App-Bereitstellungserweiterung](app-deployment-extension.md) bereitgestellt wird

> [!NOTE]
> Wenn die YAML-Spezifikationsdatei der Anwendung einen Zeitplan vorgibt, wird die Anwendung über einen Cron-Auftrag ausgelöst. Wenn Ihr Big Data-Cluster in OpenShift bereitgestellt wird, sind zusätzliche Funktionen erforderlich,um den Cron-Auftrag zu starten. Weitere Informationen finden Sie in den [Sicherheitshinweisen zu OpenShift](concept-application-deployment.md#app-deploy-security).

## <a name="capabilities"></a>Funktionen

Nachdem Sie eine Anwendung auf Ihrer Instanz von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] bereitgestellt haben, können Sie mithilfe eines RESTful-Webdiensts auf diese Anwendung zugreifen und sie verwenden. Dadurch kann diese App aus anderen Anwendungen oder Diensten (z. B. einer mobile App oder Website) integriert werden. In der folgenden Tabelle werden die Befehle zur Anwendungsbereitstellung beschrieben, die Sie mit **azdata** verwenden können, um Informationen zum RESTful-Webdienst Ihrer App abzurufen.

|Get-Help |BESCHREIBUNG |
|:---|:---|
|`azdata app describe` | Beschreiben einer Anwendung. |

Mit dem Parameter `--help` können Sie wie im folgenden Beispiel Hilfe erhalten:

```bash
azdata app describe --help
```

In den folgenden Abschnitten wird beschrieben, wie Sie einen Endpunkt für eine Anwendung abrufen und wie Sie den RESTful-Webdienst zur Anwendungsintegration verwenden.

## <a name="retrieve-the-endpoint"></a>Abrufen des Endpunkts

Der Befehl **azdata app describe** stellt Informationen zur App bereit, darunter auch den Endpunkt in Ihrem Cluster. Dieser wird in der Regel von einem App-Entwickler dazu verwendet, eine App mithilfe des Swagger-Clients zu erstellen und mithilfe des Webdiensts RESTful mit der App zu interagieren.

Beschreiben Sie Ihre App, indem Sie einen Befehl wie den folgenden ausführen:

```bash
azdata app describe --name add-app --version v1
```

```json
{
  "input_param_defs": [
    {
      "name": "x",
      "type": "int"
    },
    {
      "name": "y",
      "type": "int"
    }
  ],
  "links": {
    "app": "https://10.1.1.3:30080/app/addpy/v1",
    "swagger": "https://10.1.1.3:30080/app/addpy/v1/swagger.json"
  },
  "name": "add-app",
  "output_param_defs": [
    {
      "name": "result",
      "type": "int"
    }
  ],
  "state": "Ready",
  "version": "v1"
}
```

Notieren Sie sich die IP-Adresse (`10.1.1.3` in diesem Beispiel) und die Portnummer (`30080`) aus der Ausgabe.

Sie können diese Informationen auch abrufen, indem Sie auf dem Server in Azure Data Studio mit der rechten Maustaste auf „Verwalten“ klicken. Dort werden die Endpunkte der aufgeführten Dienste angezeigt.

![ADS-Endpunkt](media/big-data-cluster-consume-apps/ads_end_point.png)

## <a name="generate-a-jwt-access-token"></a>Generieren eines JWT-Zugriffstokens

Für den Zugriff auf den RESTful-Webdienst für die von Ihnen bereitgestellte App müssen Sie zunächst ein JWT-Zugriffstoken generieren. Die URL für das Zugriffstoken hängt von der Version des Big Data-Clusters ab. 

|Version |URL|
|------------|------|
|GDR1|  `https://[IP]:[PORT]/docs/swagger.json`|
|Kumulatives Update 1 und höher| `https://[IP]:[PORT]/api/v1/swagger.json`|

 Basierend auf der Ausgabe aus dem obigen Beispiel, dem CU4-Release, der IP-Adresse des Controllers (10.1.1.3 im Beispiel) und der Portnummer (30080), ergibt sich die folgende URL: 
 
 ```bash
    https://10.1.1.3 :30080/api/v1/swagger.json
```
 
> Versionsinformationen finden Sie im [Releaseverlauf](release-notes-big-data-cluster.md#release-history).

Öffnen Sie die entsprechende URL in Ihrem Browser, und verwenden Sie dabei die IP-Adresse und den Port, die Sie zuvor mithilfe des Befehls [`describe`](#retrieve-the-endpoint) abgerufen haben. Melden Sie sich mit denselben Anmeldeinformationen an, die Sie für `azdata login` verwendet haben.

Fügen Sie den Inhalt von `swagger.json` in den [Swagger-Editor](https://editor.swagger.io) ein, um festzustellen, welche Methoden verfügbar sind:

![API Swagger](media/big-data-cluster-consume-apps/api_swagger.png)

Hinweis: `app` ist die GET-Methode, und zum Abrufen von `token` wird die POST-Methode verwendet. Da für die App-Authentifizierung JWT-Token verwendet werden, müssen Sie ein Token abrufen. Verwenden Sie hierzu Ihr bevorzugtes Tool, um einen POST-Aufruf für die `token`-Methode auszuführen. Unter Verwendung desselben Beispiels sieht die URL zum Abrufen des JWT-Token wie folgt aus:

 ```bash
    https://10.1.1.3 :30080/api/v1/token
```


Im folgenden finden Sie ein Beispiel dafür, wie Sie dies in [Postman](https://www.getpostman.com/) durchführen:

![Postman-Token](media/big-data-cluster-consume-apps/postman_token.png)


Als Ausgabe für diese Anforderung erhalten Sie ein JWT-`access_token`, das Sie für den Aufruf der URL zum Ausführen der App benötigen.

## <a name="execute-the-app-using-the-restful-web-service"></a>Ausführen der App mithilfe des RESTful-Webdiensts

Es gibt mehrere Möglichkeiten, eine App in Big Data-Cluster auszuführen, beispielsweise über den Befehl [azdata app run](big-data-cluster-create-apps.md). In diesem Abschnitt wird veranschaulicht, wie Sie gängige Entwicklertools wie Postman verwenden können, um die App auszuführen. 

Sie können die URL für das Element `swagger` öffnen, das beim Ausführen von `azdata app describe --name [appname] --version [version]` in Ihrem Browser zurückgegeben wurde und ähnlich wie `https://[IP]:[PORT]/app/[appname]/[version]/swagger.json` sein sollte. 

> [!NOTE]
> Sie müssen dieselben Anmeldeinformationen wie für `azdata login` verwenden. Unter Verwendung desselben Beispiels sieht der Befehl wie folgt aus:

 ```bash
    azdata app describe --name add-app --version v1
```

Sie können den Inhalt von `swagger.json` in den [Swagger-Editor](https://editor.swagger.io) einfügen. Dann stellt der Webdienst die Methode `run` zur Verfügung. Dafür musste ein Anwendungsproxy passiert werden, bei dem es sich um eine Web-API handelt, die erst Benutzer authentifiziert und dann die Anforderung an die Anwendungen weiterleitet. Beachten Sie die oben angezeigte Basis-URL. Sie können die Methode `run` (`https://[IP]:30778/api/app/[appname]/[version]/run`) mithilfe eines Tools Ihrer Wahl aufrufen, wobei Sie die Parameter im Text Ihrer POST-Anforderung im JSON-Format übergeben. 


In diesem Beispiel wird [Postman](https://www.getpostman.com/) verwendet. Bevor Sie die Methode aufrufen, müssen Sie `Authorization` auf `Bearer Token` festlegen und das Token einfügen, das Sie zuvor abgerufen haben. Dadurch wird ein Header für Ihre Anforderung festgelegt. Sehen Sie sich hierzu folgenden Screenshot an.

![Postman: „run“-Header](media/big-data-cluster-consume-apps/postman_run_1.png)

Übergeben Sie als Nächstes im Anforderungstext die Parameter an die App, die Sie aufrufen, und legen Sie `content-type` auf `application/json` fest:

![Postman: „run“-Text](media/big-data-cluster-consume-apps/postman_run_2.png)

Wenn Sie die Anforderung absenden, erhalten Sie dieselbe Ausgabe, die Sie beim Ausführen der App über `azdata app run` erhalten haben:

![Postman: „run“-Ergebnis](media/big-data-cluster-consume-apps/postman_result.png)

Sie haben die App nun erfolgreich über den Webdienst aufgerufen. Sie können ähnliche Schritte durchführen, um diesen Webdienst in Ihre Anwendung zu integrieren.


## <a name="next-steps"></a>Nächste Schritte

Weitere Beispiele finden Sie außerdem unter den [Beispielen zur App-Bereitstellung](https://aka.ms/sql-app-deploy).

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
