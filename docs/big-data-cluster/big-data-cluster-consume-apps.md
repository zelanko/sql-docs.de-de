---
title: Nutzen Sie Anwendungen für big Data-Cluster
titleSuffix: SQL Server 2019 big data clusters
description: Nutzen Sie eine Anwendung, die auf SQL Server-2019 big Data-Cluster mithilfe einer RESTful-Web-Diensts (Vorschauversion) bereitgestellt.
author: jeroenterheerdt
ms.author: jterh
manager: craigg
ms.date: 03/18/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.reviewer: rothja
ms.openlocfilehash: a9ef02cae7899a1deb5ce6d84b10dac2297b9d2f
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "58389958"
---
# <a name="consume-an-app-deployed-on-sql-server-big-data-cluster-using-a-restful-web-service"></a>Nutzen einer app, die auf SQL Server-big Data-Cluster mit einem RESTful-Webdienst bereitgestellt

Dieser Artikel beschreibt, wie eine app, die auf eine SQL Server-2019 big Data-Cluster mithilfe einer RESTful-Web-Diensts (Vorschauversion) bereitgestellt wird.

## <a name="prerequisites"></a>Erforderliche Komponenten

- [SQL Server-2019 big Data-cluster](deployment-guidance.md)
- [Mssqlctl-Befehlszeilen-Hilfsprogramm](deploy-install-mssqlctl.md)
- Eine app bereitgestellt wird, entweder [ `mssqlctl` ](big-data-cluster-create-apps.md) oder [Bereitstellen von App-Erweiterung](app-deployment-extension.md)

## <a name="capabilities"></a>Funktionen

Nachdem Sie eine Anwendung in Ihrer SQL Server-2019 big Data-Cluster (Vorschau) bereitgestellt haben, können Sie Zugriff auf und nutzen die Anwendung mit einer RESTful-Webdienst. Dies ermöglicht die Integration der app von anderen Anwendungen oder Diensten (z. B. eine mobile app oder Website). Die folgende Tabelle beschreibt die Befehle der Anwendung-Bereitstellung, mit denen Sie mit **Mssqlctl** zum Abrufen von Informationen über den RESTful-Web-Dienst für Ihre app.

|Befehl |Description |
|:---|:---|
|`mssqlctl app describe` | Beschreiben Sie die Anwendung. |

Erhalten Sie Hilfe bei der `--help` Parameter wie im folgenden Beispiel gezeigt:

```bash
mssqlctl app describe --help
```

In den folgenden Abschnitten wird beschrieben, wie einen Endpunkt für eine Anwendung abgerufen und mit RESTful-Webdienst für die Anwendungsintegration funktioniert.

## <a name="retrieve-the-endpoint"></a>Abrufen des Endpunkts

Die **Mssqlctl-app beschrieben** Befehl enthält ausführliche Informationen zu der app, einschließlich der Endpunkt in Ihrem Cluster. Dies wird normalerweise durch ein app-Entwickler verwendet, zum Erstellen einer app mithilfe des Swagger-Clients und mithilfe des Webdiensts für die Interaktion mit der app RESTful-basiert.

Beschreiben Sie Ihre app einen ähnelt dem folgenden Befehl ausführen:

```bash
mssqlctl app describe --name addpy --version v1
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

Beachten Sie die IP-Adresse (`10.1.1.3` in diesem Beispiel) und die Portnummer (`30777`) in der Ausgabe.

## <a name="generate-a-jwt-access-token"></a>Generieren Sie ein JWT-Zugriffstoken

Um den RESTful-Web-Dienst für die app zugreifen, die Sie bereitgestellt haben müssen Sie zuerst ein JWT-Zugriffstoken zu generieren. Öffnen Sie die folgende URL in Ihrem Browser: `https://[IP]:[PORT]/api/docs/swagger.json` mithilfe die IP-Adresse und den Port, die Sie ausführen abgerufen haben die `describe` obigen Befehl. Müssen Sie die Anmeldung mit der gleichen Anmeldeinformationen für die Verwendung `mssqlctl login`.

Fügen Sie den Inhalt der `swagger.json` in der [Swagger Editor](https://editor.swagger.io) zu verstehen, welche Methoden zur Verfügung stehen:

![API-Swagger](media/big-data-cluster-consume-apps/api_swagger.png)

Beachten Sie, dass die `app` GET-Methode als auch die `token` POST-Methode. Da die Authentifizierung für apps JWT-Token verwendet, müssen Sie zum Abrufen eines Tokens, meine mit Ihrem bevorzugten Tool POST-Aufruf an die `token` Methode. Hier ist ein Beispiel dafür, wie Sie genau das tun, [Postman](https://www.getpostman.com/):

![Postman-Token](media/big-data-cluster-consume-apps/postman_token.png)

Das Ergebnis dieser Anforderung erhalten Sie ein JWT `access_token`, die Sie benötigen, die zum Ausführen der app-URL aufrufen.

## <a name="execute-the-app-using-the-restful-web-service"></a>Führen Sie die app mithilfe von RESTful-Webdienst

> [!NOTE]
> Wenn Sie möchten, können Sie öffnen die URL für die `swagger` , die zurückgegeben wurde, bei der Ausführung `mssqlctl app describe --name [appname] --version [version]` in Ihrem Browser, sein sollte ähnlich wie `https://[IP]:[PORT]/api/app/[appname]/[version]/swagger.json`. Müssen Sie die Anmeldung mit der gleichen Anmeldeinformationen für die Verwendung `mssqlctl login`. Den Inhalt der `swagger.json` können Sie in einfügen [Swagger Editor](https://editor.swagger.io). Sie sehen, dass der Webdienst stellt die `run` Methode. Beachten Sie auch die Basis-URL, die am oberen Rand angezeigt.

Sie können Ihr bevorzugte Tool verwenden, zum Aufrufen der `run` Methode (`https://[IP]:30778/api/app/[appname]/[version]/run`), und übergeben Sie die Parameter im Text der POST-Anforderung im JSON-Format. In diesem Beispiel verwenden wir [Postman](https://www.getpostman.com/). Vor dem Aufruf aus, Sie benötigen, legen Sie die `Authorization` zu `Bearer Token` und fügen Sie in das Token, die Sie zuvor abgerufen haben. Dadurch wird einen Header bei der Anforderung festgelegt. Sehen Sie sich hierzu folgendes Bildschirmfoto an.

![Führen Sie Postman Header](media/big-data-cluster-consume-apps/postman_run_1.png)

Als Nächstes die Parameter im Text Anforderungen an die app, die Sie aufrufen, und legen Sie übergeben die `content-type` zu `application/json`:

![Führen Sie Postman Text](media/big-data-cluster-consume-apps/postman_run_2.png)

Wenn Sie die Anforderung senden, erhalten Sie dieselbe Ausgabe wie bei der Ausführung der app über `mssqlctl app run`:

![Ergebnis der Ausführung postman](media/big-data-cluster-consume-apps/postman_result.png)

Sie haben nun die app über den Webdienst erfolgreich aufgerufen. Sie können ähnliche Schritte, um diesen Webdienst in Ihrer Anwendung zu integrieren.

## <a name="next-steps"></a>Nächste Schritte

Sie können auch zusätzliche Beispiele Auschecken [Beispiele für das Bereitstellen von Apps](https://aka.ms/sql-app-deploy).

Weitere Informationen zu SQL Server-big Data-Clustern, finden Sie unter [was SQL Server-2019 big Data-Cluster sind?](big-data-cluster-overview.md).
