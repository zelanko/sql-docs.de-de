---
title: Verwenden des VFP FoxPro-ODBC-Treibers mit Ihrer Visual Basic Anwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], visual basic applications
- Visual Basic applications [ODBC]
- FoxPro ODBC driver [ODBC], visual basic applications
- Visual FoxPro data [ODBC], visual basic applications
ms.assetid: 5223ca23-5df6-4ebc-aa3b-70682ff27a8c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 017e8e7897b2b792d7a864dc336537d76dcad8b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "68087979"
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Verwenden des VFP FoxPro-ODBC-Treibers mit Ihrer Visual Basic-Anwendung
Die Microsoft® Visual Basic®-Anwendung kann mit Visual FoxPro-Daten kommunizieren, indem ein Daten Steuerelement erstellt wird, das eine Verbindung mit einer Visual FoxPro-Datenquelle herstellt.  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>So stellen Sie mithilfe des Daten Steuer Elements in eine Verbindung mit Visual FoxPro-Daten her Visual Basic  
  
1.  Erstellen Sie eine Datenquelle mit dem Namen "Test", die eine Verbindung mit der in Visual FoxPro enthaltenen Beispieldatenbank "Tastrade" herstellt. In der Standardinstallation von Visual FoxPro wird die Beispieldatenbank "Tastrade" am Speicherort angezeigt:  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  Erstellen Sie in Visual Basic ein neues Formular, und platzieren Sie ein Textfeld und ein Daten Steuerelement.  
  
3.  Ändern Sie die Connect-Eigenschaft des Daten Steuer Elements wie folgt:  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  Ändern Sie die Eigenschaft RecordsetType in Folgendes:  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  Ändern Sie die Eigenschaft RecordSource in Folgendes:  
  
    ```  
    customer  
    ```  
  
6.  Ändern Sie die DataSource-Eigenschaft für das Textfeld in den Standardnamen für das Daten Steuerelement wie folgt:  
  
    ```  
    data1  
    ```  
  
7.  Ändern Sie die Datin-Eigenschaft des Textfelds wie folgt:  
  
    ```  
    customer_id  
    ```  
  
8.  Führen Sie das Formular aus, und verwenden Sie das Daten Steuerelement, um die Felder Customer ID aus der Beispieldatenbank Visual FoxPro Tastrade zu überspringen.
