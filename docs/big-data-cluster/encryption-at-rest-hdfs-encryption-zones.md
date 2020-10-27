---
title: Leitfaden zur Verwendung von SQL Server HDFS-Verschlüsselungszonen für Big Data-Cluster
titleSuffix: SQL Server big data clusters
description: In diesem Artikel wird gezeigt, wie Sie die SQL Server HDFS-Verschlüsselungszonenfunktion von BDC verwenden.
author: DaniBunny
ms.author: dacoelho
ms.reviewer: mihaelab
ms.date: 10/19/2020
ms.topic: tutorial
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 904b07913a63e226e5e45876f2fc520226411223
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92199568"
---
# <a name="sql-server-big-data-clusters-hdfs-encryption-zones-usage-guide"></a>Leitfaden zur Verwendung von SQL Server HDFS-Verschlüsselungszonen für Big Data-Cluster

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Leitfaden wird veranschaulicht, wie Sie Verschlüsselungsfunktionen für ruhende Daten von SQL Server Big Data-Clustern verwenden, um HDFS-Ordner mithilfe von Verschlüsselungszonen zu verschlüsseln.

Beachten Sie, dass unter __```/securelake```__ bereits eine einsatzbereite Standardverschlüsselungszone eingebunden ist. Sie wurde mit einem vom System generierten 256-Bit-Schlüssel namens __securelakekey__ erstellt. Mit diesem Schlüssel können Sie zusätzliche Verschlüsselungszonen erstellen.

## <a name="prerequisites"></a><a id="prereqs"></a> Voraussetzungen

- [SQL Server-Big Data-Cluster CU8](release-notes-big-data-cluster.md) mit Active Directory-Integration.
- Benutzer mit Administratorrechten.

## <a name="login-into-the-name-node"></a>Anmelden beim Namensknoten

Befolgen Sie die [Anweisungen für Active Directory-Verbindungen](active-directory-connect.md), um eine Clusteranmeldung durchzuführen. Melden Sie sich beim „namenode“ (nmnode-0-0) an, um Schlüssel- und Verschlüsselungszonenbefehle auszugeben.

   ```console
   kubectl exec -it -c hadoop -n <cluster_namespace> nmnode-0-0 -- /bin/bash
   ```

## <a name="create-an-encryption-zone-using-the-provided-system-managed-key"></a>Erstellen einer Verschlüsselungszone mithilfe des bereitgestellten, systemseitig verwalteten Schlüssels

1. Erstellen eines HDFS-Ordners

   ```console
   hdfs dfs -mkdir -p /user/zone/folder
   ```

1. Geben Sie den Befehl zum Erstellen der Verschlüsselungszone aus, um den Ordner mit dem Schlüssel __securelakekey__ zu verschlüsseln.

   ```console
   hdfs crypto -createZone -keyName securelakekey -path /user/zone/folder
   ```

## <a name="create-a-custom-new-key-and-encryption-zone"></a>Erstellen eines benutzerdefinierten neuen Schlüssels und einer Verschlüsselungszone

1. Verwenden Sie folgendes Muster, um einen 256-Bit-Schlüssel zu erstellen.

   ```console
   kinit hdfs
   hadoop key create mydatalakekey -size 256
   ```

1. Erstellen und verschlüsseln Sie einen neuen HDFS-Pfad mithilfe des Benutzerschlüssels.

   ```console
   hdfs dfs -mkdir -p /user/mydatalake
   hdfs crypto -createZone -keyName mydatalakekey -path /user/mydatalake
   ```
