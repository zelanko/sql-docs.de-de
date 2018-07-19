---
title: 'Lektion 2: Angeben von Verbindungsinformationen (Reporting Services) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 54405a3a-d7fa-4d95-8963-9aa224e5901e
caps.latest.revision: 47
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: c9e828696135d13263a68219c1a248325a14676d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37196790"
---
# <a name="lesson-2-specifying-connection-information-reporting-services"></a>Lektion 2: Angeben von Verbindungsinformationen (Reporting Services)
  Nachdem Sie dem Tutorial-Projekt einen Bericht hinzugefügt haben, müssen Sie eine *Datenquelle*erstellen. Bei dieser handelt es sich um Verbindungsinformationen, mit denen der Bericht auf Daten aus einer relationalen Datenbank, einer mehrdimensionalen Datenbank oder einer sonstigen Ressource zugreift.  
  
 In dieser Lektion verwenden Sie die Beispieldatenbank [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] als Datenquelle. In diesem Tutorial wird davon ausgegangen, dass diese Datenbank in der Standardinstanz von [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] auf Ihrem lokalen Computer installiert ist.  
  
### <a name="to-set-up-a-connection"></a>So richten Sie eine Verbindung ein  
  
1.  Klicken Sie im **Berichtsdatenbereich** auf **Neu** und anschließend auf **Datenquelle**.  
  
    > [!NOTE]  
    >  Zum Anzeigen des **Berichtsdatenbereichs** klicken Sie im Menü **Ansicht** auf **Berichtsdaten**.  
  
2.  In **Namen**, Typ [!INCLUDE[ssSampleDBUserInputNonLocal](../includes/sssampledbuserinputnonlocal-md.md)].  
  
3.  Stellen Sie sicher, dass **Eingebettete Verbindung** aktiviert ist.  
  
4.  Wählen Sie unter **Typ**die Option **Microsoft SQL Server**aus.  
  
5.  Geben Sie für **Verbindungszeichenfolge**Folgendes ein:  
  
    ```  
    Data source=localhost; initial catalog=AdventureWorks2012  
    ```  
  
     Bei dieser Verbindungszeichenfolge wird davon ausgegangen, dass [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], der Berichtsserver und die [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]-Datenbank zusammen auf dem lokalen Computer installiert sind und Sie über die Berechtigung verfügen, sich bei der [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)]-Datenbank anzumelden.  
  
    > [!NOTE]  
    >  Wenn Sie [!INCLUDE[ssExpress](../includes/ssexpress-md.md)] with Advanced Services oder eine benannte Instanz verwenden, muss die Verbindungszeichenfolge Instanzinformationen einschließen:  
    >   
    >  `Data source=localhost\SQLEXPRESS; initial catalog=AdventureWorks2012`  
    >   
    >  Weitere Informationen zu Verbindungszeichenfolgen finden Sie unter [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md) und [Daten Datenquelleneigenschaften, Dialogfeld, Allgemein](data-source-properties-dialog-box-general.md).  
  
6.  Klicken Sie im linken Bereich auf **Anmeldeinformationen** , und klicken Sie auf **Windows-Authentifizierung verwenden (integrierte Sicherheit)**.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)] Datenquelle [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] wird hinzugefügt, um die **Berichtsdaten** Bereich.  
  
## <a name="next-task"></a>Nächste Aufgabe  
 Sie haben erfolgreich eine Verbindung mit definiert die [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] -Beispieldatenbank. Als Nächstes erstellen Sie den Bericht. Weitere Informationen finden Sie unter [Lektion 3: Definieren eines Datasets für den Tabellenbericht (Reporting Services)](lesson-3-defining-a-dataset-for-the-table-report-reporting-services.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
