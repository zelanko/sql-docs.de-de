---
title: Hochladen einer Datei oder eines Berichts (Berichts-Manager) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 3c60005e798e2a942970d9fb7a8746256308c795
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/11/2019
ms.locfileid: "56023671"
---
# <a name="upload-a-file-or-report-report-manager"></a>Hochladen einer Datei oder eines Berichts (Berichts-Manager)
  Der Berichts-Manager umfasst eine Uploadfunktion, sodass Sie Berichte, Modelle und andere Dateien zu einem Berichtsserver hinzufügen können, ohne diese Elemente von einer Clientanwendung zu veröffentlichen. Dateien, die Sie über das Dateisystem hochladen, werden als Elemente auf dem Berichtsserver gespeichert. Die Speicherung erfolgt je nach Dateityp:  
  
-   RDL-Dateien werden als Berichte gespeichert.  
  
-   SMDL-Dateien werden als Berichtsmodelle gespeichert.  
  
-   Alle anderen Dateien, einschließlich freigegebener Datenquellendateien (RDS), werden als Ressourcen hochgeladen. Ressourcen werden nicht von einem Berichtsserver verarbeitet, können aber im Berichts-Manager angezeigt werden, wenn der Berichtsserver den MIME-Typ der Datei unterstützt.  
  
### <a name="to-upload-a-file-or-report"></a>So laden Sie eine Datei oder einen Bericht hoch  
  
1.  Starten Sie den [Berichts-Manager &#40;einheitlicher SSRS-Modus&#41;](../report-manager-ssrs-native-mode.md).  
  
2.  Navigieren Sie im Berichts-Manager zur Seite **Inhalt** . Navigieren Sie zum Ordner, zu dem Sie ein Element hinzufügen möchten.  
  
3.  Klicken Sie auf **Datei hochladen**.  
  
4.  Klicken Sie auf **Durchsuchen** , um eine Datei zum Hochladen auszuwählen. Sie können eine Berichtsdefinitionsdatei, ein Bild, ein Dokument oder jede andere Datei hochladen, die Sie auf einem Berichtsserver zur Verfügung stellen möchten.  
  
5.  Geben Sie einen Namen für das neue Element ein. Ein Element darf Leerzeichen enthalten, jedoch nicht die folgenden reservierten Zeichen: ; ? : \@ & = + , $ / * \< > |.  
  
6.  Wenn Sie ein vorhandenes Element durch ein neues ersetzen möchten, wählen Sie **Vorhandenes Element überschreiben**aus.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen, Löschen oder Ändern einer freigegebenen Datenquelle &#40;Berichts-Manager&#41;](../create-delete-or-modify-a-shared-data-source-report-manager.md)   
 [Inhalt &#40;Seite, Berichts-Manager&#41;](../contents-page-report-manager.md)   
 [Datei hochladen (Seite, Berichts-Manager)](../upload-file-page-report-manager.md)   
 [Hochladen von Dateien in einen Ordner](../report-server/upload-files-to-a-folder.md)  
  
  
