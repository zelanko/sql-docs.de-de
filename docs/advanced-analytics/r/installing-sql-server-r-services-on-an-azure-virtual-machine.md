---
title: Installieren von R-Sprache und den Python-Features auf virtuellen Azure-Computer – SQL Server Machine Learning Services
description: Führen Sie R- und Python Data Science und Machine learning-Lösungen auf einer SQL Server-VM in der Azure-Cloud.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/09/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 01fb7962a5be08f40fe1c790b335c24d34979a2a
ms.sourcegitcommit: fa2afe8e6aec51e295f55f8cc6ad3e7c6b52e042
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66462561"
---
# <a name="install-sql-server-machine-learning-services-with-r-and-python-on-an-azure-virtual-machine"></a>Installieren von SQL Server-Machine Learning-Dienste mit R und Python auf virtuellen Azure-Computer
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Sie können die Integration von R und Python in Machine Learning Services auf einer SQL Server-VM in Azure, beseitigen Installations- und Konfigurationstasks installieren. Nachdem der virtuelle Computer bereitgestellt wurde, können die Funktionen verwenden.
 
Schritt-für-Schritt-Anweisungen finden Sie unter [Gewusst wie: Bereitstellen eines Windows SQL Server-virtuellen Computers im Azure-Portal](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision).

Die [Konfigurieren von SQL Server-Einstellungen](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#3-configure-sql-server-settings) Schritt besteht in dem Sie Machine Learning mit Ihrer Instanz hinzufügen.

<a name="firewall"></a>

## <a name="unblock-the-firewall"></a>Aufhebung der firewallblockierung

Standardmäßig enthält die Firewall auf virtuellen Azure-Computer eine Regel, dass der Netzwerkzugriff für lokale Benutzerkonten blockiert.

Sie müssen diese Regel, um sicherzustellen, dass Sie zugreifen können, deaktivieren die [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Instanz anhand einer Data Science-Remoteclient.  Andernfalls kann nicht Ihre Machine learning-Code in computekontexten ausgeführt, die den VM Arbeitsbereich zu verwenden.

So aktivieren Sie den Zugriff von remoten Data Science-Clients:

1. Öffnen Sie auf dem virtuellen Computer die Windows-Firewall mit erweiterter Sicherheit.
2. Wählen Sie **Ausgehende Regeln** aus.
3. Deaktivieren Sie die folgende Regel:
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
## <a name="enable-odbc-callbacks-for-remote-clients"></a>ODBC-Rückrufe für Remoteclients aktivieren

Wenn Sie erwarten, dass Clients den Server Aufrufen von ODBC-Abfragen als Teil ihrer Machine learning-Lösungen benötigen, müssen Sie sicherstellen, dass das Launchpad ODBC-Aufrufe für den Remoteclient vornehmen kann. 

Zu diesem Zweck müssen Sie die SQL-Workerkonten zulassen, die vom Launchpad für die Anmeldung bei der Instanz verwendet werden. Weitere Informationen finden Sie unter [Hinzufügen der SQLRUserGroup als Datenbankbenutzer](../security/create-a-login-for-sqlrusergroup.md).

<a name="network"></a>

## <a name="add-network-protocols"></a>Hinzufügen von Netzwerkprotokollen

+ Aktivieren von Named Pipes
  
  Derzeit verwendet [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] das Named Pipes-Protokoll für Verbindungen zwischen dem Client und den Servercomputern und für einige externe Verbindungen. Wenn Named Pipes nicht aktiviert ist, müssen Sie es jeweils auf dem virtuellen Azure-Computer und auf alle Data Science-Clients installieren und aktivieren, die eine Verbindung mit dem Server herstellen.
  
+ Aktivieren von TCP/IP

  TCP/IP ist für Loopbackverbindungen erforderlich. Wenn Sie die Fehlermeldung "DBNETLIB; SQL Server ist nicht vorhanden oder der Zugriff verweigert", aktivieren Sie TCP/IP auf dem virtuellen Computer, die die Instanz unterstützt.