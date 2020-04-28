---
title: Hinzufügen einer Visual FoxPro-Datenquelle | Microsoft-Dokumentation
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307141"
---
# <a name="adding-a-visual-foxpro-data-source"></a>Hinzufügen einer Visual FoxPro-Datenquelle
Um von Ihrer Anwendung aus auf Visual FoxPro-Daten zuzugreifen, müssen Sie über eine Datenquelle verfügen. Sie können eine Datenquelle wie folgt erstellen:  
  
-   In einer Anwendung, wie z. b. Microsoft® Word, Microsoft Excel oder Microsoft Access, das ODBC-Treiber verwendet.  
  
-   Außerhalb Ihrer Anwendung mithilfe der Systemsteuerung Microsoft Windows® 95, Microsoft Windows 98 oder Microsoft Windows NT®/Windows 2000.  
  
 Nachdem eine Datenquelle auf dem System vorhanden ist, können Sie jedes Mal, wenn Sie auf Visual FoxPro-Daten zugreifen möchten, dieselbe Datenquelle wieder verwenden. Wenn Sie über mehrere unterschiedliche Datenbanken oder Tabellen verfügen, auf die Sie zugreifen möchten, können Sie für jede Datenbank oder jedes Verzeichnis eine separate Datenquelle erstellen.  
  
 Mit der folgenden Prozedur wird eine Datenquelle mithilfe der Systemsteuerung erstellt. Weitere Informationen zum Erstellen einer Datenquelle aus einer Anwendung finden Sie unter Zugreifen auf [Visual FoxPro-Daten aus Microsoft Office](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md).  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>So fügen Sie eine Visual FoxPro-Datenquelle hinzu  
  
1.  Öffnen Sie auf Computern, auf denen Windows 2000 ausgeführt wird, die Windows-Systemsteuerung, und doppelklicken Sie auf Verwaltung.  
  
2.  Doppelklicken Sie auf Datenquellen (ODBC), um das Dialogfeld ODBC-Datenquellen-Administrator zu öffnen. Dieses Symbol ist verfügbar, nachdem Sie den Visual FoxPro-ODBC-Treiber oder eine beliebige ODBC-Treibersoftware installiert haben.  
  
    > [!NOTE]  
    >  Wenn Sie eine frühere Version von Windows ausführen, öffnen Sie die Windows-Systemsteuerung, und doppelklicken Sie auf 32-Bit-ODBC oder ODBC, um das Dialogfeld ODBC-Datenquellen-Administrator zu öffnen.  
  
3.  Klicken Sie auf Hinzufügen.  
  
4.  Wählen Sie im Dialogfeld neue Datenquelle erstellen die Option Microsoft Visual FoxPro-Treiber aus, und klicken Sie dann auf Fertigstellen.  
  
5.  Geben Sie im [Dialogfeld Setup für ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)den Datenquellen Namen und die Beschreibung ein, wählen Sie den Datenbanktyp aus, wählen Sie die Datenbank oder das Verzeichnis aus, und klicken Sie dann auf OK.  
  
     Der neue Datenquellen Name wird im Dialogfeld ODBC-Datenquellen-Administrator auf der Registerkarte Benutzer-DSN in der Liste Benutzerdaten Quellen angezeigt.  
  
6.  Klicken Sie auf OK, um die neue Datenquelle zu speichern, und schließen Sie das Dialogfeld ODBC-Datenquellen-Administrator.
