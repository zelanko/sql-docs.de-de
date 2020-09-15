---
title: Installieren auf einem virtuellen Azure-Computer
description: In diesem Artikel erfahren Sie, wie Sie Data-Science- und Machine Learning-Lösungen für R und Python mit SQL Server Machine Learning Services auf einer VM in der Azure-Cloud ausführen.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 01/02/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ea886eed26a2f88711d1405b5130570c09c87d6c
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88180493"
---
# <a name="install-sql-server-machine-learning-services-with-python-and-r-on-an-azure-virtual-machine"></a>Installieren von SQL Server Machine Learning Services mit Python und R auf einer Azure-VM
[!INCLUDE [SQL Server 2017 and later](../../includes/applies-to-version/sqlserver2017.md)]

In diesem Artikel erfahren Sie, wie Sie Python und R mit SQL Server Machine Learning Services auf einer Azure-VM installieren. Dadurch fallen Installations- und Konfigurationstasks für Machine Learning Services weg.

Folgen Sie diesen Schritten:

1. Bereitstellen einer SQL Server-VM in Azure
1. Aufhebung der Firewallblockierung
1. ODBC-Rückrufe für Remoteclients aktivieren
1. Hinzufügen von Netzwerkprotokollen

## <a name="provision-sql-server-virtual-machine-in-azure"></a>Bereitstellen einer SQL Server-VM in Azure

Ausführliche Anweisungen finden Sie unter [Bereitstellen eines virtuellen Windows-Computers mit SQL Server im Azure-Portal](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision). 

Im Schritt [Konfigurieren der SQL Server-Einstellungen](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#3-configure-sql-server-settings) fügen Sie Ihrer Instanz Machine Learning Services hinzu.

<a name="firewall"></a>

## <a name="unblock-the-firewall"></a>Aufhebung der Firewallblockierung

Die Firewall enthält auf virtuellen Azure-Computern standardmäßig eine Regel, die den Netzwerkzugriff für lokale Benutzerkonten blockiert.

Sie müssen diese Regel deaktivieren, um sicherzustellen, dass Sie auf die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-Instanz von einem Data-Science-Remoteclient aus zugreifen können.  Andernfalls kann Ihr Machine-Learning-Code nicht in Computekontexten ausgeführt werden, die den Arbeitsbereich des virtuellen Computers verwenden.

So aktivieren Sie den Zugriff von Data Science-Remoteclients:

1. Öffnen Sie auf dem virtuellen Computer die Windows-Firewall mit erweiterter Sicherheit.
2. Wählen Sie **Ausgehende Regeln** aus.
3. Deaktivieren Sie die folgende Regel:
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
## <a name="enable-odbc-callbacks-for-remote-clients"></a>ODBC-Rückrufe für Remoteclients aktivieren

Wenn Sie erwarten, dass Clients, die den Server aufrufen, ODBC-Anfragen als Teil ihrer Machine-Learning-Lösungen ausstellen, müssen Sie sicherstellen, dass das Launchpad ODBC-Aufrufe für den Remoteclient ausführen kann. 

Zu diesem Zweck müssen Sie die SQL-Workerkonten zulassen, die vom Launchpad für die Anmeldung bei der Instanz verwendet werden. Weitere Informationen finden Sie unter [Hinzufügen von SQLRUserGroup als Datenbankbenutzer](../security/create-a-login-for-sqlrusergroup.md).

<a name="network"></a>

## <a name="add-network-protocols"></a>Hinzufügen von Netzwerkprotokollen

+ Aktivieren von Named Pipes
  
  Derzeit verwendet [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] das Named Pipes-Protokoll für Verbindungen zwischen dem Client und den Servercomputern und für einige externe Verbindungen. Wenn Named Pipes nicht aktiviert ist, müssen Sie es jeweils auf dem virtuellen Azure-Computer und auf alle Data Science-Clients installieren und aktivieren, die eine Verbindung mit dem Server herstellen.
  
+ Aktivieren von TCP/IP

  TCP/IP ist für Loopbackverbindungen erforderlich. Wenn der Fehler „DBNETLIB; SQL Server ist nicht vorhanden, oder der Zugriff wurde verweigert.“ ausgegeben wird, aktivieren Sie TCP/IP auf dem virtuellen Computer, der die Instanz unterstützt.