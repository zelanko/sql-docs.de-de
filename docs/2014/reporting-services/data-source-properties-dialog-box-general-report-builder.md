---
title: Dialog Feld "Datenquellen Eigenschaften", "Allgemein" (Berichts-Generator) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10018"
ms.assetid: b956f43a-8426-4679-acc1-00f405d5ff5b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7bedf016dce02928bbd47dbfce60943ec667a824
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109472"
---
# <a name="data-source-properties-dialog-box-general-report-builder"></a>Datenquelleneigenschaften (Dialogfeld), Allgemein (Berichts-Generator)
  Wählen Sie **Allgemein** im Dialogfeld **Datenquelleneigenschaften** aus, um eine freigegebene Datenquelle aus einem Berichtsserver zu wählen oder um Verbindungsinformationen für eine Datenquelle zu erstellen oder zu ändern, die im Bericht eingebettet ist.  
  
 Der Typ von Anmeldeinformationen, der verwendet wurde, um eine Verbindung mit einer Datenquelle herzustellen, wird in den Datenquelleneigenschaften angegeben. Wenn Sie einen Bericht vom Berichtsserver öffnen, funktionieren die Laufzeitanmeldeinformationen, die in den Datenquelleneigenschaften angegeben sind, möglicherweise nicht für Entwurfszeittasks, wie z. B. das Erstellen von Abfragen und das Anzeigen von Berichten in der Vorschau. Die Datenquelle verwendet z. B. möglicherweise andere Windows-Anmeldeinformationen als Ihre oder einen Benutzernamen und ein Kennwort, der bzw. das Ihnen nicht bekannt ist.  
  
 In Berichts-Generator wird das Dialogfeld **Datenquellen-Anmeldeinformationen eingeben** angezeigt, wenn keine Verbindung zu der Datenquelle hergestellt werden kann, die die in den Datenquelleneigenschaften angegebenen Anmeldeinformationen verwendet. Dies geschieht normalerweise in diesen Fällen:  
  
-   die Datenquelle so konfiguriert ist, dass Anmeldeinformationen angefordert werden.  
  
-   die Datenquelle so konfiguriert ist, dass gespeicherte Anmeldeinformationen verwendet werden.  Um Sicherheitsrisiken zu minimieren, werden vom Berichts-Generator standardmäßig keine Anmeldeinformationen abgerufen, die auf dem Server gespeichert sind.  
  
 Sie können das Dialogfeld **Datenquellen-Anmeldeinformationen eingeben** verwenden, um die von Berichts-Generator zur Entwurfszeit verwendeten Anmeldeinformationen zu ändern, um als der aktuelle Windows-Benutzer eine Verbindung zu der Datenquelle herzustellen oder einen Benutzernamen und ein Kennwort einzugeben. Wenn Sie einen Benutzernamen und ein Kennwort eingeben, können Sie angeben, ob diese als Windows-Anmeldeinformationen verwendet werden.  
  
> [!NOTE]  
>  Sie können mit den Abfrage-Designern zwar einen anderen Anmeldeinformationstyp für Entwurfszeitanmeldeinformationen angeben, in der Berichtsvorschau können Sie jedoch nur den Benutzernamen und das Kennwort für die vorhandenen Anmeldeinformationsoptionen angeben, die in der Datenquelle angegeben sind.  
  
 Wenn Sie auf **Verbindung testen**klicken, wird die Verbindung zu der Datenquelle mit den Anmeldeinformationen getestet, die in den Datenquelleneigenschaften sind. Sie können Verbindungen für eingebettete und freigegebene Datenquellen testen.  
  
 Wenn die angegebenen Anmeldeinformationen unvollständig sind (wenn z. B. ein Kennwort erforderlich ist), werden Sie in Berichts-Generator erneut zur Eingabe von Laufzeitanmeldeinformationen aufgefordert, wenn eine Verbindung mit der Datenquelle hergestellt werden muss. Die Entwurfszeitanmeldeinformationen werden gespeichert, und Sie werden nicht erneut aufgefordert.  
  
## <a name="options"></a>Tastatur  
 **Name**  
 Geben Sie den Namen der Datenquelle ein. Der Datenquellenname muss innerhalb des Berichts eindeutig sein. Standardmäßig wird der Datenquelle ein allgemeiner Name, wie DataSource1 oder DataSource2, zugewiesen.  
  
 **Gemeinsam genutzte Verbindung verwenden**  
 Wählen Sie diese Option, um eine freigegebene Datenquelle zu suchen, die auf einem Berichtsserver veröffentlicht wurde.  
  
 Nachdem Sie eine Datenquelle aus einem Berichtsserver gewählt haben, hält Berichts-Generator eine Verbindung mit diesem Berichtsserver aufrecht.  
  
 **In Bericht eingebettete Verbindung verwenden**  
 Wählen Sie diese Option, um eine Datenquelle zu erstellen, die nur von diesem Bericht verwendet wird.  
  
 **Typ**  
 Wählen Sie eine Datenverarbeitungserweiterung aus. In der Liste werden alle registrierten Erweiterungen aufgeführt.  
  
 **Verbindungszeichenfolge**  
 Geben Sie eine Verbindungszeichenfolge für die Datenquelle ein. Klicken Sie auf **Erstellen** , um die Verbindungszeichenfolge mithilfe des Dialogfelds **Verbindungseigenschaften** zu erstellen. Klicken Sie auf die Schaltfläche **Ausdruck** (*fx*), um den Ausdruck zu bearbeiten.  
  
 **Einzelne Transaktion bei der Verarbeitung der Abfragen verwenden**  
 Wählen Sie diese Option, um anzugeben, dass Datasets, die diese Datenquelle verwenden, in einer einzelnen Transaktion für die Datenbank ausgeführt werden. Um Transaktionen für Unterberichte aufzunehmen, die dieselbe Datenquelle verwenden, wählen Sie den Unterbericht und legen im Eigenschaftenbereich **MergeTransactions** auf **True**fest.  
  
 **Testen der Verbindung**  
 Klicken Sie auf diese Option, um zu überprüfen, dass die Datenquellenverbindung mit den angegebenen Anmeldeinformationen funktioniert. Wenn die Verbindung nicht hergestellt werden kann, müssen Sie die Anmeldeinformationen und die Serververfügbarkeit überprüfen. Sie können Datenquellenverbindungen für eingebettete und freigegebene Datenquellen testen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Hinzufügen von Daten zu einem Bericht &#40;Berichts-Generator und SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Hinzufügen und Überprüfen einer Datenverbindung oder Datenquelle &#40;Berichts-Generator und SSRS&#41;](report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)   
 [Datenverbindungen, Datenquellen und Verbindungs Zeichenfolgen in Berichts-Generator](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)   
 [Datenquellen Eigenschaften (Dialog Feld), Anmelde Informationen &#40;Berichts-Generator&#41;](../../2014/reporting-services/data-source-properties-dialog-box-credentials-report-builder.md)   
 [Hilfe zu Dialogfeldern, Bereichen und Assistenten in Berichts-Generator](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)  
  
  
