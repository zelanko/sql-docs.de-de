---
title: Erstellen ein Clustering-Modells (mittleres Datamining-Lernprogramm) für verwandte Sequenzen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1fb4f5bc-1756-45ca-9cd7-411a8c5992a9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 71db7ba5246e151bbca8a52972a2ba835b80ddb6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "62855876"
---
# <a name="creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial"></a>Erstellen eines Clustermodells für verwandte Sequenzen (Data Mining-Lernprogramm für Fortgeschrittene)
  Bei der Untersuchung des Sequenzclustermodells haben Sie gelernt, dass Attribute wie "Region" oder "Einkommen" starke Auswirkungen auf die Modelle haben. Aus diesem Grund erstellen Sie nun ein Clustermodell für verwandte Sequenzen und entfernen die Attribute für demografische Kundendaten, um ein besseres Verständnis der Sequenzen zu entwickeln.  
  
 In dieser Aufgabe erstellen Sie eine Kopie des Clustermodells für regionale Sequenzen und entfernen alle Spalten aus dem Modell, die keinen direkten Bezug zu Sequenzen haben.  
  
 Das neue Modell enthält die gleichen Spalten wie das zugrunde liegende Miningmodell. Das Entfernen der Spalten aus der Miningstruktur ist jedoch nicht erforderlich; Sie müssen nur festlegen, dass die Spalten im neuen Miningmodell ignoriert werden.  
  
### <a name="to-make-a-copy-of-the-sequence-clustering-model"></a>So erstellen Sie eine Kopie des Sequenzclustermodells  
  
1.  Klicken Sie in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]im Data Mining-Designer auf die Registerkarte **Miningmodelle** .  
  
2.  Klicken Sie mit der rechten Maustaste auf das Modell, das Sie kopieren möchten, und wählen Sie **Neues Miningmodell**aus.  
  
3.  In der **Neues Miningmodell** Dialogfeld Geben Sie einen Modellnamen ein, und wählen Sie die Microsoft `Sequence Clustering`.  
  
     Geben Sie für dieses Tutorial den Namen `Sequence Clustering`.  
  
4.  Klicken Sie auf **OK**.  
  
### <a name="to-remove-columns-from-the-mining-model"></a>So entfernen Sie Spalten aus dem Miningmodell  
  
1.  In der **Miningmodell** Registerkarte in der Spalte für das neue Modell mit dem Namen Sequence Clustering, klicken Sie auf die Zeile für die **Einkommensgruppe** Attribut, und wählen Sie **ignorieren**.  
  
2.  Wiederholen Sie diesen Schritt für das Attribut **Region**.  
  
3.  Klicken Sie auf das Pluszeichen neben dem Tabellennamen **v Assoc Seq Line Items**, um die Tabelle zu erweitern und die Spalten der geschachtelten Tabelle anzuzeigen.  
  
     Das neue Modell sollte nur aus folgenden Spalten bestehen:  
  
     **Reihenfolge NumberKey**  
  
     **Anzahl ein Schlüssel für direktverbindungen**  
  
     **Modell Vorhersagen**  
  
### <a name="to-process-the-new-sequence-clustering-model"></a>So verarbeiten Sie das neue Sequenzclustermodell  
  
1.  In der **Miningmodell** Registerkarte der rechten Maustaste auf das neue Modell `Sequence Clustering`, und wählen Sie **Prozessmodell**.  
  
     Da das neue vereinfachte Miningmodell auf einer Struktur basiert, die bereits verarbeitet wurde, muss diese nicht erneut verarbeitet werden. Eine Verarbeitung des neuen Miningmodells ist ausreichend.  
  
2.  Klicken Sie auf **Ja** , um das aktualisierte Data Mining-Projekt auf dem Server bereitzustellen.  
  
3.  Klicken Sie im Dialogfeld **Miningmodell verarbeiten** auf **Ausführen**.  
  
4.  Klicken Sie auf **Schließen** , um das Dialogfeld **Verarbeitungsstatus** zu schließen, und klicken Sie im Dialogfeld **Miningmodell verarbeiten** erneut auf **Schließen** .  
  
## <a name="next-task-in-lesson"></a>Nächste Aufgabe in dieser Lektion  
 [Erstellen von Vorhersagen für ein Sequenzclustermodell &#40;Datamining-Lernprogramm für fortgeschrittene&#41;](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Anforderungen und Überlegungen zur Verarbeitung &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
