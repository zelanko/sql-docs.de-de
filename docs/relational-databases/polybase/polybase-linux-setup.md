---
title: Installieren von PolyBase unter Linux
titlesuffix: SQL Server
description: In diesem Artikel wird beschrieben, wie SQL Server PolyBase unter Linux installiert wird.
author: MikeRayMSFT
ms.author: mikeray
ms.date: 7/22/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-linux-ver15 || >= sql-server-ver15 || =sqlallproducts-allversions'
ms.openlocfilehash: f72635a68b0b47a29151d45d2bf1e32e85c1f1bc
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823575"
---
# <a name="install-polybase-on-linux"></a>Installieren von PolyBase unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Im Folgenden werden die Schritte beschrieben, mit denen Sie [PolyBase](../../relational-databases/search/full-text-search.md) (**mssql-server-polybase**) unter Linux installieren können. Mit PolyBase können Sie externe Abfragen für Remotedatenquellen ausführen. 

>[!NOTE]
> [Installieren Sie zunächst die Vorschauversion von SQL Server 2019](../../linux/sql-server-linux-setup.md#platforms), bevor Sie PolyBase installieren. Dadurch werden die Schlüssel und Repositorys konfiguriert, die Sie beim Installieren des **mssql-server-polybase**-Pakets verwenden.
>
> PolyBase wird unter SQL Server 2017 für Linux nicht unterstützt.
> Eine horizontale Skalierung für PolyBase ist derzeit unter Linux nicht verfügbar.

Installieren Sie PolyBase für Ihr Betriebssystem:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)



## <a name=""></a><a name="RHEL">Installation unter RHEL</a>

Verwenden Sie zum Installieren von **mssql-server-polybase** unter Red Hat Enterprise Linux (RHEL) den folgenden Befehl: 

```bash
sudo yum install -y mssql-server-polybase
```

Sie werden zu einem Neustart der SQL Server-Instanz aufgefordert. Verwenden Sie hierfür den folgenden Befehl:

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>Nach der Installation müssen Sie das [PolyBase-Feature aktivieren](#enable).

Wenn Sie eine Offlineinstallation benötigen, suchen Sie in den [Versionshinweisen](../../linux/sql-server-linux-release-notes.md) nach der Downloadmöglichkeit für das PolyBase-Paket. Führen Sie dann die im Artikel [Installieren von SQL Server](../../linux/sql-server-linux-setup.md#offline) beschriebenen Schritte für die Offlineinstallation aus.

## <a name=""></a><a name="ubuntu">Installation unter Ubuntu</a>

Verwenden Sie zum Installieren von **mssql-server-polybase** unter Ubuntu den folgenden Befehl: 

```bash
sudo apt-get install mssql-server-polybase
```

Sie werden zu einem Neustart der SQL Server-Instanz aufgefordert. Verwenden Sie hierfür den folgenden Befehl:

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>Nach der Installation müssen Sie das [PolyBase-Feature aktivieren](#enable).

Wenn Sie eine Offlineinstallation benötigen, suchen Sie in den [Versionshinweisen](../../linux/sql-server-linux-release-notes.md) nach der Downloadmöglichkeit für das PolyBase-Paket. Führen Sie dann die im Artikel [Installieren von SQL Server](../../linux/sql-server-linux-setup.md#offline) beschriebenen Schritte für die Offlineinstallation aus.

## <a name=""></a><a name="SLES">Installation unter SLES</a>

Verwenden Sie zum Installieren von **mssql-server-polybase** unter SUSE Linux Enterprise Server (SLES) den folgenden Befehl: 

```bash
sudo zypper install mssql-server-polybase
```

Sie werden zu einem Neustart der SQL Server-Instanz aufgefordert. Verwenden Sie hierfür den folgenden Befehl:

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>Nach der Installation müssen Sie das [PolyBase-Feature aktivieren](#enable).


Wenn Sie eine Offlineinstallation benötigen, suchen Sie in den [Versionshinweisen](../../linux/sql-server-linux-release-notes.md) nach der Downloadmöglichkeit für das PolyBase-Paket. Führen Sie dann die im Artikel [Installieren von SQL Server](../../linux/sql-server-linux-setup.md#offline) beschriebenen Schritte für die Offlineinstallation aus.


## <a name=""></a><a name="enable">Aktivieren von PolyBase</a> 

Nach der Installation muss PolyBase aktiviert werden, um auf die Features zugreifen zu können. Stellen Sie eine Verbindung mit der installierten SQL Server-Instanz her, und verwenden Sie zum Aktivieren den folgenden Transact-SQL-Befehl:

```sql
exec sp_configure @configname = 'polybase enabled', @configvalue = 1;
RECONFIGURE WITH OVERRIDE;
```

## <a name="update-polybase"></a>Aktualisieren von PolyBase

Wenn Sie **mssql-server-polybase** bereits installiert haben, können Sie es mit den folgenden Befehlen auf die neueste Version aktualisieren:

### <a name="rhel"></a>RHEL

```bash
sudo yum remove -y mssql-server-polybase
sudo yum check-update
sudo yum install -y mssql-server-polybase
```

Sie werden zu einem Neustart der SQL Server-Instanz aufgefordert. Verwenden Sie hierfür den folgenden Befehl:

```
sudo systemctl restart mssql-server
```

### <a name="ubuntu"></a>Ubuntu

```bash
sudo apt-get remove mssql-server-polybase
sudo apt-get update 
sudo apt-get install mssql-server-polybase
```

Sie werden zu einem Neustart der SQL Server-Instanz aufgefordert. Verwenden Sie hierfür den folgenden Befehl:

```
sudo systemctl restart mssql-server
```

### <a name="sles"></a>SLES

```bash
sudo zypper remove mssql-server-polybase
sudo zypper refresh
sudo zypper install mssql-server-polybase
```

Sie werden zu einem Neustart der SQL Server-Instanz aufgefordert. Verwenden Sie hierfür den folgenden Befehl:

```
sudo systemctl restart mssql-server
```

>[!NOTE]
>Nach der Installation müssen Sie das [PolyBase-Feature aktivieren](#enable).

## <a name="next-steps"></a>Nächste Schritte

PolyBase kann unter Linux auf die folgenden Datenquellen zugreifen. Informationen zum Erstellen einer externen Tabelle aus diesen Quellen, wenn PolyBase aktiviert ist, finden Sie unter den folgenden Links: 

- [SQL Server (sowie SQL Database und Azure SQL Data Warehouse)](../../relational-databases/polybase/polybase-configure-sql-server.md)
- [Oracle](../../relational-databases/polybase/polybase-configure-oracle.md)
- [Teradata](../../relational-databases/polybase/polybase-configure-teradata.md)
- [MongoDB (& Cosmos DB)](../../relational-databases/polybase/polybase-configure-mongodb.md)

Weitere Informationen zur Verwendung finden Sie im Transact-SQL-Referenzartikel für [CREATE EXTERNAL TABLE](../../t-sql/statements/create-external-table-transact-sql.md).
