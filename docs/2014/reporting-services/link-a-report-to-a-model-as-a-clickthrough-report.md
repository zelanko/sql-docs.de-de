---
title: Verknüpfen eines Berichts mit einem Modell als Bericht mit durchklicken | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- customizing clickthrough reports
- clickthrough reports, customizing
- clickthrough reports, templates
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 90b21c6fa21322afe1d9351e73460fce1a4592f8
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "59944156"
---
# <a name="link-a-report-to-a-model-as-a-clickthrough-report"></a>Verknüpfen eines Berichts mit einem Modell als Bericht mit Durchklicken
  Statt die Standardvorlagen für Berichte mit Durchklicken zu verwenden, können Sie einen Bericht im Berichts-Generator erstellen und dann mit einer bestimmten Entität im Berichtsmodell verknüpfen. Wenn ein Benutzer beim Anzeigen des Berichts auf die interaktiven Daten im Hauptbericht klickt, wird der Bericht als Bericht mit Durchklicken angezeigt. Um einen Bericht mit einer Entität zu verknüpfen, verwenden Sie den [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] -Berichts-Manager.  
  
> [!IMPORTANT]  
>  Der Bericht muss mit der Entität verknüpft werden, die im Bericht als primäre oder Basisentität verwendet wird.  
  
### <a name="to-start-report-manager-from-a-browser"></a>So starten Sie den Berichts-Manager aus einem Browser  
  
1.  Öffnen Sie [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 oder höher.  
  
2.  Geben Sie die URL des Berichts-Managers in die Adressleiste des Webbrowsers ein. Standardmäßig lautet die URL http://\<*ComputerName*> / reports.  
  
### <a name="to-create-a-customized-clickthrough-report"></a>So erstellen Sie einen benutzerdefinierten Bericht mit Durchklicken  
  
1.  Navigieren Sie zum Berichtsmodell, dem Sie den benutzerdefinierten Bericht mit Durchklicken hinzufügen möchten.  
  
2.  Doppelklicken Sie auf das Berichtsmodell.  
  
3.  Klicken Sie auf **Durchklicken**.  
  
4.  Wählen Sie die Entität aus, an die Sie den benutzerdefinierten Bericht mit Durchklicken anhängen möchten.  
  
    > [!NOTE]  
    >  Diese Entität muss mit der Basisentität des benutzerdefinierten Berichts mit Durchklicken identisch sein.  
  
5.  Um den benutzerdefinierten Bericht anzuzeigen, wenn auf eine Instanz der ausgewählten Entität geklickt wird, klicken Sie auf die Schaltfläche **Durchsuchen** des Berichts mit einer einzigen Instanz.  
  
     -oder-  
  
     Um den benutzerdefinierten Bericht anzuzeigen, wenn auf eine Multiinstanz der ausgewählten Entität geklickt wird, klicken Sie auf die Schaltfläche **Durchsuchen** des Multiinstanzberichts.  
  
6.  Wählen Sie den Bericht aus, und klicken Sie dann auf **OK**.  
  
7.  Klicken Sie auf **Anwenden**.  
  
## <a name="see-also"></a>Siehe auch  
 [Berichte mit durchklicken &#40;SSRS&#41;](reports/clickthrough-reports-ssrs.md)  
  
  
