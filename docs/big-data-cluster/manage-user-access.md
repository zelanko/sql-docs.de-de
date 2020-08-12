---
title: Verwalten des Zugriffs auf Big Data-Cluster im Active Directory-Modus
description: Verwalten des Zugriffs auf den Big Data-Cluster
author: NelGson
ms.author: negust
ms.reviewer: mikeray
ms.date: 12/06/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 94719ef65023b1afd4edcf7770887323d0267127
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85730617"
---
# <a name="manage-big-data-cluster-access-in-active-directory-mode"></a>Verwalten des Zugriffs auf Big Data-Cluster im Active Directory-Modus

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel wird beschrieben, wie Sie die Active Directory-Gruppen aktualisieren können, die während der Bereitstellung für Clusteradministratoren (clusterAdmins) und -benutzer (clusterUsers) bereitgestellt werden.

## <a name="two-overarching-roles-in-the-big-data-cluster"></a>Zwei übergeordnete Rollen im Big Data-Cluster

Active Directory-Gruppen können im Sicherheitsabschnitt des Bereitstellungsprofils als Teil von zwei übergreifenden Rollen für die Autorisierung innerhalb des Big Data-Clusters bereitgestellt werden:

* `clusterAdmins`: Dieser Parameter akzeptiert eine einzelne Active Directory-Gruppe. Mitglieder dieser Gruppe erhalten Administratorberechtigungen im gesamten Cluster. Sie haben die Berechtigungen *sysadmin* in SQL Server, *superuser* in Hadoop Distributed File System (HDFS) und Spark sowie *Administrator*-Rechte auf dem Controller.

* `clusterUsers`: Diese Active Directory-Gruppen sind normale Benutzer ohne Administratorberechtigungen im Cluster. Sie verfügen über Berechtigungen für die Anmeldung bei der SQL Server-Masterinstanz. Standardmäßig haben sie jedoch keine Berechtigungen für Objekte oder Daten.

Eine Möglichkeit, dem Big Data-Cluster nach der Bereitstellung zusätzliche Berechtigungen für Active Directory-Gruppen zu erteilen, besteht darin, während der Bereitstellung den bereits nominierten Gruppen zusätzliche Benutzer und Gruppen hinzuzufügen. 

Allerdings ist es Administratoren nicht immer möglich, die Gruppenmitgliedschaften innerhalb von Active Directory zu ändern. Um zusätzliche Berechtigungen für Active Directory-Gruppen zu erteilen, ohne die Gruppenmitgliedschaft innerhalb von Active Directory zu ändern, führen Sie die Schritte in den folgenden Abschnitten aus.

## <a name="grant-administrator-permissions-to-additional-active-directory-groups"></a>Erteilen von Administratorberechtigungen für zusätzliche Active Directory-Gruppen

>[!IMPORTANT]
>Dieses Verfahren gewährt zusätzlichen Active Directory-Gruppen-Administratoren im Big Data-Cluster keinen Zugriff auf die Hadoop-Komponenten wie z. B. HDFS und Spark. Diese Komponenten lassen nur eine Active Directory-Gruppe als Superuser-Gruppe zu. Diese Einschränkung bedeutet, dass die Gruppe, die während der Bereitstellung in `clusterAdmins` angegeben wird, auch nach diesem Schritt die Superuser-Gruppe bleibt.

Wenn Sie die Anweisungen in diesem Abschnitt befolgen, können Sie dem Administrator Zugriff sowohl auf den Controller als auch auf die SQL Server-Masterinstanz gewähren.

### <a name="create-a-login-for-the-active-directory-user-or-group-in-the-sql-server-master-instance"></a>Erstellen einer Anmeldung für den Active Directory-Benutzer oder die Active Directory-Gruppe in der SQL Server-Masterinstanz 

1. Stellen Sie mithilfe Ihres bevorzugten SQL-Clients eine Verbindung mit dem SQL-Masterendpunkt her. Verwenden Sie eine beliebige Administratoranmeldung (z. B. `AZDATA_USERNAME`), die während der Bereitstellung zur Verfügung gestellt wurde. Alternativ kann auch ein beliebiges Active Directory-Konto verwendet werden, das zur Active Directory-Gruppe gehört, die in der Sicherheitskonfiguration als `clusterAdmins` angegeben ist.

1. Um eine Anmeldung für den Active Directory-Benutzer oder die Active Directory-Gruppe zu erstellen, führen Sie den folgenden TSQL-Befehl aus:

   ```sql
   CREATE LOGIN [<domain>\<principal>] FROM WINDOWS;
   ```

   Wenn Sie in der SQL Server-Instanz Administratorberechtigungen erteilen, erteilen Sie auch die folgende Berechtigung:

   ```sql
   ALTER SERVER ROLE sysadmin ADD MEMBER [<domain>\<principal>];
   GO
   ```

### <a name="add-the-active-directory-user-or-group-to-the-roles-table-in-the-controller-database"></a>Hinzufügen des Active Directory-Benutzers oder der Active Directory-Gruppe zur Rollentabelle in der Controllerdatenbank 

1. Rufen Sie die SQL Server-Anmeldeinformationen des Controllers ab, indem Sie die folgenden Befehle ausführen:

   a. Führen Sie diesen Befehl als Kubernetes-Administrator aus:

   ```bash
   kubectl get secret controller-sa-secret -n <cluster name> -o yaml | grep password
   ```

   b. Decodieren Sie das Geheimnis mit Base64:

   ```bash
   echo <password from kubectl command>  | base64 --decode && echo
   ```

1. Machen Sie in einem separaten Befehlsfenster den Port des Datenbankservers des Controllers verfügbar:

   ```bash
   kubectl port-forward controldb-0 1433:1433 --address 0.0.0.0 -n <cluster name>
   ```

1. Verwenden Sie die vorhergehende Verbindung, um eine Zeile in die Rollentabelle einzufügen. Geben Sie den Wert *REALM* in Großbuchstaben ein.

   Wenn Sie Administratorberechtigungen gewähren, verwenden Sie die Rolle *bdcAdmin* in der Rolle *\<role name>* . Verwenden Sie für Benutzer ohne Administratorrechte die Rolle *bdcUser*.

   ```sql
   USE controller;
   GO

   INSERT INTO [controller].[auth].[roles] VALUES (N'<user or group name>@<REALM>', N'<role name>')
   GO
   ```

1. Vergewissern Sie sich, dass die Mitglieder der Gruppe, die Sie hinzugefügt haben, über Administratorrechte für Big Data-Cluster verfügen, indem Sie sich am Controllerendpunkt anmelden und den folgenden Befehl ausführen:

   ```bash
   azdata bdc config show
   ```

1. Für Benutzer ohne Administratorrechte können Sie den Zugriff durch Authentifizierung bei der SQL-Masterinstanz oder beim Controller mit `azdata login` überprüfen.

## <a name="next-steps"></a>Nächste Schritte

- [Sicherheitskonzepte für Big Data-Cluster in SQL Server 2019](concept-security.md)
