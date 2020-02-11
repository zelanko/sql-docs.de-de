---
title: 'Schritt 2: Initialisieren des Haupt Listen Felds | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: a1454493-1c86-46c2-ada8-d3c6fcdaf3c1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8ad89d806f8a6774cb0fe2de056e30fd274a517c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924086"
---
# <a name="step-2-initialize-the-main-list-box"></a>Schritt 2: Initialisieren des Listenfelds „Main“
Um globale Datensatz-und Recordset-Objekte zu deklarieren, fügen Sie den folgenden Code in (allgemein) (Deklarationen) für Form1 ein:  
  
```  
Option Explicit  
Dim grec As Record  
Dim grs As Recordset  
```  
  
 Dieser Code deklariert globale Objekt Verweise für Datensatz-und Recordset-Objekte, die später in diesem Szenario verwendet werden.  
  
## <a name="to-connect-to-a-url-and-populate-lstmain"></a>So stellen Sie eine Verbindung mit einer URL her und füllen lstMain auf  
 Fügen Sie den folgenden Code in den Ereignishandler für die Ereignis Behandlung für Form1 ein:  
  
```  
Private Sub Form_Load()  
    Set grec = New Record  
    Set grs = New Recordset  
    grec.Open "", "URL=https://servername/foldername/", , _  
        adOpenIfExists Or adCreateCollection  
    Set grs = grec.GetChildren  
    While Not grs.EOF  
        lstMain.AddItem grs(0)  
        grs.MoveNext  
    Wend  
End Sub  
```  
  
 Dieser Code instanziiert die globalen Datensatz-und Recordset-Objekte. Das Daten Satz Objekt `grec`,, wird mit einer URL geöffnet, die als ActiveConnection angegeben ist. Wenn die URL vorhanden ist, wird Sie geöffnet. Wenn Sie nicht bereits vorhanden ist, wird Sie erstellt. Beachten Sie, dass Sie "<https://servername/foldername/>" durch eine gültige URL aus Ihrer Umgebung ersetzen sollten.  
  
 Das Recordset-Objekt `grs`,, wird für die untergeordneten Elemente des Daten `grec`Satzes geöffnet,. Anschließend `lstMain` wird mit den Dateinamen der Ressourcen aufgefüllt, die in der URL veröffentlicht werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Szenario für die Internet Veröffentlichung](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Schritt 1: Einrichten des Visual Basic Projekts](../../../ado/guide/data/step-1-set-up-the-visual-basic-project.md)   
 [Schritt 3: Auffüllen des Listenfelds „Fields“](../../../ado/guide/data/step-3-populate-the-fields-list-box.md)
