---
title: 'Lektion 5: Automatisieren der Bereinigung und des Abgleich mit SSIS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f068d4db-2d56-41b1-bed2-0cffa3ca411d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 90f967b2446e11a27f5a87803bb71d6e1ec53557
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039836"
---
# <a name="lesson-5-automating-the-cleansing-and-matching-using-ssis"></a>Lektion 5: Automatisierung der Bereinigung und des Abgleich mit SSIS
  In Lektion 1 haben Sie die Wissensdatenbank Suppliers erstellt und verwendet, um Daten in Lektion 2 zu bereinigen und Daten in Lektion 3 mithilfe des Tool- **DQS-Clients**abzugleichen. In einem realen Szenario müssen Sie möglicherweise Daten aus einer Quelle abrufen, die von DQS nicht unterstützt wird, oder Sie möchten den Bereinigungs-und Abgleichsprozess automatisieren, ohne das **DQS-Client** Tool verwenden zu müssen. SQL Server Integration Services (SSIS) verfügt über Komponenten, die Sie verwenden können, um Daten aus verschiedenen heterogenen Quellen und eine Transformations Komponente der **[DQS-Bereinigung](https://msdn.microsoft.com/library/ee677619.aspx)** zum Aufrufen der von DQS verfügbar gemachten Bereinigungs Funktionalität aufzurufen Derzeit stellt DQS keine abgleichsfunktionen für die Verwendung durch SSIS zur Verfügung, Sie können jedoch die **[Transformation für Fuzzygruppierung](../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)** verwenden, um Duplikate in den Daten zu identifizieren.  
  
 Mithilfe des **Entitäts basierten stagingfeatures**können Sie Daten in MDS hochladen. Wenn Sie eine Entität in MDS erstellen, werden entsprechende Stagingtabellen und gespeicherte Prozeduren automatisch erstellt. Wenn Sie z. b. die Entität "Supplier" erstellt haben, wurden die Tabelle " **STG. supplier_Leaf** " und die gespeicherte Prozedur " **STG. udp_Supplier_Leaf** " automatisch erstellt. Sie verwenden die Stagingtabellen und Prozeduren, um Entitätselemente zu erstellen, zu aktualisieren und zu löschen. In dieser Lektion erstellen Sie neue Entitätselemente für die Entität "Suppliers". Um Daten auf den MDS-Server zu laden, lädt das SSIS-Paket zuerst die Daten in die Stagingtabelle stg.supplier_Leaf und löst dann die zugeordnete gespeicherte Prozedur stg.udp_Supplier_Leaf aus. Weitere Informationen finden Sie unter [Importieren von Daten](../master-data-services/overview-importing-data-from-tables-master-data-services.md) .  
  
 In dieser Lektion führen Sie die folgenden Aufgaben aus:  
  
1.  Entfernen Sie Lieferantendaten in MDS (wenn Sie die vorherigen vier Lektionen durchgearbeitet haben). Das SSIS-Paket, das Sie in dieser Lektion erstellen, lädt die Daten in MDS automatisch hoch. Sie haben die bereinigten und abgeglichenen Lieferantendaten in einem früheren Schritt manuell mit DQS-Client auf den MDS-Server hochgeladen.  
  
2.  Erstellen Sie eine Abonnementsicht in der Entität "Suppliers", um Daten in der Entität anderen Anwendungen bereitzustellen. Diese Aktion erstellt eine SQL-Sicht, die Sie mit SQL Server Management Studio überprüfen. Sie werden diese Sicht nicht in dieser Version des Lernprogramms nutzen.  
  
3.  Erstellen und Ausführen eines SSIS-Projekts mit **SQL Server Data Tools**. Das Projekt verwendet **Daten** Bereinigungs Transformation, um eine Bereinigungs Anforderung an den DQS-Server zu senden. Die abgleichsfunktionalität wird von DQS noch nicht verfügbar gemacht, sodass Sie Duplikate mithilfe der Transformation für **Fuzzygruppierung** identifizieren können.  
  
4.  Überprüfen Sie mit Master Data Manager, ob die Daten in MDS erstellt wurden.  
  
5.  Überprüfen Sie die Ergebnisse des DQS-Bereinigungsprojekts, das vom SSIS-Paket erstellt wurde, und führen Sie optional eine interaktive Bereinigung durch, um die Wissensdatenbank auszubauen.  
  
## <a name="next-step"></a>Nächster Schritt  
 [Aufgabe 1 &#40;Voraussetzung&#41;: Entfernen von Lieferantendaten in MDS](../../2014/tutorials/task-1-prerequisite-removing-supplier-data-in-mds.md)  
  
  
