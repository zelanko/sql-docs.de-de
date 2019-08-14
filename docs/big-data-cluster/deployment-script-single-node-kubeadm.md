---
title: Bereitstellen mit einem Bash-Skript in einem Kubernetes-Einzelknotencluster
titleSuffix: SQL Server big data clusters
description: Verwenden Sie ein Bash-Bereitstellungsskript, um einen Big Data-Cluster für SQL Server 2019 (Vorschau) in einem Kubernetes-Einzelknotencluster bereitzustellen.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 37017221b636146a003f8af8890c655ed605bca9
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68473072"
---
# <a name="deploy-with-a-bash-script-to-a-single-node-kubeadm-cluster"></a>Bereitstellen mit einem Bash-Skript in einem Kubernetes-Einzelknotencluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial verwenden Sie ein Bash-Beispielbereitstellungsskript, um einen Kubernetes-Einzelknotencluster über kubeadm und in dem Cluster einen Big Data-Cluster für SQL Server bereitzustellen.  

## <a name="prerequisites"></a>Voraussetzungen

- Eine VM mit einem Vanilla-Ubuntu 18.04- oder 16.04-**Server**. Alle Abhängigkeiten werden vom Skript eingerichtet, und Sie führen das Skript aus der VM aus.

  > [!NOTE]
  > Das Verwenden von Azure-VMs wird noch nicht unterstützt.

- Die VM (virtueller Computer) muss mindestens 8 CPUs, 64 GB RAM und 100 GB Speicherplatz haben. Nachdem Sie alle Docker-Images für den Big Data-Cluster abgerufen haben, verbleiben Ihnen 50 GB für Daten und Protokolle, die für alle Komponenten verwendet werden.

## <a name="instructions"></a>Instructions

1. Laden Sie das Skript auf die VM herunter, die Sie für die Bereitstellung verwenden möchten.

   ```bash
   curl --output setup-bdc.sh https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/setup-bdc.sh
   ```

2. Machen Sie das Skript mit dem folgenden Befehl ausführbar.

   ```bash
   chmod +x setup-bdc.sh
   ```

3. Führen Sie das Skript mit **sudo** aus.

   ```bash
   sudo ./setup-bdc.sh
   ```

   Wenn Sie dazu aufgefordert werden, geben Sie das Kennwort an, das für die folgenden externen Endpunkte verwendet werden soll: Controller, SQL Server-Master und -Gateway. Der Benutzername für den Controller ist standardmäßig *admin*.

4. Richten Sie einen Alias für das **azdata**-Tool ein.

   ```bash
   source ~/.bashrc
   ```

5. Überprüfen Sie, ob der Alias funktioniert.

   ```bash
   azdata --version
   ```

## <a name="next-steps"></a>Nächste Schritte

Folgen Sie [diesem Tutorial](tutorial-load-sample-data.md), um die ersten Schritte zur Verwendung eines Big Data-Clusters auszuführen.
