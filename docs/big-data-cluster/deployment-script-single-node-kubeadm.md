---
title: Bereitstellen mit einem Bash-Skript in einem Kubernetes-Einzelknotencluster
titleSuffix: SQL Server big data clusters
description: Verwenden Sie ein Bash-Bereitstellungs Skript zum Bereitstellen einer [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] für einen kubeadm-Cluster mit einem einzelnen Knoten.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 2379f96e3b5288fc33f5c925613bf9fd5d35612d
ms.sourcegitcommit: c4875c097e3aae1b76233777d15e0a0ec8e0d681
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71341837"
---
# <a name="deploy-with-a-bash-script-to-a-single-node-kubeadm-cluster"></a>Bereitstellen mit einem Bash-Skript in einem Kubernetes-Einzelknotencluster

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

In diesem Tutorial verwenden Sie ein Bash-Beispielbereitstellungsskript, um einen Kubernetes-Einzelknotencluster über kubeadm und in dem Cluster einen Big Data-Cluster für SQL Server bereitzustellen.  

## <a name="prerequisites"></a>Erforderliche Komponenten

- Einen virtuellen oder physischen Computer mit einem Vanille-Ubuntu 18,04-oder 16,04- **Server** . Alle Abhängigkeiten werden vom Skript eingerichtet, und Sie führen das Skript aus der VM aus.

  > [!NOTE]
  > Die Verwendung von Azure-Linux-VMs wird noch nicht unterstützt.

- Der virtuelle Computer muss über mindestens 8 CPUs, 64 GB RAM und 100 GB Speicherplatz verfügen. Nachdem Sie alle Docker-Images für den Big Data-Cluster abgerufen haben, verbleiben Ihnen 50 GB für Daten und Protokolle, die für alle Komponenten verwendet werden.

- Aktualisieren Sie vorhandene Pakete mithilfe der folgenden Befehle, um sicherzustellen, dass das Betriebssystem Image auf dem neuesten Stand ist.

   ``` bash
   sudo apt update && sudo apt upgrade -y
   sudo systemctl reboot
   ```

## <a name="recommended-virtual-machine-settings"></a>Empfohlene Einstellungen für virtuelle Computer

1. Verwenden Sie die statische Arbeitsspeicher Konfiguration für den virtuellen Computer. Beispielsweise wird in Hyper-V-Installationen nicht die dynamische Speicher Belegung verwendet, sondern stattdessen die empfohlenen 64 GB oder höher zugeordnet.

1. Verwenden Sie die Prüfpunkt-oder Momentaufnahme Funktion in Ihrem Hypervisor, damit Sie einen Rollback für den virtuellen Computer ausführen können.


## <a name="instructions-to-deploy-sql-server-big-data-cluster"></a>Anweisungen zum Bereitstellen von SQL Server Big Data-Cluster

1. Laden Sie das Skript auf die VM herunter, die Sie für die Bereitstellung verwenden möchten.

   ```bash
   curl --output setup-bdc.sh https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/setup-bdc.sh
   ```

2. Machen Sie das Skript mit dem folgenden Befehl ausführbar.

   ```bash
   chmod +x setup-bdc.sh
   ```

3. Ausführen des Skripts (stellen Sie sicher, dass Sie mit *sudo*ausführen)

   ```bash
   sudo ./setup-bdc.sh
   ```

   Wenn Sie dazu aufgefordert werden, geben Sie das Kennwort an, das für die folgenden externen Endpunkte verwendet werden soll: Controller, SQL Server-Master und -Gateway. Das Kennwort sollte basierend auf den vorhandenen Regeln für SQL Server Kennwort ausreichend komplex sein. Der Benutzername für den Controller ist standardmäßig *admin*.

4. Richten Sie einen Alias für das **azdata**-Tool ein.

   ```bash
   source ~/.bashrc
   ```

5. Aktualisieren Sie Alias Setup für azdata.

   ```bash
   azdata --version
   ```

## <a name="cleanup"></a>Bereinigen

Das [Cleanup-BDC.sh](https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/cleanup-bdc.sh) -Skript wird als praktische Hilfe bereitgestellt, um die Umgebung bei Bedarf zurückzusetzen. Es empfiehlt sich jedoch, einen virtuellen Computer zu Testzwecken zu verwenden und die Momentaufnahme Funktion in Ihrem Hypervisor zu verwenden, um einen Rollback für den virtuellen Computer in einen sauberen Zustand auszuführen.

## <a name="next-steps"></a>Nächste Schritte

Informationen zu den ersten Schritten mit der Verwendung von Big Data Clustern finden Sie im [tutorial: Laden von Beispiel Daten in eine SQL Server Big Data Cluster @ no__t-0.
