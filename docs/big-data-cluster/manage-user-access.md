---
title: Verwalten des Zugriffs auf Big Data-Cluster im Active Directory-Modus
description: Verwalten des Zugriffs auf den Big Data-Cluster
author: NelGson
ms.author: negust
ms.reviewer: mikeray
ms.date: 08/04/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ef2df0bec343d73de90a43e411da92530c3c50c8
ms.sourcegitcommit: 6ab28d954f3a63168463321a8bc6ecced099b247
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87790265"
---
# <a name="manage-big-data-cluster-access-in-active-directory-mode"></a>Verwalten des Zugriffs auf Big Data-Cluster im Active Directory-Modus

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

In diesem Artikel wird beschrieben, wie Sie zusätzlich zu den im Rahmen der Bereitstellung über die Konfigurationseinstellung *clusterUsers* bereitgestellten Gruppen neue Active Directory-Gruppen mit *bdcUser*-Rollen hinzufügen.

>[!IMPORTANT]
>Verwenden Sie dieses Verfahren nicht, um neue Active Directory-Gruppen mit der Rolle *bdcAdmin* hinzuzufügen. Hadoop-Komponenten wie HDFS und Spark lassen nur eine Active Directory-Gruppe als Superuser-Gruppe zu. Diese entspricht der Rolle *bdcAdmin* in BDC. Um dem Big Data-Cluster nach der Bereitstellung zusätzliche Active Directory-Gruppen mit *bdcAdmin*-Berechtigungen hinzufügen zu können, müssen Sie während der Bereitstellung den bereits nominierten Gruppen zusätzliche Benutzer und Gruppen hinzufügen. Sie können dasselbe Verfahren anwenden, um die Gruppenmitgliedschaften zu aktualisieren, die über die Rolle *bdcUsers* verfügen.

## <a name="two-overarching-roles-in-the-big-data-cluster"></a>Zwei übergeordnete Rollen im Big Data-Cluster

Active Directory-Gruppen können im Sicherheitsabschnitt des Bereitstellungsprofils als Teil von zwei übergreifenden Rollen für die Autorisierung innerhalb des Big Data-Clusters bereitgestellt werden:

* `clusterAdmins`: Dieser Parameter akzeptiert eine einzelne Active Directory-Gruppe. Mitglieder dieser Gruppe verfügen über die Rolle *bdcAdmin*, was bedeutet, dass sie Administratorberechtigungen für den gesamten Cluster erhalten. Sie haben die Berechtigungen *sysadmin* in SQL Server, *superuser* in Hadoop Distributed File System (HDFS) und Spark sowie *Administrator*-Rechte auf dem Controller.

* `clusterUsers`: Diese Active Directory-Gruppen werden der Rolle *bdcUsers* in BDC zugeordnet. Es handelt sich dabei um normale Benutzer ohne Administratorberechtigungen im Cluster. Sie verfügen über Berechtigungen für die Anmeldung bei der SQL Server-Masterinstanz. Standardmäßig haben sie jedoch keine Berechtigungen für Objekte oder Daten. Diese Benutzer sind in HDFS und Spark normale Benutzer ohne *Superuser*-Berechtigungen. Beim Herstellen einer Verbindung mit dem Controllerendpunkt können diese Benutzer nur die Endpunkte (mit *azdata bdc endpoints list*) abfragen.

Um zusätzlichen Active Directory-Gruppen *bdcUser*-Berechtigungen zu erteilen, ohne die Gruppenmitgliedschaften innerhalb von Active Directory zu ändern, führen Sie die Schritte in den folgenden Abschnitten aus.

## <a name="grant-bdcuser-permissions-to-additional-active-directory-groups"></a>Erteilen von *bdcUser*-Berechtigungen für zusätzliche Active Directory-Gruppen

### <a name="create-a-login-for-the-active-directory-user-or-group-in-the-sql-server-master-instance"></a>Erstellen einer Anmeldung für den Active Directory-Benutzer oder die Active Directory-Gruppe in der SQL Server-Masterinstanz

1. Stellen Sie mithilfe Ihres bevorzugten SQL-Clients eine Verbindung mit dem SQL-Masterendpunkt her. Verwenden Sie eine beliebige Administratoranmeldung (z. B. `AZDATA_USERNAME`), die während der Bereitstellung zur Verfügung gestellt wurde. Alternativ kann auch ein beliebiges Active Directory-Konto verwendet werden, das zur Active Directory-Gruppe gehört, die in der Sicherheitskonfiguration als `clusterAdmins` angegeben ist.

1. Um eine Anmeldung für den Active Directory-Benutzer oder die Active Directory-Gruppe zu erstellen, führen Sie den folgenden TSQL-Befehl aus:

   ```sql
   CREATE LOGIN [<domain>\<principal>] FROM WINDOWS;
   ```

   Erteilen Sie die gewünschten Berechtigungen in der SQL Server-Instanz:

   ```sql
   ALTER SERVER ROLE <server role> ADD MEMBER [<domain>\<principal>];
   GO
   ```

Eine vollständige Liste der Serverrollen finden Sie unter dem entsprechenden Thema zur SQL Server-Sicherheit [hier](../relational-databases/security/authentication-access/server-level-roles.md).

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

1. Verwenden Sie die vorherige Verbindung, um eine neue Zeile in die Tabellen *roles* und *active_directory_principals* einzufügen. Geben Sie den Wert *REALM* in Großbuchstaben ein.

   ```sql
   USE controller;
   GO

   INSERT INTO [controller].[auth].[roles] VALUES (N'<user or group name>@<REALM>', 'bdcUser')
   GO

   INSERT INTO [controller].[auth].[active_directory_principals] VALUES (N'<user or group name>@<REALM>', N'<SID>')
   GO
   ```

   Zum Ermitteln der SID des hinzugefügten Benutzers oder der hinzugefügten Gruppe können Sie den PowerShell-Befehl [Get-ADUser](/powershell/module/addsadministration/get-aduser/) bzw. [Get-ADGroup](/powershell/module/addsadministration/get-adgroup/) verwenden.

2. Vergewissern Sie sich, dass die Mitglieder der Gruppe, die Sie hinzugefügt haben, über die erwarteten *bdcUser*-Berechtigungen verfügen, indem Sie sich beim Controllerendpunkt anmelden oder die Authentifizierung bei der SQL Server-Masterinstanz ausführen. Beispiel:

   ```bash
   azdata login
   azdata bdc endpoints list
   ```

## <a name="next-steps"></a>Nächste Schritte

- [Sicherheitskonzepte für Big Data-Cluster in SQL Server 2019](concept-security.md)
