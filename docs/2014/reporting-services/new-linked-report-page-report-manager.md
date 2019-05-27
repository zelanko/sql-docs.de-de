---
title: Seite für neuen verknüpften Bericht (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: fefb46e8-6901-4d50-a3f8-7c49ad72e7b1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b6aab8fc0c8e083181779c13654b0d7d42531e50
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66108168"
---
# <a name="new-linked-report-page-report-manager"></a>Neuer verknüpfter Bericht (Seite) (Berichts-Manager)
  Auf der Seite Neuer verknüpfter Bericht können Sie einen verknüpften Bericht erstellen. Als verknüpfter Bericht wird ein Bericht mit eigenen Einstellungen und Eigenschaften bezeichnet, der jedoch mit der Berichtsdefinition eines anderen Berichts verknüpft ist. Verwenden Sie verknüpfte Berichte, wenn Sie über einen Basisbericht verfügen, der für spezifische Gruppen oder Benutzer unterschiedlich angezeigt werden soll. Dies kann z. B. ein regionaler Bericht sein, der auf der Grundlage einer Regionalkennzahl, die Sie als Parameter angeben, unterschiedliche Daten zurückgibt. Ein verknüpfter Bericht wird in der Regel aus einem parametrisierten Bericht erstellt, den Sie variieren und für den Sie anschließend unterschiedliche Parameterwerte für jede einzelne Berichtsinstanz speichern. Sie können aus jedem beliebigen Bericht, auf den Sie zugreifen können, einen verknüpften Bericht erstellen.  
  
 Ein verknüpfter Bericht kann über einen eigenen Namen und Speicherort, eine eigene Beschreibung sowie eigene Parametereigenschaften, Berichtsausführungseigenschaften, Berichtsverlaufseigenschaften, Berechtigungen und Abonnements verfügen. Ein verknüpfter Bericht muss jedoch die Datenquelleneigenschaften und das Layout des Basisberichts verwenden, der die Berichtsdefinition bereitstellt.  
  
## <a name="navigation"></a>Navigation  
 Verwenden Sie folgende Verfahren, um zu dieser Position in der Benutzeroberfläche zu navigieren.  
  
###### <a name="to-open-the-new-linked-report-page-from-the-contents-page"></a>So öffnen Sie die Seite "Neuer verknüpfter Bericht" über die Seite "Inhalt"  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie einen Bericht, für den Sie einen verknüpften Bericht erstellen möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verknüpften Bericht erstellen**.  
  
###### <a name="to-open-the-new-linked-report-page-from-the-general-properties-page-of-a-report"></a>So öffnen Sie die Seite 'Neuer verknüpfter Bericht' von der Seite 'Allgemeine Eigenschaften' eines Berichts  
  
1.  Öffnen Sie den Berichts-Manager, und suchen Sie einen Bericht, für den Sie einen verknüpften Bericht erstellen möchten.  
  
2.  Zeigen Sie auf den Bericht, und klicken Sie auf den Dropdownpfeil.  
  
3.  Klicken Sie im Dropdownmenü auf **Verwalten**. Dadurch wird die Seite Allgemeine Eigenschaften für den Bericht geöffnet.  
  
4.  Klicken Sie auf der Elementsymbolleiste auf **Verknüpften Bericht erstellen**.  
  
## <a name="options"></a>Optionen  
 **Name**  
 Geben Sie den Namen des verknüpften Berichts an. Der Name muss mindestens ein alphanumerisches Zeichen enthalten. Er kann auch Leerzeichen und bestimmte Sonderzeichen enthalten. Folgende Zeichen können nicht beim Angeben eines Namens verwendet werden: ; ? : \@ & = +, $ / * \< > | "oder / beim Angeben eines Namens.  
  
 **Beschreibung**  
 Geben Sie eine Beschreibung des Berichtsinhalts ein. Diese Beschreibung wird für Benutzer, die über die Berechtigung zum Zugreifen auf den Bericht verfügen, auf der Seite Inhalt angezeigt.  
  
 **Speicherort**  
 Geben Sie den Ordnerpfad des Berichts an. Standardmäßig werden verknüpfte Berichte als gleichgeordnete Elemente des Basisberichts erstellt. Klicken Sie auf **Speicherort ändern** , um den verknüpften Bericht in einem anderen Ordner zu speichern.  
  
 **OK**  
 Klicken Sie auf **OK** , um die Änderungen zu speichern und zur Eigenschaftenseite Allgemein des Basisberichts zurückzukehren.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen eines verknüpften Berichts](reports/create-a-linked-report.md)   
 [Allgemeine Eigenschaften (Seite) (Berichte, Berichts-Manager)](../../2014/reporting-services/general-properties-page-reports-report-manager.md)   
 [Berichts-Manager (F1-Hilfe)](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
