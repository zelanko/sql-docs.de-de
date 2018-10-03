---
title: Erweitern die Funktionalität von Azure Data Studio | Microsoft-Dokumentation
description: Informationen Sie zum Erweitern von Azure Data Studio
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.prod_service: sql-tools
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b458234f0a166f3dc820cbfa58269bb90d7c33b2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "48038491"
---
# <a name="getting-started-with-includename-sosincludesname-sos-shortmd-extensibility"></a>Erste Schritte mit [!INCLUDE[name-sos](../includes/name-sos-short.md)] Erweiterbarkeit

[!INCLUDE[name-sos](../includes/name-sos.md)] verfügt über mehrere Mechanismen zur Erweiterbarkeit Anpassung der benutzerumgebung und diese Anpassungen für der gesamte Benutzercommunity zur Verfügung stellen. Die wichtigsten [!INCLUDE[name-sos](../includes/name-sos.md)] Plattform basiert auf Visual Studio Code, sodass die meisten der Visual Studio Code-Erweiterbarkeits-APIs verfügbar sind. Darüber hinaus haben wir Weitere Erweiterungspunkte für Data Management-spezifische Aktivitäten bereitgestellt.

Einige der wichtigsten Erweiterungspunkte sind:

- Visual Studio Code-Erweiterbarkeits-APIs
- Tools zum Erstellen von Azure Data Studio-Erweiterung
- Verwalten von Dashboard-Registerkarte Bereich Beiträge
- Einblicke mit Aktionen Erfahrungen
- Azure Data Studio-Erweiterbarkeits-APIs
- Benutzerdefinierte Anbieter-APIs

## <a name="visual-studio-code-extensibility-apis"></a>Visual Studio Code-Erweiterbarkeits-APIs

Da die wichtigsten [!INCLUDE[name-sos](../includes/name-sos.md)] Plattform baut auf Visual Studio Code, Details zu den Visual Studio Code-Erweiterungs-APIs befinden sich die [Extension Authoring](https://code.visualstudio.com/docs/extensions/overview) und [Erweiterungs-API](https://code.visualstudio.com/docs/extensionAPI/overview) die Dokumentation auf der Visual Studio Code-Website.

## <a name="manage-dashboard-tab-panel-contributions"></a>Verwalten von Dashboard-Registerkarte Bereich Beiträge

Weitere Informationen finden Sie unter [Beitrag Punkte](#contribution-points) und [Kontextvariablen](#context-variables).

## <a name="azure-data-studio-extensibility-apis"></a>Azure Data Studio-Erweiterbarkeits-APIs

Weitere Informationen finden Sie unter [Erweiterbarkeits-APIs](extensibility-apis.md).


## <a name="contribution-points"></a>Beitrag zeigt

Dieser Abschnitt behandelt die verschiedenen Beitrag Punkte, die im Erweiterungsmanifest "Package.JSON" definiert sind.

IntelliSense wird innerhalb von Azuredatastudio unterstützt.

## <a name="contributes-dashboard"></a>Dashboard beitragen

Tragen Sie die Registerkarte "," Container "," Insight-Widgets zum Dashboard.

![Dashboard](media/extensibility/dashboard-page.png)

`dashboard.tabs`

Dashboard.Tabs wird die Registerkarte Abschnitte in der Dashboard-Seite erstellt. Es erwartet ein Objekt oder ein Array von Objekten.  

```json
"dashboard.tabs": [
{
    "id": "test-tab1",
    "title": "Test 1",
    "description": "The test 1 displays a list of widgets.",
    "when": "connectionProvider == 'MSSQL' && !mssql:iscloud",
    "alwaysShow": true,
    "container": {
        …
    }
}
]
```

`dashboard.containers`

Anstatt Dashboard Container Inline (im Rahmen der dashboard.tab). Sie können den Container mithilfe der dashboard.containers registrieren. Es akzeptiert ein Objekt oder ein Array des Objekts.

```json
"dashboard.containers": [
{
    "id": "innerTab1",
    "container": {
        …
    }
},
{
    "id": "innerTab2",
    "container": {
       …
    }
}
]
```

Geben Sie zum Verweisen auf den registrierten Container. die Id des Containers

```json
"dashboard.tabs": [
{
    ...
    "container": {
        "innerTab1": {             
        }
    }
}
]

```

`dashboard.insights`

Sie können mithilfe von dashboard.insights Insights registrieren. Dies ist vergleichbar mit [Tutorial: erstellen ein benutzerdefinierten Einblicks-Widgets](https://docs.microsoft.com/en-us/sql/sql-operations-studio/tutorial-build-custom-insight-sql-server)

```json
"dashboard.insights": {
"id": "my-widget"
"type": {
    "count": {
        "dataDirection": "vertical",
        "dataType": "number",
        "legendPosition": "none",
           "labelFirstColumn": false,
        "columnsAsLabels": false
       }
   },
   "queryFile": "{your file folder}/activeSession.sql"
}
```


### <a name="dashboard-container-types"></a>Dashboard-Containertypen

Derzeit stehen vier unterstützten Containertypen:

1. `widgets-container`

    ![Widgets-container](media/extensibility/widgets-container.png)

    Die Liste von Widgets, die im Container angezeigt werden. Es ist eine Flow-Layout. Er akzeptiert die Liste von Widgets.

    ```json
    "container": {
        "widgets-container": [
        {
            "widget": {
                "query-data-store-db-insight": {
                }
            }
        },
        {
            "widget": {
                "explorer-widget": {
                }
            }
        }
      ]
    }
    ```

2. `webview-container`

    ![WebView-container](media/extensibility/webview-container.png)

    Die Webansicht werden in den gesamten Container angezeigt. Es erwartet, dass Webview-Id zu, dass dem Registerkarten-ID übereinstimmt

    ```json
    "container": {
        "webview-container": null
    }
    ```

3. `grid-container`

   !["Grid"-Container](media/extensibility/grid-container.png)

   Die Liste der Widgets oder Webviews, die im Rasterlayout angezeigt werden

    ```json
    "container": {
        "grid-container": [
        {
            "name": "widget 1",
            "widget": {
                "explorer-widget": {
                }
            },
            "row":0,
            "col":0
        },
        {
            "name": "widget 2",
            "widget": {
                "tasks-widget": {
                    "backup", 
                    "restore",
                    "configureDashboard",
                    "newQuery"
                }
            },
            "row":0,
            "col":1
        },
        {
            "name": "Webview 1",
            "webview": {
                "id": "google"
            },
            "row":1,
            "col":0,
            "colspan":2
        },
        {
            "name": "widget 3",
            "widget": {
                "explorer-widget": {}
            },
            "row":0,
            "col":3,
            "rowspan":2
        },
    ]
    ```

4.  `nav-section`

    ![NAV-Abschnitt](media/extensibility/nav-section.png)

    Im Abschnitt für die Navigation wird im Container angezeigt werden

    ```json
    "container": {
        "nav-section": [
            {
                "id": "innerTab1",
                "title": "inner-tab1",
                "icon": {
                    "light": "./icons/tab1Icon.svg",
                    "dark": "./icons/tab1Icon_dark.svg"
                }
                "container": {
                    …
                }
            },
            {
                "id": "innerTab2",
                "title": "inner-tab2",
                "icon": {
                    "light": "./icons/tab2Icon.svg",
                    "dark": "./icons/tab2Icon_dark.svg"
                }
                "container": {
                    …
                }
            }
        ]
    }
    ```



## <a name="context-variables"></a>Kontextvariablen

Allgemeine Informationen zu Kontext in Visual Studio Code und anschließend auf Azure Data Studio, finden Sie unter [Erweiterbarkeit](https://code.visualstudio.com/docs/extensionAPI/extension-points#_example).

In Azure Data Studio haben wir die spezifischen Kontext zu Datenbankverbindungen für Erweiterungen verfügbar.

### <a name="dashboard"></a>Dashboard

Im Dashboard bieten wir die folgenden Kontextvariablen:

|Kontextvariablen| description|
|:---|:---|
|`connectionProvider` | Eine Zeichenfolge des Bezeichners für den Anbieter der aktuellen Verbindung. Ex. `connectionProvider == 'MSSQL'`. installiert haben.|
|`serverName`|Eine Zeichenfolge mit den Namen des die aktuelle Verbindung. Ex. `serverName == 'localhost'`. installiert haben.|
|`databaseName` | Eine Zeichenfolge mit der Datenbankname des die aktuelle Verbindung. Ex. `databaseName == 'master'`. installiert haben.|
|`connection` | Das Profilobjekt für vollständige Verbindungszeichenfolge für die aktuelle Verbindung (IConnectionProfile)|
|`dashboardContext` | Eine Zeichenfolge mit dem Kontext der Seite des Dashboards befindet sich derzeit auf. 'Database' oder 'Server'. Ex. `dashboardContext == 'database'`|
