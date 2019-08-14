---
title: Installieren des SQL Server-Agent unter Linux
description: In diesem Artikel ist beschrieben, wie der SQL Server-Agent unter Linux installiert wird.
author: VanMSFT
ms.author: vanto
ms.date: 02/20/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.openlocfilehash: c27a31a5e6b9ed771df82e942087d7be88270038
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/25/2019
ms.locfileid: "68032468"
---
# <a name="install-sql-server-agent-on-linux"></a>Installieren des SQL Server-Agent unter Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

 Der [SQL Server-Agent](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent) führt geplante SQL Server-Aufträge aus. Ab SQL Server 2017 CU4 ist der SQL Server-Agent im **mssql-server**-Paket enthalten und standardmäßig deaktiviert. Informationen zu den Funktionen, die in dieser Version des SQL Server-Agent unterstützt werden, sowie Versionsinformationen finden Sie in den [Versionshinweisen](sql-server-linux-release-notes.md).

 Installieren/aktivieren Sie den SQL Server-Agent:
- [Bei einer Version ab 2017 CU4: „Aktivieren“ des SQL Server-Agent](#EnableAgentAfterCU4)
- [Bei einer Version bis einschließlich 2017 CU3: „Installieren“ des SQL Server-Agent](#InstallAgentBelowCU4)


## <a name="EnableAgentAfterCU4">Bei einer Version ab 2017 CU4: „Aktivieren“ des SQL Server-Agent</a>

 Um den SQL Server-Agent zu aktivieren, führen Sie die folgenden Schritte aus.

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true 
sudo systemctl restart mssql-server
```

> [!NOTE]
> Wenn Sie von 2017 CU3 oder darunter mit installiertem Agent ein Upgrade durchführen, wird der SQL Server-Agent automatisch aktiviert, und frühere Agent-Pakete werden deinstalliert.  

## <a name="InstallAgentBelowCU4">Bei einer Version bis einschließlich 2017 CU3: „Installieren“ des SQL Server-Agent</a>

> [!NOTE]
> Die folgenden Installationsanweisungen gelten für die SQL Server-Versionen bis einschließlich 2017 CU3. Bevor Sie die den SQL Server-Agent installieren, müssen Sie zunächst [SQL Server installieren](sql-server-linux-setup.md#platforms). Dadurch werden die Schlüssel und Repositorys konfiguriert, die Sie verwenden, wenn Sie das **mssql-server-agent**-Paket installieren.

Installieren Sie den SQL Server-Agent für Ihre Plattform:
- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

### <a name="RHEL">Installation unter RHEL</a>

Führen Sie zum Installieren von **mssql-server-agent** unter Red Hat Enterprise Linux die folgenden Schritte aus. 

```bash
sudo yum install mssql-server-agent
sudo systemctl restart mssql-server
```

Wenn Sie **mssql-server-agent** bereits installiert haben, können Sie mit den folgenden Befehlen auf die neueste Version aktualisieren:

```bash
sudo yum check-update
sudo yum update mssql-server-agent
sudo systemctl restart mssql-server
```

Wenn Sie eine Offlineinstallation benötigen, suchen Sie in den [Versionshinweisen](sql-server-linux-release-notes.md) nach der Downloadmöglichkeit für das SQL Server-Agent-Paket. Führen Sie dann die im Artikel [Installieren von SQL Server](sql-server-linux-setup.md#offline) beschriebenen Schritte für die Offlineinstallation aus.

### <a name="ubuntu">Installation unter Ubuntu</a>

Führen Sie zum Installieren von **mssql-server-agent** unter Ubuntu die folgenden Schritte aus. 

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Wenn Sie **mssql-server-agent** bereits installiert haben, können Sie mit den folgenden Befehlen auf die neueste Version aktualisieren:

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

Wenn Sie eine Offlineinstallation benötigen, suchen Sie in den [Versionshinweisen](sql-server-linux-release-notes.md) nach der Downloadmöglichkeit für das SQL Server-Agent-Paket. Führen Sie dann die im Artikel [Installieren von SQL Server](sql-server-linux-setup.md#offline) beschriebenen Schritte für die Offlineinstallation aus.

### <a name="SLES">Installation unter SLES</a>

Führen Sie zum Installieren von **mssql-server-agent** unter SUSE Linux Enterprise Server die folgenden Schritte aus. 

Installieren Sie **mssql-server-agent**. 

```bash
sudo zypper install mssql-server-agent
sudo systemctl restart mssql-server
```

Wenn Sie **mssql-server-agent** bereits installiert haben, können Sie mit den folgenden Befehlen auf die neueste Version aktualisieren:

```bash
sudo zypper refresh
sudo zypper update mssql-server-agent
sudo systemctl restart mssql-server
```

Wenn Sie eine Offlineinstallation benötigen, suchen Sie in den [Versionshinweisen](sql-server-linux-release-notes.md) nach der Downloadmöglichkeit für das SQL Server-Agent-Paket. Führen Sie dann die im Artikel [Installieren von SQL Server](sql-server-linux-setup.md#offline) beschriebenen Schritte für die Offlineinstallation aus.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen dazu, wie der SQL Server-Agent verwendet wird, um Aufträge zu erstellen, zu planen und auszuführen, finden Sie unter [Erstellen und Ausführen von SQL Server-Agent-Aufträgen unter Linux](sql-server-linux-run-sql-server-agent-job.md).
