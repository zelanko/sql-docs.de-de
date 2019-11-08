---
title: HDFS-Tieringberechtigungen für Big Data-Cluster für SQL Server
titleSuffix: Manage HDFS tiering permissions for SQL Server Big Data Clusters
description: Verwalten Sie Sicherheitsoptionen für das HDFS-Tiering für Big Data-Cluster für SQL Server wie z. B. Berechtigungen für andere Linux-basierte Systeme.
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 758338618a312d8efe92503581ae82d49d353e51
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73531972"
---
# <a name="manage-hdfs-permissions-for-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Verwalten von HDFS-Berechtigungen für [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Das Dateisystem HDFS ähnelt den Linux-basierten Dateisystemen, die POSIX für Dateiberechtigungen verwenden. Neben dem traditionellen POSIX-Berechtigungsmodell unterstützt HDFS auch POSIX-Zugriffssteuerungslisten (Access Control Lists, ACL). Weitere Informationen finden Sie im [Artikel von Apache Hadoop über ACLs](https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/HdfsPermissionsGuide.html#ACLs_.28Access_Control_Lists.29).

Die folgenden Abschnitte enthalten Beispiele für die Verwendung der `azdata`-CLI zum Verwalten von HDFS-Berechtigungen für Dateien und Verzeichnisse.

## <a name="prerequisites"></a>Voraussetzungen

- [Bereitgestellte Big Data-Cluster](deployment-guidance.md)
- [Big-Data-Tools](deploy-big-data-tools.md)
  
## <a name="hdfs-shell"></a>HDFS-Shell

Mit der Shellfunktion `hdfs` in `azdata` können Sie Befehle direkt in einer Shell ausgeben, um HDFS-Berechtigungen für Dateien und Verzeichnisse zu verwalten. Der zugrunde liegende Mechanismus verwendet WebHDFS-Aufrufe, um die Befehle auszugeben.

Mit dem folgenden Befehl wird die Shell geöffnet:

```bash
azdata bdc hdfs shell
```

Führen Sie den folgenden Befehl aus, sobald die Shell aktiv ist, um die Hilfe für die `hdfs`-Shell zu öffnen und Informationen zur Ausgabe von Befehlen zu erhalten:

```bash
[hdfs] ?
```

Das folgende Beispiel zeigt, wie Sie ein Verzeichnis erstellen, Verzeichnisse auflisten, Berechtigungen für ein Verzeichnis ändern und einem Benutzer namens `bob` Lese-, Schreib- und Ausführungszugriff auf das Verzeichnis `sales` erteilen.

```bash
[hdfs] mkdir sales
[hdfs] ls
rwxr-xr-x  hdfs bdcadmins        0 Oct 09 18:02 system/
rwxrwxr-x admin bdcadmins        0 Oct 10 16:47 sales/
--xrwxrwxrwx  hdfs bdcadmins        0 Oct 09 18:03 tmp/
rwxrwxrwx  hdfs bdcadmins        0 Oct 09 17:59 user/

[hdfs] acl modify  '/sales/' 'user:bob:rwx'
acl modify: Change completed.
[hdfs] acl status  '/sales/'
{
  `AclStatus`: {
    `entries`: [
      `user:bob:rwx`,
      `group::r-x`
    ],
    `group`: `bdcadmins`,
    `owner`: `admin`,
    `permission`: `775`,
    `stickyBit`: false
  }
}
```

## <a name="create-a-directory-in-hdfs-using-azdata"></a>Erstellen eines Verzeichnisses in HDFS mit `azdata`

Erstellen Sie im Pfad `/sales` ein Verzeichnis mit dem Namen `data`.

```bash
azdata bdc hdfs mkdir --path '/sales/data'
```

## <a name="change-owner-of-a-directory-or-file"></a>Ändern des Besitzers eines Verzeichnisses oder einer Datei

Ändern Sie den besitzenden Benutzer des Verzeichnisses `data` in HDFS, und legen Sie *`alice`* als besitzenden Benutzer und *`salesgroup`* als besitzende Gruppe fest. Um den Besitzer ändern zu können, müssen Sie selbst Besitzer sein.

```bash
azdata bdc hdfs chown --owner alice --group 'salesgroup' --path '/sales/data'
```

## <a name="change-permissions-of-a-file-or-directory-with-chmod"></a>Ändern von Berechtigungen für eine Datei oder ein Verzeichnis mit `chmod`

Mit `chmod` können Sie Berechtigungen für Dateien und Verzeichnisse (wie den Besitzer, die besitzende Gruppe usw.) ändern. Weitere Informationen finden Sie unter [Ändern von Berechtigungen für ein Linux-Dateisystem](https://www.lifewire.com/uses-of-command-chmod-2201064). In HDFS ist das Muster identisch. Beispiel:

```bash
azdata bdc hdfs chmod --permission 750 --path /sales/data
```

```bash
azdata bdc hdfs chmod --permission 775 --path /sales/data/file.txt
```

## <a name="set-sticky-bit-on-directories"></a>Festlegen der Sticky Bit-Berechtigung für Verzeichnisse

Legen Sie die Sticky Bit-Berechtigung für Verzeichnisse fest, um ein versehentliches Löschen oder Verschieben von Dateien zu verhindern. Durch diese Berechtigung kann nur der Superuser, der Besitzer des Verzeichnisses oder der Besitzer der Datei eine Datei löschen oder verschieben. Diese Einstellung hat keine Auswirkungen auf die Datei. Im folgenden Beispiel wird für das Verzeichnis `users` eine Sticky Bit-Berechtigung festgelegt, indem den Berechtigungen eine `1` vorangestellt wird.

```bash
azdata bdc hdfs chmod --path /sales/users --permission 1750
```

## <a name="setting-acls-on-files-and-directories"></a>Festlegen von ACLs für Dateien und Verzeichnisse

Verwenden Sie zum Festlegen von ACLs für Dateien und Verzeichnisse in HDFS die `azdata`-Befehle.

Im folgenden Beispiel werden ACLs für ein Verzeichnis festgelegt und einem Benutzer namens *`tom`* Lese-, Schreib- und Ausführungszugriff auf das Verzeichnis *`data`* erteilt. 

> [!NOTE]
> Stellen Sie bei Verwendung des `set`-Befehls sicher, dass Sie die vollständige ACL-Spezifikation einschließlich der ACL-Spezifikation für den besitzenden Benutzer, die besitzende Gruppe usw. bereitstellen.

```bash
azdata bdc hdfs acl set --path '/sales' --aclspec  'user::rw-,user:tom:rwx,group::rw-,other::rw-'
```

## <a name="default-acl-on-directories"></a>Standard-ACL für Verzeichnisse

Durch die Standard-ACL erben Unterverzeichnisse Berechtigungen vom übergeordneten Verzeichnis. Nur Verzeichnisse können eine Standard-ACL besitzen. Wird eine neue Datei oder ein Unterverzeichnis erstellt, wird die Standard-ACL des übergeordneten Elements automatisch in die jeweilige Zugriffs-ACL übernommen. Auf diese Weise wird die Standard-ACL beim Erstellen von neuen Unterverzeichnissen beliebig weit in der Verzeichnisstruktur nach unten vererbt.

Das folgende Beispiel zeigt, wie Sie die Standard-ACL mit „azdata“ festlegen:

```bash
azdata bdc hdfs acl set --path '/sale' --aclspec  'user::rw-,user:tom:rwx,group::rw-,other::rw-,default:group::rw-,default:user::rw-,default:other::rw-'
```

## <a name="next-steps"></a>Nächste Schritte

- [Referenz zu `azdata`](reference-azdata.md)

- [Was sind [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
