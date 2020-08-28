---
description: Verweis auf die ADO-Bibliotheken in Visual Basic 6 -Anwendungen
title: Verweisen auf die ADO-Bibliotheken in einer Visual Basic 6-Anwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual Basic application[ADO]
- ADO, libraries
ms.assetid: cfd37a82-aad2-41cd-8d13-1566c43d95f0
author: rothja
ms.author: jroth
ms.openlocfilehash: 71ae81dc98d0fffe7463759be0846afccd708f0f
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88978511"
---
# <a name="referencing-the-ado-libraries-in-a-visual-basic-6-application"></a>Verweis auf die ADO-Bibliotheken in Visual Basic 6 -Anwendungen
Wenn Sie die ADO-Bibliotheken in eine Microsoft Visual Basic 6-Anwendung importieren möchten, müssen Sie im Visual Basic-Projekt einen Verweis festlegen.  
  
### <a name="to-set-a-reference-to-the-ado-libraries-in-a-visual-basic-project"></a>So legen Sie einen Verweis auf die ADO-Bibliotheken in einem Visual Basic Projekt fest  
  
1.  Erstellen Sie ein neues, oder öffnen Sie ein vorhandenes Visual Basic Projekt.  
  
2.  Klicken Sie auf das Menü Element **Projekt** , und wählen Sie dann im Dropdown Menübereich die Option **Verweise** aus.  
  
3.  Aktivieren Sie das Kontrollkästchen für die **Bibliothek "Microsoft ActiveX Data Objects *n. n* ** **", wobei**" ***n. n*** " die aktuelle Versionsnummer darstellt. Das Feld "Location" ( **Speicherort** ) sollte als *$installDir\msado15.dll*ausgewählt werden, wobei *$installDir* den Pfad des Verzeichnisses darstellt, in dem die ADO-Bibliothek installiert wurde.  
  
4.  Wenn Sie ADO MD verwenden möchten, wiederholen Sie Schritt 3, um die **Bibliothek "Microsoft ActiveX Data Objects (mehrdimensional) *n. n* **" auszuwählen. Im Feld **Speicherort** sollte diese Auswahl als *$installDir\msadomd.dll*identifiziert werden.  
  
5.  Wenn Sie ADOX verwenden möchten, wiederholen Sie Schritt 3, um **Microsoft ADO Ext. *n. n* für DDL und Sicherheit**auszuwählen. Im Feld **Speicherort** sollte diese Auswahl als *$installDir\msadox.dll*identifiziert werden.  
  
6.  Klicken Sie auf **OK** , um das Festlegen der Verweise abzuschließen.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Bei der Installation von ADO werden auch die folgenden Typbibliotheken früherer Versionen kopiert:  
  
-   *msado27. tlb*, ADO 2,7-Typbibliothek  
  
-   *msado26. tlb*, ADO 2,6-Typbibliothek  
  
-   *msado25. tlb*, ADO 2,5-Typbibliothek  
  
-   *MSADO21. tlb*, ADO 2,1-Typbibliothek  
  
-   *msado20. tlb*, ADO 2,0-Typbibliothek  
  
 Wenn Ihre Anwendung diese ADO-Bibliotheken aus Gründen der Abwärtskompatibilität verwenden muss, müssen Sie die entsprechende Version der Typbibliothek importieren. Befolgen Sie hierzu die Schritte im vorherigen Abschnitt, indem Sie *msado15.dll* durch *msadoxx. tlb*ersetzen, wobei *xx* die Versionsnummer darstellt, die Sie importieren müssen.
