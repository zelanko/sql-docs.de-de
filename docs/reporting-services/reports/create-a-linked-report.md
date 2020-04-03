---
title: Erstellen eines verknüpften Berichts | Microsoft-Dokumentation
description: Erfahren Sie, wie Sie einen verknüpften Bericht erstellen, damit Sie zusätzliche Versionen eines vorhandenen Berichts erstellen können.
ms.date: 05/30/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- linked reports [Reporting Services], creating
ms.assetid: 12be8341-cb57-45e8-a421-2bf66b50234d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: cb362f699e8bf87e0f386c3ec726869f67aec934
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "79510161"
---
# <a name="create-a-linked-report"></a>Erstellen eines verknüpften Berichts
  Ein verknüpfter Bericht ist ein Berichtsserverelement, das einen Zugriffspunkt auf einen vorhandenen Bericht bereitstellt. Grundsätzlich ist er mit einer Programmverknüpfung vergleichbar, die Sie verwenden, um ein Programm auszuführen oder eine Datei zu öffnen.  
  
 Ein verknüpfter Bericht wird von einem vorhandenen Bericht abgeleitet und behält die Berichtsdefinition des Originals bei. Ein verknüpfter Bericht erbt immer das Berichtslayout und die Datenquelleneigenschaften des ursprünglichen Berichts. Alle anderen Eigenschaften und Einstellungen können sich von denen des ursprünglichen Berichts unterscheiden, einschließlich Sicherheit, Parameter, Speicherort, Abonnements und Zeitpläne.  
  
 Sie können einen verknüpften Bericht erstellen, wenn Sie zusätzliche Versionen eines vorhandenen Berichts erstellen möchten. Beispielsweise könnten Sie einen einzelnen regionalen Vertriebsbericht verwenden, um regionsspezifische Berichte für alle Vertriebsgebiete zu erstellen.  
  
 Obwohl verknüpfte Berichte in der Regel auf parametrisierten Berichten basieren, ist kein parametrisierter Bericht erforderlich. Sie können immer dann verknüpfte Berichte erstellen, wenn Sie einen vorhandenen Bericht mit anderen Einstellungen bereitstellen möchten.  
  
## <a name="to-create-a-linked-report"></a>So erstellen Sie einen verknüpften Bericht  
  
1. Navigieren Sie im Webportal zum gewünschten Bericht, klicken Sie mit der rechten Maustaste auf diesen, und wählen Sie dann im Dropdownmenü **Verwalten** aus.

2. Klicken Sie auf der Seite **<reportname> verwalten** auf **Verknüpften Bericht erstellen**.  
  
3. Geben Sie einen Namen für den neuen verknüpften Bericht ein. Geben Sie optional eine Beschreibung ein.  
  
4. Klicken Sie rechts neben ***Speicherort*** auf die Schaltfläche mit Auslassungspunkten (...), um einen anderen Ordner für den Bericht auszuwählen.  Navigieren Sie zum neuen Ordner für den Bericht, und klicken Sie auf **Auswählen**. Wenn Sie keinen anderen Ordner auswählen, wird der verknüpfte Bericht im aktuellen Ordner erstellt.  
  
5. Klicken Sie auf **Erstellen**. Der verknüpfte Bericht wird erstellt.  

6. Wählen Sie bei Bedarf unter **Erweitert** einen anderen **Berichtstimeout**-Wert aus, und klicken Sie dann auf **Anwenden**, um die Änderungen zu speichern.
  
     Das Symbol für einen verknüpften Bericht unterscheidet sich von anderen Elementen, die von einem Berichtsserver verwaltet werden. Das folgende Symbol steht für einen verknüpften Bericht:  
  
     ![Symbol für einen verknüpften Bericht](../../reporting-services/report-server/media/hlp-16linked.gif "Symbol für einen verknüpften Bericht")  
  
## <a name="see-also"></a>Weitere Informationen  

 [Konzepte von Reporting Services &#40;SSRS&#41;](../../reporting-services/reporting-services-concepts-ssrs.md)  
 [Das Webportal eines Berichtsservers (einheitlicher SSRS-Modus)](../../reporting-services/web-portal-ssrs-native-mode.md)
  
