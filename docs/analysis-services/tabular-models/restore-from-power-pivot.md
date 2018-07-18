---
title: Wiederherstellen von PowerPivot | Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f95c1e891a218af73eb7c5bacbd1ea5a48e3a830
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "34041925"
---
# <a name="restore-from-power-pivot"></a>Wiederherstellen von PowerPivot
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  Sie können die Funktion „Von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] wiederherstellen“ in SQL Server Management Studio verwenden, um eine neue Datenbank für tabellarische Modelle auf einer (im Tabellenmodus ausgeführten) Analysis Services-Instanz zu erstellen oder um eine vorhandene Datenbank aus einer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe (.xlsx) wiederherzustellen.  
  
> [!NOTE]  
>  Die Projektvorlage „Aus [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] importieren“ in SQL Server Data Tools verfügt über ähnliche Funktionen. Weitere Informationen finden Sie unter [importieren aus PowerPivot](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md).  
  
 Folgendes sollte bei Verwendung der Funktion „Von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]wiederherstellen“ beachtet werden:  
  
-   Um die Funktion „Von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]wiederherstellen“ zu verwenden, müssen Sie als Mitglied der Rolle Serveradministrator bei der Analysis Services-Instanz angemeldet sein.  
  
-   Das Dienstkonto der Analysis Services-Instanz muss über Leseberechtigungen für die Arbeitsmappendatei verfügen, aus der Daten wiederhergestellt werden.  
  
-   Wenn Sie eine Datenbank von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]wiederherstellen, ist die Eigenschaft Identitätswechselinformationen der Datenquelle der Datenbank für tabellarische Modelle auf den Standardwert festgelegt, der dem Dienstkonto der Analysis Services-Instanz entspricht. Es wird empfohlen, die Identitätswechsel-Anmeldeinformationen in den Datenbankeigenschaften in ein Windows-Benutzerkonto zu ändern. Weitere Informationen finden Sie unter [Identitätswechsel](../../analysis-services/tabular-models/impersonation-ssas-tabular.md).  
  
-   Daten im [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Datenmodell werden in eine vorhandene oder neue Datenbank für tabellarische Modelle auf der Analysis Services-Instanz kopiert. Wenn die [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe verknüpfte Tabellen enthält, werden sie ähnlich wie eine Tabelle, die mit In neue Tabelle einfügen erstellt wurde, als Tabelle ohne Datenquelle neu erstellt.  
  
### <a name="to-restore-from-power-pivot"></a>So führen Sie eine Wiederherstellung aus PowerPivot aus  
  
1.  Klicken Sie in SSMS auf der Active Directory-Instanz, auf der die Wiederherstellung erfolgen soll, mit der rechten Maustaste auf **Datenbanken**, und klicken Sie anschließend auf **Von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] wiederherstellen**.  
  
2.  Klicken Sie im Dialogfeld **Von [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] wiederherstellen** unter **Wiederherstellungsquelle** in **Sicherungsdatei** auf **Durchsuchen**, und wählen Sie anschließend eine ABF- oder XSLX-Datei aus, aus der Daten wiederhergestellt werden sollen.  
  
3.  Geben Sie in **Datenbank wiederherstellen** unter **Wiederherstellungsziel** den Namen einer neuen oder vorhandenen Datenbank ein. Wenn Sie keinen Namen angeben, wird der Name der Arbeitsmappe verwendet.  
  
4.  Klicken Sie unter **Speicherort**auf **Durchsuchen**, und wählen Sie anschließend einen Ort zum Speichern der Datenbank aus.  
  
5.  Lassen Sie unter **Optionen**das Kontrollkästchen **Sicherheitsinformationen einschließen** aktiviert. Diese Einstellung gilt nicht beim Wiederherstellen von Daten aus einer [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Arbeitsmappe.  
  
## <a name="see-also"></a>Siehe auch  
 [Tabellenmodell-Datenbanken](../../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)   
 [Importieren aus PowerPivot](../../analysis-services/tabular-models/import-from-power-pivot-ssas-tabular.md)  
  
  
