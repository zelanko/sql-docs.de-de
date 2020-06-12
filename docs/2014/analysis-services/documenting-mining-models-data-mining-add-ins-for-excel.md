---
title: Dokumentieren von Mining Modellen (Data Mining-Add-Ins für Excel) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- documenting models
- mining structures, managing
- mining models, managing
- model properties
ms.assetid: 0a663e11-e40c-4708-ad18-fabb6c976fa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 92ed5c43fa2b7484485b915d42946121487386d9
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528486"
---
# <a name="documenting-mining-models-data-mining-add-ins-for-excel"></a>Dokumentieren von Miningmodellen (Data Mining-Add-Ins für Excel)
  ![Dokumentmodell (Schaltfläche auf Data Mining-Menüband)](media/dmc-docmodel.gif "Dokumentmodell (Schaltfläche auf Data Mining-Menüband)")  
  
 Der **Dokument Modell** -Assistent erstellt einen Bericht, der nützliche Informationen zu den von Ihnen erstellten Mining Modellen bereitstellt. Durch Dokumentieren der erstellten Modelle können Sie die Datenquelle zurückverfolgen, die zum Generieren eines Modells verwendet wurde. Zudem können Sie so zusätzliche Informationen zur Verarbeitung des Modells abrufen und Parameteränderungen nachverfolgen, die die Ergebnisse des Modells beeinflussen.  
  
## <a name="using-the-document-model-wizard"></a>Verwenden des Dokumentmodell-Assistenten  
  
1.  Klicken Sie auf die Registerkarte **Data Mining** .  
  
2.  Klicken Sie in der Gruppe **Modell Verwendung** auf **Dokument Modell**.  
  
3.  Wählen Sie im Dialogfeld **Modell auswählen** das Modell aus, für das der Bericht angezeigt werden soll, und klicken Sie dann auf **weiter**. Sie müssen den **Dokument Modell** -Assistenten für jedes Modell, das Sie dokumentieren möchten, separat ausführen.  
  
4.  Wählen Sie im Dialogfeld **Dokumentations Details auswählen** eine der beiden folgenden Optionen aus: **umfassende Informationen** oder **Zusammenfassungs Informationen**.  
  
5.  Klicken Sie auf **Fertig stellen**.  
  
6.  Der Assistent erstellt automatisch ein neues Arbeitsblatt, das den angegebenen Bericht mit der Bezeichnung **Modelldokumentation**enthält.  
  
## <a name="understanding-the-report"></a>Grundlegendes zum Bericht  
 Wenn Sie einen Bericht erstellen, in dem ein Data Mining-Modell dokumentiert wird, können Sie eine Zusammenfassung erstellen, die den Namen und eine Beschreibung des Modells enthält. Sie können aber auch einen vollständigen Bericht erstellen, der Details zur zugrunde liegenden Struktur und ausführliche Informationen zum Miningmodell enthält.  
  
 Abhängig vom Algorithmus, der zum Erstellen des Modells verwendet wurde, werden unterschiedliche Informationen angegeben. In einem Zuordnungsmodell sind beispielsweise die Anzahl von Itemsets und die generierten Regeln von Bedeutung. Bei einem Clustermodell ist dagegen die Anzahl von Clustern interessanter.  
  
 In der folgenden Tabelle werden die Optionen und die Informationen aufgeführt, die im Bericht für jede Option angegeben werden.  
  
> [!NOTE]  
>  Die Spalten im Bericht werden standardmäßig auf eine spezielle Größe festgelegt. Wenn also Spaltennamen oder -werte sehr lang sind, werden Sie in Excel möglicherweise nicht oder als ### angezeigt. Sie können Sie die Größe der Zeile ändern, um die Werte sichtbar zu machen. Wenn die Zelle ausgewählt ist, können Sie darauf klicken und die Doppelpfeile zum rechten Ende der Bearbeitungsleiste ziehen, um den vollständigen Wert oder die ganze Zeichenfolge anzuzeigen.  
  
### <a name="summary-report"></a>Zusammenfassungsbericht  
  
||||  
|-|-|-|  
|**Metadaten**|Modellname<br /><br /> Modellbeschreibung<br /><br /> Algorithmusname<br /><br /> Datum der letzten Verarbeitung||  
|**Modellergebnisse**|Zuordnung|Anzahl von Itemsets<br /><br /> Anzahl von Regeln|  
||Clustering|Anzahl von Clustern<br /><br /> Unterstützung für jeden Cluster|  
||Entscheidungsstruktur|Anzahl von Strukturen<br /><br /> Anzahl von Knoten in jeder Struktur|  
||Lineare Regression|Anzahl von Strukturen (immer 1)<br /><br /> Anzahl von Knoten (immer 1)|  
||Naive Bayes|Wichtige Attribute|  
||Neuronales Netzwerk|Anzahl von Eingabeknoten<br /><br /> Anzahl von Ausgabeknoten<br /><br /> Anzahl ausgeblendeter Knoten|  
||Sequenzclustering|Anzahl der Cluster|  
  
### <a name="complete-report"></a>Vollständiger Bericht  
 Der vollständige Bericht enthält sämtliche Informationen des Zusammenfassungsberichts und zusätzlich Angaben zu den im Modell verwendeten Datenspalten und die Ergebnisse der Analyse:  
  
||||  
|-|-|-|  
|**Metadaten**|Modellmetadaten|Algorithmusparameter und -werte|  
||Spaltenmetadaten|Spaltenname<br /><br /> Verwendung<br /><br /> Datentyp<br /><br /> Inhaltstyp<br /><br /> Werte (Liste diskreter Werte oder Wertebereich)|  
|**Modell Statistiken**|Kontinuierliche Spalten|Mittelwert<br /><br /> Minimalwert<br /><br /> Maximalwert<br /><br /> Wurzel des mittleren quadratischen Fehlers<br /><br /> Mittlerer absoluter Fehler<br /><br /> Logarithmisches Ergebnis<br /><br /> Regressionsformel (nur für lineare Regressionsmodelle)|  
||Diskrete Spalten|Anzahl von Übergaben<br /><br /> Anzahl der Fehler<br /><br /> Logarithmisches Ergebnis<br /><br /> Lift|  
  
> [!NOTE]  
>  Sie können jeden Modelltyp dokumentieren, der von SQL Server Analysis Services unterstützt wird. Deshalb sind in der Tabelle Modelltypen aufgeführt, die mit den Tabellenanalysetools oder den Assistenten im Data Mining-Client nicht erstellt werden können. Allerdings können Sie alle Modelltypen mit dem **erweiterten Data Mining-Abfrage-Editor**erstellen. Weitere Informationen finden Sie unter [Abfrage &#40;SQL Server Data Mining-Add-ins&#41;](query-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Bereitstellen und Skalieren von Mining Modellen &#40;Data Mining-Add-Ins für Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
