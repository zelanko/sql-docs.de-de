---
title: Hinzufügen einer Visual FoxPro-Datenquelle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro data source [ODBC], adding
- adding data sources [ODBC], Visual FoxPro ODBC driver
ms.assetid: 1487e188-52c8-4f48-b4fe-25a650dd9e97
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1fd0c0f929ca00b7cf731dc92f07f69b6503f884
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307141"
---
# <a name="adding-a-visual-foxpro-data-source"></a>Hinzufügen einer Visual FoxPro-Datenquelle
Um auf Visual FoxPro-Daten aus Ihrer Anwendung zugreifen zu können, benötigen Sie eine Datenquelle. Sie können eine Datenquelle wie folgt erstellen:  
  
-   In einer Anwendung, z. B. Microsoft® Word, Microsoft Excel oder Microsoft Access, die ODBC-Treiber verwendet.  
  
-   Außerhalb Ihrer Anwendung verwenden Sie die Systemsteuerung Microsoft Windows® 95, Microsoft Windows 98 oder Microsoft Windows NT®/Windows 2000.  
  
 Nachdem auf Ihrem System eine Datenquelle vorhanden ist, können Sie dieselbe Datenquelle jedes Mal wiederverwenden, wenn Sie auf Visual FoxPro-Daten zugreifen möchten. Wenn Sie über mehrere verschiedene Datenbanken oder Tabellen verfügen, auf die Sie zugreifen möchten, können Sie für jede Datenbank oder jedes Verzeichnis eine separate Datenquelle erstellen.  
  
 Mit dem folgenden Verfahren wird mithilfe der Systemsteuerung eine Datenquelle erstellt. Weitere Informationen zum Erstellen einer Datenquelle aus einer Anwendung finden Sie [unter Zugriff auf Visual FoxPro-Daten von Microsoft Office](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md).  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>So fügen Sie eine Visual FoxPro-Datenquelle hinzu  
  
1.  Öffnen Sie auf Computern, auf denen Windows 2000 ausgeführt wird, das Windows-Bedienfeld, und doppelklicken Sie auf Verwaltungstools.  
  
2.  Doppelklicken Sie auf Datenquellen (ODBC), um das Dialogfeld ODBC Data Source Administrator zu öffnen. Dieses Symbol ist verfügbar, nachdem Sie den Visual FoxPro ODBC-Treiber oder eine ODBC-Treibersoftware installiert haben.  
  
    > [!NOTE]  
    >  Wenn Sie eine frühere Windows-Version ausführen, öffnen Sie das Windows-Bedienfeld, und doppelklicken Sie auf 32-Bit-ODBC oder ODBC, um das Dialogfeld ODBC-Datenquellenadministrator zu öffnen.  
  
3.  Klicken Sie auf Hinzufügen.  
  
4.  Wählen Sie im Dialogfeld Neue Datenquelle erstellen die Option Microsoft Visual FoxPro Driver aus, und klicken Sie dann auf Fertig stellen.  
  
5.  Geben Sie im [Dialogfeld ODBC Visual FoxPro Setup](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)den Namen und die Beschreibung der Datenquelle ein, wählen Sie den Datenbanktyp aus, wählen Sie die Datenbank oder das Verzeichnis aus, und klicken Sie dann auf OK.  
  
     Der neue Datenquellenname wird in der Liste Benutzerdatenquellen auf der Registerkarte Benutzer-DSN im Dialogfeld ODBC-Datenquellenadministrator angezeigt.  
  
6.  Klicken Sie auf OK, um die neue Datenquelle zu speichern und das Dialogfeld ODBC Data Source Administrator zu schließen.
