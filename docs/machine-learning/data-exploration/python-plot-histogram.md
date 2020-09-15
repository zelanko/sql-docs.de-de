---
title: Zeichnen eines Histogramms für das Durchsuchen von Daten mit Python
description: Hier erfahren Sie, wie Sie ein Histogramm zum Visualisieren von Daten mithilfe von Python erstellen.
author: cawrites
ms.author: chadam
ms.date: 07/14/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: machine-learning
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=azuresqldb-current||=sqlallproducts-allversions'
ms.openlocfilehash: d4ec56f02dd038d87e8b4e8e4c8597b7ba047ffa
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88179811"
---
# <a name="plot-histograms-in-python"></a>Anzeigen von Histogrammen in Python 
[!INCLUDE[SQL Server SQL DB SQL MI](../../includes/applies-to-version/sql-asdb-asdbmi.md)]

In diesem Artikel wird beschrieben, wie Sie Daten mithilfe des Python-Pakets [pandas'.hist()](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.hist.html) darstellen können. Eine SQL-Datenbank ist die Quelle, die verwendet wird, um die Histogrammdatenintervalle zu visualisieren, die über aufeinanderfolgende, nicht überlappende Werte verfügen.

## <a name="prerequisites"></a>Voraussetzungen:

::: moniker range=">=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions"
* SQL Server. Informationen zur Installation finden Sie unter [Installationsleitfaden für SQL Server](../../database-engine/install-windows/install-sql-server.md) oder [SQL Server unter Linux](../../linux/sql-server-linux-overview.md).
::: moniker-end

::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"
* Azure SQL-Datenbank. Informationen zur Registrierung finden Sie unter [Azure SQL-Datenbank](https://docs.microsoft.com/azure/sql-database/sql-database-get-started-portal).
::: moniker-end

::: moniker range="=azuresqldb-mi-current||=sqlallproducts-allversions"
* Azure SQL Managed Instance. Informationen zur Registrierung finden Sie unter [Azure SQL Managed Instance](https://docs.microsoft.com/azure/azure-sql/managed-instance/instance-create-quickstart).

* [SQL Server Management Studio](../../ssms/download-sql-server-management-studio-ssms.md) zum Wiederherstellen der Beispieldatenbank in Azure SQL Managed Instance
::: moniker-end

* Azure Data Studio. Informationen zur Installation finden Sie unter [Was ist Azure Data Studio?](../../azure-data-studio/what-is.md).

* [Wiederherstellen einer Data Warehouse-Beispieldatenbank](../../samples/adventureworks-install-configure.md), um die in diesem Artikel verwendeten Beispieldaten zu erhalten

## <a name="verify-restored-database"></a>Überprüfen der wiederhergestellten Datenbank

Sie können überprüfen, ob die wiederhergestellte Datenbank vorhanden ist, indem Sie die Tabelle **Person.CountryRegion** abfragen:
```sql
USE AdventureWorksDW;
SELECT * FROM Person.CountryRegion;
```
  
## <a name="install-python-packages"></a>Installieren von Python-Paketen

[Laden Sie Azure Data Studio herunter, und führen Sie die Installation durch.](../../azure-data-studio/download-azure-data-studio.md)

Installieren Sie die folgenden Python-Pakete:
  * pyodbc
  * pandas

  Installieren Sie diese Pakete wie folgt:

  1. Klicken Sie in Ihrem Azure Data Studio-Notebook auf die Option **Pakete verwalten**.
  2. Klicken Sie dann im Bereich **Manage Packages** (Pakete verwalten) auf die Registerkarte **Add new** (Neue hinzufügen).
  3. Geben Sie für jedes der folgenden Pakete den jeweiligen Paketnamen ein, klicken Sie auf **Suchen** und dann auf **Installieren**.

## <a name="plot-histogram"></a>Anzeigen des Histogramms

Die im Histogramm angezeigten verteilten Daten basieren auf einer SQL-Abfrage von AdventureWorksDW. Im Histogramm werden Daten und die Häufigkeit von Datenwerten visualisiert. Bearbeiten Sie die Verbindungszeichenfolgenvariablen „server“, „database“, „username“ und „password“, um eine Verbindung mit der SQL-Datenbank herzustellen.

So erstellen Sie ein neues Notebook

1. Klicken Sie in Azure Data Studio auf **Datei** und dann auf **Neues Notebook**.
2. Wählen Sie im Notebook den Kernel **Python3** aus, und klicken Sie dann auf **+code**.
3. Fügen Sie den Code in das Notebook ein, und klicken Sie auf **Alle ausführen**.

```python
import pyodbc 
import pandas as plt
# Some other example server values are
# server = 'localhost\sqlexpress' # for a named instance
# server = 'myserver,port' # to specify an alternate port
server = 'servername' 
database = 'AdventureWorksDW' 
username = 'yourusername' 
password = 'databasename'  
cnxn = pyodbc.connect('DRIVER={SQL Server};SERVER='+server+';DATABASE='+database+';UID='+username+';PWD='+ password)
cursor = cnxn.cursor()
sql = "SELECT DATEDIFF(year, c.BirthDate, GETDATE()) AS Age FROM [dbo].[FactInternetSales] s INNER JOIN dbo.DimCustomer c ON s.CustomerKey = c.CustomerKey"
df = pd.read_sql(sql, cnxn)
df.hist(bins=10)
```

Die Anzeige zeigt die Altersverteilung von Kunden in der FactInternetSales-Tabelle an.

![Pandas-Histogramm](./media/python-histogram.png)


