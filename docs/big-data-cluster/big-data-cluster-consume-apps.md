---
title: Verwenden von Anwendungen auf SQL Server Big Data Clustern
titleSuffix: SQL Server big data clusters
description: '[!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] Verwenden Sie eine Anwendung, die mithilfe eines Rest-Webdiensts (Vorschau) bereitgestellt wird.'
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5d65cb2577749a45bccf1383bdf880ce8c5a7a46
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653075"
---
# <a name="consume-an-app-deployed-on-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd-using-a-restful-web-service"></a>Nutzen einer in [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] bereitgestellten App mithilfe eines Rest-Webdiensts

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie eine App verwenden, die mithilfe eines RESTful-Webdiensts (Vorschauversion) auf einem Big-Data-Cluster für SQL Server 2019 bereitgestellt wird.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [SQL Server 2019: Big Data-Cluster](deployment-guidance.md)
- [Befehlszeilen-Hilfsprogramm „azdata“](deploy-install-azdata.md)
- Eine App, die entweder mithilfe von [azdata](big-data-cluster-create-apps.md) oder der [App-Bereitstellungserweiterung](app-deployment-extension.md) bereitgestellt wird

## <a name="capabilities"></a>Funktionen

Nachdem Sie eine Anwendung für den [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]bereitgestellt haben, können Sie mit einem Rest-Webdienst auf diese Anwendung zugreifen und diese nutzen. Dadurch kann diese App aus anderen Anwendungen oder Diensten (z. B. einer mobile App oder Website) integriert werden. In der folgenden Tabelle werden die Befehle zur Anwendungsbereitstellung beschrieben, die Sie mit **azdata** verwenden können, um Informationen zum RESTful-Webdienst Ihrer App abzurufen.

|Befehl |Beschreibung |
|:---|:---|
|`azdata app describe` | Beschreiben der Anwendung |

Mit dem Parameter `--help` können Sie wie im folgenden Beispiel Hilfe erhalten:

```bash
azdata app describe --help
```

In den folgenden Abschnitten wird beschrieben, wie Sie einen Endpunkt für eine Anwendung abrufen und wie Sie den RESTful-Webdienst zur Anwendungsintegration verwenden.

## <a name="retrieve-the-endpoint"></a>Abrufen des Endpunkts

Der Befehl **azdata app describe** stellt Informationen zur App bereit, darunter auch den Endpunkt in Ihrem Cluster. Dieser wird in der Regel von einem App-Entwickler dazu verwendet, eine App mithilfe des Swagger-Clients zu erstellen und mithilfe des Webdiensts RESTful mit der App zu interagieren.

Beschreiben Sie Ihre APP, indem Sie einen Befehl ausführen, der dem folgenden Beispiel ähnelt:

```bash
azdata app describe --name addpy --version v1
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

Eine der anderen Möglichkeiten, diese Informationen zu erhalten, besteht darin, mit der rechten Maustaste auf dem Server in Azure Data Studio zu verwalten, wo Sie die Endpunkte der aufgelisteten Dienste finden.

![ADS-Endpunkt](media/big-data-cluster-consume-apps/ads_end_point.png)

## <a name="generate-a-jwt-access-token"></a>Generieren eines JWT-Zugriffstokens

Für den Zugriff auf den RESTful-Webdienst für die von Ihnen bereitgestellte App müssen Sie zunächst ein JWT-Zugriffstoken generieren. Öffnen Sie die URL `https://[IP]:[PORT]/docs/swagger.json` in Ihrem Browser, und verwenden Sie dabei die IP-Adresse und den Port, die Sie weiter oben durch Ausführen des Befehls `describe` abgerufen haben. Sie müssen sich mit denselben Anmelde Informationen anmelden, die Sie für `azdata login`verwendet haben.

Fügen Sie den Inhalt von `swagger.json` in den [Swagger-Editor](https://editor.swagger.io) ein, um festzustellen, welche Methoden verfügbar sind:

![API Swagger](media/big-data-cluster-consume-apps/api_swagger.png)

Notieren Sie sich die `app`-GET-Methode sowie die `token`-POST-Methode. Da bei der Authentifizierung für apps JWT-Token verwendet werden, benötigen Sie ein Token, das mit Ihrem bevorzugten Tool verwendet wird, um einen Post `token` -Abruf für die-Methode durchführen zu können. Im folgenden finden Sie ein Beispiel dafür, wie Sie dies in [Postman](https://www.getpostman.com/) durchführen:

![Postman-Token](media/big-data-cluster-consume-apps/postman_token.png)

Das Ergebnis dieser Anforderung ist ein JWT `access_token`, das Sie zum Ausführen der APP an die URL wenden müssen.

## <a name="execute-the-app-using-the-restful-web-service"></a>Ausführen der App mithilfe des RESTful-Webdiensts

> [!NOTE]
> Wenn Sie möchten, können Sie die URL für das `swagger`-Element öffnen, das beim Ausführen von `azdata app describe --name [appname] --version [version]` in Ihrem Browser zurückgegeben wurde, das ähnlich wie `https://[IP]:[PORT]/app/[appname]/[version]/swagger.json` sein sollte. Sie müssen dieselben Anmeldeinformationen wie für `azdata login` verwenden. Sie können den Inhalt von `swagger.json` in den [Swagger-Editor](https://editor.swagger.io) einfügen. Sie werden sehen, dass der Webdienst die `run`-Methode verfügbar macht. Beachten Sie auch die oben angezeigte Basis-URL.

Sie können die `run`-Methode (`https://[IP]:30778/api/app/[appname]/[version]/run`) mithilfe Ihres bevorzugten Tools aufrufen, wobei Sie die Parameter im Text Ihrer POST-Anforderung als JSON übergeben. In diesem Beispiel verwenden wir [Postman](https://www.getpostman.com/). Bevor Sie die Methode aufrufen, müssen Sie `Authorization` auf `Bearer Token` festlegen und das Token einfügen, das Sie zuvor abgerufen haben. Dadurch wird ein Header für Ihre Anforderung festgelegt. Sehen Sie sich hierzu folgenden Screenshot an.

![Postman: „run“-Header](media/big-data-cluster-consume-apps/postman_run_1.png)

Übergeben Sie als Nächstes im Anforderungstext die Parameter an die App, die Sie aufrufen, und legen Sie `content-type` auf `application/json` fest:

![Postman: „run“-Text](media/big-data-cluster-consume-apps/postman_run_2.png)

Wenn Sie die Anforderung absenden, erhalten Sie dieselbe Ausgabe, die Sie beim Ausführen der App über `azdata app run` erhalten haben:

![Postman: „run“-Ergebnis](media/big-data-cluster-consume-apps/postman_result.png)

Sie haben die App nun erfolgreich über den Webdienst aufgerufen. Sie können ähnliche Schritte durchführen, um diesen Webdienst in Ihre Anwendung zu integrieren.

## <a name="next-steps"></a>Nächste Schritte

Weitere Beispiele finden Sie außerdem unter den [Beispielen zur App-Bereitstellung](https://aka.ms/sql-app-deploy).

Weitere Informationen zu [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]finden Sie unter [was [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]ist?](big-data-cluster-overview.md).
