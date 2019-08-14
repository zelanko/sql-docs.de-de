---
title: Verwenden von Anwendungen auf Big-Data-Clustern
titleSuffix: SQL Server big data clusters
description: Verwenden Sie eine Anwendung, die mithilfe eines RESTful-Webdiensts (Vorschauversion) auf einem Big-Data-Cluster für SQL Server 2019 bereitgestellt wird.
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a2135ef64fb17eba62eab75b81739eda047167ab
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68419507"
---
# <a name="consume-an-app-deployed-on-sql-server-big-data-cluster-using-a-restful-web-service"></a>Verwenden einer App, die mithilfe eines RESTful-Webdiensts auf einem Big-Data-Cluster für SQL Server bereitgestellt wird

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie eine App verwenden, die mithilfe eines RESTful-Webdiensts (Vorschauversion) auf einem Big-Data-Cluster für SQL Server 2019 bereitgestellt wird.

## <a name="prerequisites"></a>Voraussetzungen

- [SQL Server 2019: Big-Data-Cluster](deployment-guidance.md)
- [Befehlszeilen-Hilfsprogramm „mssqlctl“](deploy-install-azdata.md)
- Eine App, die entweder mithilfe von [azdata](big-data-cluster-create-apps.md) oder der [App-Bereitstellungserweiterung](app-deployment-extension.md) bereitgestellt wird

## <a name="capabilities"></a>Funktionen

Nachdem Sie eine Anwendung für den Big-Data-Cluster für SQL Server 2019 (Vorschauversion) bereitgestellt haben, können Sie mithilfe eines RESTful-Webdiensts auf diese Anwendung zugreifen und sie verwenden. Dadurch kann diese App aus anderen Anwendungen oder Diensten (z. B. einer mobile App oder Website) integriert werden. In der folgenden Tabelle werden die Befehle zur Anwendungsbereitstellung beschrieben, die Sie mit **azdata** verwenden können, um Informationen zum RESTful-Webdienst Ihrer App abzurufen.

|Befehl |und Beschreibung |
|:---|:---|
|`azdata app describe` | Beschreiben der Anwendung |

Mit dem Parameter `--help` können Sie wie im folgenden Beispiel Hilfe erhalten:

```bash
azdata app describe --help
```

In den folgenden Abschnitten wird beschrieben, wie Sie einen Endpunkt für eine Anwendung abrufen und wie Sie den RESTful-Webdienst zur Anwendungsintegration verwenden.

## <a name="retrieve-the-endpoint"></a>Abrufen des Endpunkts

Der Befehl **azdata app describe** stellt Informationen zur App bereit, darunter auch den Endpunkt in Ihrem Cluster. Dieser wird in der Regel von einem App-Entwickler dazu verwendet, eine App mithilfe des Swagger-Clients zu erstellen und mithilfe des Webdiensts RESTful mit der App zu interagieren.

Beschreiben Sie Ihre App, indem Sie einen Befehl wie den folgenden ausführen:

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
    "app": "https://10.1.1.3:30777/api/app/addpy/v1",
    "swagger": "https://10.1.1.3:30777/api/app/addpy/v1/swagger.json"
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

Notieren Sie sich die IP-Adresse (`10.1.1.3` in diesem Beispiel) und die Portnummer (`30777`) aus der Ausgabe.

## <a name="generate-a-jwt-access-token"></a>Generieren eines JWT-Zugriffstokens

Für den Zugriff auf den RESTful-Webdienst für die von Ihnen bereitgestellte App müssen Sie zunächst ein JWT-Zugriffstoken generieren. Öffnen Sie die URL `https://[IP]:[PORT]/api/docs/swagger.json` in Ihrem Browser, und verwenden Sie dabei die IP-Adresse und den Port, die Sie weiter oben durch Ausführen des Befehls `describe` abgerufen haben. Sie müssen dieselben Anmeldeinformationen wie für `azdata login` verwenden.

Fügen Sie den Inhalt von `swagger.json` in den [Swagger-Editor](https://editor.swagger.io) ein, um festzustellen, welche Methoden verfügbar sind:

![API Swagger](media/big-data-cluster-consume-apps/api_swagger.png)

Notieren Sie sich die `app`-GET-Methode sowie die `token`-POST-Methode. Da für die App-Authentifizierung JWT-Token verwendet werden, müssen Sie mithilfe Ihres bevorzugten Tools ein Token abrufen, um einen POST-Aufruf für die `token`-Methode auszuführen. Im folgenden finden Sie ein Beispiel dafür, wie Sie dies in [Postman](https://www.getpostman.com/) durchführen:

![Postman-Token](media/big-data-cluster-consume-apps/postman_token.png)

Als Ergebnis dieser Anforderung erhalten Sie ein JWT-`access_token`, das Sie für den Aufruf der URL zum Ausführen der App benötigen.

## <a name="execute-the-app-using-the-restful-web-service"></a>Ausführen der App mithilfe des RESTful-Webdiensts

> [!NOTE]
> Wenn Sie möchten, können Sie die URL für das `swagger`-Element öffnen, das beim Ausführen von `azdata app describe --name [appname] --version [version]` in Ihrem Browser zurückgegeben wurde, das ähnlich wie `https://[IP]:[PORT]/api/app/[appname]/[version]/swagger.json` sein sollte. Sie müssen dieselben Anmeldeinformationen wie für `azdata login` verwenden. Sie können den Inhalt von `swagger.json` in den [Swagger-Editor](https://editor.swagger.io) einfügen. Sie werden sehen, dass der Webdienst die `run`-Methode verfügbar macht. Beachten Sie auch die oben angezeigte Basis-URL.

Sie können die `run`-Methode (`https://[IP]:30778/api/app/[appname]/[version]/run`) mithilfe Ihres bevorzugten Tools aufrufen, wobei Sie die Parameter im Text Ihrer POST-Anforderung als JSON übergeben. In diesem Beispiel verwenden wir [Postman](https://www.getpostman.com/). Bevor Sie die Methode aufrufen, müssen Sie `Authorization` auf `Bearer Token` festlegen und das Token einfügen, das Sie zuvor abgerufen haben. Dadurch wird ein Header für Ihre Anforderung festgelegt. Sehen Sie sich hierzu folgenden Screenshot an.

![Postman: „run“-Header](media/big-data-cluster-consume-apps/postman_run_1.png)

Übergeben Sie als Nächstes im Anforderungstext die Parameter an die App, die Sie aufrufen, und legen Sie `content-type` auf `application/json` fest:

![Postman: „run“-Text](media/big-data-cluster-consume-apps/postman_run_2.png)

Wenn Sie die Anforderung absenden, erhalten Sie dieselbe Ausgabe, die Sie beim Ausführen der App über `azdata app run` erhalten haben:

![Postman: „run“-Ergebnis](media/big-data-cluster-consume-apps/postman_result.png)

Sie haben die App nun erfolgreich über den Webdienst aufgerufen. Sie können ähnliche Schritte durchführen, um diesen Webdienst in Ihre Anwendung zu integrieren.

## <a name="next-steps"></a>Nächste Schritte

Weitere Beispiele finden Sie außerdem unter den [Beispielen zur App-Bereitstellung](https://aka.ms/sql-app-deploy).

Weitere Informationen zu Big-Data-Clustern unter SQL Server finden Sie unter [Was sind SQL Server 2019-Big-Data-Cluster?](big-data-cluster-overview.md).
