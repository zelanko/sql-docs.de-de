---
title: Konnektivitätsbibliotheken und Frameworks
description: Listet die Konnektivitätstreiber auf, die Client-Apps aus verschiedenen Sprachen verwenden können, um eine Verbindung mit einer Microsoft SQL Server-Instanz, die lokal oder in der Cloud, unter Linux, Windows oder Docker ausgeführt wird, oder mit Azure SQL-Datenbank und Azure SQL Data Warehouse herzustellen.
author: VanMSFT
ms.author: vanto
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.openlocfilehash: 105204e58080b07e13c02d3799977d77413f9467
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245620"
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>Konnektivitätsbibliotheken und-Frameworks für Microsoft SQL Server

[!INCLUDE [SQL Server - Linux](../includes/applies-to-version/sql-linux.md)]

Arbeiten Sie die [Erste-Schritte-Tutorials](https://aka.ms/sqldev) durch, um schnell erste Schritte mit Programmiersprachen wie C#, Java, Node.js, PHP und Python auszuführen und eine App mit SQL Server für Linux oder Windows oder Docker für macOS zu erstellen.

In der folgenden Tabelle sind die Konnektivitätsbibliotheken oder *-treiber* aufgeführt, die Clientanwendungen aus verschiedenen Sprachen verwenden können, um eine Verbindung mit einer Microsoft SQL Server-Instanz, die lokal oder in der Cloud, unter Linux, Windows oder Docker ausgeführt wird, oder mit Azure SQL-Datenbank und Azure SQL Data Warehouse herzustellen und die entsprechenden Datenbanken zu verwenden. 

| Sprache | Plattform | Zusätzliche Ressourcen | Download | Erste Schritte |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Microsoft ADO.NET für SQL Server](/sql/connect/ado-net/microsoft-ado-net-sql-server) | [Download](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [Erste Schritte](https://www.microsoft.com/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows, Linux, macOS | [Microsoft JDBC-Treiber für SQL Server](https://msdn.microsoft.com/library/mt484311.aspx) | [Download](https://go.microsoft.com/fwlink/?LinkId=245496) |  [Erste Schritte](https://www.microsoft.com/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows, Linux, macOS| [Treiber für PHP für SQL Server](../connect/php/microsoft-php-driver-for-sql-server.md) | Betriebssystem: <br/> \* [Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \* [Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \* [macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [Erste Schritte](https://www.microsoft.com/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows, Linux, macOS | [Node.js-Treiber für SQL Server](../connect/node-js/node-js-driver-for-sql-server.md) |  [Erste Schritte](https://www.microsoft.com/sql-server/developer-get-started/node/ubuntu)
| Python | Windows, Linux, macOS | [Python-SQL-Treiber](../connect/python/python-driver-for-sql-server.md) <br/> \* [pyodbc](https://msdn.microsoft.com/library/mt763257.aspx) |  [Erste Schritte](https://www.microsoft.com/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows, Linux, macOS | [Ruby-Treiber für SQL Server](../connect/ruby/ruby-driver-for-sql-server.md) | [Erste Schritte](https://www.microsoft.com/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows, Linux, macOS | [Microsoft ODBC-Treiber für SQL Server](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) | [Download](https://msdn.microsoft.com/library/mt654048(v=sql.1).aspx) |  

In der folgenden Tabelle sind einige Beispiele zu ORM-Frameworks (Object Relational Mapping, objektrelationale Abbildung) und Webframeworks aufgeführt, die Clientanwendungen mit einer Microsoft SQL Server-Instanz, die lokal oder in der Cloud, unter Linux, Windows oder Docker ausgeführt wird, oder mit Azure SQL-Datenbank und Azure SQL Data Warehouse verwenden können. 

| Sprache | Plattform | ORM(s) |
| :-- | :-- | :-- |
| C# | Windows, Linux, macOS | [Entity Framework](https://docs.microsoft.com/ef)<br>[Entity Framework Core](https://docs.microsoft.com/ef/core/index) |
| Java | Windows, Linux, macOS |[Hibernate ORM](https://hibernate.org/orm)|
| PHP | Windows, Linux | [Laravel (Eloquent)](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows, Linux, macOS | [Sequelize ORM](http://sequelize.org/) |
| Python | Windows, Linux, macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows, Linux, macOS | [Ruby on Rails](https://rubyonrails.org/) |

## <a name="related-links"></a>Verwandte Links
- [SQL Server Treiber](https://msdn.microsoft.com/library/mt654049.aspx) zum Herstellen einer Verbindung aus Clientanwendungen
