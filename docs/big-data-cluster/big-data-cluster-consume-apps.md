---
title: Verwenden von Anwendungen auf Big Data Clustern
titleSuffix: SQL Server big data clusters
description: Verwenden Sie eine Anwendung, die auf SQL Server 2019-Big Data Cluster mit einem Rest-Webdienst (Vorschau) bereitgestellt wird
author: jeroenterheerdt
ms.author: jterh
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a2135ef64fb17eba62eab75b81739eda047167ab
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419507"
---
# <a name="consume-an-app-deployed-on-sql-server-big-data-cluster-using-a-restful-web-service"></a>Nutzen einer APP, die auf SQL Server Big Data Cluster mithilfe eines Rest-Webdiensts bereitgestellt wird

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Artikel wird beschrieben, wie Sie eine APP nutzen, die auf einem SQL Server 2019 Big Data-Cluster mit einem Rest-Webdienst (Vorschau) bereitgestellt wird.

## <a name="prerequisites"></a>Vorraussetzungen

- [SQL Server 2019 Big Data Cluster](deployment-guidance.md)
- [mssqlctl (Befehlszeilenprogramm)](deploy-install-azdata.md)
- Eine APP, die entweder mit [azdata](big-data-cluster-create-apps.md) oder der APP-Bereitstellungs [Erweiterung](app-deployment-extension.md) bereitgestellt wird

## <a name="capabilities"></a>Funktionen

Nachdem Sie eine Anwendung für den SQL Server 2019 Big Data-Cluster (Vorschauversion) bereitgestellt haben, können Sie mit einem Rest-Webdienst auf diese Anwendung zugreifen und diese nutzen. Dies ermöglicht die Integration dieser APP aus anderen Anwendungen oder Diensten (z. b. einem Mobile App oder einer Website). In der folgenden Tabelle werden die Befehle für die Anwendungs Bereitstellung beschrieben, die Sie mit **azdata** verwenden können, um Informationen über den Rest-Webdienst für Ihre APP zu erhalten.

|Befehl |Beschreibung |
|:---|:---|
|`azdata app describe` | Beschreiben Sie die Anwendung. |

Sie können wie im folgenden Beispiel `--help` mit dem-Parameter Hilfe erhalten:

```bash
azdata app describe --help
```

In den folgenden Abschnitten wird beschrieben, wie Sie einen Endpunkt für eine Anwendung abrufen und mit dem Rest-Webdienst für die Anwendungsintegration arbeiten.

## <a name="retrieve-the-endpoint"></a>Abrufen des Endpunkts

Der Befehl **azdata-APP-Beschreibung** bietet ausführliche Informationen über die APP, einschließlich des Endpunkts in Ihrem Cluster. Dies wird in der Regel von einem App-Entwickler verwendet, um eine APP mit dem Swagger-Client zu erstellen und den Webdienst zu verwenden, um auf eine restliche Weise mit der APP zu interagieren.

Beschreiben Sie Ihre APP, indem Sie einen Befehl wie den folgenden ausführen:

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

Notieren Sie sich die IP`10.1.1.3` -Adresse (in diesem Beispiel) und die`30777`Portnummer () in der Ausgabe.

## <a name="generate-a-jwt-access-token"></a>Generieren eines JWT-Zugriffs Tokens

Um auf den Rest-Webdienst für die von Ihnen bereitgestellte App zuzugreifen, müssen Sie zuerst ein JWT-Zugriffs Token generieren. Öffnen Sie die folgende URL in Ihrem Browser `https://[IP]:[PORT]/api/docs/swagger.json` : Verwenden Sie die IP-Adresse und den Port `describe` , die Sie zum Ausführen des obigen Befehls abgerufen haben. Sie müssen sich mit denselben Anmelde Informationen anmelden, die Sie für `azdata login`verwendet haben.

Fügen Sie den Inhalt von `swagger.json` in den [Swagger-Editor](https://editor.swagger.io) ein, um zu verstehen, welche Methoden verfügbar sind:

![API-Swagger](media/big-data-cluster-consume-apps/api_swagger.png)

Beachten Sie `app` sowohl die Get-Methode als `token` auch die Post-Methode. Da bei der Authentifizierung für apps JWT-Token verwendet werden, benötigen Sie ein Token, das mit Ihrem bevorzugten Tool verwendet wird, um einen `token` Post-Abruf für die-Methode durchführen zu können. Im folgenden finden Sie ein Beispiel dafür, wie Sie dies in [Postman](https://www.getpostman.com/)tun können:

![Postman-Token](media/big-data-cluster-consume-apps/postman_token.png)

Das Ergebnis dieser Anforderung ist ein JWT `access_token`, das Sie zum Ausführen der APP an die URL wenden müssen.

## <a name="execute-the-app-using-the-restful-web-service"></a>Ausführen der APP mit dem Rest-Webdienst

> [!NOTE]
> Wenn Sie möchten, können Sie die URL für den `swagger` öffnen, der zurückgegeben wurde, als Sie in Ihrem Browser ausgeführt `azdata app describe --name [appname] --version [version]` haben `https://[IP]:[PORT]/api/app/[appname]/[version]/swagger.json`. Dies sollte etwa wie folgt aussehen:. Sie müssen sich mit denselben Anmelde Informationen anmelden, die Sie für `azdata login`verwendet haben. Der Inhalt von `swagger.json` , den Sie in den [Swagger-Editor](https://editor.swagger.io)einfügen können. Sie werden sehen, dass der Webdienst die `run` -Methode verfügbar macht. Beachten Sie auch die oben angezeigte Basis-URL.

Sie können Ihr bevorzugtes Tool verwenden, um `run` die-`https://[IP]:30778/api/app/[appname]/[version]/run`Methode () aufzurufen, und die Parameter im Text der Post-Anforderung als JSON-Code übergeben. In diesem Beispiel verwenden wir [Postman](https://www.getpostman.com/). Bevor Sie den-Befehl ausführen, müssen Sie den `Authorization` auf `Bearer Token` festlegen und das Token einfügen, das Sie zuvor abgerufen haben. Dadurch wird ein Header für Ihre Anforderung festgelegt. Weitere Informationen finden Sie im folgenden Screenshot.

![Postman Run Headers](media/big-data-cluster-consume-apps/postman_run_1.png)

Übergeben Sie im Anforderungs Text die Parameter an die APP, die Sie aufrufen, und legen Sie `content-type` auf `application/json`fest:

![Postman Run Body](media/big-data-cluster-consume-apps/postman_run_2.png)

Wenn Sie die Anforderung senden, erhalten Sie dieselbe Ausgabe wie beim Ausführen der APP über `azdata app run`:

![Ergebnis der Postman-Laufzeit](media/big-data-cluster-consume-apps/postman_result.png)

Sie haben die App nun erfolgreich über den Webdienst aufgerufen. Sie können ähnliche Schritte ausführen, um diesen Webdienst in Ihre Anwendung zu integrieren.

## <a name="next-steps"></a>Nächste Schritte

Weitere Beispiele finden Sie unter Beispiele für die [App](https://aka.ms/sql-app-deploy)-Bereitstellung.

Weitere Informationen zu SQL Server Big Data Clustern finden Sie unter [Was sind SQL Server 2019 Big Data Cluster?](big-data-cluster-overview.md).
