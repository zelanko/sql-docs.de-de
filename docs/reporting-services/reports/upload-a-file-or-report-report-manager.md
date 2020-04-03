---
title: Hochladen einer Datei oder eines Berichts auf den Berichtsserver | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie Berichte und andere Dateien einem Berichtsserver hinzufügen, ohne diese Elemente in einer Clientanwendung veröffentlichen zu müssen.
ms.date: 05/24/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- publishing reports [Reporting Services], uploading files
- reports [Reporting Services], publishing
- uploading reports [Reporting Services]
- uploading files [Reporting Services]
- files [Reporting Services], uploading
ms.assetid: 79027e11-f4ba-4bfd-bd8c-d334e3da02a1
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 6d5d70a2147ea5cb9846ed37ea8963cc8c3f98e3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/29/2020
ms.locfileid: "79510051"
---
# <a name="upload-a-file-or-report-in-the-report-server"></a>Hochladen einer Datei oder eines Berichts auf den Berichtsserver
Das Webportal des Berichtsservers umfasst ein Uploadfeature, sodass Sie Berichte und andere Dateien zu einem Berichtsserver hinzufügen können, ohne diese Elemente von einer Clientanwendung zu veröffentlichen. Dateien, die Sie über das Dateisystem hochladen, werden als Elemente auf dem Berichtsserver gespeichert. Die Speicherung erfolgt je nach Dateityp:  
  
-   RDL-Dateien werden als paginierte Berichte gespeichert.  
  
-   Alle anderen Dateien, einschließlich freigegebener Datenquellendateien (RDS), werden als Ressourcen hochgeladen. Ressourcen werden nicht von einem Berichtsserver verarbeitet, können aber im Webportal angezeigt werden, wenn der Berichtsserver den MIME-Typ der Datei unterstützt.  
  
### <a name="to-upload-a-file-or-report"></a>So laden Sie eine Datei oder einen Bericht hoch  
  
1.  Klicken Sie im Webportal auf **Upload**.  
  
4.  Navigieren Sie zu der Datei, die Sie hochladen möchten. Sie können eine Berichtsdefinitionsdatei, ein Bild, ein Dokument oder jede andere Datei hochladen, die Sie auf einem Berichtsserver zur Verfügung stellen möchten.  
  
5.  Geben Sie einen Namen für das neue Element ein. Der Name eines Elements kann Leerzeichen enthalten, jedoch nicht die folgenden reservierten Zeichen: \; \? \: \@ \& \= \+ \, \$ \/ \* \< \> \|.  
  
6.  Wenn Sie ein vorhandenes Element durch ein neues ersetzen möchten, wählen Sie **Vorhandenes Element überschreiben**aus.  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Weitere Informationen   
[Erstellen, Ändern und Löschen von freigegebenen Datenquellen](../../reporting-services/report-data/create-modify-and-delete-shared-data-sources-ssrs.md)
[Hochladen von Dateien in einen Ordner](../../reporting-services/report-server/upload-files-to-a-folder.md)  
  
  
