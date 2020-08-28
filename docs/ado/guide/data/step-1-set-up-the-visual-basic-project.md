---
description: 'Schritt 1: Einrichten des Visual Basic-Projekts'
title: 'Schritt 1: Einrichten des Visual Basic Projekts | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 77d3bfa5-fc9f-4a72-93b4-790c7d227988
author: rothja
ms.author: jroth
ms.openlocfilehash: 7c0c8208fa8e5352a720ef057bb54d2d0b51b923
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979541"
---
# <a name="step-1-set-up-the-visual-basic-project"></a>Schritt 1: Einrichten des Visual Basic-Projekts
In diesem Szenario wird davon ausgegangen, dass Sie Microsoft Visual Basic 6,0, ADO 2,5 oder höher und den Microsoft OLE DB-Anbieter für die Internet Veröffentlichung auf Ihrem System installiert haben. Erstellen Sie zunächst ein neues Projekt, und fügen Sie dann dem Standardformular im Projekt einige Steuerelemente hinzu.  
  
### <a name="to-create-an-ado-project"></a>So erstellen Sie ein ADO-Projekt:  
  
1.  Erstellen Sie in Microsoft Visual Basic ein neues Standard-EXE-Projekt.  
  
2.  Wählen Sie im Menü Projekt die Option Verweise aus.  
  
3.  Wählen Sie "Microsoft ActiveX Data Objects 2,5 Library" aus, und klicken Sie auf OK.  
  
### <a name="to-insert-controls-on-the-main-form"></a>So fügen Sie Steuerelemente in das Hauptformular ein:  
  
1.  Fügen Sie ein ListBox-Steuerelement zu Form1 hinzu. Legen Sie die Name-Eigenschaft auf **lstMain**fest.  
  
2.  Fügen Sie Form1 ein weiteres ListBox-Steuerelement hinzu. Legen Sie die Name-Eigenschaft auf **lstdetails**fest.  
  
3.  Fügen Sie Form1 ein TextBox-Steuerelement hinzu. Legen Sie die Name-Eigenschaft auf **TxtDetails**fest.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Szenario für die Internet Veröffentlichung](../../../ado/guide/data/internet-publishing-scenario.md)   
 [Schritt 2: Initialisieren des Listenfelds „Main“](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)
