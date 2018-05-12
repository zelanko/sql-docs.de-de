---
title: Anzeigen oder Ändern von Modellierungsflags (Datamining) | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e587be4fe975ee35752e668f9a5d49e0afdf4488
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
---
# <a name="view-or-change-modeling-flags-data-mining"></a>Anzeigen oder Ändern von Modellierungsflags (Data Mining)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Modellierungsflags sind Eigenschaften, die Sie für eine Miningstrukturspalte oder für Miningmodellspalten festlegen, um zu steuern, wie der Algorithmus die Daten während der Analyse verarbeitet.  
  
 Im Data Mining-Designer können Sie die Modellierungsflags, die einer Miningstruktur oder Miningspalte zugeordnet sind, betrachten und ändern, indem Sie die Eigenschaften der Struktur oder des Modells anzeigen. Sie können Modellierungsflags auch mit DMX, AMO oder XMLA festlegen.  
  
 Diese Prozedur beschreibt, wie die Modellierungsflags im Designer geändert werden.  
  
### <a name="view-or-change-the-modeling-flag-for-a-structure-column-or-model-column"></a>Anzeigen oder Ändern des Modellierungsflags für eine Strukturspalte oder eine Modellspalte  
  
1.  Öffnen Sie in SQL Server Design Studio den Projektmappen-Explorer, und doppelklicken Sie dann auf die Miningstruktur.  
  
2.  Um das NOT NULL-Modellierungsflag festzulegen, klicken Sie auf die Registerkarte **Miningstruktur** . Um das REGRESSOR-Flag oder das MODEL_EXISTENCE_ONLY-Flag festzulegen, klicken Sie auf die Registerkarte **Miningmodell** .  
  
3.  Klicken Sie mit der rechten Maustaste auf die Spalte, die Sie anzeigen oder ändern möchten, und wählen Sie **Eigenschaften**aus.  
  
4.  Um ein neues Modellierungsflag hinzuzufügen, klicken Sie auf das Textfeld neben der Eigenschaft **ModelingFlags** , und aktivieren Sie das bzw. die Kontrollkästchen für die Modellierungsflags, die Sie verwenden möchten.  
  
     Modellierungsflags werden nur angezeigt, wenn sie für den Datentyp der Spalte geeignet sind.  
  
    > [!NOTE]  
    >  Nachdem ein Modellierungsflag geändert wurde, muss das Modell erneut verarbeitet werden.  
  
### <a name="get-the-modeling-flags-used-in-the-model"></a>Abrufen der im Modell verwendeten Modellierungsflags  
  
-   Öffnen Sie in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ein DMX-Abfragefenster, und geben Sie eine Anweisung ähnlich der folgenden ein:  
  
    ```  
    SELECT COLUMN_NAME, CONTENT_TYPE, MODELING_FLAG  
    FROM $system.DMSCHEMA_MINING_COLUMNS  
    WHERE MODEL_NAME = 'Forecasting'  
  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Miningmodelltasks und Anweisungen Mining](../../analysis-services/data-mining/mining-model-tasks-and-how-tos.md)   
 [Modellieren von Ablaufverfolgungsflags & #40; Datamining & #41;](../../analysis-services/data-mining/modeling-flags-data-mining.md)  
  
  
