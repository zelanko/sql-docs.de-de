---
title: Verwenden von Anwendungen
titleSuffix: SQL Server Big Data Clusters
description: Verwenden Sie eine auf Big Data-Clustern für SQL Server bereitgestellte Anwendung mithilfe eines RESTful-Webdiensts.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 01/07/2020
ms.metadata: seo-lt-2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 305080d5c3b0a1c517d757c1f6f2bd07fefb216c
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2020
ms.locfileid: "75721405"
---
# <a name="consume-an-app-deployed-on-big-data-clusters-2019-using-a-restful-web-service"></a>Verwenden einer auf [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] bereitgestellten App mithilfe eines RESTful-Webdiensts

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie mithilfe eines RESTful-Webdiensts eine auf einem Big Data-Cluster für SQL Server bereitgestellte App verwenden.

## <a name="prerequisites"></a>Voraussetzungen

- [Big Data-Cluster für SQL Server](deployment-guidance.md)
- [Befehlszeilen-Hilfsprogramm „azdata“](deploy-install-azdata.md)
- Eine App, die entweder mithilfe von [azdata](big-data-cluster-create-apps.md) oder der [App-Bereitstellungserweiterung](app-deployment-extension.md) bereitgestellt wird

## <a name="capabilities"></a>Funktionen

Nachdem Sie eine Anwendung auf Ihrer Instanz von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] bereitgestellt haben, können Sie mithilfe eines RESTful-Webdiensts auf diese Anwendung zugreifen und sie verwenden. Dadurch kann diese App aus anderen Anwendungen oder Diensten (z. B. einer mobile App oder Website) integriert werden. In der folgenden Tabelle werden die Befehle zur Anwendungsbereitstellung beschrieben, die Sie mit **azdata** verwenden können, um Informationen zum RESTful-Webdienst Ihrer App abzurufen.

|Get-Help |Beschreibung |
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

> Versionsinformationen finden Sie im [Releaseverlauf](release-notes-big-data-cluster.md#release-history).

Öffnen Sie die entsprechende URL in Ihrem Browser, und verwenden Sie dabei die IP-Adresse und den Port, die Sie zuvor mithilfe des Befehls [`describe`](#retrieve-the-endpoint) abgerufen haben. Melden Sie sich mit denselben Anmeldeinformationen an, die Sie für `azdata login` verwendet haben.

Fügen Sie den Inhalt von `swagger.json` in den [Swagger-Editor](https://editor.swagger.io) ein, um festzustellen, welche Methoden verfügbar sind:

![API Swagger](media/big-data-cluster-consume-apps/api_swagger.png)

Notieren Sie sich die `app`-GET-Methode sowie die `token`-POST-Methode. Da für die App-Authentifizierung JWT-Token verwendet werden, müssen Sie ein Token abrufen. Verwenden Sie hierzu Ihr bevorzugtes Tool, um einen POST-Aufruf für die `token`-Methode auszuführen. Im folgenden finden Sie ein Beispiel dafür, wie Sie dies in [Postman](https://www.getpostman.com/) durchführen:

![Postman-Token](media/big-data-cluster-consume-apps/postman_token.png)

Als Ergebnis dieser Anforderung erhalten Sie ein JWT-`access_token`, das Sie für den Aufruf der URL zum Ausführen der App benötigen.

## <a name="execute-the-app-using-the-restful-web-service"></a>Ausführen der App mithilfe des RESTful-Webdiensts

> [!NOTE]
> Wenn Sie möchten, können Sie die URL für das `swagger`-Element öffnen, das beim Ausführen von `azdata app describe --name [appname] --version [version]` in Ihrem Browser zurückgegeben wurde, das ähnlich wie `https://[IP]:[PORT]/app/[appname]/[version]/swagger.json` sein sollte. Sie müssen dieselben Anmeldeinformationen wie für `azdata login` verwenden. Sie können den Inhalt von `swagger.json` in den [Swagger-Editor](https://editor.swagger.io) einfügen. Sie werden sehen, dass der Webdienst die `run`-Methode verfügbar macht. Beachten Sie auch die oben angezeigte Basis-URL.

Sie können die `run`-Methode (`https://[IP]:30778/api/app/[appname]/[version]/run`) mithilfe Ihres bevorzugten Tools aufrufen, wobei Sie die Parameter im Text Ihrer POST-Anforderung als JSON übergeben. In diesem Beispiel wird [Postman](https://www.getpostman.com/) verwendet. Bevor Sie die Methode aufrufen, müssen Sie `Authorization` auf `Bearer Token` festlegen und das Token einfügen, das Sie zuvor abgerufen haben. Dadurch wird ein Header für Ihre Anforderung festgelegt. Sehen Sie sich hierzu folgenden Screenshot an.

![Postman: „run“-Header](media/big-data-cluster-consume-apps/postman_run_1.png)

Übergeben Sie als Nächstes im Anforderungstext die Parameter an die App, die Sie aufrufen, und legen Sie `content-type` auf `application/json` fest:

![Postman: „run“-Text](media/big-data-cluster-consume-apps/postman_run_2.png)

Wenn Sie die Anforderung absenden, erhalten Sie dieselbe Ausgabe, die Sie beim Ausführen der App über `azdata app run` erhalten haben:

![Postman: „run“-Ergebnis](media/big-data-cluster-consume-apps/postman_result.png)

Sie haben die App nun erfolgreich über den Webdienst aufgerufen. Sie können ähnliche Schritte durchführen, um diesen Webdienst in Ihre Anwendung zu integrieren.

## <a name="next-steps"></a>Nächste Schritte

Weitere Beispiele finden Sie außerdem unter den [Beispielen zur App-Bereitstellung](https://aka.ms/sql-app-deploy).

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
