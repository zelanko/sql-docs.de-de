---
title: 'HelloData: Eine einfache ADO-Anwendung | Microsoft-Dokumentation'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- HelloData sample application [ADO]
- ADO, samples
ms.assetid: de4bcd56-dac2-45e6-95ab-9fd7f25878fc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 97957adf53cfea64693530b79920dd54d6d0a1bf
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700637"
---
# <a name="hellodata-a-simple-ado-application"></a>HelloData: Eine einfache ADO-Anwendung
Diese einfache Anwendung führt in jeder der vier wichtigsten ADO-Vorgänge: Abrufen, untersuchen, bearbeiten und Aktualisieren von Daten. Diese Vorgänge werden mit der Northwind-Beispieldatenbank, die in Microsoft® SQL Server enthalten. Im Beispiel für die Fehlerbehandlung ist minimal, die sich auf den Grundlagen von ADO und Übersichtlichkeit des Code zu verhindern.  
  
### <a name="to-run-hellodata"></a>Ausführen von HelloData  
  
1.  Erstellen Sie ein neues Standard-EXE-Datei Visual Basic-Projekt, das die ADO-Bibliothek verweist. Weitere Informationen finden Sie unter [verweisen auf die ADO-Bibliotheken](../../../ado/guide/referencing-the-ado-libraries.md).  
  
2.  Erstellen Sie vier Schaltflächen oben auf der das Formular, setzen die **Namen** und **Beschriftung** Eigenschaften mit den Werten in der Tabelle am Ende dieses Themas aufgeführt.  
  
3.  Fügen Sie unterhalb der Schaltflächen, eine **Microsoft DataGrid Control** (Msdatgrd.ocx). Die Msdatgrd.ocx-Datei ist im Lieferumfang von Visual Basic und befindet sich in Ihrem Verzeichnis \windows\system32 oder \winnt\system32. Wählen Sie zum Hinzufügen des DataGrid-Steuerelements in Ihre Visual Basic-Toolbox-Bereich **Komponenten...**  aus der **Projekt** Menü. Aktivieren Sie das Kontrollkästchen neben "Microsoft DataGrid Control 6.0 (SP3) (OLEDB)", und klicken Sie dann auf **OK**. Zum Hinzufügen des Steuerelements auf das Projekt, ziehen Sie das DataGrid-Steuerelement aus der Toolbox auf das Visual Basic-Formular.  
  
4.  Erstellen Sie eine **Textfeld** auf dem Formular unter dem Raster und seine Eigenschaften festlegen, wie in der Tabelle dargestellt. Das Formular sollte in der folgende Abbildung ähneln, wenn Sie fertig sind.  
  
5.  Schließlich kopieren Sie den Code in [HelloData-Code](../../../ado/guide/data/hellodata-code.md), und fügen Sie ihn in das Fenster des Code-Editor des Formulars. Drücken Sie **F5** um den Code auszuführen.  
  
> [!NOTE]
>  Im folgenden Beispiel und in der Anleitung ist die Benutzer-Id "Meine-ID" mit dem Kennwort "123abc" verwendet, um die Authentifizierung auf dem Server. Sie sollten diese Werte mit gültigen Anmeldeinformationen für den Server ersetzen. Ersetzen Sie außerdem den Wert "MySQLServer" mit dem Namen Ihres Servers.  
  
 Eine detaillierte Beschreibung des Codes, finden Sie unter [Kommentare zur HelloData](../../../ado/guide/data/comments-on-hellodata.md).  
  
 ![Zeigt Form1 für die HelloData VB-Anwendung](../../../ado/guide/data/media/hellodata.gif "HelloData")  
  
|Steuerelementtyp|Eigenschaft|Wert|  
|------------------|--------------|-----------|  
|Form|Name|Form1|  
||Höhe|6500|  
||Breite|6500|  
|MS-DataGrid|Name|grdDisplay1|  
|TextBox|Name|txtDisplay1|  
||Multiline|true|  
|Schaltfläche "Befehl"|Name|cmdGetData|  
||Beschriftung|Get Data|  
|Schaltfläche "Befehl"|Name|cmdExamineData|  
||Beschriftung|Untersuchen von Daten|  
|Schaltfläche "Befehl"|Name|cmdEditData|  
||Beschriftung|Bearbeiten von Daten|  
|Schaltfläche "Befehl"|Name|cmdUpdateData|  
||Beschriftung|Aktualisierungsdaten|
