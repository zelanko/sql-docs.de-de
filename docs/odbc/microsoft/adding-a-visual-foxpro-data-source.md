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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 262e8487e8133cf1c312659fa2fc28276aafa07e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63198277"
---
# <a name="adding-a-visual-foxpro-data-source"></a>Hinzufügen einer Visual FoxPro-Datenquelle
Um Visual FoxPro-Daten aus Ihrer Anwendung zuzugreifen, müssen Sie eine Datenquelle verfügen. Sie können eine Datenquelle wie folgt erstellen:  
  
-   In einer Anwendung wie Microsoft® Word, Microsoft Excel oder Microsoft Access verwendet, ODBC-Treiber.  
  
-   Verwenden außerhalb der Anwendung die Microsoft Windows® 95, Microsoft Windows 98 oder Microsoft Windows/Windows 2000-Systemsteuerung aus.  
  
 Nachdem eine Datenquelle auf dem System vorhanden ist, können Sie die gleiche Datenquelle jedes Mal verwenden, die auf Visual FoxPro-Daten zugreifen möchten. Wenn Sie mehrere verschiedene Datenbanken oder Tabellen, die Sie zugreifen möchten, können Sie eine anderen Datenquelle, für jede Datenbank oder ein Verzeichnis erstellen.  
  
 Die folgende Prozedur erstellt eine Datenquelle mithilfe der Systemsteuerung. Weitere Informationen dazu, wie Sie eine Datenquelle aus einer Anwendung zu erstellen, finden Sie unter [den Zugriff auf Visual FoxPro-Daten aus Microsoft Office](../../odbc/microsoft/accessing-visual-foxpro-data-from-microsoft-office.md).  
  
### <a name="to-add-a-visual-foxpro-data-source"></a>Hinzufügen eine Visual FoxPro-Datenquelle  
  
1.  Klicken Sie auf Computern, auf denen Windows 2000 ausgeführt werden, öffnen Sie die Windows-Systemsteuerung, und doppelklicken Sie auf Verwaltung.  
  
2.  Doppelklicken Sie auf Datenquellen (ODBC) um das Dialogfeld ODBC-Datenquellenadministrator zu öffnen. Dieses Symbol ist nach der Installation der Visual FoxPro-ODBC-Treiber oder alle ODBC-Treiber-Software verfügbar.  
  
    > [!NOTE]  
    >  Wenn Sie eine frühere Version von Windows ausführen, öffnen Sie die Windows-Systemsteuerung, und doppelklicken Sie auf 32-Bit-ODBC- oder ODBC um das Dialogfeld ODBC-Datenquellenadministrator zu öffnen.  
  
3.  Klicken Sie auf Hinzufügen.  
  
4.  Wählen Sie Microsoft Visual FoxPro-Treiber, und klicken Sie dann auf "Fertig stellen", klicken Sie im Dialogfeld "neue Datenquelle erstellen".  
  
5.  In der [Dialogfeld ODBC-Visual FoxPro-Setup](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md), geben Sie den ODBC-Datenquellenname und die Beschreibung, wählen Sie den Typ, wählen Sie die Datenbank oder das Verzeichnis, und klicken Sie dann auf OK.  
  
     Der neue Name der Datenquelle wird in der Liste der Datenquellen für die Benutzer auf der Registerkarte "Benutzer-DSN" im Dialogfeld ODBC-Datenquellen-Administrator angezeigt.  
  
6.  Klicken Sie auf OK, um die neue Datenquelle zu speichern und schließen Sie das Dialogfeld ODBC-Datenquellen-Administrator.
