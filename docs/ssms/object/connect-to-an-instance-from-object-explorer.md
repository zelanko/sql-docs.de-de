---
title: Verbinden mit einem SQL-Server oder einer Azure SQL-Datenbank
ms.custom: seo-lt-2019
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9803a8a0-a8f1-4b65-87b8-989b06850194
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8241bb0edff2a424d42d79ad3e6aa514519e79b3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "75257214"
---
# <a name="connect-to-a-sql-server-or-azure-sql-database"></a>Verbinden mit einem SQL-Server oder einer Azure SQL-Datenbank

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Um mit Servern und Datenbanken arbeiten zu können, müssen Sie zuerst eine Verbindung mit dem Server herstellen. Eine Verbindung zu mehreren Servern gleichzeitig ist jedoch nicht möglich.

[SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md) unterstützt verschiedene Typen von Verbindungen. In diesem Artikel finden Sie Informationen zum Herstellen einer Verbindung mit SQL Server und Azure SQL-Datenbank (Herstellen einer Verbindung mit einem Azure SQL Singleton oder Pool für elastische Datenbanken). Informationen zu den anderen Verbindungsoptionen finden Sie unter den [Links](#see-also) unten auf dieser Seite.
  
## <a name="connecting-to-a-server"></a>Verbinden mit einem Server  

1. Klicken Sie im **Objekt-Explorer** auf **Verbinden &gt; Datenbank-Engine…** .

   ![Verbinden](../media/connect-to-server/connect-db-engine.png)

1. Füllen Sie das Formular **Verbindung mit Server herstellen** aus, und klicken Sie auf **Verbinden**:

   ![Verbindung mit dem Server herstellen](../media/connect-to-server/connect.png)

1. Wenn Sie eine Verbindung zu einem Azure SQL-Server herstellen, werden Sie möglicherweise dazu aufgefordert, sich anzumelden, um eine Firewallregel zu erstellen. Klicken Sie auf **Anmelden…** . Falls dies nicht der Fall ist, fahren Sie mit Schritt 6 fort.

   ![Firewall](../media/connect-to-server/firewall-rule-sign-in.png)

1. Nachdem Sie sich angemeldet haben, wird das Formular mit Ihrer IP-Adresse ausgefüllt. Wenn sich Ihre IP-Adresse häufig ändert, kann es einfacher sein, Zugriff auf einen IP-Bereich zu gewähren. Wählen Sie also die Option aus, die für Ihre Umgebung am besten geeignet ist. 

   ![Firewall](../media/connect-to-server/new-firewall-rule.png)

1. Um eine Firewallregel zu erstellen und eine Verbindung zum Server herzustellen, klicken Sie auf **OK**.

1. Nach der Verbindungsherstellung wird der Server im **Objekt-Explorer** angezeigt:

   ![connected](../media/connect-to-server/connected.png)

## <a name="next-steps"></a>Nächste Schritte

[Entwerfen, Erstellen und Aktualisieren von Tabellen](../visual-db-tools/design-tables-visual-database-tools.md)

## <a name="see-also"></a>Weitere Informationen

[SQL Server Management Studio (SSMS)](../sql-server-management-studio-ssms.md)  
[Herunterladen von SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md)

[Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/connect-to-analysis-services)  
[Integrationsdienste](https://docs.microsoft.com/sql/integration-services/sql-server-integration-services)  
[Reporting Services](https://docs.microsoft.com/sql/reporting-services/tools/connect-to-a-report-server-in-management-studio)  
[Azure Storage (in englischer Sprache)](../f1-help/connect-to-microsoft-azure-storage.md)  
