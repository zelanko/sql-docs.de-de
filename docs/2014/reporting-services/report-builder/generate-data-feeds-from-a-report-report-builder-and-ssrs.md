---
title: Generieren von Datenfeeds aus einem Bericht (Berichts-Generator und SSRS) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: e68baae2-9f2a-4f13-9179-9ac7f29111c5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ceca9ef914afeab3420bbd35c46c582c112644dc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66107850"
---
# <a name="generate-data-feeds-from-a-report-report-builder-and-ssrs"></a>Generieren von Datenfeeds aus einem Bericht (Berichts-Generator und SSRS)
  Sie können Atom-kompatible Datenfeeds aus Berichten generieren und dann in Anwendungen wie dem [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] -Client verwenden, der in der Lage ist, Datenfeeds zu nutzen.  
  
 Die [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] -Atom-Renderingerweiterung generiert ein Atom-Dienstdokument, in dem die aus einem Bericht verfügbaren Datenfeeds aufgeführt sind. Im Dokument ist mindestens ein Datenfeed für jeden Datenbereich im Bericht enthalten. Abhängig vom Typ des Datenbereichs und den darin angezeigten Daten könnte [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] mehrere Datenfeeds aus einem Datenbereich generieren.  
  
 Ein Atom-Dienstdokument enthält einen eindeutigen Bezeichner für jeden Datenfeed. Sie verwenden den Bezeichner in einer URL, um den Inhalt des Datenfeeds anzuzeigen.  
  
 Weitere Informationen finden Sie unter [Generieren von Datenfeeds aus Berichten &#40;Berichts-Generator und SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md)mit den Daten arbeiten.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-generate-an-atom-service-document"></a>So generieren Sie ein Atom-Dienstdokument  
  
1.  Navigieren Sie auf der Seite **Home** des Berichts-Managers zu dem Bericht, aus dem Sie Datenfeeds generieren möchten.  
  
2.  Klicken Sie auf den Bericht.  
  
     Der Bericht wird ausgeführt.  
  
3.  Klicken Sie auf der Symbolleiste auf das Symbol In Datenfeed exportieren.  
  
     Sie werden in einer Meldung gefragt, ob Sie das Atom-Dokument, das den Datenfeed enthält, speichern oder öffnen möchten.  
  
4.  Klicken Sie auf **Speichern** , um das Dokument im Dateisystem zu speichern, oder auf **Öffnen** , um den Dokumentinhalt vor dem Speichern anzuzeigen. **Das Dokument wird standardmäßig in einem Browser geöffnet.**  
  
5.  Navigieren Sie zum Speicherort, an dem das Dokument gespeichert werden soll.  
  
6.  Ändern Sie optional den Namen des Dokuments.  
  
    > [!NOTE]  
    >  Standardmäßig entspricht der Dokumentname dem Berichtsnamen.  
  
7.  Stellen Sie sicher, dass der Dokumenttyp einer **ATOMSVC-Datei**entspricht, und klicken Sie dann auf **Speichern**.  
  
8.  Öffnen Sie die ATOMSVC-Datei optional in einem Browser bzw. einem Text- oder XML-Editor.  
  
### <a name="to-view-an-atom-compliant-data-feed"></a>So zeigen Sie einen Atom-kompatiblen Datenfeed an  
  
1.  Falls das Atom-Dienstdokument noch nicht geöffnet ist, suchen Sie es und öffnen das Dokument in einem Browser wie Internet Explorer.  
  
2.  Kopieren Sie die URL des Datenfeeds, den Sie anzeigen möchten, aus dem Atom-Dienstdokument in den Browser.  
  
     Die URL hat folgendes Format:  
  
 `http://<server name>/ReportServer?%2f<ReportName>rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=<Identifier>`  
  
1.  Drücken Sie die EINGABETASTE.  
  
     Sie werden in einer Meldung gefragt, ob Sie das Atom-Dokument, das den Datenfeed enthält, speichern oder öffnen möchten.  
  
2.  Klicken Sie auf **Speichern** , um das Dokument im Dateisystem zu speichern, oder auf **Öffnen** , um den Datenfeed vor dem Speichern anzuzeigen.  
  
3.  Navigieren Sie zum Speicherort, an dem das Dokument gespeichert werden soll.  
  
4.  Ändern Sie optional den Namen des Dokuments.  
  
    > [!NOTE]  
    >  Standardmäßig entspricht der Dokumentname dem Berichtsnamen. Wenn das Atom-Dienstdokument mehrere Feeds enthält, verwenden alle standardmäßig den gleichen Namen, und zwar den Berichtsnamen. Um zwischen den Datenfeeds zu unterscheiden, benennen Sie diese mit aussagekräftigen Namen um.  
  
5.  Stellen Sie sicher, dass der Dokumenttyp einer **ATOM-Datei**entspricht, und klicken Sie dann auf **Speichern**.  
  
6.  Öffnen Sie die ATOM-Datei optional in einem Browser bzw. Text-Editor oder XML-Editor.  
  
## <a name="see-also"></a>Siehe auch  
 [Exportieren von Berichten &#40;Berichts-Generator und SSRS&#41;](export-reports-report-builder-and-ssrs.md)  
  
  
