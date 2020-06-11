---
title: Importieren aus einer relationalen Datenquelle (SSAS-tabellarisch) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 043201cc-fbef-4ed0-bde8-dc5e3a3e8bea
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9504ae981e301c6f602a5930eecef47fc6667630
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544202"
---
# <a name="import-from-a-relational-data-source-ssas-tabular"></a>Import von einer relationalen Datenquelle (SSAS – tabellarisch)
  Mit dem Tabellenimport-Assistenten können Sie Daten aus einer Vielzahl relationaler Datenbanken importieren: Der Assistent ist in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]im Menü **Modell** verfügbar. Der entsprechende Anbieter muss auf dem Computer installiert sein, um eine Verbindung mit einer Datenquelle herzustellen. Weitere Informationen zu unterstützten Datenquellen und -anbietern finden Sie unter [Unterstützte Datenquellen &#40;SSAS – tabellarisch&#41;](tabular-models/data-sources-supported-ssas-tabular.md).  
  
 Der Tabellenimport-Assistent unterstützt das Importieren von Daten aus den folgenden Datenquellen:  
  
 **Relationale Datenbanken**  
  
-   Microsoft SQL Server-Datenbank  
  
-   Microsoft SQL Azure  
  
-   Microsoft Access-Datenbank  
  
-   Microsoft SQL Server Parallel Data Warehouse  
  
-   Oracle  
  
-   Teradata  
  
-   Sybase  
  
-   Informix  
  
-   IBM DB2  
  
-   OLE DB/ODBC  
  
 **Mehrdimensionale Quellen**  
  
-   Microsoft SQL Server Analysis Services-Cube  
  
 Der Tabellenimport-Assistent unterstützt keine Datenimporte, bei denen eine [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] -Arbeitsmappe als Datenquelle verwendet wird.  
  
### <a name="to-import-data-from-a-database"></a>So importieren Sie Daten aus einer Datenbank  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]auf das Menü **Modell** und dann auf **Aus Datenquelle importieren**.  
  
2.  Wählen Sie auf der Seite **Mit einer Datenquelle verbinden** den Typ der Datenbank aus, mit der eine Verbindung hergestellt werden soll, und klicken Sie dann auf **Weiter**.  
  
3.  Führen Sie die Schritte im Tabellenimport-Assistenten aus. Auf den nachfolgenden Seiten können Sie bestimmte Tabellen und Sichten auswählen, oder Sie können Filter anwenden, indem Sie die Seite **Tabellen und Sichten auswählen** verwenden oder eine SQL-Abfrage auf der Seite **SQL-Abfrage angeben** erstellen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Importieren von Daten &#40;tabellarischen SSAS-&#41;](import-data-ssas-tabular.md)   
 [Unterstützte Datenquellen &#40;SSAS – tabellarisch&#41;](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
