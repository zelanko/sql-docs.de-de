---
title: Installieren von R-Sprache und Python-Funktionen auf einem virtuellen Azure-Computer
description: Führen Sie R-und python-Data Science und Machine Learning-Lösungen auf einem SQL Server virtuellen Computer in der Azure-Cloud aus.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/09/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 6f034f3a766e4f82bd1bcfd182f4eee285f7f829
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345040"
---
# <a name="install-sql-server-machine-learning-services-with-r-and-python-on-an-azure-virtual-machine"></a>Installieren von SQL Server Machine Learning Services mit R und python auf einem virtuellen Azure-Computer
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Sie können die R-und python-Integration mit Machine Learning Services auf einem SQL Server virtuellen Computer in Azure installieren, wodurch Installations-und Konfigurationsaufgaben vermieden werden. Nachdem der virtuelle Computer bereitgestellt wurde, können die Features verwendet werden.
 
Schritt-für-Schritt-Anweisungen finden [Sie unter Bereitstellen eines virtuellen Windows SQL Server-Computers in der Azure-Portal](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision).

Mit dem Schritt [SQL Server-Einstellungen konfigurieren](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#3-configure-sql-server-settings) können Sie Machine Learning zu Ihrer Instanz hinzufügen.

<a name="firewall"></a>

## <a name="unblock-the-firewall"></a>Sperre der Firewall entsperren

Standardmäßig enthält die Firewall auf dem virtuellen Azure-Computer eine Regel, die den Netzwerk Zugriff für lokale Benutzerkonten blockiert.

Sie müssen diese Regel deaktivieren, um sicherzustellen, dass Sie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] von einem Remote Data Science-Client aus auf die-Instanz zugreifen können.  Andernfalls kann der Machine Learning-Code nicht in computekontexten ausgeführt werden, die den Arbeitsbereich des virtuellen Computers verwenden.

So aktivieren Sie den Zugriff von Remote Data Science-Clients:

1. Öffnen Sie auf dem virtuellen Computer die Windows-Firewall mit erweiterter Sicherheit.
2. Wählen Sie **Ausgehende Regeln** aus.
3. Deaktivieren Sie die folgende Regel:
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
## <a name="enable-odbc-callbacks-for-remote-clients"></a>ODBC-Rückrufe für Remoteclients aktivieren

Wenn Sie davon ausgehen, dass Clients, die den Server aufrufen, als Teil ihrer Machine Learning-Lösungen ODBC-Abfragen ausgeben müssen, müssen Sie sicherstellen, dass das Launchpad ODBC-Aufrufe für den Remote Client durchführen kann. 

Zu diesem Zweck müssen Sie die SQL-Workerkonten zulassen, die vom Launchpad für die Anmeldung bei der Instanz verwendet werden. Weitere Informationen finden Sie unter [Hinzufügen von sqlrusergroup als Datenbankbenutzer](../security/create-a-login-for-sqlrusergroup.md).

<a name="network"></a>

## <a name="add-network-protocols"></a>Netzwerkprotokolle hinzufügen

+ Aktivieren von Named Pipes
  
  Derzeit verwendet [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] das Named Pipes-Protokoll für Verbindungen zwischen dem Client und den Servercomputern und für einige externe Verbindungen. Wenn Named Pipes nicht aktiviert ist, müssen Sie es jeweils auf dem virtuellen Azure-Computer und auf alle Data Science-Clients installieren und aktivieren, die eine Verbindung mit dem Server herstellen.
  
+ Aktivieren von TCP/IP

  TCP/IP ist für Loopback Verbindungen erforderlich. Wenn Sie den Fehler "dbnetlib;" erhalten, SQL Server ist nicht vorhanden oder Zugriff verweigert ", aktivieren Sie TCP/IP auf dem virtuellen Computer, der die Instanz unterstützt.