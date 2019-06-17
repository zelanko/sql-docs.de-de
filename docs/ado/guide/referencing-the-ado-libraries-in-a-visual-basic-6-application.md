---
title: Verweis auf die ADO-Bibliotheken In Visual Basic 6-Anwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- libraries [ADO]
- referencing libraries in a Visual Basic application[ADO]
- ADO, libraries
ms.assetid: cfd37a82-aad2-41cd-8d13-1566c43d95f0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 80385161bcfce2c4b39ec9fa1257358cabe5f98c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704378"
---
# <a name="referencing-the-ado-libraries-in-a-visual-basic-6-application"></a>Verweis auf die ADO-Bibliotheken in Visual Basic 6 -Anwendungen
Um die ADO-Bibliotheken in einer Microsoft Visual Basic 6-Anwendung zu importieren, müssen Sie einen Verweis in Visual Basic-Projekt festlegen.  
  
### <a name="to-set-a-reference-to-the-ado-libraries-in-a-visual-basic-project"></a>So legen Sie einen Verweis auf die ADO-Bibliotheken in Visual Basic-Projekt fest  
  
1.  Erstellen Sie ein neues oder öffnen Sie ein vorhandenes Visual Basic-Projekt.  
  
2.  Klicken Sie auf die **Projekt** Menüelement, und wählen Sie dann **Verweise...**  aus dem Dropdown-Menü-Bereich.  
  
3.  Von **Verfügbare Verweise**, aktivieren Sie das Kontrollkästchen **Microsoft ActiveX Data Objects *ist n.n* Bibliothek**, wobei ***ist n.n*** stellt dar, die neueste Version die Versionsnummer. Die **Speicherort** Feld darunter sollten Identifizieren Ihrer Wahl als *$installDir\msado15.dll*, wobei *$installDir* steht für den Pfad des Verzeichnisses, in dem die ADO-Bibliothek wurde installiert.  
  
4.  Wenn Sie ADO MD verwenden möchten, wiederholen Sie Schritt 3 auf **Microsoft ActiveX Data Objects (Multi-dimensional) *ist n.n* Bibliothek**. Die **Speicherort** Feld sollte diese Option als identifiziert *$installDir\msadomd.dll*.  
  
5.  Wenn Sie ADOX verwenden möchten, wiederholen Sie Schritt 3 auf **Microsoft ADO automatischer *ist n.n* für DDL-Befehle und Sicherheit**. Die **Speicherort** Feld sollte diese Option als identifiziert *$installDir\msadox.dll*.  
  
6.  Klicken Sie auf **OK** zum Festlegen der Verweise.  
  
## <a name="backward-compatibility"></a>Backward Compatibility  
 Installieren von ADO wird außerdem die folgenden Typbibliotheken früherer Versionen kopiert:  
  
-   *msado27.tlb*, ADO 2.7 Typbibliothek.  
  
-   *msado26.tlb*, ADO 2.6-Typbibliothek  
  
-   *msado25.tlb*, ADO-2,5-Typbibliothek  
  
-   *MSADO21.tlb*, ADO 2.1 Typbibliothek.  
  
-   *msado20.tlb*, ADO-2.0-Typbibliothek  
  
 Wenn Ihre Anwendung diese ADO-Bibliotheken aus Gründen der Abwärtskompatibilität verwenden muss, müssen Sie die entsprechende Version der Typbibliothek zu importieren. Zu diesem Zweck die Schritte im vorherigen Abschnitt, und Ersetzen Sie dabei *"MSADO15.dll"* von *msadoXX.tlb*, wobei *XX* stellt die Versionsnummer, die Sie importieren möchten.
