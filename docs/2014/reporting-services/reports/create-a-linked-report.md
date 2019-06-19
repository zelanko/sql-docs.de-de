---
title: Erstellen eines verknüpften Berichts | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0df6a3bdb6f542b02b62ccf4aa6614da290551f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66102696"
---
# <a name="create-a-linked-report"></a>Erstellen eines verknüpften Berichts
  Ein verknüpfter Bericht ist ein Berichtsserverelement, das einen Zugriffspunkt auf einen vorhandenen Bericht bereitstellt. Grundsätzlich ist er mit einer Programmverknüpfung vergleichbar, die Sie verwenden, um ein Programm auszuführen oder eine Datei zu öffnen.  
  
 Ein verknüpfter Bericht wird von einem vorhandenen Bericht abgeleitet und behält die Berichtsdefinition des Originals bei. Ein verknüpfter Bericht erbt immer das Berichtslayout und die Datenquelleneigenschaften des ursprünglichen Berichts. Alle anderen Eigenschaften und Einstellungen können sich von denen des ursprünglichen Berichts unterscheiden, einschließlich Sicherheit, Parameter, Speicherort, Abonnements und Zeitpläne.  
  
 Sie können einen verknüpften Bericht erstellen, wenn Sie zusätzliche Versionen eines vorhandenen Berichts erstellen möchten. Beispielsweise könnten Sie einen einzelnen regionalen Vertriebsbericht verwenden, um regionsspezifische Berichte für alle Vertriebsgebiete zu erstellen.  
  
 Obwohl verknüpfte Berichte in der Regel auf parametrisierten Berichten basieren, ist kein parametrisierter Bericht erforderlich. Sie können immer dann verknüpfte Berichte erstellen, wenn Sie einen vorhandenen Bericht mit anderen Einstellungen bereitstellen möchten.  
  
### <a name="to-create-a-linked-report"></a>So erstellen Sie einen verknüpften Bericht  
  
1.  Navigieren Sie im Berichts-Manager zum Ordner, der den Bericht enthält, zu dem Sie einen Link erstellen möchten, und öffnen Sie dann das Menü Optionen und klicken Sie auf **Verknüpften Bericht erstellen**.  
  
2.  Geben Sie einen Namen für den neuen verknüpften Bericht ein. Geben Sie optional eine Beschreibung ein.  
  
3.  Um einen anderen Ordner für den Bericht auszuwählen, klicken Sie auf **Speicherort ändern**. Klicken Sie auf den Ordner, den Sie verwenden möchten, oder geben Sie den Ordnernamen im Feld **Speicherort** ein. [!INCLUDE[clickOK](../../../includes/clickok-md.md)] Wenn Sie keinen anderen Ordner auswählen, wird der verknüpfte Bericht im aktuellen Ordner (in dem der Bericht, auf dem er basiert, gespeichert ist) erstellt.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)] Der verknüpfte Bericht wird geöffnet.  
  
     Das Symbol für einen verknüpften Bericht unterscheidet sich von anderen Elementen, die von einem Berichtsserver verwaltet werden. Das folgende Symbol steht für einen verknüpften Bericht:  
  
     ![Symbol verknüpfte Berichte](../media/hlp-16linked.gif "Linked report icon")  
  
## <a name="see-also"></a>Siehe auch  
 [Öffnen und Schließen eines Berichts &#40;Berichts-Manager&#41;](../reports/open-and-close-a-report-report-manager.md)   
 [Neuer verknüpfter Bericht (Seite) &#40;Berichts-Manager&#41;](../new-linked-report-page-report-manager.md)   
 [Speicherort für Elemente auswählen (Seite) (Berichts-Manager)](../choose-item-location-page-report-manager.md)   
 [Allgemeine Eigenschaften (Seite) (Berichte, Berichts-Manager)](../general-properties-page-reports-report-manager.md)   
 [Konzepte von Reporting Services (SSRS)](../reporting-services-concepts-ssrs.md)   
 [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md)  
  
  
