---
title: Erstellen eines verknüpften Berichts | Microsoft-Dokumentation
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
ms.openlocfilehash: 77590da41aa09f66d7549a0d7ff615cdb3f63af3
ms.sourcegitcommit: 561cee96844b82ade6cf543a228028ad5c310768
ms.translationtype: MTE75
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2019
ms.locfileid: "66506645"
---
# <a name="create-a-linked-report"></a>Erstellen eines verknüpften Berichts
  Ein verknüpfter Bericht ist ein Berichtsserverelement, das einen Zugriffspunkt auf einen vorhandenen Bericht bereitstellt. Grundsätzlich ist er mit einer Programmverknüpfung vergleichbar, die Sie verwenden, um ein Programm auszuführen oder eine Datei zu öffnen.  
  
 Ein verknüpfter Bericht wird von einem vorhandenen Bericht abgeleitet und behält die Berichtsdefinition des Originals bei. Ein verknüpfter Bericht erbt immer das Berichtslayout und die Datenquelleneigenschaften des ursprünglichen Berichts. Alle anderen Eigenschaften und Einstellungen können sich von denen des ursprünglichen Berichts unterscheiden, einschließlich Sicherheit, Parameter, Speicherort, Abonnements und Zeitpläne.  
  
 Sie können einen verknüpften Bericht erstellen, wenn Sie zusätzliche Versionen eines vorhandenen Berichts erstellen möchten. Beispielsweise könnten Sie einen einzelnen regionalen Vertriebsbericht verwenden, um regionsspezifische Berichte für alle Vertriebsgebiete zu erstellen.  
  
 Obwohl verknüpfte Berichte in der Regel auf parametrisierten Berichten basieren, ist kein parametrisierter Bericht erforderlich. Sie können immer dann verknüpfte Berichte erstellen, wenn Sie einen vorhandenen Bericht mit anderen Einstellungen bereitstellen möchten.  
  
## <a name="to-create-a-linked-report"></a>So erstellen Sie einen verknüpften Bericht  
  
1. Wechseln Sie in der Webportal zu den gewünschten Bericht, mit der rechten Maustaste darauf und wählen Sie **verwalten** aus der Dropdown-Menü.

2. Auf der **verwalten <reportname>**  Seite **verknüpften Bericht erstellen**.  
  
3. Geben Sie einen Namen für den neuen verknüpften Bericht ein. Geben Sie optional eine Beschreibung ein.  
  
4. Um einen anderen Ordner für den Bericht auszuwählen, wählen Sie die Schaltfläche mit den Auslassungspunkten (...) rechts neben ***Speicherort***.  Navigieren Sie zu den neuen Ordner für den Bericht, und wählen Sie **wählen**. Wenn Sie einen anderen Ordner nicht auswählen, wird der verknüpfte Bericht im aktuellen Ordner erstellt.  
  
5. Wählen Sie **Erstellen**aus. Der verknüpfte Bericht wird erstellt.  

6. Klicken Sie unter **erweitert**, wählen Sie einen anderen **berichtstimeout** -Wert, wenn gewünscht, und wählen Sie **übernehmen** zum Speichern der Änderungen.
  
     Das Symbol für einen verknüpften Bericht unterscheidet sich von anderen Elementen, die von einem Berichtsserver verwaltet werden. Das folgende Symbol steht für einen verknüpften Bericht:  
  
     ![Symbol verknüpfte Berichte](../../reporting-services/report-server/media/hlp-16linked.gif "Linked report icon")  
  
## <a name="see-also"></a>Siehe auch  
 [Öffnen und Schließen eines Berichts &#40;-Webportal&#41;](../../reporting-services/reports/open-and-close-a-report-report-manager.md)  
 [Konzepte von Reporting Services (SSRS)](../../reporting-services/reporting-services-concepts-ssrs.md)  
 [Das Webportal eines Berichtsservers (einheitlicher SSRS-Modus)](../../reporting-services/web-portal-ssrs-native-mode.md)
  
