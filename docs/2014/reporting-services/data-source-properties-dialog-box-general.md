---
title: Dialogfeld "Eigenschaften", "Allgemein" Datenquelle "| Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.general.f1
- "10120"
ms.assetid: 44b5edd3-5c11-4d3d-91b8-5871aa0572ed
caps.latest.revision: 35
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 823604c6116c78f4313d5f1e328d98d7ed35f950
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2018
ms.locfileid: "36159951"
---
# <a name="data-source-properties-dialog-box-general"></a>Datenquelleneigenschaften (Dialogfeld), Allgemein
  Mithilfe der Registerkarte **Allgemein** im Dialogfeld **Datenquelleneigenschaften** können Sie die Verbindungsinformationen für eine Datenquelle im Bericht anzeigen und ändern.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie den Namen der Datenquelle ein. Der Datenquellenname muss innerhalb des Berichts eindeutig sein. Standardmäßig wird der Datenquelle ein allgemeiner Name, wie DataSource1 oder DataSource2, zugewiesen.  
  
 **Eingebettete Verbindung**  
 Aktivieren Sie diese Option, wenn Sie keine freigegebene Datenquelle verwenden möchten.  
  
 **Typ**  
 Wählen Sie eine Datenverarbeitungserweiterung aus. In der Liste werden alle registrierten Erweiterungen aufgeführt.  
  
 **Verbindungszeichenfolge**  
 Geben Sie eine Verbindungszeichenfolge für die Datenquelle ein. Klicken Sie auf **Bearbeiten** , um die Verbindungszeichenfolge mithilfe des Dialogfeldes **Verbindungseigenschaften** zu erstellen. Klicken Sie auf die Schaltfläche **Ausdruck** (*fx*), um den Ausdruck zu bearbeiten.  
  
 **Freigegebenen Datenquellenverweis verwenden**  
 Wählen Sie diese Option aus, um einen Link zu einer freigegebenen Datenquelle herzustellen. Wählen Sie in der Dropdownliste eine freigegebene Datenquelle aus. Um die ausgewählte Datenquelle zu bearbeiten, klicken Sie auf **Bearbeiten**. Falls die Option **Freigegebenen Datenquellenverweis verwenden** aktiviert ist, sind die Optionen **Typ** und **Verbindungszeichenfolge** deaktiviert.  
  
 **Beim Verarbeiten der Abfragen verwenden Sie einzelne Transaktion**  
 Wählen Sie diese Option, um anzugeben, dass Datasets, die diese Datenquelle verwenden, in einer einzelnen Transaktion für die Datenbank ausgeführt werden. Um Transaktionen für Unterberichte, die die gleiche Datenquelle verwenden, einzuschließen, setzen Sie die Option **MergeTransactions** im Eigenschaftenabschnitt **Sonstige** des Unterberichts im Bereich **Eigenschaften** auf **True** .  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Erstellen einer eingebettete oder freigegebene Datenquelle &#40;SSRS&#41;](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md)   
 [Datenverbindungen, Datenquellen und Verbindungszeichenfolgen in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Datenquelleneigenschaften (Dialogfeld), Anmeldeinformationen](../../2014/reporting-services/data-source-properties-dialog-box-credentials.md)  
  
  