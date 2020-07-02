---
title: SQLXML ist in SQL Server nicht installiert
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 3dbb4f65-41de-48b8-ad62-47c9d7932de3
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3412b02a7164a5cb57421c52b3662e226bf7e537
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85665921"
---
# <a name="sqlxml-is-not-installed-in-sql-server"></a>SQLXML ist in SQL Server nicht installiert
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Vor der Veröffentlichung von [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]wurde SQLXML 4.0 mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] veröffentlicht und war Bestandteil der Standardinstallation aller [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -Versionen außer [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]. Ab [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]ist die neueste Version von SQLXML (SQLXML 4.0 SP1) nicht mehr in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]enthalten. Zum Installieren von SQLXML 4.0 SP1 laden Sie dieses von [Installationspfad für SQLXML 4.0 SP1](https://www.microsoft.com/download/details.aspx?id=30403)herunter.  
  
 Wenn eine Anwendung unter ausgeführt [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] wird und SQLXML 4,0 erforderlich ist, müssen Sie SQLXML 4,0 SP1 herunterladen und installieren.  
  
## <a name="sqlxml-40-sp1-behavior-with-new-data-types-using-sqloledb-and-sql-server-native-client-ole-db-provider"></a>Verhalten von SQLXML 4.0 SP1 mit neuen Datentypen, die SQLOLEDB und SQL Server Native Client-OLE DB-Anbieter verwenden  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]in wurden die folgenden Datentypen eingeführt, die Entwickler, die SQLXML verwenden, möglicherweise verwenden:  
  
-   **Datum**  
  
-   **Time**  
  
-   **Datetime2**  
  
-   **DateTimeOffset**  
  
 Wenn Sie SQLXML 4,0 SP1 mit SQLOLEDB oder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB aus verwenden [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , werden diese Typen als Zeichen folgen für einen Entwickler angezeigt. SQLXML 4,0 SP1 aktiviert diese vier neuen Datentypen als integrierte skalare Typen, wenn Sie mit [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB Anbieter 11,0 oder höher verwendet werden. Wenn Sie SQLXML 4.0 SP1 noch nicht heruntergeladen haben, kann die Zuordnung dieser Typen zu anderen als Zeichenfolgentypen zum Abschneiden einiger Daten führen. Beispielsweise führt die Zuordnung von **DateTime2** zu **xsd:date** will cause data zu be truncated zu the [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] **DateTime** -Genauigkeit von 3,33 Millisekunden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [SQLXML 4.0-Programmierkonzepte](../../relational-databases/sqlxml/sqlxml-4-0-programming-concepts.md)  
  
  
