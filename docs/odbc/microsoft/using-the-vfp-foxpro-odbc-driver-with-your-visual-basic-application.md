---
title: Verwenden Sie den VFP FoxPro ODBC-Treiber mit Ihrer Visual Basic-Anwendung | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 871c392166fa2f5726e6f9e8651bf758dc144a00
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292700"
---
# <a name="using-the-vfp-foxpro-odbc-driver-with-your-visual-basic-application"></a>Verwenden des VFP FoxPro-ODBC-Treibers mit Ihrer Visual Basic-Anwendung
Ihre Microsoft® Visual Basic®-Anwendung kann mit Visual FoxPro-Daten kommunizieren, indem Sie ein Datensteuerelement erstellen, das eine Verbindung mit einer Visual FoxPro-Datenquelle herstellt.  
  
#### <a name="to-connect-to-visual-foxpro-data-using-the-data-control-in-visual-basic"></a>So stellen Sie eine Verbindung mit Visual FoxPro-Daten über das Datensteuerelement in Visual Basic her  
  
1.  Erstellen Sie eine Datenquelle mit dem Namen "test", die eine Verbindung mit der in Visual FoxPro enthaltenen TasTrade-Beispieldatenbank herstellt. Die standardmäßige Visual FoxPro-Installation platziert die TasTrade-Beispieldatenbank an der Position:  
  
    ```  
    c:\vfp\samples\mainsamp\data\tastrade.dbc  
    ```  
  
2.  Erstellen Sie in Visual Basic ein neues Formular, und platzieren Sie ein Textfeld und ein Datensteuerelement darauf.  
  
3.  Ändern Sie die Connect-Eigenschaft des Datensteuerelements wie folgt:  
  
    ```  
    ODBC;DATABASE=tastrade;DSN=test  
    ```  
  
4.  Ändern Sie die RecordsetType-Eigenschaft in Folgendes:  
  
    ```  
    2 - Snapshot  
    ```  
  
5.  Ändern Sie die RecordSource-Eigenschaft in Folgendes:  
  
    ```  
    customer  
    ```  
  
6.  Ändern Sie die DataSource-Eigenschaft für das Textfeld in den Standardnamen für das Datensteuerelement wie folgt:  
  
    ```  
    data1  
    ```  
  
7.  Ändern Sie die DataField-Eigenschaft des Textfelds in Folgendes:  
  
    ```  
    customer_id  
    ```  
  
8.  Führen Sie das Formular aus, und verwenden Sie das Datensteuerelement, um die Felder der Kunden-ID aus der Visual FoxPro TasTrade-Beispieldatenbank zu überspringen.
