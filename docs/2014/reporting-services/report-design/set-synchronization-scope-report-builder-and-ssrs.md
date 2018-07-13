---
title: Festlegen des Synchronisierungsbereichs (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6f4a11e6-6151-47be-a43f-e3dbf6c0e737
caps.latest.revision: 6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 73751e253c70964419d0691525a920f63e125637
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37274166"
---
# <a name="set-synchronization-scope-report-builder-and-ssrs"></a>Festlegen des Synchronisierungsbereichs (Berichts-Generator und SSRS)
  Indikatoren übermitteln Datenwerte, indem sie Indikatorwerte innerhalb eines angegebenen Bereichs synchronisieren. Standardmäßig ist der Bereich der übergeordnete Container des Indikators, z. B. die Tabelle oder die Matrix mit dem Indikator. Sie können die Synchronisierung des Indikators abhängig vom Layout des Berichts ändern. Wenn ein Datenbereich wie eine Tabelle z. B. über eine Zeilengruppe verfügt, können Sie die Gruppe als Indikatorbereich angeben. Der Indikator kann die Synchronisierung auch überspringen.  
  
 Optionen wie Maßeinheiten können mithilfe von Ausdrücken festgelegt werden. Weitere Informationen finden Sie unter [Ausdrücke &#40;Berichts-Generator und SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
 Allgemeine Informationen zum Verständnis und zum Festlegen von Bereichen in Berichten finden Sie unter [Ausdrucksbereich für Gesamtwerte, Aggregate und integrierte Sammlungen (Berichts-Generator und SSRS)](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-synchronization-scope-of-an-indicator"></a>So ändern Sie den Synchronisierungsbereich eines Indikators  
  
1.  Klicken Sie mit der rechten Maustaste auf den Indikator, der geändert werden soll, und klicken Sie auf **Indikatoreigenschaften**.  
  
2.  Klicken Sie im linken Bereich auf **Wert und Status** .  
  
3.  Klicken Sie in der Liste **Synchronisierungsbereich** auf den Bereich, den Sie übernehmen möchten.  
  
     Die Option **(Keine)** ist immer verfügbar. Mit ihr wird der Synchronisierungsbereich aus dem Indikator entfernt. Andere Optionen hängen vom Layout des Berichts ab.  
  
     Klicken Sie optional auf die Schaltfläche **Ausdruck** (*fx*), um einen Ausdruck zu bearbeiten, der den Bereich festlegt.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Indikatoren &#40;Berichts-Generator und SSRS&#41;](indicators-report-builder-and-ssrs.md)  
  
  
