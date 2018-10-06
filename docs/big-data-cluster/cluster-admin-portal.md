---
title: Überwachen eines Clusters mithilfe von Cluster-Verwaltungsportal | Microsoft-Dokumentation
description: ''
author: yualan
ms.author: alayu
manager: craigg
ms.date: 10/01/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 3ae85c9e9078b91589b828d1bee9d3218b5316cc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796407"
---
# <a name="introduction-to-the-cluster-administration-portal"></a>Einführung in das Verwaltungsportal für Cluster
Wenn Sie überwachen oder Ihre SQL Server-big Data-Cluster behandeln möchten, verwenden Sie das Verwaltungsportal für den Cluster. 

Das Cluster-Verwaltungsportal können Sie:
- Zeigen Sie Anzahl von Pods ausgeführt wird und Probleme schnell an
- Überwachen des Bereitstellungsstatus
- Die dienstverfügbarkeit Endpunkte anzeigen
- Ansichtscontroller und SQL Server-Masterinstanz.
- Durchsuchen Sie Informationen zu Pods, einschließlich Zugriff auf Grafana-Dashboards und Kibana-Protokolle

## <a name="access-the-cluster-administration-portal"></a>Zugriff auf das Verwaltungsportal für cluster
Führen Sie die [schnellstartanleitung aus, um Ihre big Data-Cluster bereitstellen](quickstart-big-data-cluster-deploy.md) bis Sie auf die **Cluster Verwaltungsportal** Abschnitt. Nachdem Sie die big Data-Cluster mit Mssqlctl ausgeführt haben, gehen Sie wie folgt vor:

Sobald der Controller-Pod ausgeführt wird, können Sie das Cluster-Verwaltungsportal, zum Überwachen der Bereitstellung. Sie können den Portalzugriff mithilfe der externen IP-Adresse und den Port für die `service-proxy-lb` (z. B.: **https://\<Ip-Adresse\>: 30777**). Anmeldeinformationen für den Zugriff auf die Administratorportal die Werte sind `CONTROLLER_USERNAME` und `CONTROLLER_PASSWORD` oben angegebenen Umgebungsvariablen.
> [!NOTE]
> Es wird eine sicherheitswarnung angezeigt werden, wenn die Webseite zugreifen, da wir automatisch generierte SSL-Zertifikate verwenden. In zukünftigen Versionen werden wir die Möglichkeit, eigene selbstsignierte Zertifikate bieten bieten.

## <a name="overview"></a>Übersicht
![Übersicht über die](./media/cluster-admin-portal/portal-overview.png)

Wenn Sie zunächst im Portal eingegeben haben, können Sie schnell die Anzahl von Pods auf anzeigen:
- Controller
- Master-Instanz
- Compute-Pool
- Speicherpool
- Datenpool

Wenn Probleme vorliegen, können Sie einen Link zu bekannten Problemen öffnen. Sie können den linken Navigationsbereich verwenden, um an den bestimmten Pool zu wechseln, wenn ein Problem vorliegt.

## <a name="deployment"></a>Bereitstellung
![Bereitstellung](./media/cluster-admin-portal/portal-deployment.png)

Um Ihrer Bereitstellung überwachen möchten, klicken Sie auf der Registerkarte "Bereitstellung" auf der linken Seite. Sie sehen eine Strukturansicht der Bereitstellung, und wenn Probleme, in der Bereitstellung vorliegen.

## <a name="service-endpoints"></a>Dienstendpunkte
![-Endpunkte](./media/cluster-admin-portal/portal-endpoints.png)

Sie können die verfügbaren Dienstendpunkte anzeigen, indem Sie auf der Registerkarte "Endpunkte" auf den linken Navigationsbereich auf.

Dies schließt Links zu Spark-Endgerät, Grafana-Dashboard und Kibana protokolliert.

## <a name="controller"></a>Controller
![Controller](./media/cluster-admin-portal/portal-controller.png)

Der Controller zeigt alle Pods, die im Zusammenhang mit dem Controller an. Weitere Informationen finden Sie Informationen zu den Controller [hier.](concept-controller.md)

Weitere zusätzliche Informationen zu jedem Pod zu finden, klicken Sie auf **Metriken** Spalte zum Anzeigen von Grafana-Dashboards.

Weitere Informationen zu Protokollen für Pods mit Problemen klicken Sie auf die **Protokolle** Spalte.

## <a name="master-instance"></a>Master-Instanz
![-Endpunkte](./media/cluster-admin-portal/portal-master.png)

Die Master-Instanz zeigt alle Pods, die im Zusammenhang mit der SQL Server-Masterinstanz. Weitere Informationen finden Sie Informationen zu den SQL Server-Masterinstanz [hier.](concept-master-instance.md)

Weitere zusätzliche Informationen zu jedem Pod zu finden, klicken Sie auf **Metriken** Spalte zum Anzeigen von Grafana-Dashboards.

Weitere Informationen zu Protokollen für Pods mit Problemen klicken Sie auf die **Protokolle** Spalte.

## <a name="pool-and-pod-pages"></a>Pools und Pod-Seiten
![Pool](./media/cluster-admin-portal/portal-data-pool.png)

Auf jeder Poolauslagerungsseite (Compute, Speicher und Daten), Sie können einen Drilldown zum jede der Pod Seiten durch Klicken auf **Standard**

![Pod](./media/cluster-admin-portal/portal-data-default-pool.png)

Dadurch wird die Breadcrumb am oberen Rand der Drilldown Pfad.

Weitere zusätzliche Informationen zu jedem Pod zu finden, klicken Sie auf **Metriken** Spalte zum Anzeigen von Grafana-Dashboards.

Weitere Informationen zu Protokollen für Pods mit Problemen klicken Sie auf die **Protokolle** Spalte.

Weitere Informationen zu jedem Pool:
- [Compute-pool](concept-compute-pool.md)
- [Speicherpool](concept-storage-pool.md)
- [Datenpool](concept-data-pool.md)

## <a name="about-page"></a>Zu den Seiten
![Informationen zu](./media/cluster-admin-portal/portal-about.png)

Hier sehen Sie Informationen zu Ihrem Cluster wie die unterschiedliche Versionsnummern, Container und einen Link in der Dokumentation.
