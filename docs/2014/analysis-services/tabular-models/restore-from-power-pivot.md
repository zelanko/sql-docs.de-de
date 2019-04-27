---
title: Von PowerPivot wiederherstellen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql11.asvs.ssmsimbi.RestoreFromPP.f1
ms.assetid: 232ac8ed-77fe-47d8-acd3-59bc2fdfdf48
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 21b3c477c87861d224d72a52dcce89ceacf7bb3a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62756572"
---
# <a name="restore-from-powerpivot"></a>Von PowerPivot wiederherstellen
  Sie können die Funktion Von PowerPivot wiederherstellen in SQL Server Management Studio verwenden, um eine neue Datenbank für tabellarische Modelle auf einer (im Tabellenmodus ausgeführte) Analysis Services-Instanz zu erstellen oder um eine vorhandene Datenbank aus einer PowerPivot-Arbeitsmappe (.xlsx) wiederherzustellen.  
  
> [!NOTE]  
>  Die Projektvorlage Aus PowerPivot importieren in SQL Server Data Tools verfügt über ähnliche Funktionen. Weitere Informationen finden Sie unter [aus PowerPivot importieren &#40;SSAS – tabellarisch&#41;](import-from-power-pivot-ssas-tabular.md).  
  
 Folgendes sollte bei Verwendung der Funktion Von PowerPivot wiederherstellen beachtet werden:  
  
-   Um die Funktion Von PowerPivot wiederherstellen zu verwenden, müssen Sie als Mitglied der Rolle Serveradministrator bei der Analysis Services-Instanz angemeldet sein.  
  
-   Das Dienstkonto der Analysis Services-Instanz muss über Leseberechtigungen für die Arbeitsmappendatei verfügen, aus der Daten wiederhergestellt werden.  
  
-   Wenn Sie eine Datenbank von PowerPivot wiederherstellen, ist die Eigenschaft Identitätswechselinformationen der Datenquelle der Datenbank für tabellarische Modelle auf den Standardwert festgelegt, der dem Dienstkonto der Analysis Services-Instanz entspricht. Es wird empfohlen, die Identitätswechsel-Anmeldeinformationen in den Datenbankeigenschaften in ein Windows-Benutzerkonto zu ändern. Weitere Informationen finden Sie unter [Identitätswechsel &#40;SSAS – tabellarisch&#41;](impersonation-ssas-tabular.md).  
  
-   Daten im PowerPivot-Datenmodell werden in eine vorhandene oder neue Datenbank für tabellarische Modelle auf der Analysis Services-Instanz kopiert. Wenn die PowerPivot-Arbeitsmappe verknüpfte Tabellen enthält, werden sie ähnlich wie eine Tabelle, die mit In neue Tabelle einfügen erstellt wurde, als Tabelle ohne Datenquelle neu erstellt.  
  
### <a name="to-restore-from-powerpivot"></a>So stellen Sie Daten von PowerPivot wieder her  
  
1.  Klicken Sie in SSMS in der Active Directory-Instanz, die Sie wiederherstellen, möchten rechten Maustaste auf **Datenbanken**, und klicken Sie dann auf **von PowerPivot wiederherstellen**.  
  
2.  In der **von PowerPivot wiederherstellen** Dialogfeld **Wiederherstellungsquelle**im **Sicherungsdatei**, klicken Sie auf **Durchsuchen**, und wählen Sie dann eine ABF- oder xslx die Datei aus.  
  
3.  Geben Sie in **Datenbank wiederherstellen**unter **Wiederherstellungsziel**den Namen einer neuen oder vorhandenen Datenbank ein. Wenn Sie keinen Namen angeben, wird der Name der Arbeitsmappe verwendet.  
  
4.  Klicken Sie unter **Speicherort**auf **Durchsuchen**, und wählen Sie anschließend einen Ort zum Speichern der Datenbank aus.  
  
5.  Lassen Sie unter **Optionen**das Kontrollkästchen **Sicherheitsinformationen einschließen** aktiviert. Diese Einstellung gilt nicht beim Wiederherstellen von Daten aus einer PowerPivot-Arbeitsmappe.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellarische Modelldatenbanken &#40;SSAS – tabellarisch&#41;](tabular-model-databases-ssas-tabular.md)   
 [Aus PowerPivot importieren &#40;SSAS – tabellarisch&#41;](import-from-power-pivot-ssas-tabular.md)  
  
  
