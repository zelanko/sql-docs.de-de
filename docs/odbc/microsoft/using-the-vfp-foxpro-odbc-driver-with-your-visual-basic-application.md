---
title: Verwenden des VFP FoxPro-ODBC-Treibers mit Visual Basic-Anwendung | Microsoft-Dokumentation
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
manager: craigg
ms.openlocfilehash: 4b77fdee70ff73772710c9758eeb2bf2594f365d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2018
ms.locfileid: "47697880"
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Verwenden des VFP FoxPro-ODBC-Treibers mit Ihrer Visual Basic-Anwendung
Ihr Microsoft® Visual Basic®-Anwendung kann mit Visual FoxPro-Daten kommunizieren, indem Sie ein Steuerelement die Verbindung mit einer Visual FoxPro-Datenquelle erstellen.  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>Verbindung mit Visual FoxPro-Daten, die über das Steuerelement in Visual Basic  
  
1.  Erstellen Sie eine Datenquelle mit dem Namen "test" die Verbindung mit der TasTrade-Beispieldatenbank, die im Visual FoxPro enthalten. Die Visual FoxPro-Standardinstallation fügt die TasTrade-Beispieldatenbank, an der Position:  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  Klicken Sie in Visual Basic erstellen ein neues Formular, und platzieren Sie ein Textfeld und ein Steuerelement auf.  
  
3.  Ändern Sie die Connect-Eigenschaft des Steuerelements wie folgt:  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  Ändern der Eigenschaft Recordsettyp wie folgt:  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  Ändern Sie die Datenherkunft-Eigenschaft wie folgt aus:  
  
    ```  
    customer  
    ```  
  
6.  Ändern Sie die DataSource-Eigenschaft für das Textfeld, in der Standardname für das Steuerelement die folgenden:  
  
    ```  
    data1  
    ```  
  
7.  Ändern Sie das Textfeld DataField-Eigenschaft wie folgt aus:  
  
    ```  
    customer_id  
    ```  
  
8.  Führen Sie das Formular, und verwenden Sie das Steuerelement über die Felder der Kunden-Id aus der Visual FoxPro-TasTrade-Beispieldatenbank zu überspringen.
