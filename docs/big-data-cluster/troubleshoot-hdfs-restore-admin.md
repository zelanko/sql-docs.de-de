---
title: Wiederherstellen von HDFS-Berechtigungen
titleSuffix: SQL Server Big Data Cluster
description: TRestore von HDFS-Administratorrechten
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mikeray
ms.date: 04/21/2020
ms.topic: how-to
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: c6d09921074ca2f2e386535baff5060620a7a3c8
ms.sourcegitcommit: 4cb53a8072dbd94a83ed8c7409de2fb5e2a1a0d9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83669387"
---
# <a name="restore-hdfs-permissions"></a>Wiederherstellen von HDFS-Berechtigungen

Änderungen an den HDFS-Zugriffssteuerungslisten (ACLs) haben möglicherweise Auswirkungen auf die Ordner `/system` und `/tmp` in HDFS. Die wahrscheinlichste Ursache von ACL-Änderungen ist ein Benutzer, der die Ordner-ACLs manuell bearbeitet. Das direkte Ändern von Berechtigungen im Ordner „/system“ und im Ordner „/tmp/logs“ wird nicht unterstützt.

## <a name="symptom"></a>Symptom

Ein Spark-Auftrag wird über ADS eingereicht, dessen Ausführung mit einem SparkContext-Initialisierungsfehler und einer AccessControlException fehlschlägt.

```
583 ERROR spark.SparkContext: Error initializing SparkContext.
org.apache.hadoop.security.AccessControlException: Permission denied: user=<UserAccount>, access=WRITE, inode="/system/spark-events":sph:BDCAdmin:drwxr-xr-x
```

Auf der Yarn-Benutzeroberfläche wird als Status der Anwendungs-ID KILLED angegeben.

Versuche, als Domänenbenutzer in den Ordner zu schreiben, schlagen ebenfalls fehl. Sie können das mit dem folgenden Beispiel überprüfen:

```bash
kinit <UserAccount>
hdfs dfs -touch /system/spark-events/test
hdfs dfs -rm /system/spark-events/test
```

## <a name="cause"></a>Ursache

Die HDFS ACLs wurden für die Domänensicherheitsgruppe des BDC-Benutzers geändert. Zu den möglichen Änderungen gehörten ACLs für die Ordner „/system“ und „/tmp“. Änderungen dieser Ordner werden nicht unterstützt.

Überprüfen Sie die Wirkung in den Livy-Protokollen:

```
INFO utils.LineBufferedStream: YYYY-MM-DD-HH:MM:SS,858 INFO yarn.Client: Application report for application_1580771254352_0041 (state: ACCEPTED)
...
WARN rsc.RSCClient: Client RPC channel closed unexpectedly.
INFO interactive.InteractiveSession: Failed to ping RSC driver for session <ID>. Killing application
```

Auf der YARN-Benutzeroberfläche wird der Status von Anwendungen für die Anwendungs-ID mit KILLED angezeigt.

Um die Grundursache für das Schließen der RPC-Verbindung zu ermitteln, überprüfen Sie das YARN-Anwendungsprotokoll auf Apps, die der Anwendung entsprechen. Im vorherigen Beispiel verweist dies auf `application_1580771254352_0041`. Verwenden Sie `kubectl`, um eine Verbindung mit dem Pod „sparkhead-0“ herzustellen, und führen Sie diesen Befehl aus:

Mit dem folgenden Befehl wird YARN nach der Anwendung abgefragt.

```bash
yarn logs -applicationId application_1580771254352_0041
```

In den Ergebnissen unten wird dem Benutzer die Berechtigung verweigert. 

```
YYYY-MM-DD-HH:MM:SS,583 ERROR spark.SparkContext: Error initializing SparkContext.
org.apache.hadoop.security.AccessControlException: Permission denied: user=user1, access=WRITE, inode="/system/spark-events":sph:BDCAdmin:drwxr-xr-x
```

Die Ursache ist möglicherweise, dass der BDC-Benutzer dem HDFS-Stammordner rekursiv hinzugefügt wurde. Dies hat sich möglicherweise auf die Standardberechtigungen ausgewirkt.

## <a name="resolution"></a>Lösung

Stellen Sie die Berechtigungen mit dem folgenden Skript wieder her: `kinit` mit Administratorberechtigungen verwenden:

```bash
hdfs dfs -chmod 733 /system/spark-events
hdfs dfs -setfacl --set default:user:sph:rwx,default:other::--- /system/spark-events
hdfs dfs -setfacl --set default:user:app-setup:r-x,default:other::--- /system/appdeploy
hadoop fs -chmod 733 /tmp/logs
hdfs dfs -setfacl --set default:user:yarn:rwx,default:other::--- /tmp/logs
```
