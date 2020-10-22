---
title: Bereitstellen von anderen Containern als dem Stammcontainer in Big Data-Clustern
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird beschrieben, wie Sie andere Container als den Stammcontainer in Big Data-Clustern in SQL Server bereitstellen.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 06/22/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e74e08146ea4c92f23ba17816738122147150e7b
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257120"
---
# <a name="non-root-big-data-clusters-containers"></a>Bereitstellen von anderen Containern als dem Stammcontainer in Big Data-Clustern

Mit dem fünften kumulativen Update (Cumulative Update 5, CU5) für SQL Server 2019 wurde Unterstützung für andere Container als den Stammcontainer eingeführt. Die Plattformimplementierung ist sicherer, da diese gewährleistet, dass alle im Big Data-Cluster (BDC) ausgeführten Containeranwendungen auf allen unterstützten Plattformen automatisch nicht als Root-Benutzer gestartet werden. Diese Funktionen sind für alle neuen Bereitstellungen verfügbar, die das Imagetag für das fünfte kumulative Update für SQL Server 2019 (CU5) verwenden. BDC-Bereitstellungen, die vor CU5 veröffentlicht wurden, sind von dieser Änderung nicht betroffen, und die Anwendungen in diesen Clustern werden weiterhin als Root-Benutzer ausgeführt. 

## <a name="technical-background"></a>Technischer Hintergrund

[In diesem technische Whitepaper](https://aka.ms/sql-bdc-openshift-security) erfahren Sie mehr zum Sicherheitsentwurf für die Bereitstellung von Benutzern, die keine Root-Benutzer sind. Dabei wird hervorgehoben, in welchem Umfang und warum Big Data-Cluster in bestimmten Fällen vorübergehend Berechtigungen erhöhen. Der Inhalt des Whitepapers wurde in Zusammenarbeit mit Sicherheitsexperten von SQL Server und Red Hat entwickelt und konzentriert sich auf Sicherheitskontexte und -funktionen in OpenShift. Die BDC-Sicherheitskonzepte sowie der entsprechende Sicherheitsentwurf sind jedoch auf alle unterstützten Plattformen übertragbar.

> [!NOTE]
> Zum Zeitpunkt der Veröffentlichung von CU5 wird der Setupschritt der Anwendungen, die mit [App Deploy](concept-application-deployment.md)-Schnittstellen bereitgestellt wurden, weiterhin als *Root*-Benutzer ausgeführt. Dies ist erforderlich, da während des Setups zusätzliche, von der Anwendung verwendete Pakete installiert werden. Anderer, als Teil der Anwendung bereitgestellter Benutzercode wird als Benutzer mit niedrigen Berechtigungen ausgeführt. 

> [!NOTE]
> Es wird empfohlen, den Cluster mit der Standardeinstellung, d. h. nicht mit der Stammeinstellung auszuführen. Falls Sie das Verhalten vor CU5 wiederherstellen möchten und einige Ihrer Container im BDC als `root`-Benutzer ausgeführt werden, können Sie das Standardverhalten mit dem neuen Featureoption `allowRunAsRoot` deaktivieren. Dieses kann nur zur Bereitstellungszeit festgelegt werden. Geben Sie die Einstellung zum Festlegen im Abschnitt `security` der Konfigurationsdatei der `control.json`-Bereitstellung an:

```json
 "security": {
  …
    "allowRunAsRoot": true,
  …
}
```

> [!IMPORTANT]
> Das Ändern dieser Einstellung wird für OpenShift-Umgebungen nicht unterstützt.

Wenn Dienste innerhalb des BDC mit einem anderen Benutzerkonto als dem Root-Benutzer ausgeführt werden, enthalten die Anmeldeinformationen, mit denen über den Gatewayendpunkt eine Verbindung mit Diensten hergestellt wird, nicht den `root`-Benutzernamen. Wenn mithilfe der Anwendung mit den falschen Anmeldeinformationen eine Verbindung mit dem Gatewayendpunkt hergestellt wird, wird ein Authentifizierungsfehler angezeigt. Der neue Benutzername für den Gatewayendpunkt basiert auf dem Wert, der von der Umgebungsvariablen `AZDATA_USERNAME` übergeben wurde. Es handelt sich hierbei um denselben Benutzernamen, der für den Controller und die SQL Server-Endpunkte verwendet wird. Dies betrifft nur neue Bereitstellungen. Bestehende Big Data-Cluster mit einem der vorherigen Releases verwenden weiterhin `root`. Es ergeben sich keine Auswirkungen auf Anmeldeinformationen, wenn der Cluster für die Active Directory-Authentifizierung konfiguriert wurde. 

## <a name="use-the-latest-azure-data-studio"></a>Verwenden der neuesten Version von Azure Data Studio

Azure Data Studio verarbeitet die Änderung der Anmeldeinformationen transparent für die Verbindung, die über das Gateway hergestellt wurde, um das Durchsuchen von HDFS im Objekt-Explorer oder das Senden von Spark-Aufträgen über Notebooks zu ermöglichen. Installieren Sie [die neueste Version des Insider-Builds von Azure Data Studio](../azure-data-studio/download-azure-data-studio.md#download-insiders-build-of-azure-data-studio). Dieser Build enthält die erforderlichen Änderungen für diesen Anwendungsfall.

In anderen Szenarios, in denen Sie Anmeldeinformationen für den Zugriff auf den Dienst über das Gateway angeben müssen (z. B. Anmelden mit [!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)], Zugreifen auf Webdashboards für Spark), sollten Sie sicherstellen, dass die richtigen Anmeldeinformationen verwendet werden. Wenn die Bereitstellung in einem vorhandenen Cluster erfolgen soll, der vor CU5 bereitgestellt wurde, verwenden Sie weiterhin den `root`-Benutzernamen, um eine Verbindung mit dem Gateway herzustellen. Dies gilt auch nachdem Sie den Cluster auf CU5 aktualisiert haben. Wenn Sie einen neuen Cluster mithilfe des CU5-Builds bereitstellen, melden Sie sich mithilfe des Benutzernamens an, der zur Umgebungsvariablen `AZDATA_USERNAME` gehört.

## <a name="configuration-file-switches"></a>Optionen in der Konfigurationsdatei

Ab CU5 wurden zwei neue Featureoptionen hinzugefügt, um die Sammlung von Pod- und Knotenmetriken zu steuern. Wenn Sie Ihre Kubernetes-Infrastruktur mithilfe verschiedener Lösungen überwachen, können Sie die integrierte Metriksammlung für Pods und Hostknoten deaktivieren, indem Sie `allowNodeMetricsCollection` und `allowPodMetricsCollection`* in der Bereitstellungskonfigurationsdatei `control.json` auf `false` festlegen. 

Beispiel: 

```json
"security": {
  ...
  "allowPodMetricsCollection": true,
  "allowNodeMetricsCollection": true,
  ...
}
```

> [!NOTE]
> Für OpenShift-Umgebungen werden diese Einstellungen in den integrierten Bereitstellungsprofilen automatisch auf FALSE festgelegt. Die Erfassung von Pod- und Knotenmetriken erforderte privilegierte Funktionen. Im empfohlenen Sicherheitskontext für OpenShift sind die Berechtigungen jedoch *eingeschränkt*.

Zusätzlich zu nicht privilegierten Containern werden Container ab CU5 in allen neuen BDC-Bereitstellungen und auf allen unterstützten Plattformen automatisch nicht als Root-Benutzer ausgeführt. Diese Funktionen sind für alle neuen Bereitstellungen verfügbar, die das Imagetag für das fünfte kumulative Update für SQL Server 2019 (CU5) verwenden. BDC-Bereitstellungen, die vor CU5 veröffentlicht wurden, sind nicht betroffen, und die Anwendungen in diesen Clustern werden weiterhin als Root-Benutzer ausgeführt.

## <a name="next-steps"></a>Nächste Schritte
[Bereitstellen von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] in Kubernetes](deployment-guidance.md)

[Bereitstellen von [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] in OpenShift](deploy-openshift.md)

[Whitepaper zur Sicherheit](https://aka.ms/sql-bdc-openshift-security)
