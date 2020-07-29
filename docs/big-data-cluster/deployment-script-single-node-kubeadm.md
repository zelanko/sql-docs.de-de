---
title: Bereitstellen eines kubeadm-Clusters mit einem einzelnen Knoten
titleSuffix: SQL Server Big Data Clusters
description: Verwenden Sie ein Bash-Bereitstellungsskript, um einen Big Data-Cluster für SQL Server 2019 in einem kubeadm-Einzelknotencluster bereitzustellen.
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ad5509d3718c0ccd579893d1b260e558437b882a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730657"
---
# <a name="deploy-with-a-bash-script-to-a-single-node-kubeadm-cluster"></a>Bereitstellen mit einem Bash-Skript in einem Kubernetes-Einzelknotencluster

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Tutorial verwenden Sie ein Bash-Beispielbereitstellungsskript, um einen Kubernetes-Einzelknotencluster über kubeadm und in dem Cluster einen Big Data-Cluster für SQL Server bereitzustellen.

## <a name="prerequisites"></a>Voraussetzungen

- Ein virtueller oder physischer Computer mit einem Vanilla-Ubuntu 18.04- oder 16.04-**Server**. Alle Abhängigkeiten werden vom Skript eingerichtet, und Sie führen das Skript aus der VM aus.

  > [!NOTE]
  > Das Verwenden von Azure Linux-VMs wird noch nicht unterstützt.

- Die VM (virtueller Computer) muss mindestens 8 CPUs, 64 GB RAM und 100 GB Speicherplatz haben. Nachdem Sie alle Docker-Images für den Big Data-Cluster abgerufen haben, verbleiben Ihnen 50 GB für Daten und Protokolle, die für alle Komponenten verwendet werden.

- Aktualisieren Sie vorhandene Pakete mithilfe der folgenden Befehle, um sicherzustellen, dass das Betriebssystemimage auf dem neuesten Stand ist.

   ``` bash
   sudo apt update && sudo apt upgrade -y
   sudo systemctl reboot
   ```

## <a name="recommended-virtual-machine-settings"></a>Empfohlene Einstellungen für den virtuellen Computer

1. Verwenden Sie für den virtuellen Computer eine statische Arbeitsspeicherkonfiguration. Verwenden Sie beispielsweise in Hyper-V-Installationen keine dynamische Speicherbelegung, sondern belegen Sie mindestens die empfohlenen 64 GB.

1. Verwenden Sie eine Prüfpunkt- oder Momentaufnahmefunktion in Ihrem Hypervisor, sodass Sie den virtuellen Computer in einen fehlerfreien Zustand zurücksetzen können.


## <a name="instructions-to-deploy-sql-server-big-data-cluster"></a>Anleitung zum Bereitstellen von Big Data-Clustern für SQL Server

1. Laden Sie das Skript auf die VM herunter, die Sie für die Bereitstellung verwenden möchten.

   ```bash
   curl --output setup-bdc.sh https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/setup-bdc.sh
   ```

2. Machen Sie das Skript mit dem folgenden Befehl ausführbar.

   ```bash
   chmod +x setup-bdc.sh
   ```

3. Führen Sie das Skript aus. (Verwenden Sie hierzu *sudo*.)

   ```bash
   sudo ./setup-bdc.sh
   ```

   Wenn Sie dazu aufgefordert werden, geben Sie das Kennwort an, das für die folgenden externen Endpunkte verwendet werden soll: Controller, SQL Server-Master und -Gateway. Das Kennwort muss gemäß der vorhandenen Regeln für SQL Server-Kennwörter ausreichend komplex sein. Der Benutzername für den Controller ist standardmäßig *admin*.

4. Richten Sie einen Alias für das **azdata**-Tool ein.

   ```bash
   source ~/.bashrc
   ```

5. Aktualisieren Sie die Aliaseinrichtung für azdata.

   ```bash
   azdata --version
   ```

## <a name="cleanup"></a>Cleanup

Das Skript [cleanup-bdc.sh](https://raw.githubusercontent.com/microsoft/sql-server-samples/master/samples/features/sql-big-data-cluster/deployment/kubeadm/ubuntu-single-node-vm/cleanup-bdc.sh) wird als praktische Hilfe bereitgestellt, um die Umgebung ggf. zurücksetzen zu können. Es wird jedoch empfohlen, einen virtuellen Computer zu Testzwecken und die Momentaufnahmefunktion im Hypervisor zu verwenden, um den virtuellen Computer in einen fehlerfreien Zustand zurückzusetzen.

## <a name="next-steps"></a>Nächste Schritte

Informationen zu den ersten Schritten zur Verwendung von Big Data-Clustern finden Sie unter [Tutorial: Laden von Beispieldaten in einen Big Data-Cluster für SQL Server](tutorial-load-sample-data.md).
