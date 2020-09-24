---
title: Installieren von azdata mit yum
titleSuffix: ''
description: Hier erfahren Sie, wie Sie das Tool „azdata“ mit yum installieren.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: eae81ccee65899335b161b3a32fbb260d0a8517a
ms.sourcegitcommit: d56f1eca807c55cf606a6316f3872585f014fec1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90914893"
---
# <a name="install-azdata-with-yum"></a>Installieren von `azdata` mit yum

Für Linux-Distributionen mit `yum` gibt es ein Paket für die `azdata-cli`. Das CLI-Paket wurde mit den folgenden Linux-Versionen getestet, die `yum` verwenden:

- RHEL 7, RHEL 8


[!INCLUDE [azdata-package-installation-remove-pip-install](../../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-yum"></a>Installieren mit yum

>[!IMPORTANT]
> Das RPM-Paket von `azdata-cli` ist vom Python 3-Paket abhängig. Auf Ihrem System handelt es sich dabei möglicherweise um eine ältere Python-Version als die erforderliche *Version 3.6.x*. Sollte dies ein Problem für Sie darstellen, ersetzen Sie das Python 3-Paket, oder führen Sie die Anweisungen zur manuellen Installation mit [`pip`](../install/deploy-install-azdata-pip.md) aus.

1. Importieren Sie den Microsoft-Repositoryschlüssel.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

1. Erstellen Sie lokale Repositoryinformationen.

   Führen Sie für einen RHEL 7-Client Folgendes aus:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/prod.repo
   ```
  
   Führen Sie für einen RHEL 8-Client Folgendes aus:

   ```bash
   sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/8/prod.repo
   ```

1. Installieren Sie das Paket mit dem Befehl `yum install`.

   ```bash
   sudo yum install azdata-cli
   ```

## <a name="verify-install"></a>Überprüfen der Installation

```
azdata
azdata --version
```

## <a name="update"></a>Aktualisieren

Aktualisieren Sie die `azdata-cli` mit dem Befehl `yum update`.

```bash
sudo yum update azdata-cli
```

## <a name="uninstall"></a>Deinstallieren

1. Entfernen Sie das Paket aus Ihrem System.

   ```bash
   sudo yum remove azdata-cli
   ```

1. Entfernen Sie die Repositoryinformationen, wenn Sie nicht planen, `azdata-cli` neu zu installieren.

   ```bash
   sudo rm /etc/yum.repos.d/azdata-cli.repo
   ```

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Big Data-Clustern finden Sie unter [Was sind [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ver15.md)]?](../../big-data-cluster/big-data-cluster-overview.md).

Verwenden von azdata mit [Azure Arc-fähigen Datendiensten](/azure/azure-arc/data/)
